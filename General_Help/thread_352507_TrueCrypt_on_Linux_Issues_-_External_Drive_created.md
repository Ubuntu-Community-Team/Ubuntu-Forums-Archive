---
title: "TrueCrypt on Linux Issues - External Drive created on Windows"
date: 2007-02-03
forum: General Help
---

### Post by r1u on 2007-02-03
Hello Guys, thanks for taking time to read my post. (Using Ubuntu 6.10 Edgy)

I have researched this on many sites and have progressed but not as much as I wished, Basically I have an external hard drive, using hidden volume and AES-Two others as well that was created under WIndows, This is a 250GB Maxtor HD USB, now this works fine with windows etc.

I would like to transfer files to it from LInux but do not know how to open it, I have seen lines of code like

truecrypt --size 200MB --type normal --encryption AES --hash RIPEMD-160 --filesystem FAT -c myvolume.tc

This creates it fine in linux I tried, but the myvolume.tc file I dont know what this is in relation to windows as the mount command for external devices as far as I know and have researched is

truecrypt -u /media/usbdisk/myvol.tc tcmount

Now for one, what would my device be under media? I cant see it listed in Linux and the myvol.tc what is this? I never saw reference to this in Windows, I just want the code to mount and dismount but more than anything mount.

Thanks so much
Sarah

---

### Post by chewearn on 2007-02-06
What a coincidence.  I stumbled into exactly the same problem.  Searched both the truecrypt forum and saw your question there too.  Unfortunately, the replies degenerated into debates on encryption schemes and methods.  Can't blame them though; it sort of a more "security" centric forum over there.

Anyway, after mugging around, I finally solve the problem myself.  Here is how; for the ubuntu/linux experts reading this, please excuse my amateurish approach :-)

First, using the gui file browser (natilus) navigate into /dev directory.  Scroll down to the general vicinity of hda, hdb.  Then, plug in your external usb drive.  Within a few seconds, new entries should appear (mine are sdc and sdc1).  These devices should represent you usb drive.  Now, I'm sure there are command line you can execute, but I am still trying to recover from windows sickness.

Next, open a terminal, run the truecrypt mount command; for my case:

$ mkdir /home/userme/usbhd
$ truecrypt -u /dev/sdc1  /home/userme/usbhd

You should be prompted for the truecrypt volume password; I tried sdc first, didn't work, then finally success with sdc1

Regards.

---

### Post by r1u on 2007-02-06
Read next, accidental multi post

---

### Post by r1u on 2007-02-06
Thanks a lot AstaLavista,

I will try this tommorow and get back to you to see if it works, If I had created the secret volume on Windows, if I do as you say and enter the password for the outer volume then these contents will be displayed? and if i enter password for the secret one these will be displayed? 

Thanks again

P:S

What is the myvolume.tc aspect of it then? as you have not used it and it shows it being used in documentation on Linux, I never had to name the volume on windows for this i am sure.

---

### Post by chewearn on 2007-02-06
hi
I have not used hidden volume feature, so the method I used referred to normal volume.  I have no experience myself on using hidden volume.

But the truecrypt linux documentation mentioned these commands you might be able to use:

 $ truecrypt -P /dev/hdc1 /mnt/tc
   Map  and  mount outer volume /dev/hdc1 and protect hidden volume within it.

$ truecrypt -i
  Map and mount a volume. Options are requested interactively.

Just replace with your detected usb drive dev.

I tried the -i option, the third question asked "Protect hidden volume?"; if you answer "y", it will later asked for the hidden volume password.  But I don't use hidden volume myself, so I can't comment on success.

As for the "volume.tc" stuff, this refer to a truecrypt file, instead of partition or drive.  This mean the .tc file is like any other file on you computer, you can copy/move it around.  But inside the file is an encrypted volume, which you can use truecrypt to mount to a drive letter (Windows) or folder (Linux).

Note you can also create the .tc file in the Windows version; I have done so before in my work PC.  Very useful when you are not able to tamper with the partition.

---

