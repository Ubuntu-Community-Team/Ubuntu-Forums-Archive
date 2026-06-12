---
title: "Lubuntu will not shutdown properly"
date: 2013-01-21
forum: General Help
---

### Post by mastergunner on 2013-01-21
Folks I am trying Lubuntu on an old HP Pavilion ZE4400. I had an issue installing it but got the work around to get it installed.Now everytime I hit shutdown the computer will begin the process of shutting down, goes to the Lubuntu splash but never shuts down. If I hit the power button it will shut down. I have tried modifying the Grub but to no avail. Any help would be appreciated.

---

### Post by dino99 on 2013-01-21
you should remove "quiet splash" from /etc/default/grub, then update it (sudo update-grub) to get the verbose mode. So when you will shut down the system,, you will see where/when it hang (probably a driver not unloaded yet, like networkmanager)

---

### Post by mastergunner on 2013-01-21
I did this and Chromium stopped working but did see that nothing was stopping it from shutting down. Last line was shutting down in 1 sec. It never shut down.

---

### Post by pjalegria on 2013-01-22
Do you get check disk at boot? Can be related to this bug [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1066484](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1066484)

---

### Post by mastergunner on 2013-01-22
The computer boots normally and nothing appears at boot other than the Lubuntu splash.

---

### Post by gifford on 2013-01-29
I'm not sure which version of Lubuntu you are using but I have had this issue with Ubuntu 12.04.

I followed some threads and changed /etc/default/grub file to reflect the following:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" 
Change to
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=force"

and then do sudo update-grub.

It is not a perfect fix but works most of the time. This has been an issue for me since Ubuntu 12.04 was released.
Hope it helps.

---

### Post by mastergunner on 2013-01-29
Gifford I have tried this and nothing happens. I wonder if it has something to do with the brand of computer. Mine is an HP.

---

### Post by gifford on 2013-01-29
Mine is HP also, I do not have the problem on any other computers, just my desktop, so you could be onto something.
This has been an ongoing issue for me and I have not found a 100% fix.
It is frustrating as Ubuntu has usually worked without a flaw for me.

It now is working but when it stops I will try the item listed under 2 at
[http://askubuntu.com/questions/125844/shutdown-does-not-power-off-computer](http://askubuntu.com/questions/125844/shutdown-does-not-power-off-computer) 

Which stated:
"The solution above worked for a while but then the problem re-occurred. So I removed acpi=force from GRUB_CMDLINE_LINUX_DEFAULT and added it to GRUB_CMDLINE_LINUX instead, using the steps above (i.e. GRUB_CMDLINE_LINUX="acpi=force")"

---

### Post by mastergunner on 2013-01-30
I have used both and neither one of those worked. We need the Ubuntu gurus to help us out on this.

---

### Post by dino99 on 2013-01-30
well, thats not very new, and users are quitely waiting a real fix.

[https://bugs.launchpad.net/ubuntu/precise/+source/libnih/+bug/740390](https://bugs.launchpad.net/ubuntu/precise/+source/libnih/+bug/740390)
[https://bugs.launchpad.net/ubuntu/+source/modemmanager/+bug/1024868](https://bugs.launchpad.net/ubuntu/+source/modemmanager/+bug/1024868)

---

### Post by mastergunner on 2013-01-30
Well after reading these bugs it looks like no one is willing to test the fixes. If no one does then the bug disappears and we are back to square one.

---

### Post by gifford on 2013-01-31
I tried something different. Instead of just update-grub, I did:
sudo update-grub & sudo update-grub2.

Since doing that I have had no more problems with shutting down, even after Kernel update. 
On one of the threads I read researching the issue there seemed to be an issue with just the update grub command.

---

### Post by mastergunner on 2013-02-05
> **gifford said:**
> I tried something different. Instead of just update-grub, I did:
sudo update-grub & sudo update-grub2.

Since doing that I have had no more problems with shutting down, even after Kernel update. 
On one of the threads I read researching the issue there seemed to be an issue with just the update grub command.

This did not work for me. Does anyone else have a solution?

---

### Post by gifford on 2013-02-06
Do you have lo-menubar for LibreOffice installed?

---

### Post by mastergunner on 2013-02-06
I have libreoffice installed but not sure about what your asking.

---

### Post by gifford on 2013-02-06
Lo-menubar is an add-on for LibreOffice and is in the software center. It provides a global menu for LibreOffice which integrates with the OS.
I had to remove the one I installed early on in the process of trying to fix the issue as it did cause the problem with shutting down. However, it still did not fix the problem completely and I had to do more research and trial and error.

---

