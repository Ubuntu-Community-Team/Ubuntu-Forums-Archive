---
title: "Not able to backup to my WD Passport External Hard Disk"
date: 2008-06-17
forum: General Help
---

### Post by irshadcharm on 2008-06-17
Guys Im not able to backup my ubuntu system to WD Passport external hard disk...im not able to navigate to my WD through terminal....donno wats the reason...? Am i missing something out...ive done this as a root user, but of no use...could anyone tell me how to backup to my WD Passport? This is what i get when navigating thru the terminal...plz help....

```
irshadcharm@irshadcharm-desktop:/$ ls

bin   cdrom  etc   host    initrd.img      lib         media  opt   root  srv  tmp  var      vmlinuz.old
boot  dev    home  initrd  initrd.img.old  lost+found  mnt    proc  sbin  sys  usr  vmlinuz  windows

irshadcharm@irshadcharm-desktop:/$ cd media

irshadcharm@irshadcharm-desktop:/media$ ls

cdrom  cdrom0  disk  disk-1  disk-2  WD Passport

irshadcharm@irshadcharm-desktop:/media$ cd WD Passport

bash: cd: WD: No such file or directory

irshadcharm@irshadcharm-desktop:/media$ 
 
```

---

### Post by avtolle on 2008-06-17
As there is a space in the name, could it be as simple as cd "WD Passport"?

---

### Post by irshadcharm on 2008-06-17
not able to get it...when i give

cd WD Passport

No such file or directory is returned...

i wanna backup my ubuntu system to my external disk...plese help

---

### Post by dlmoak on 2008-06-17
I have a WD Passport external drive and I use Simple backup to backup to it with no problems.  The drive is referred to as "My Passport" on my computer.  If yours is the same and you want to go through the Terminal you might try that name.

---

### Post by avtolle on 2008-06-17
Sorry, wasn't clear before. When you do the cd command, enclose the WD Passport in quotation marks like this```
cd "WD Passport"
``` The space in the name is causing the problem, see the error message you posted earlier (
bash: cd: WD: No such file or directory)

---

### Post by irshadcharm on 2008-06-18
> **avtolle said:**
> Sorry, wasn't clear before. When you do the cd command, enclose the WD Passport in quotation marks like this```
cd "WD Passport"
``` The space in the name is causing the problem, see the error message you posted earlier (
bash: cd: WD: No such file or directory)

will try this buddy...and thanks for your time on answering my question...thx a lot...ill keep u posted...

---

### Post by irshadcharm on 2008-06-20
buddy how do we backup only the host drive to external hard disk..in my case ...i have 4 partitions **_C: D: E: F:_** ...in the F: drive i have installed ubuntu using a**_ wubi installer and i have allocated 10GB space_** for it...how do i backup only the ubuntu and restore it if at all i have a problem...i need the complete steps since im a newbie...please help...

---

### Post by avtolle on 2008-06-20
> **irshadcharm said:**
> buddy how do we backup only the host drive to external hard disk..in my case ...i have 4 partitions **_C: D: E: F:_** ...in the F: drive i have installed ubuntu using a**_ wubi installer and i have allocated 10GB space_** for it...how do i backup only the ubuntu and restore it if at all i have a problem...i need the complete steps since im a newbie...please help...
[https://wiki.ubuntu.com/WubiGuide#head-43f03ca4035e8b66458a83c7b4209aedcf1637d8](https://wiki.ubuntu.com/WubiGuide#head-43f03ca4035e8b66458a83c7b4209aedcf1637d8) gives the steps to back up the Wubi installation files. Since you did a Wubi installation, the same exists as a "folder" under your Windows installation on Drive F:, so (I've not tried this, you are on your own here) I'd look in that folder under the Windows OS and back the whole thing up (the folder, that is). When applying the link to back up the installation files, obviously where it refers to C:, you would use F:, but you already know that.

---

### Post by washburnello on 2009-11-05
> **irshadcharm said:**
> not able to get it...when i give

cd WD Passport

No such file or directory is returned...

i wanna backup my ubuntu system to my external disk...plese help

I know this thread is old but I landed here so maybe someone else will too ;)

Try
```
cd WD\ Passport
```
If your still unsure, open a terminal and cd into it's containing folder and type WD then press tab to auto complete it.
(If the path looks like /media/WD Passport then cd into /media)

---

