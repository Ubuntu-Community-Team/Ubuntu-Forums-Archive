---
title: "getting an access to files in Windows System"
date: 2005-05-02
forum: General Help
---

### Post by young on 2005-05-02
Hello there,


              I have some important files (perl, C++ and java files) stored in Windows XP
      System (NTFS).  I want to somehow get an access to them (when I say this, I mean 
      I would actually like to transfer them into my /dev/hda1.  because I don't want to
      type them all by hand).  I also have some mp3 and wma files, which I would like
      to have in my Ubuntu as well.  Is there any way to solve this problem (I know
       how to mount nfts system into /dev/hda1, but just don't know where to go 
      from there)?   Thank you in advance.


                                                                                                                    Young

---

### Post by Gandalf on 2005-05-02
[QUOTE=young]Hello there,


              I have some important files (perl, C++ and java files) stored in Windows XP
      System (NTFS).  I want to somehow get an access to them (when I say this, I mean 
      I would actually like to transfer them into my /dev/hda1.  because I don't want to
      type them all by hand).  I also have some mp3 and wma files, which I would like
      to have in my Ubuntu as well.  Is there any way to solve this problem (I know
       how to mount nfts system into /dev/hda1, but just don't know where to go 
      from there)?   Thank you in advance.


                                                                                                                    Young[/QUOTE]
 well if you mount NFTS drive you can browse it in windows explorer!!! can you get into it? is this why you asking??

---

### Post by young on 2005-05-02
Hello Gandalf,


              Thanx for the reply, I appreicate it.  Well I know how to browse and FIND the
       file myself after mounting NTFS, but I don't know how to LOAD it into the Ubuntu.



                                                                                                                        Young

---

### Post by Gandalf on 2005-05-02
[QUOTE=young]Hello Gandalf,


              Thanx for the reply, I appreicate it.  Well I know how to browse and FIND the
       file myself after mounting NTFS, but I don't know how to LOAD it into the Ubuntu.



                                                                                                                        Young[/QUOTE]
 oh you mean use them on linux????

---

### Post by young on 2005-05-02
Hello Gandalf,

            yes that's exactly what I want to do.


                                                                                                   Young

---

### Post by Gandalf on 2005-05-02
[QUOTE=young]Hello Gandalf,

            yes that's exactly what I want to do.


                                                                                                   Young[/QUOTE]
 well try
sudo apt-get install build-essential perl
for perl and c++

for java download from sun.com the java sdk and follow [HOWTO: Installing Java J2SDK | J2RE with firefox plugins](http://ubuntuforums.org/showthread.php?t=23592)

---

### Post by Stormy Eyes on 2005-05-02
Try the following steps in a terminal:

1. mkdir ~/windows
2. sudo mkdir /media/windows

If your NTFS filesystem is on /dev/hdb1, do the following. Change /dev/hdb1 as needed.
3. mount -t ntfs /dev/hdb1 /media/windows

4. cd ~/windows
5. cp -R /media/windows/* .
6. umount /media/windows

Let me know if this helps you. This was how I transferred my father's data from Windows to Ubuntu.

---

### Post by FunnyLookinHat on 2005-05-04
I tried the above command after changing my fstab file did not work.  I have three NTFS drives that I want to read from and all of which are "seen" by the OS when I type this command:
> dmesg | egrep "^(s|h)d"

However, when mounting the third drive (160 GB, as opposed to 80 and 120) I receive this error:

> sudo mount -t ntfs /dev/hdf1 /media/media3
mount: wrong fs type, bad option, bad superblock on /dev/hdf1,
       missing codepage or other error
       (aren't you trying to mount an extended partition,
       instead of some logical partition inside?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

The drive works fine in windows, so I doubt that it is a "bad" partition.  Any suggestions?

---

