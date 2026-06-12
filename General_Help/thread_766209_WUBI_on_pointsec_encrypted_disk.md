---
title: "WUBI on pointsec encrypted disk"
date: 2008-04-25
forum: General Help
---

### Post by vleutmans on 2008-04-25
Hi there,

I took the challenge to install Ubunti/WUBI on a system that has harddisk encryption (pointsec for windows 2000).

The WUBI setup runs fine, and creates the virtual disks etc. within windows.

After reboot (and pointsec login) I get the multiboot option, to start either windows or ubuntu. 

After starting ubuntu I soon receive the busybox terminal screen.

Then I read about adding irqpoll to the bootmenu 'boot','second line', as described on WUBI page.

This method doesn't work for me, I added irqpoll (without quotes) to the second line, exactly as described...but I still get to the busybox terminal after reboot.

Anyone has an idea what could be the problem ?

Furthermore, after a reboot the irqpoll is gone from the second line.

I hope I did something stupid and someone can tell me what I did wrong :-)

Best regards

Michel

---

### Post by ago on 2008-04-25
Pointsec encrypted hard disks are not supported at the moment

---

### Post by yellowbkpk on 2008-04-25
I also have this issue on my laptop. It has Safeboot hard disk encryption, though.

The drive is unlocked when you login after boot (because it loads the Ubuntu boot picture is shown and busybox is loaded), but it appears that NTFS-3g cannot read the drive.

---

### Post by kweiner on 2008-05-02
I am having the problem on a Dell D430 Laptop.  I also have Safeboot installed.

> **yellowbkpk said:**
> I also have this issue on my laptop. It has Safeboot hard disk encryption, though.

The drive is unlocked when you login after boot (because it loads the Ubuntu boot picture is shown and busybox is loaded), but it appears that NTFS-3g cannot read the drive.

---

### Post by ago on 2008-05-02
Safeboot is not supported either at this stage

---

### Post by jakechance on 2008-12-03
My company just rolled out SafeBoot today. As soon as I saw it, I figured my Ubuntu via Wubi was screwed. I've tried it and confirmed it is. What I'm now wondering is:

1) Is it possible to see the files inside root.disk from windows?

2) Can I use root.disk with something like VMWare Player? I'm going to try it out, but figured I'd ask as there might be tips or tricks.

Just wanted to add that Wubi is awesome!

---

### Post by Jammanuser on 2008-12-03
> **jakechance said:**
> My company just rolled out SafeBoot today. As soon as I saw it, I figured my Ubuntu via Wubi was screwed. I've tried it and confirmed it is. What I'm now wondering is:

1) Is it possible to see the files inside root.disk from windows?

2) Can I use root.disk with something like VMWare Player? I'm going to try it out, but figured I'd ask as there might be tips or tricks.

Just wanted to add that Wubi is awesome!

yes...with something like [cygin]("http://www.cygwin.com/") you can mount ur root.disk from Windows!

Hope this helps! :)

-jammanuser

:guitar:

---

### Post by jakechance on 2008-12-03
Hi all,

I just found out that I can still get to root.disk using explore2fs. The good news is that I can get all my files and settings out.

I'm going to see if I can use root.disk with VMWare Player or if I can actually partition my hard disk and move the ubuntu files where they aren't encrypted.

---

### Post by Orlsend on 2008-12-05
The encryption worked on my fathers laptop,but he had to unencrypted the whole hard drive first and then install wubi, and encrypt it again.

He uses PGP whole disk encryption.

---

### Post by jakechance on 2008-12-08
SafeBoot is the devil. It screwed up my Wubi so I quickly made a small partition for Ubuntu. The problem here is that something happens between the BIOS and the Windows MBR with my former OS choices which was created by Wubi. Ubuntu overwrote that and I could no longer get into Windows. Also, restoring the MBR doesn't help. Until Wubi supports encryption or IT has a few more laptops like mine come in for repairs, I won't have Linux on this computer :-/.

---

### Post by martincs14 on 2009-02-18
hey

i have xp (pro) and have whole drive encryped with truecrypt.

as i understand i cannot install wubi.

what if i decrypt the hard drive, install wubi and reencrypt it
(all with truecrypt)

would that work?

thanks for help.

martin

---

