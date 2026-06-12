---
title: "Intel vs. ARM repositories"
date: 2019-03-03
forum: General Help
---

### Post by gilius2 on 2019-03-03
I noticed that the sources.list points to archive.ubuntu.com in the Intel distros and ports.ubuntu.com in the ARM distros.

Firstly, can anyone explain what the difference is and why that's the case?

Secondly, when I run sudo apt-get install libvirt-bin it finds it under Intel distros but not ARM64 distros, so how can I install it for the latter? 

Can we change from ports.ubuntu.com to archive.ubuntu.com in the ARM64 distros?

---

### Post by QIII on 2019-03-03
In the interest of teaching a man to fish:

ARM = Advanced RISC Machine.
RISC = Reduced Instruction Set Computing.

I believe that if you did some research (there is far too much information to present concisely in a forum post) on those two acronyms, you would be able to answer your own questions here and also your previous question about virtualization.

The short answer is this:  ARM architecture does not support the full breadth of the capabilities supported by x86/64 instruction sets, making it incapable of providing the same functionality.  Thus, software needs to be written with the reduced instruction set complexity in mind.  It is possible to refactor (port) some code from x86/64 to work in the ARM environment.  That, however, takes a good bit of work.  Still not all original functionality can be reproduced.

The code bases are not interchangeable.  Attempting to use x86/64 code on an ARM device will fail.

---

### Post by gilius2 on 2019-03-03
> **QIII said:**
> In the interest of teaching a man to fish:

ARM = Advanced RISC Machine.
RISC = Reduced Instruction Set Computing.

I believe that if you did some research (there is far too much information to present concisely in a forum post) on those two acronyms, you would be able to answer your own questions here and also your previous question about virtualization.
I've spent months researching this and there are no answers out there to be found... both must be down to the incompetence of the Ubuntu devs maintaining the ARM64 branches - relegated to "ports"?

Other ARM64 Linux distros have that app inside their package manager, so I guess I need to switch.

---

### Post by CatKiller on 2019-03-03
Even ignoring the architectural limitations of both ARM and x86, they are simply *not the same*. They don't even have the least-significant number in the same place. The repositories contain **compiled binaries**. Something compiled for ARM will not run on x86 without a translation layer.

You can, of course, download the source code and compile your own binaries for whichever architecture you wish.

---

### Post by QIII on 2019-03-03
> **gilius2 said:**
> I've spent months researching this and there are no answers out there to be found... both must be down to the incompetence of the Ubuntu devs maintaining the ARM64 branches - relegated to "ports"?

Other ARM64 Linux distros have that app inside their package manager, so I guess I need to switch.

Perhaps you do.  You should not tolerate incompetence.

---

### Post by gilius2 on 2019-03-03
BTW, are you guys suggesting that ARM is inferior to other architectures? What can you do with Intel that you can't do with ARM in term of benefiting the end user...?

---

### Post by QIII on 2019-03-03
No.

[By the way ...]("https://packages.ubuntu.com/search?suite=default&section=all&arch=arm64&keywords=libvirt&searchon=names")

---

### Post by gilius2 on 2019-03-03
> **QIII said:**
> No.

[By the way ...]("https://packages.ubuntu.com/search?suite=default&section=all&arch=arm64&keywords=libvirt&searchon=names")
I wish you guys wouldn't talk in riddles.

Does that mean the ARM64 package is only missing from cosmic and disco? I can test in Bionic and see if it installs.

---

### Post by gilius2 on 2019-03-03
That's led me to this:
[https://askubuntu.com/questions/1089753/kvm-qemu-installation-issue-18-10](https://askubuntu.com/questions/1089753/kvm-qemu-installation-issue-18-10)

I guess I would never have known that. The package manager doesn't report it's discontinued. And it's not like the package has a homepage with a blog! :)

Will I get the same problem with Chromium? I am going to try to install that next.

---

### Post by him610 on 2019-03-03
Even Linus Torvalds has his opinion of Arm vs x86....[https://www.theregister.co.uk/2019/02/23/linus_torvalds_arm_x86_servers/]("https://www.theregister.co.uk/2019/02/23/linus_torvalds_arm_x86_servers/")

---

### Post by lisati on 2019-03-03
> **him610 said:**
> Even Linus Torvalds has his opinion of Arm vs x86....[https://www.theregister.co.uk/2019/02/23/linus_torvalds_arm_x86_servers/]("https://www.theregister.co.uk/2019/02/23/linus_torvalds_arm_x86_servers/")

He was talking about SERVER platforms, which usually have different requirements to a simple hand held device used only for checking email and the occasional browsing of web pages, or one which is used to assist in the production of the latest movies with knock-your-socks-off special effects.

ARM and x86 architectures aren't necessarily better or worse than one another, just different. It can take a LOT of work to adapt software originally written for one environment so that it will be useful when transplanted to a different environment.

---

### Post by deadflowr on 2019-03-03
> Firstly, can anyone explain what the difference is and why that's the case?

Space and popularity, really.
[https://wiki.ubuntu.com/UbuntuDevelopment/PackageArchive#Ports]("https://wiki.ubuntu.com/UbuntuDevelopment/PackageArchive#Ports")

---

### Post by him610 on 2019-03-03
@QIII
> 
ARM = Advanced RISC Machine.
RISC = Reduced Instruction Set Computing.

Thanks. I was not aware of what ARM meant; although, I was aware of RISC.
My only experience with configuring an ARM-based machine has been with Raspberry Pi, Models B and 3B, both running Raspbian Stretch which I believe is a port of Debian Stretch. I even installed Raspberry Pi Desktop on one of my Atom-powered Acer Aspire One 110 netbook.

---

