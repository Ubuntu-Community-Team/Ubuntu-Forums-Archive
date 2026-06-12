---
title: "What the most compatible OSs with Ubuntu"
date: 2007-11-09
forum: General Help
---

### Post by sshahir on 2007-11-09
Hi all

I am trying to download and install ARM simulator. The software is available for the following Linux operating systems, but not Ubuntu:


Debian 3.1
Fedora Core 1 (also for FC2)
Fedora Core 3 (also for FC4)
Fedora Core 5
Mandrake 9.2
Red Hat 9.0
SuSE Linux 9.2
SuSE Linux 10.1
Other 2.6 series kernel
Other 2.4 series kernel

I am wondering which version of the software is the most compatible with Ubuntu OS, particularly v6.06.

I appreciate for any suggestion.

Thanks,
sshahir

---

### Post by -grubby on 2007-11-09
debian,you could run into problems though. Just try and see

---

### Post by sshahir on 2007-11-09
Which one is mostly going to work?

---

### Post by Maestro23 on 2007-11-09
> **sshahir said:**
> Which one is mostly going to work?

Your best bet is to get the source code (if availble) and compile it for Ubuntu. If it is available, it should be in the Downloads section of the program's website.

---

### Post by sshahir on 2007-11-09
> **Maestro23 said:**
> Your best bet is to get the source code (if availble) and compile it for Ubuntu. If it is available, it should be in the Downloads section of the program's website.

Unfortunately, the source code is not available. In this case, please let me know the platform through which the success rate would be higher.

---

### Post by Maestro23 on 2007-11-09
> **sshahir said:**
> Unfortunately, the source code is not available. In this case, please let me know the platform through which the success rate would be higher.

I would say Debian because Ubuntu is Debian based.  Can I guarantee it's going to work.. NO.

---

### Post by sshahir on 2007-11-17
> **Maestro23 said:**
> I would say Debian because Ubuntu is Debian based.  Can I guarantee it's going to work.. NO.

I am trying to install the debian application on my Ubuntu 6.0.6  using the following command:

sudo apt-get install ./vm-arm-se-1.0.6-15.debian3_1.i386.rpm

the installation stopped because a package couldn't be found.

> Reading package lists... Done
Building dependency tree... Done
[COLOR="Red"]E: Couldn't find package [/COLOR].

even when I try to install the .rpm application using the Synaptic Package Manager, I received the "Archive type not supported" (see the attached screenshot).

Any suggestion how I can install the application?

---

### Post by farruinn on 2007-11-17
When you run apt-get you are asking it to search the online repositories for the name of a package. To install an rpm I believe the command is 'rpm -i file.rpm' (you may have to do 'sudo apt-get install rpm' first). I imagine you'd be better off trying the release for Debian though as it will give you a .deb file. You can install it will the dpkg command: 'dpkg -i file.deb' and then if you need to remove it later on you can use the dpkg system. Much cleaner in my opinion.

Good luck.

---

