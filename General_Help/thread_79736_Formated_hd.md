---
title: "Formated hd????"
date: 2005-10-20
forum: General Help
---

### Post by UbuntuUbuntu7 on 2005-10-20
I had the bad luck to enter: sudo mkfs.ext3 /dev/hdb1 on my harddrive. I just copied and past, thought it was the mount command. I realised it was not, untill it had come to about 700 och 895 in the counter. The disk is almost full, 105 gig.

What to do with the disk? When i try to mount it i get: 

mount: wrong fs type, bad option, bad superblock on /dev/hdb1,
            missing codepage or other error
            In some cases useful info is found in syslog - try
            dmesg | tail  or so

"Fparted" label it as "Unknown Filesystem". :confused: Help?
"Fparted" label it as "Unknown Filesystem".
"Unable to detect filesystem! Possible reasons are:
-The filesystem is damaged.
-The filesystem is unknown to libparted
-There is no filesystem available (unformatted)

---

### Post by stuporglue on 2005-10-20
You can try running fsck.ext3, but it probably won't help. 

sudo fsck.ext3 /dev/hdb1

Say yes to everything. 

And watch the copy/paste w/out knowing what's happening.

---

### Post by dave9191 on 2005-10-20
[QUOTE=UbuntuUbuntu7]I had the bad luck to enter: sudo mkfs.ext3 /dev/hdb1 on my harddrive. I just copied and past, thought it was the mount command. I realised it was not, untill it had come to about 700 och 895 in the counter. The disk is almost full, 105 gig.

What to do with the disk? When i try to mount it i get: 

mount: wrong fs type, bad option, bad superblock on /dev/hdb1,
            missing codepage or other error
            In some cases useful info is found in syslog - try
            dmesg | tail  or so

"Fparted" label it as "Unknown Filesystem". :confused: Help?
"Fparted" label it as "Unknown Filesystem".
"Unable to detect filesystem! Possible reasons are:
-The filesystem is damaged.
-The filesystem is unknown to libparted
-There is no filesystem available (unformatted)[/QUOTE]

Is this a disk that you were trying to mount that had your files on it ? If so then you've formated it or started to format it. I dont quite understand, but did you say you cancelled the format? To use the disk again you will have to format it. But if you want to try and get your data back you will have to use some data recovery tools. Im affriad I cant recommend any. 

Dave

---

### Post by UbuntuUbuntu7 on 2005-10-21
> Is this a disk that you were trying to mount that had your files on it ? 
Yes.
> If so then you've formated it or started to format it. I dont quite understand, but did you say you cancelled the format? 
Yes, when it was about 700 of 895.
> To use the disk again you will have to format it. 
I dont hope so.

---

### Post by dave9191 on 2005-10-21
[QUOTE=UbuntuUbuntu7]I dont hope so.[/QUOTE]

By starting the format you started to overwrite the old filesystem, but because you didn't finish the format the computer can't make sense of the drive now. You may also have overwritten some of the data beyond recovery now. 

However there is still hope with data recovery tools to get some / most of the information stored on the drive back. But I can't recommend any, and last time I looked for them, they all cost a lot of money. 

Dave

---

