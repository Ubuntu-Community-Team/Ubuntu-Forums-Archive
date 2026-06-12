---
title: "An simple way to run Android software in Ubuntu ?"
date: 2023-06-27
forum: General Help
---

### Post by aug7744 on 2023-06-27
Hello.
Thanks for reading my topic.
Here Lubuntu 20.04.6.
Have an simple secure way to run Android software in Ubuntu  ?
I only want run simple android software.
Have some software and even VirtualBox Android-X86 , but I not understand if is possible access the host 3G MODEM so having information about SIM cell card.

Have an nice week.

---

### Post by ian-weisser on 2023-06-27
Android software and Ubuntu software are generally incompatible. So there is no "simple way" to run "simple android software".

It's a bit like trying to fit the wrong type of tyre onto your bicycle. It's designed to use tyres...but it's not easily compatible with *that* tyre. Kludging it on will likely put you in a ditch, wasted effort.

Accessing hardware from a virtual machine requires cooperation of the VM host application and OS.

---

### Post by MAFoElffen on 2023-06-28
Well, I run android software on my test bed, but is actually running witin a KVM VM Guest running Andriod-x86 from android-x86.org It will also run in VirtualBox and VMware Player...

There was an Android Emulator that Canonical 'was' working on, called "Anbox", but the project died. It branched and turned into something else...

Currently, the Linux based Android Emulators that people seem to be using currently are Android-x86, Waydroid, Genymotion, Android Studio, Bliss OS and Anbox Cloud.

Anbox Cloud is what Canonical's Anbox Emulator turned into... But is 'now' geared towards commercial interests, for businesses too run their Android app's in the cloud, for access from their customers.

EDIT:
And doing some digging, I found this: 
```

mafoelffen@Mikes-ThinkPad-T520:~$ sudo snap find anbox 
Name               Version  Publisher  Notes  Summary
cloud-gaming-demo  0.1      morphis    -      Cloud gaming demo for Anbox Cloud

```
And from that: [https://snapcraft.io/cloud-gaming-demo](https://snapcraft.io/cloud-gaming-demo) which runs on Desktop... I have not installed it to see what it actually is...

---

### Post by aug7744 on 2023-06-28
@MAFoElffen

Thanks for your reply.
VirtualBox running Android-x86 is really good ?
In Android-X86 is possible access in the host modem 3G so having the sim card cell number and sharing that information with installled Android softwares (whatsapp) ?
Is possible transfer copy Android software (apk is the name ?) to be installed in VM Android-X86 so avoiding download again ?

Perhaps VirtualBox and Android-X86 are more secure and avoid spread files and config in host OS Ubuntu.
Have an sites saying to be possible run android directly in Google Chrome using an extension , but I want avoid it ... Google Chrome use extremely the HHD writing much data. Few time using that browser ahd will use more than 1 GB written on disk.

---

### Post by TheFu on 2023-06-28
I don't consider any Android to be secure.  It is the OS I trust the least.

Also, if you want to access hardware directly from a virtual machine, you'll need to setup passthru. This can be trivial, like for USB2 devices, or very complex for PCIe devices. This passthru of hardware provides exclusive use of that hardware to the VM. The host system cannot have any access to it.

I haven't tried running Android under a virtual environment in about 10 yrs. What I do know is that it was very slow and used 3x more resources than the physical device used. It muist be better now. Hard to be worse.
If my Phone had 2GB of RAM, then the VM needed 6G.  Things like that.  It was always slow.  In the end, I decided to use a remote connection and screen sharing from the physical android device to my PC for those needs.  There are lots of options for this. KDEConnect and GSConnect come to mind. [https://www.omgubuntu.co.uk/2018/11/connect-android-ubuntu-gsconnect](https://www.omgubuntu.co.uk/2018/11/connect-android-ubuntu-gsconnect)  I've not used either and have reloaded a new OS since the last time I needed this capability. I don't recall the exact program.  scrscp ... or something like that is what I used.

---

### Post by BBQdave on 2023-06-28
> **aug7744 said:**
> I only want run simple android software.

Not sure of the application of *android software* (smart device) on a computer?

I use Google Chrome and it's suite of software on GNU/Linux machines.
It is nice to have function across my computer and Android phone with suite of applications in Chrome.

---

### Post by MAFoElffen on 2023-06-28
> **aug7744 said:**
> @MAFoElffen
Thanks for your reply.
VirtualBox running Android-x86 is really good ?
In Android-X86 [COLOR=#ff0000]is possible access in the host modem 3G so having the sim card cell number and sharing that information with installled Android softwares (whatsapp)[/COLOR] ?
Is possible transfer copy Android software (apk is the name ?) to be installed in VM Android-X86 so avoiding download again ?
No. That is not possible with any Android Emulator. Ubuntu itself, installed on your computer, does not have a Phone Sim Card. Per-say, if you had a laptop, with a WAN card, that used a cellular service vendor's Sim card, you could possibly pass that through into a KVM Guest (That would not be possible with VirtualBox)... But I don't know that "that" would give you anything, because I do not know of any Android Emulator that is going to try to connect to a SIM card to do "anything." That really isn't a thing with those.

Rather they run Android from a Linux Host to run Android applications, and try to use the resource given them... Which come to your next question:
> **aug7744 said:**
> 
Perhaps VirtualBox and Android-X86 are more secure and avoid spread files and config in host OS Ubuntu.
Yes, it will be sandbowed within the VM Guest. 

I don't think what you are looking to do is possible or feasible. At least not what you described.

What "is" your goal that you think Android can do, but Linux cannot? I think that is the real question.

---

