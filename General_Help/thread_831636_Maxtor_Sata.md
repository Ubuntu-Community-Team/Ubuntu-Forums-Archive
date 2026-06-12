---
title: "Maxtor Sata"
date: 2008-06-17
forum: General Help
---

### Post by allstar1971 on 2008-06-17
I just purchased a Maxtor Sata 250mb (7L250S0) and I cannot get Ubuntu to recognize the hard drive.

When my system is booting (AMD 3700+), it is seen right after the initial boot screens (memory, cd-roms, etc.) but I cannot install anything on it because when I get to ubuntu, it says my hard drive doesn't exist.

Help!

JP

---

### Post by cdtech on 2008-06-17
You should see the drive using the command line after you boot:
sudo fdisk -l

Then use that information to mount it during boot.

Or you could just creat a directory to mount it and mount it manually.

Is it formatted and with which file system?

---

### Post by allstar1971 on 2008-06-17
I cannot get it to format. I am lost.

---

### Post by allstar1971 on 2008-06-17
Obviously, nobody can help me.

I would love to run ubuntu, but here is my problem:

Previously, I ran Ubuntu Gutsy on my system. I upgraded to a Western Digital 120 GB hard drive and a new DVD read-write. (HL-DT-STDVD-RAM GSA-h55N)

Now Ubuntu gutsy, heron will not install. I always come up with errors. Either on the boot, on when I try to install from Live CD.

I tried putting my old hard drive and dvd back in, but I still have install errors.

I have googled and tried every type of suggestion out there and I feel Ubuntu is the issue.

NOW, I purchased a sata maxtor 250gb HD and it will not work.

I can install Mandriva, PC Linux (gnome or KDE), etc. with no problems. When I try to install any type of Ubuntu distro (mint, etc.), it comes up with the same errors (intramfs, or install error).

---

### Post by allstar1971 on 2008-06-18
I guess I found something nobody could answer.

I am now using PCLinuxOS. It installs and works.

Still didn't find the sata problem though.

---

