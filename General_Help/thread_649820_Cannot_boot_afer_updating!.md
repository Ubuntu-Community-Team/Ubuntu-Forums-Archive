---
title: "Cannot boot afer updating!"
date: 2007-12-25
forum: General Help
---

### Post by Boomy on 2007-12-25
I just ran the updates for Ubuntu. Everything went smootly and I rebooted as new linux headers were part of the update. After rebooting I get an error from grub that says it cannot mount the partion. Why did I even bother updating? Everytime I do it it seems to break something...

---

### Post by LaRoza on 2007-12-25
Search the forums for the same issue.

I don't know why this happens to some people, especially recently, and why it didn't affect me at all.

---

### Post by TidusBlade on 2007-12-25
I remember a safe mode or something, have you tried that?

---

### Post by Boomy on 2007-12-25
Yes I tried the safe boot option, same problem. I think the kernel is corrupt. I didn't really check the updates I was installing, but I think it installed a new kernel, which is not showing up in grub, only the old one is showing up, which is broken. I think if I pointed grub to the new one it would boot, but this is just a guess. I've been wanting to try some other distros for some time now. I think this might be a good time to try Mandriva. I'm kinda pissed at Ubuntu right now, lol.

---

### Post by logos34 on 2007-12-25
> **Boomy said:**
>  After rebooting I get an error from grub that says it cannot mount the partion. 

sounds like error 17...on the highlighted ubuntu entry hit 'e' to edit and check the 'root' line--maybe the update changed it.

EDIT: or boot from the live cd and run a filesystem check:

**sudo fsck /dev/sda1 **(or whatever root partition is)

---

### Post by meierfra on 2007-12-25
This should be fairly easy to fix. 

Is it correct that the grub menu appears at boot up?

If yes, select the ubuntu item, but do not press "enter". Press "e" instead . A new screen will appear. The first line should say something like "root (hd0,2)".  Post the exact content of that line.

Reboot via "Ctrl Alr Del" . Boot from the Ubuntu live CD. Open a terminal (Applications->Accesories->Terminal) and post the output of

 ```
sudo fdisk -l
```


Seems logos34 was a little faster than me,

---

