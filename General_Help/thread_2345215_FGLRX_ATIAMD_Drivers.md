---
title: "FGLRX ATI/AMD Drivers"
date: 2016-12-01
forum: General Help
---

### Post by gabers2004 on 2016-12-01
When will the fglrx driver be supported for Ubuntu 16.10 yakkety? I've been wanting to play saints row 4 for a while. Is there a website in which I can check such? 
If they ARE released, please give me info on how to install them
I have an R9 270X (AMD)
The ubuntu-common(additional drivers)package does not detect anything either, except for my CPU (amd4-microcode)

Thanks a lot!

---

### Post by QIII on 2016-12-01
Hello!

fglrx will not be available for 16.04 or beyond.  From 16.04 forward, the open source Radeon or AMDGPU driver will be installed at install time depending on the hardware you have.  This is part of AMD's process of completely revamping its driver support for Linux -- to provide what the Linux community has been asking for for years.

Also depending on your hardware, you may be able to install AMDGPU-PRO, which is the open source AMDGPU driver with a proprietary overlay providing better OpenCL support and Vulkan support.

I have compiled a current list of GPUs which will work with AMDGPU(-PRO) [here]("http://theleftcoastgeek.net/index.php/general-interest/11-amd-gpu-support-with-amdgpu-and-amdgpu-pro").

If your hardware is not listed there and it is GCN 1.0 or above, it will probably be supported soon.

---

### Post by gabers2004 on 2016-12-01
Ouch- Looks like my card isnt supported.
I remember installing this once and it detected my display as a 'laptop' and locked my resolution to 800x600.

---

### Post by QIII on 2016-12-01
It looks like there is experimental support for it (full support is coming) with kernel 4.9.

Are you interested in experimenting (and possibly breaking your OS)?

---

### Post by gabers2004 on 2016-12-01
Hah. I've installed the 4.9rc expiremental version by manually pulling it in.(stupid ubuntu). It simply gave me a black screen. I could try again with your help, or I could just wait. 

So what youre saying is that fglrx will be in kernel 4.9 so I can finaaly play some steam games, or that amdgpu is getting support in the kernel?

If all else fails, I do have a windows partition.

---

### Post by QIII on 2016-12-01
No.  fglrx will never be available again for Linux.  fglrx is dead and AMD is moving on with better Linux support as we have asked.  What I am saying is that your GPU is expected to be supported by AMDGPU(-PRO) in 4.9.

You might try 4.8 from Zesty (which I am running Xenial with right now to get AMDGPU-PRO and Vulkan support).  Then you could try adding the AMDGPU-PRO driver from [here]("http://support.amd.com/en-us/kb-articles/Pages/AMD-Radeon-GPU-PRO-Linux-Beta-Driver%E2%80%93Release-Notes.aspx") and then the Vulkan SDK .

One caveat:  I highly recommend adding yourself to the video group *before *installing AMDGPU-PRO so you don't forget.

But I'm not sure if that will work, given your GPU.

On my Zesty install, I am running AMDGPU-PRO and Vulkan SDK right out of the Ubuntu repo.  Like with fglrx, Canonical gets the candy first.  Then again, I have a supported card.

---

### Post by mastablasta on 2016-12-02
fglrx is still available on 14.04 (but not the higher versions) as it has the old kernel which can be patched. that or Windows. still a better choice for gaming i guess.

---

### Post by richardsdma on 2016-12-06
all the people are talking about discrete video cards, but what about the APUs? will they be supported? i own an e2-7110 apu on a laptop.

---

### Post by QIII on 2016-12-06
Some (most?) will.  I've been working on compiling a list of the GPUs that work and those that *may* work based on AMD's guidance.

Each APU has a GPU on-die, and the GPUs are generally in the named series.  So it might be possible to see what will and will not be supported.

For instance, most of the Kaveri APUs and the Carrizo APUs should be supported.  I don't know about earlier ones.

Yours is a Carrizo, so you may be in luck!  But we'll have to wait and see.

---

### Post by gabers2004 on 2016-12-06
Alright. I've managed to install the amdgpu pro driver. Honestly, I don't see a difference... is it activated by default? Or do I have to get the kernel to recognize it?
I may start a new thread on this topic

SO i Managed to install the amdgpu-pro proprietary driver on my R9 270X. Unfortunately I don't really see a preformance change... at all. Are they activated by default? Or do I have to get them to be recognized by the kernel? Thanks.

---

