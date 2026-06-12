---
title: "Wubi Says not enough space to install"
date: 2007-07-31
forum: General Help
---

### Post by CodyZ on 2007-07-31
Hi there, I'm really excited about using wubi to install xubuntu onto my Toshiba Satellite 3110ct laptop.  It's an older machine, and XP runs extra slow on it.  Unfortunately, I can't boot from CD so using wubi really is my only option as far as installing linux goes.  

I ran the wubi installer and it told me I didn't have enough disk space, and it requires at least 4 gigs to install.  I cleaned up my system, uninstalled *everything*, and now I have 4.20 gigs free (it's only a 6 gig drive).  But still it says I don't have enough space.

What can I do?

Thanks!

---

### Post by ago on 2007-07-31
You need 5GB free (of which 4 GB are used by the virtual drive and 700MB by the ISO). To use it on less space you'd need to have to modify the source code and recompile.

---

### Post by CodyZ on 2007-07-31
> **ago said:**
> You need 5GB free (of which 4 GB are used by the virtual drive and 700MB by the ISO). To use it on less space you'd need to have to modify the source code and recompile.

Oh ok, I'll give that a try.  I'm not sure what else I can do to reduce the size of my XP install, any tips would be appreciated.  I've already turned off save points, hibernation, and the paging file.  I've also uninstalled all the sizable programs.

Thanks!

---

### Post by Odegard on 2007-08-01
Hehe, this reminds me when I had a 286 with 20mb harddrive, and I wanted to put windows 3.11 on it. That was not the problem, I could barely manage, but I also wanted civ2 which took all of 2MB or something. I deleted all *.hlp and stuff I could find, even calc.exe and similar stuff. Great times. (I even did stacker, a program that compressed the content of the harddrive, yilding a few more MBs but it was naturally oh so painfully slow!)

---

### Post by ghostdog87 on 2007-08-05
hey, same problem for me, i have 18gb free, but wubi installation says that i need 4gb.,,.,.,.,.,.,.,.,.,.what dows that mean?

---

### Post by tuxcantfly on 2007-08-05
> hey, same problem for me, i have 18gb free, but wubi installation says that i need 4gb.,,.,.,.,.,.,.,.,.,.what dows that mean?

Do you have the right drive selected? Try the other drives as installation targets, they might work.

---

### Post by Xenomorph on 2007-08-06
> **CodyZ said:**
> Hi there, I'm really excited about using wubi to install xubuntu onto my Toshiba Satellite 3110ct laptop.  It's an older machine, and XP runs extra slow on it.  Unfortunately, I can't boot from CD so using wubi really is my only option as far as installing linux goes.  

I ran the wubi installer and it told me I didn't have enough disk space, and it requires at least 4 gigs to install.  I cleaned up my system, uninstalled *everything*, and now I have 4.20 gigs free (it's only a 6 gig drive).  But still it says I don't have enough space.

What can I do?

Thanks!

with such an old system, i'd recommend Windows 2000.

---

### Post by Xenomorph on 2007-08-06
> **Odegard said:**
> Hehe, this reminds me when I had a 286 with 20mb harddrive, and I wanted to put windows 3.11 on it. That was not the problem, I could barely manage, but I also wanted civ2 which took all of 2MB or something. I deleted all *.hlp and stuff I could find, even calc.exe and similar stuff. Great times. (I even did stacker, a program that compressed the content of the harddrive, yilding a few more MBs but it was naturally oh so painfully slow!)

with the awesome power of my 486 and DOS6, i decided doublespace/drivespace disk compression would be a great way to increase my available drive space.

the system churned away all night trying to compress things.

then everything ran nice and super slow, and it hardly "doubled" my available space.

---

### Post by zach12 on 2007-08-06
i'm haveing that problem too on one of my laptops too
and i have 7gb free

---

### Post by david_kt on 2007-08-08
Mostlikely it was due to your harddisk is fragmented as  I think wubi need 4 GB unfragmented disk space, not 4 GB free space a little bit here and a little bit there.

I suggest you to run disk defragmenter, and then try to run Wubi again. Hopefully it could solve your problem.

DK

---

### Post by minhmeoke on 2007-08-08
If you need more space in WinXP, you could delete old Windows Update Hotfix backups, see this article for more details: [http://www.askdavetaylor.com/can_i_delete_the_contents_of_windows_ntuninstall.html]("http://www.askdavetaylor.com/can_i_delete_the_contents_of_windows_ntuninstall.html")

---

### Post by tuxcantfly on 2007-08-08
You might have some better luck with UNetbootin (see my sig) it installs Ubuntu without needing a CD and since it downloads while it installs instead of requiring a predownloaded iso file, it only needs 4 GB to install

---

### Post by zach12 on 2007-08-12
ok thanks

---

