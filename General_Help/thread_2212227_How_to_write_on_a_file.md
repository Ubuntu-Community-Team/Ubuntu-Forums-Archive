---
title: "How to write on a file?"
date: 2014-03-20
forum: General Help
---

### Post by M1ck4el on 2014-03-20
Hi,
I have troubles to write on my file /etc/lightdm/lightdm.conf
I typed sudo nano /etc/lightdm/lightdm.conf to open my file but I can only read (and not write).

This didn't work 
[http://ubuntuforums.org/showthread.php?t=2141347](http://ubuntuforums.org/showthread.php?t=2141347)

but it's true, I am in recovery mode

---

### Post by Elfy on 2014-03-20
If you've only got read access then I'd say you've not mounted it properly to enable write.

mount -o rw,remount /

IF you still have issues - run one of the other commands in the recovery menu - grub update for instance, then try the root terminal again

---

### Post by Korkel on 2014-03-20
Run the following script, it will open the requested file as root so you can edit it.
[ATTACH]251309[/ATTACH]
[I]Make sure that you allow the file to run in a terminal.

[/I]Try also advice given above. :)

---

### Post by ajgreeny on 2014-03-20
Recovery mode by default mounts the filesystem now as read only (to save potentially damaging activity by users who don't know what they're doing, I think), so to make any changes to the system files you need to run that command mentioned by Elfy.

---

### Post by Elfy on 2014-03-20
> **Korkel said:**
> Run the following script, it will open the requested file as root so you can edit it.
[ATTACH]251309[/ATTACH]
[I]Make sure that you allow the file to run in a terminal.

[/I]Try also advice given above. :)

How does a script that includes running gedit help? 

In addition the thread has no prefix - what about if they are using Xubuntu, Lubuntu, Kubuntu ?

Please stay on topic for the thread - which is running nano in recovery mode - there would be no need for sudo anyway once the filesystem is mounted.

---

