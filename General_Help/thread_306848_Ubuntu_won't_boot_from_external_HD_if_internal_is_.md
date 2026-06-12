---
title: "Ubuntu won't boot from external HD if internal is connected"
date: 2006-11-25
forum: General Help
---

### Post by wilsonisme on 2006-11-25
Hey mates,

I installed Xubuntu on an external USB hard drive. To make this simple I unplugged my internal SATA HD so I could whiz through the installation with confidence that nothing will be installed on my internal HD (Don't feel like dual booting it atm, I am already running ubuntu inside of vista with VMWare). 

My thinking was if I wanted to boot into Xubuntu I could just turn on my external HD at boot, if not I would leave it off and it would boot into Vista. My mobo supports this, and it works perfectly, except for one thing:

If I boot into Xubuntu with the internal hard drive connected, it hangs at the boot screen (Xubuntu splash screen) and refuses to start up. If I boot into Xubuntu with the internal drive disconnected, it works perfectly.

Any ideas on what to do here so Xubuntu booting works even with the internal HDD connected?

Thanks!
Wilson

---

### Post by iamhugeinjapan on 2006-11-25
What are the boot device settings in your BIOS?

---

### Post by wilsonisme on 2006-11-25
Boot order isn't the issue, the computer will successfully boot into Xubuntu with both drives connected, it is Xubuntu that hangs if the computer boots into it with both drives connected. 

But just incase:

1) CD Drive
2) USB HDD
3) Internal HDD

---

### Post by iamhugeinjapan on 2006-11-25
How long do you leave it before declaring it stuck? There is another thread down the page with someone complaining of 3 minutes to boot an external HD Ubuntu.

I think it would be a good idea to boot Xubuntu without any splash screen. Choose the recovery kernel from the grub menu so you can get the text of where it stops.

---

### Post by CatKiller on 2006-11-25
I think it's because your internal drive is SATA. When you installed Xubuntu, it thought that the external drive was sda for your /etc/fstab, and hd0 for GRUB. When you plug in your internal drive, **that** becomes sda and hd0, I'd imagine. So (although I'm not entirely sure how to do this) you could switch to UUIDs, so that it **always** refers to the right drive, or change them to sdb and hd1 respectively and never unplug the internal drive (since you'll just have the same problem when you do).

EDIT: Never mind - you've said that it **does** boot. Guess it's something else.

---

### Post by wilsonisme on 2006-11-25
Yeah grub boots into Xubuntu but then Xubuntu hangs. I know it isn't doing anything because it eventually drops me to the shell. I think you are right about the drive assignment thing but maybe it is Xubuntu who is having that problem and not grub?

---

### Post by wilsonisme on 2006-11-25
Alright I just tried booting with recovery mode with the internal hard drive connected. This is the error that I can see:

"Attach SCSI Disk sdb"
-Huge wait- "Done."
-Immediately after- "Alert! /dev/sda3 does not exsist. Dropping to a shell!"

By the way I am typing this post from within Xubuntu, it booted fine as usual with the internal drive unplugged.

---

### Post by CatKiller on 2006-11-25
Does your fstab refer to sda? Might be worth changing that to sdb, since it appears that it (sort of) finds sdb OK. Just some more wild speculation on my part, though.

---

### Post by wilsonisme on 2006-11-25
Still looking for an answer ](*,)

---

