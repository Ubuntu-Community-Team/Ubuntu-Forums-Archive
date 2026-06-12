---
title: "Do I need the 64 bit Ubuntu with a Intel B960"
date: 2013-07-19
forum: General Help
---

### Post by Derelinquat fenestras on 2013-07-19
Hello,

My wife just bought a new computer with the horrors of Windows 8 preinstalled, and from my research it seems that there is no straight path to Ubuntu bliss from Windows 8...  Anyway,  I'm looking to install Ubuntu 12.04.2 on it, but I'm not sure what version that I need the 32 or the 64 bit.  I has an Intel B960 2.2GHz processor... I looked up some product specs that said it has a 64 bit instruction set (???), but honestly, I don't know what that means.

On the download site for Ubuntu 12.04.2, it says:

> [64-bit PC (AMD64) desktop CD]("http://releases.ubuntu.com/precise/ubuntu-12.04.2-desktop-amd64.iso")Choose this to take full advantage of computers based on the AMD64 or EM64T architecture (e.g., Athlon64, Opteron, EM64T Xeon, Core 2). If you have a non-64-bit processor made by AMD, or if you need full support for 32-bit code, use the Intel x86 images instead.


So I'm not sure if the Intel is indeed a 64 bit processor or if I'll need full support for 64 bit code...

Can anyone make any recommendations, or explain to me the difference between the 32bit and the 64bit from a functionality standpoint?
 
Thanks!

---

### Post by Derelinquat fenestras on 2013-07-19
Also...  forgot to ask... and please forgive if this is an imbecilic question, but the downloads on the 12.04.2 page all say for "Desktop CD" etc... will I be able to make a bootable USB from them?

---

### Post by howefield on 2013-07-19
You can use either the 32 bit or the 64 bit, I'd recommend 64 bit.

And yes, you can build a bootable USB from it.

---

### Post by Derelinquat fenestras on 2013-07-19
Thank you!

Can you tell me a little about the differences between the 64 and 32 bit systems?

I've only ever used the 32...

---

### Post by grahammechanical on 2013-07-19
As I understand you would have to use Ubuntu 64 bit for installing on a machine with Windows 8. You really do need to study this.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

So, you want to be confused by science, do you? I will offer a mostly likely inaccurate explanation. Computer Processing Units (CPU) run instructions. Each instruction is thought of as a word. Over the decades the words have increased in size from 4 bits to 8 bits and on to 16 bits, 32 bits and 64 bits. A unit of digital information is called a byte and 8 bits make up one byte. So, a CPU that processes 16 bits at a time will do more work than a CPU that processes 8 bits at a time.

Intel became the design leader of CPUs for the IMB Personal Computer (PC) with the introduction of the Intel 8086 CPU with its x86 instruction set. Intel's first 32 bit CPU to be released was the 80386. It was also known as i386. Rival chip manufacturers, such as AMD were able to produce their own CPUs that ran the same x86 instruction set as the Intel 80386. And they were often as powerful and certainly cheaper than Intel's CPUs

Linux kernels that run on 32 bit CPUs using the x86 instruction set are called i386. So, we have an ISO image of Ubuntu called i386 or 32 bit or Intel x86 that runs on both Intel and AMD 32 bit CPUs.

AMD brought out a CPU that could run 64 bit x86 instructions before Intel. So, we have a Ubuntu ISO image called amd64 or 64 bit that also runs on both Intel and AMD 64 bit CPUs. I am running an Intel 64 bit Core2 Duo CPU and I am using Ubuntu amd64 ISO image.

For the record, Ubuntu 32 bit will run on both 32 bit and 64 bit CPUs but Ubuntu 64 bit will only run on 64 bit CPUs.

With Windows 8 installed you need 64 bit Ubuntu and at least 12.04.2. The original 12.04 could not deal with secure boot. Ubuntu 12.10 was the first Linux distribution that could install on a machine that was secure boot enabled. Almost six months ago 12.04 got its second point release (12.04.2) and that came with the signed kernel image that is necessary for secure boot enabled machines. As the link that I gave you says, the Ubuntu 32 bit installer cannot deal with EFI boot systems. This is the next step up from the BIOS boot system. So, all things considered - go for 64 bit.

Regards.

---

### Post by Derelinquat fenestras on 2013-07-19
Thank you for all of the info!  That was great!

Successfully got the 12.04.2 installed and the system works great!

I appreciate all of the advice

---

