---
title: "Booting impossible cause GRUB rescue won't let me"
date: 2013-01-25
forum: General Help
---

### Post by kingdm on 2013-01-25
I created two bootable USB: ***Lubuntu 12.10*** and ***Ubuntu 12.04*** from my windows machine.

**SCENE 1**

I installed **Ubuntu 12.04**, everything is fine. A popup window appears that says something like "I have successfully installed the operating system and a reboot is required." I am about to click the reboot now button, when the electricity went off (No laptop battery, dammit)! Now I boot back, and found out that my Ubuntu will only normally boot if the USB is plugged in, if I removed it, only the blinking insert cursor will just be there for me.

**SCENE 2**

With my crazy mind, I thought of installing the **Lubuntu 12.04** so it will forget memories of **Ubuntu 12.04**. I inserted the USB and there goes the installation. All went well, I played with Lubuntu for a couple of hours. But then, my consciousness reminds me : I want my Ubuntu back.

**SCENE 3**

Once more, I inserted the **Ubuntu 12.04**. I miss the violets, so I expected that much I'll see it. But then, I am a failure. Here is this ****** GRUB rescue that keeps telling me error blah, blah.

**SCENE 4**

Nowhere to go, booted back to **Lubuntu 12.10**. Type my story here and hoping someone will lead me back to my home... Ubuntu.

---

### Post by oldfred on 2013-01-25
So we can see what is where:

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by kingdm on 2013-01-25
Here is the link it generates:

[http://paste.ubuntu.com/1570148/](http://paste.ubuntu.com/1570148/)

---

### Post by oldfred on 2013-01-25
It says it reinstalled  grub to the MBR of sda. Does it now boot?

Otherwise I do not see anything wrong. 

If you still have issues you may be booting grub ok. Grub does not show a menu if only one system installed and then you may have a driver issue. If still an issue try holding shift key from BIOS until menu appears.

---

