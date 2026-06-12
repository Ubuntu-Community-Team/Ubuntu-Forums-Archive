---
title: "Persistent Mount"
date: 2007-11-13
forum: General Help
---

### Post by dm6257 on 2007-11-13
I am fairly new to Linux.  How do I get mount to persist so that I don't have to run the same mount command each time I restart Ubuntu Gutsy?

Dale

---

### Post by Zorael on 2007-11-13
You'll want to edit your /etc/fstab file. I don't know of any GUI alternative.

Perform your mount command, then view the contents of /etc/mtab (through the text editor of your choice, or cat). There'll be a line there that reflects how fstab and mtab expresses your mount. Copy that line and paste it in /etc/fstab.

To see if it worked, unmount your resource (share, disk, whatever), then do 'mount -a' with root privileges. It should read fstab and remount it, and if it doesn't, output a neat error message hopefully explaining why.

---

### Post by dm6257 on 2007-11-14
I changed the fstab file and ran the mount -a command and it worked great.  Does not work during reboot however.  Maybe I can create a shell script that will do it.  Thanks, Dale

---

### Post by bodhi.zazen on 2007-11-14
It should work during boot.

Post your line from fstab

---

### Post by dm6257 on 2007-11-15
A little more background.  I am running Ubuntu 7.10 under Virtual Box and am mounting the Windows directory named MyDocs.  The fstab line is below.  I noticed in the mountall.sh file in init.d the mount command didn't list vboxsf as an allowable file type.

MyDocs  /mnt/share vboxsf rw 0 0

Thanks for your assistance.

Dale

---

### Post by bodhi.zazen on 2007-11-15
Two pieces of advice ...

1. You need to install the AddOns into the guest.

[http://doc.gwos.org/doku.php/doc:office:virtualbox#additions_.iso](http://doc.gwos.org/doku.php/doc:office:virtualbox#additions_.iso)

2. To mount a share : [http://doc.gwos.org/doku.php/doc:office:virtualbox#sharing_your_hard_drive](http://doc.gwos.org/doku.php/doc:office:virtualbox#sharing_your_hard_drive)

I have not tried this with fstab.


One suggestion: Lately I find it easiest just to network share rather then mount a shared hard drive.

---

