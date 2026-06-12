---
title: "What is amdgpu and amdgpu-PRO drivers? and where to download?"
date: 2020-05-23
forum: General Help
---

### Post by demoncloud on 2020-05-23
I heard that amdgpu-PRO is not as good as amdgpu for gaming only certain situation where PRO is better. I'm not sure if this is true. 
 I don't plan to play games on linux, but I want to develop games with game engines. I work with Unity before and a bit of Unreal on Windows.


I know amdgpu-PRO drivers is at amd's official site. I don't know where to get amdgpu.

---

### Post by CatKiller on 2020-05-23
> **demoncloud said:**
> I know amdgpu-PRO drivers is at amd's official site. I don't know where to get amdgpu.

You already have it, and it's enabled by default on newer cards. Old cards can't use amdgpu and use radeon instead. There are some cards in between that *could* use amdgpu, but it's experimental, so they default to radeon.

---

### Post by JakcV on 2020-05-23
If you want to enable support for Open-GL & Open-CL, need to get the amdgpu-Pro driver from AMD website. 

Installation instruction
[https://amdgpu-install.readthedocs.io/en/latest/]("https://amdgpu-install.readthedocs.io/en/latest/")

---

### Post by CatKiller on 2020-05-23
> **JakcV said:**
> If you want to enable support for Open-GL & Open-CL, need to get the amdgpu-Pro driver from AMD website. 

Installation instruction
[https://amdgpu-install.readthedocs.io/en/latest/]("https://amdgpu-install.readthedocs.io/en/latest/")

Amdgpu handles OpenGL just fine: they are the same driver, but amdgpu-pro has some propriety shaders. You do need some parts of amdgpu-pro for OpenCL currently, but not the whole driver; you can just extract the bits you need.

---

### Post by Yellow Pasque on 2020-05-23
> I don't plan to play games on linux, but I want to develop games with game engines.

I personally wouldn't mess with the PRO driver for that. But if you do experiment, beware that the latest PRO driver does not support Ubuntu 20.04.
The only use I could see for the PRO driver in your situation is if I didn't have a Windows install to test on (and I was targeting Windows). Then, the PRO driver might be a good test since it shares 3D code with AMD's Windows driver.

---

### Post by demoncloud on 2020-05-23
Thanks all!

I forgot the add my specs. I'm running 16.04(Ubuntu Unity and Cinnamon) with Sapphire AMD RX 580.
I'll upgrade ubuntu(either cinnamon, mate, kylin, or dde) next year when they fix the bugs.

---

### Post by Kusho on 2020-05-26
> **CatKiller said:**
> Amdgpu handles OpenGL just fine: they are the same driver, but amdgpu-pro has some propriety shaders. You do need some parts of amdgpu-pro for OpenCL currently, but not the whole driver; you can just extract the bits you need.

I went to the AMD website and the only downloads I could find were the Windows ones.  I need the PRO drivers to run BOINC and get it to use my Radeon GPU.  I couldn't even find the PRO driver for 18.04.  Did they stop supporting Linux completely?

---

### Post by JakcV on 2020-05-26
I run FAH with the OpenCL driver, I didn't test with BOINC.

[https://www.amd.com/en/support/kb/release-notes/rn-amdgpu-unified-linux]("https://www.amd.com/en/support/kb/release-notes/rn-amdgpu-unified-linux")
should have a newer version 20.

---

### Post by Yellow Pasque on 2020-05-26
Latest version: [https://www.amd.com/en/support/kb/release-notes/rn-amdgpu-unified-linux-20-10](https://www.amd.com/en/support/kb/release-notes/rn-amdgpu-unified-linux-20-10)
Make sure your GPU is in the list of supported products!

---

### Post by mastablasta on 2020-05-27
In linux opensource drivers are (usually) built into kernel. AMDGPU: [https://help.ubuntu.com/community/AMDGPU-Driver](https://help.ubuntu.com/community/AMDGPU-Driver)

proprietary drivers are the only ones that need additional install.

---

