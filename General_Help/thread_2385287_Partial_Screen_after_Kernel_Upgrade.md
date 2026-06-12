---
title: "Partial Screen after Kernel Upgrade"
date: 2018-02-18
forum: General Help
---

### Post by uRock on 2018-02-18
Hi all! I have the feeling this has already been answered, but Google isn't returning any useful results.

I have an Asus Netbook running 16.04.3 32bit and after the kernel upgrade a couple of months ago I am only able to see part of the screen. This normally wasn't a problem as I maintained it remotely using SSH. The computer's only purpose is for running as a Motion cam server.

I hadn't bothered with trying to fix this before and am regretting it as I no longer have SSH connectivity due to one of my WAPs dying.

I tried running lspci in recovery mode, but the graphics info is not visible because of the small screen. If I end up having to, then I will boot via USB and get the info that way.

Specs can be found here [https://www.amazon.com/Asus-Eee-PC-1005HAB-Netbook/dp/B002U6JVDO](https://www.amazon.com/Asus-Eee-PC-1005HAB-Netbook/dp/B002U6JVDO)

I've added a screenshot showing what it looks like after logging in.

Any help would be greatly appreciated.

---

### Post by tinylagarto on 2018-02-18
What kernel are you using?

---

### Post by uRock on 2018-02-18
14.3.0-31 and 32 both have the issue. This started after the Meltdown update.

---

### Post by DuckHook on 2018-02-18
Haven't the foggiest idea if this will help. [https://01.org/linuxgraphics/downloads](https://01.org/linuxgraphics/downloads)

It may just make things worse. But if you are fully backed up and don't mind reinstalling, it may help.

Have you tried "nomodeset"? If that helps to at least get readable output, post results of xrandr.

---

### Post by uRock on 2018-02-18
> **DuckHook said:**
> Haven't the foggiest idea if this will help. [https://01.org/linuxgraphics/downloads](https://01.org/linuxgraphics/downloads)

It may just make things worse. But if you are fully backed up and don't mind reinstalling, it may help.

Have you tried "nomodeset"? If that helps to at least get readable output, post results of xrandr.

I did manage to find a bug report on the issue. Though listed as critical since last year, there doesn't seem to have anyone actively working to fix it. I am downloading and installing 16.04.1 to install and will work to prevent it from upgrading to the 4.13.* kernel set as it seems to be a bad kernel on all of my machines. Even there recovery mode keeps restarting and going to the screen where you select to clean, repair packages, or go to root terminal.

---

### Post by tinylagarto on 2018-02-18
> **uRock said:**
> This started after the Meltdown update.

I thought so. That is unfortunate but you could try to boot or to install into kernel 4.4. 
Though it is strange because I have similar hardware and no problem with the newest kernels.

---

### Post by uRock on 2018-02-18
Reinstalling with the 16.04.2 installer seems to have fixed the issue. Now using the 4.4.* kernel and all is well.

Thanks for the support. :guitar:

---

