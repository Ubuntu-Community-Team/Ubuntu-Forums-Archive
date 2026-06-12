---
title: "Update Kernel With force PAE"
date: 2016-02-15
forum: General Help
---

### Post by christian92 on 2016-02-15
Hello

it´s a known issue that if you installed with forcePAE you can´t update the Kernel without a Error.
Now the Workaround works fine, but you have it to do on each Update. And the Updates are many.
Can i intert into the Updater a little Batch witch it has to run before each update?
If there´s no Kernel update it doesn´t matter, the Batch only copy one file and mount/remount.

I Use Lubuntu 15.10 at Moment.

greetings ck

---

### Post by mörgæs on 2016-02-16
> **christian92 said:**
> 
it´s a known issue that if you installed with forcePAE you can´t update the Kernel without a Error.

How is that known? Links please.


> **christian92 said:**
> 
Now the Workaround works fine, but you have it to do on each Update. And the Updates are many.

Which workaround? Links.

---

### Post by sudodus on 2016-02-16
The method described in the following link works for me (because the boot option forcepae will be ported to the installed system).

[BootOptions/before--after](https://help.ubuntu.com/community/BootOptions/before--after)

If you did not do it during the installation, you can make  the boot option forcepae stay in the grub system by combining the tips in the previous link and the next link.

[Boot options](http://ubuntuforums.org/showthread.php?t=2230389&p=13370808#post13370808)

---

### Post by christian92 on 2016-02-16
Hi
@ [**[COLOR=#DD4814][B]mörgæs**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=939075")

I get the infos when i sent the error log, this ist the Workaround was shown:

#!/bin/bash

cat /proc/cpuinfo | sed 's/flags\t*:/& pae/' > /tmp/cpuinfo_pae
      sudo mount -o bind /tmp/cpuinfo_pae /proc/cpuinfo
      sudo mount -o remount,ro,bind /proc/cpuinfo

Sorry that j have no Link, the page open&#347; automatic after i sent the errors

@sudodus

I Know the Problem you tell, i had do this. If you do not you can install but the system doesnt run. My System run, only the Update requires the Workaround

---

### Post by sudodus on 2016-02-16
If you have the boot option forcepae in the installed system, you need no [other] workaround for dist-upgrading (to get a new kernel).

---

### Post by christian92 on 2016-02-17
Oh, that´s great

then i had make a misstype on Installing, it´s easy to fix, i install new, then i will see

or can I change this without new installation?

---

### Post by sudodus on 2016-02-17
See this link, that describes how to make persistent edits of the boot options. See this link

[Setup#Configuring_GRUB_2](https://help.ubuntu.com/community/Grub2/Setup#Configuring_GRUB_2)

> Editing the File

The grub file is a system file, therefore any editing must be done by a user with 'Administrator/root' privileges. The file is a simple text file and can be edited by any text editor. The default text editor in Ubuntu is Gedit, and the file can be edited with the following command. "gksu" is the graphical equivalent of "sudo" and the "&" allows the terminal to be used to update GRUB 2 once the user saves the file.

    ```
gksu gedit /etc/default/grub &
```

After making changes and saving the file, the GRUB 2 menu must be updated to include the changes by running:

    ```
sudo update-grub
```

> GRUB_CMDLINE_LINUX

    Entries on this line are added to the end of the 'linux' command line (GRUB legacy's "kernel" line) for both normal and recovery modes. It is used to pass options to the kernel. 

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

    This line imports any entries to the end of the 'linux' line (GRUB legacy's "kernel" line). The entries are appended to the end of the normal mode only.
        To view a black screen with boot processes displayed in text, remove "quiet splash". To see the grub splash image plus a condensed text output, use "splash". 

---

### Post by christian92 on 2016-02-21
Works fine, thanks

---

