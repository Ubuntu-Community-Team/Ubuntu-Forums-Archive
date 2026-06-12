---
title: "Ubuntu VirtualBox Devices Menu??"
date: 2008-05-29
forum: General Help
---

### Post by Josh08 on 2008-05-29
Hello,

Ive just installed Windows Vista on VirtualBox what comes with UBuntu. And i'm trying to make it fit a widescreen and ive looked around for help and it says i have to install a guest addition or something related but first i have to access the devices menu. I'm confused on my virtualbox there isn't a devices list. The only lists i see are: FILE, MACHINE, HELP

and that's it, so i'm kinda confused.. could anyone help??

cheers, josh.

---

### Post by bollix47 on 2008-05-29
Start your Vista virtual machine first.

The Devices menu item should show up.

---

### Post by imking on 2009-03-15
The devices menu will not be in the virtual box window but it will show up in the guest window when its booting up

---

### Post by Gary Nored on 2009-07-21
I'm really curious to know how your Vista inside Ubuntu is working. I want to do the same thing because Photoshop CS4 requires Vista and I just don't want to have to live in Vista.

Gary

---

### Post by UranUtan on 2009-07-21
> **Josh08 said:**
> Hello,

Ive just installed Windows Vista on VirtualBox what comes with UBuntu. And i'm trying to make it fit a widescreen and ive looked around for help and it says i have to install a guest addition or something related but first i have to access the devices menu. I'm confused on my virtualbox there isn't a devices list. The only lists i see are: FILE, MACHINE, HELP

and that's it, so i'm kinda confused.. could anyone help??

cheers, josh.

The Vista VM is launched inside a window. In the top border of this windows, there is a menu "Machine, Devices, Help". Once Vista started and you log in.

Click on the Devices Menu (of the VM window, not inside Vista). Then click on the item "Install Guest Additions". After that Virtualbox will emulate a CD Drive and auto start the installer. If you have disabled auto start, then within Vista, start Windows Explorer, go to the CD drive and Execute VBoxWindowsAddition.exe.

---

