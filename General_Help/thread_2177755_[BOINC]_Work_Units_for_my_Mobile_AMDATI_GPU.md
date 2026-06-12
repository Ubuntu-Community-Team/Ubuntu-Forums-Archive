---
title: "[BOINC] Work Units for my Mobile AMD/ATI GPU"
date: 2013-09-30
forum: General Help
---

### Post by manoriax on 2013-09-30
Hello!

I just have a short question, which one of the people here will surely be able to answer correctly. So, I am travelling abroad right now and I have only got my laptop with me. When I am not working, I use all four CPU cores to crunch some work units for different BOINC projects. Now I would like to let my GPU crunch some, aswell, but it does not seem to work. Particularly, I am trying to get some GPU work units for PrimeGrid. I checked the box on the PrimeGrid website, telling the system to get me some GPU work and I also told the BOINC manager to use my GPU, even if the computer is being used. However, I do not get any work units for my GPU. Is this because I am on a mobile device?

Here are some console lines that might help:

```
phil@phil-laptop:~$ fglrxinfo
 display: :0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon HD 6400M Series
OpenGL version string: 4.2.12217 Compatibility Profile Context 12.104
```

```
phil@phil-laptop:~$ lspci | grep VGA
00:01.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI BeaverCreek [Radeon HD 6520G]
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Seymour [Radeon HD 6400M/7400M Series]
```

I just updated the AMD/ATI drivers, so I have the most recent version installed (it did not work with the old version, either). Also, I am using BOINC version 7.0.27.

I would be most grateful for any help offered. Thanks!

Kind regards,
manoriax

---

### Post by manoriax on 2013-09-30
Alright, I have the solution for my problem. I did not install[2] the AMD-APP-SDK[1]. After BOINC told me that there were no OpenCL-capable GPUs installed[3], a

```
sudo /etc/init.d/boinc-client restart
```

did the trick. It is working now.

[1] [http://developer.amd.com/tools-and-sdks/heterogeneous-computing/amd-accelerated-parallel-processing-app-sdk/](http://developer.amd.com/tools-and-sdks/heterogeneous-computing/amd-accelerated-parallel-processing-app-sdk/)
[2] [http://www.thebigblob.com/getting-started-with-opencl-and-gpu-computing/](http://www.thebigblob.com/getting-started-with-opencl-and-gpu-computing/)
[3] [https://bugs.launchpad.net/ubuntu/+source/boinc/+bug/1077316](https://bugs.launchpad.net/ubuntu/+source/boinc/+bug/1077316)

---

