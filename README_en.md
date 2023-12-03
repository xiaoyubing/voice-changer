## VC Client

[Japanese](/README_ja.md) [Korean](/README_ko.md)

## What's New!
- v.1.5.3.17b
  - bugfix:
    - clear setting
  - improve
    - file sanitizer
  - chage:
    - default input chunk size: 192.
      - decided by this chart.(https://rentry.co/VoiceChangerGuide#gpu-chart-for-known-working-chunkextra)

- v.1.5.3.17a
  - Bug Fixes:
    - Server mode error
    - RVC Model merger
  - Misc
    - Add RVC Sample Chihaya-Jinja (https://chihaya369.booth.pm/items/4701666)

- v.1.5.3.17
  - New Features:
    - Added similarity graph for Beatrice speaker selection 
  - Bug Fixes:
    - Fixed crossfade issue with Beatrice speaker

- v.1.5.3.16a
  - Bug fix:
    - Lazy load Beatrice.


- v.1.5.3.16 (Only for Windows, CPU dependent)
  - New Feature:
    - Beatrice is supported(experimental) 

- v.1.5.3.15
  - Improve:
    - new rmvpe checkpoint for rvc (torch, onnx)
    - Mac: upgrade torch version 2.1.0


# What is VC Client

1. This is a client software for performing real-time voice conversion using various Voice Conversion (VC) AI. The supported AI for voice conversion are as follows.

- [MMVC](https://github.com/isletennos/MMVC_Trainer)
- [so-vits-svc](https://github.com/svc-develop-team/so-vits-svc)
- [RVC(Retrieval-based-Voice-Conversion)](https://github.com/liujing04/Retrieval-based-Voice-Conversion-WebUI)
- [DDSP-SVC](https://github.com/yxlllc/DDSP-SVC)
- [Beatrice JVS Corpus Edition](https://prj-beatrice.com/) * experimental,  (***NOT MIT Licnsence*** see [readme](https://github.com/w-okada/voice-changer/blob/master/server/voice_changer/Beatrice/)) *  Only for Windows, CPU dependent

1. Distribute the load by running Voice Changer on a different PC
   The real-time voice changer of this application works on a server-client configuration. By running the MMVC server on a separate PC, you can run it while minimizing the impact on other resource-intensive processes such as gaming commentary.

![image](https://user-images.githubusercontent.com/48346627/206640768-53f6052d-0a96-403b-a06c-6714a0b7471d.png)

3. Cross-platform compatibility
   Supports Windows, Mac (including Apple Silicon M1), Linux, and Google Colaboratory.

# usage

This is an app for performing voice changes with MMVC and so-vits-svc.

It can be used in two main ways, in order of difficulty:

- Using a pre-built binary
- Setting up an environment with Docker or Anaconda and using it

## (1) Usage with pre-built binaries

- You can download and run executable binaries.

- Please see [here](tutorials/tutorial_rvc_en_latest.md) for the tutorial. ([troubule shoot](https://github.com/w-okada/voice-changer/blob/master/tutorials/trouble_shoot_communication_ja.md))

- It's now easy to try it out on [Google Colaboratory](https://github.com/w-okada/voice-changer/blob/master/Realtime_Voice_Changer_on_Colab.ipynb) (requires a ngrok account). You can launch it from the 'Open in Colab' button in the top left corner.

<img src="https://github.com/w-okada/voice-changer/assets/48346627/3f092e2d-6834-42f6-bbfd-7d389111604e" width="400" height="150">

- We offer Windows and Mac versions.

  - If you are using a Windows and Nvidia GPU, please download ONNX (cpu, cuda), PyTorch (cpu, cuda).
  - If you are using a Windows and AMD/Intel GPU, please download ONNX (cpu, DirectML) and PyTorch (cpu, cuda). AMD/Intel GPUs are only enabled for ONNX models.
  - In either case, for GPU support, PyTorch and Onnxruntime are only enabled if supported.
  - If you are not using a GPU on Windows, please download ONNX (cpu, cuda) and PyTorch (cpu, cuda).

- For Windows user, after unzipping the downloaded zip file, please run the `start_http.bat` file corresponding to your VC.

- For Mac version, after unzipping the downloaded file, double-click the `startHttp.command` file corresponding to your VC. If a message indicating that the developer cannot be verified is displayed, please press the control key and click to run it again (or right-click to run it).

- If you are connecting remotely, please use the `.command` file (Mac) or `.bat` file (Windows) with https instead of http.

- The encoder of DDPS-SVC only supports hubert-soft.

- Download (When you cannot download from google drive, try [hugging_face](https://huggingface.co/wok000/vcclient000/tree/main))

| Version     | OS  | Framework                             | link                                                                | support VC                                                                          | size   |
| ----------- | --- | ------------------------------------- | ------------------------------------------------------------------- | ----------------------------------------------------------------------------------- | ------ |
| v.1.5.3.17b | mac | ONNX(cpu), PyTorch(cpu,mps)           | [hugging face](https://huggingface.co/wok000/vcclient000/tree/main) | MMVC v.1.5.x, MMVC v.1.3.x, so-vits-svc 4.0, RVC                                    | 797MB  |
|             | win | ONNX(cpu,cuda), PyTorch(cpu,cuda)     | [hugging face](https://huggingface.co/wok000/vcclient000/tree/main) | MMVC v.1.5.x, MMVC v.1.3.x, so-vits-svc 4.0, RVC, DDSP-SVC, Diffusion-SVC, Beatrice | 3240MB |
|             | win | ONNX(cpu,DirectML), PyTorch(cpu,cuda) | [hugging face](https://huggingface.co/wok000/vcclient000/tree/main) | MMVC v.1.5.x, MMVC v.1.3.x, so-vits-svc 4.0, RVC, DDSP-SVC, Diffusion-SVC, Beatrice | 3125MB |
| v.1.5.3.16a | mac | ONNX(cpu), PyTorch(cpu,mps)           | N/A                                                                 | MMVC v.1.5.x, MMVC v.1.3.x, so-vits-svc 4.0, RVC                                    | 797MB  |
|             | win | ONNX(cpu,cuda), PyTorch(cpu,cuda)     | [hugging face](https://huggingface.co/wok000/vcclient000/tree/main) | MMVC v.1.5.x, MMVC v.1.3.x, so-vits-svc 4.0, RVC, DDSP-SVC, Diffusion-SVC, Beatrice | 3240MB |
|             | win | ONNX(cpu,DirectML), PyTorch(cpu,cuda) | [hugging face](https://huggingface.co/wok000/vcclient000/tree/main) | MMVC v.1.5.x, MMVC v.1.3.x, so-vits-svc 4.0, RVC, DDSP-SVC, Diffusion-SVC, Beatrice | 3125MB |
| v.1.5.3.15  | mac | ONNX(cpu), PyTorch(cpu,mps)           | [hugging face](https://huggingface.co/wok000/vcclient000/tree/main) | MMVC v.1.5.x, MMVC v.1.3.x, so-vits-svc 4.0, RVC                                    | 797MB  |
|             | win | ONNX(cpu,cuda), PyTorch(cpu,cuda)     | [hugging face](https://huggingface.co/wok000/vcclient000/tree/main) | MMVC v.1.5.x, MMVC v.1.3.x, so-vits-svc 4.0, RVC, DDSP-SVC, Diffusion-SVC           | 3240MB |
|             | win | ONNX(cpu,DirectML), PyTorch(cpu,cuda) | [hugging face](https://huggingface.co/wok000/vcclient000/tree/main) | MMVC v.1.5.x, MMVC v.1.3.x, so-vits-svc 4.0, RVC, DDSP-SVC, Diffusion-SVC           | 3125MB |

(\*1) You can also download from [hugging_face](https://huggingface.co/wok000/vcclient000/tree/main)
(\*2) The developer does not have an AMD graphics card, so it has not been tested. This package only includes onnxruntime-directml.
(\*3) If unpacking or starting is slow, there is a possibility that virus checking is running on your antivirus software. Please try running it with the file or folder excluded from the target. (At your own risk)

## (2) Usage after setting up the environment such as Docker or Anaconda

Clone this repository and use it. Setting up WSL2 is essential for Windows. Additionally, setting up virtual environments such as Docker or Anaconda on WSL2 is also required. On Mac, setting up Python virtual environments such as Anaconda is necessary. Although preparation is required, this method works the fastest in many environments. **<font color="red"> Even without a GPU, it may work well enough with a reasonably new CPU </font>(refer to the section on real-time performance below)**.

[Explanation video on installing WSL2 and Docker](https://youtu.be/POo_Cg0eFMU)

[Explanation video on installing WSL2 and Anaconda](https://youtu.be/fba9Zhsukqw)

To run docker, see [start docker](docker_vcclient/README_en.md).

To run on Anaconda venv, see [server developer's guide](README_dev_en.md)

To run on Linux using an AMD GPU, see [setup guide linux](tutorials/tutorial_anaconda_amd_rocm.md)

# Real-time performance

Conversion is almost instantaneous when using GPU.

https://twitter.com/DannadoriYellow/status/1613483372579545088?s=20&t=7CLD79h1F3dfKiTb7M8RUQ

Even with CPU, recent ones can perform conversions at a reasonable speed.

https://twitter.com/DannadoriYellow/status/1613553862773997569?s=20&t=7CLD79h1F3dfKiTb7M8RUQ

With an old CPU (i7-4770), it takes about 1000 msec for conversion.

# Software Signing

This software is not signed by the developer. A warning message will appear, but you can run the software by clicking the icon while holding down the control key. This is due to Apple's security policy. Running the software is at your own risk.

![image](https://user-images.githubusercontent.com/48346627/212567711-c4a8d599-e24c-4fa3-8145-a5df7211f023.png)

https://user-images.githubusercontent.com/48346627/212569645-e30b7f4e-079d-4504-8cf8-7816c5f40b00.mp4

# Acknowledgments

- [Tachizunda-mon materials](https://seiga.nicovideo.jp/seiga/im10792934)
- [Irasutoya](https://www.irasutoya.com/)
- [Tsukuyomi-chan](https://tyc.rei-yumesaki.net)

> This software uses the voice data of the free material character "Tsukuyomi-chan," which is provided for free by CV. Yumesaki Rei.
>
> - Tsukuyomi-chan Corpus (CV. Yumesaki Rei)
>
> https://tyc.rei-yumesaki.net/material/corpus/
>
> Copyright. Rei Yumesaki

- [Amitaro's Onsozai kobo](https://amitaro.net/)
- [Replica doll](https://kikyohiroto1227.wixsite.com/kikoto-utau)

# Terms of Use

In accordance with the Tsukuyomi-chan Corpus Terms of Use for the Tsukuyomi-chan Real-time Voice Changer, the use of the converted voice for the following purposes is prohibited.

- Criticizing or attacking individuals (the definition of "criticizing or attacking" is based on the Tsukuyomi-chan character license).

- Advocating for or opposing specific political positions, religions, or ideologies.

- Publicly displaying strongly stimulating expressions without proper zoning.

- Publicly disclosing secondary use (use as materials) for others.
  (Distributing or selling as a work for viewing is not a problem.)

Regarding the Real-time Voice Changer Amitaro, we prohibit the following uses in accordance with the terms of use of the Amitaro's koe-sozai kobo.[detail](https://amitaro.net/voice/faq/#index_id6)

Regarding the Real-time Voice Changer Kikoto Mahiro, we prohibit the following uses in accordance with the terms of use of Replica doll.[detail](https://kikyohiroto1227.wixsite.com/kikoto-utau/ter%EF%BD%8Ds-of-service)

# Disclaimer

We are not liable for any direct, indirect, consequential, incidental, or special damages arising out of or in any way connected with the use or inability to use this software.
