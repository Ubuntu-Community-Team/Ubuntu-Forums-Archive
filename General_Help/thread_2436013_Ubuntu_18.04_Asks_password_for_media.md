---
title: "Ubuntu 18.04 Asks password for media"
date: 2020-01-30
forum: General Help
---

### Post by coerrace on 2020-01-30
I have a Lattepanda and I have plugged in the m.2 m port a Samsung EVO 970 all runs fine but at si estime it asks for password with the message “authentication required” when I try to access a partition in the media route the Samsung Evo is horrible and uncomfortable and also virtualbox not works so good because it says destinations don’t exist. How can we remove that the Ubuntu 18.04 stops asking password to access the media route directory for the Samsung Evo?

Thank you

---

### Post by CelticWarrior on 2020-01-30
If you created any encrypted partition then it's expected asking for a password. Also if the partition is owned by another user or root, of course.

---

### Post by Skaperen on 2020-01-30
what commands or programs are you using to access the EVO 970?

---

### Post by coerrace on 2020-01-30
I don&#8217;t have encryption for anything, It&#8217;s just in exfat and other in NTFS partitions.

Program to access nothing it is just plugged to the m.2 m key port and done is detected automatically including for booting but inside linux it likes to ask password for everything regarding the media directory routes. The samsung evo is in a route for example it&#8217;s in the route &#8220;/media/myusername/HD&#8221;, where HD is the name of the evo.

How can I remove the password request?

---

### Post by CelticWarrior on 2020-01-30
Are you dual-booting with Windows? If so you need to disable Fast Startup (in Windows) otherwise it'll keep those partitions semi-hibernated and that might be the reason why Ubuntu is asking for a password (to mount them read-only).

If the above is not the case, you have some serious issue. Normal exFAT or NTFS partitions are usually mounted without fuss.

---

### Post by coerrace on 2020-01-30
Yes I have dual booting with Windows. What I do is in the bios select the EFI boot install and select windows or linux to boot. Actually I use more linux because I like more the performance for what I do. But where I disable the Fast Startup?

---

### Post by CelticWarrior on 2020-01-30
[https://www.windowscentral.com/how-disable-windows-10-fast-startup](https://www.windowscentral.com/how-disable-windows-10-fast-startup)

Very easy to google, by the way.

Unrelated PS:

> in the bios select the EFI boot install and select windows or linux to boot

If both OSes are properly installed in UEFI mode you should open UEFI settings (what you call "BIOS" but really isn't, it's UEFI) > Boot menu (or equivalent depending on the manufacturer) and select "Ubuntu" as the primary bootloader. Then boot Ubuntu and run ```
sudo update-grub
``` to assure Windows is detected and included in the Grub menu. Do this **after** disabling Fast Startup.

---

### Post by coerrace on 2020-01-30
I solved the problem simply clicking right button over the drive and then assign all the permissions and problem gone no more password requests.

Thank you anyway

---

