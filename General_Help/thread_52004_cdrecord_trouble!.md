---
title: "cdrecord trouble!"
date: 2005-07-26
forum: General Help
---

### Post by vladuz976 on 2005-07-26
i am trying to use cdrecord.
i understand that i need to know the scsi bus number to use it. i try "sudo cdrecord -scanbus" to get that information,
but this is what i get:

cdrecord: Warning: Running on Linux-2.6.10-5-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
cdrecord: No such file or directory. Cannot open '/dev/pg*'. Cannot open SCSI driver.
cdrecord: For possible targets try 'cdrecord -scanbus'.
cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
cdrecord:
cdrecord: For more information, install the cdrtools-doc
cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .


plus this==>>"read /usr/share/doc/cdrecord/README.ATAPI.setup" doesn't exist.

is there anybody here who has got cdrecord working or knows how to fix this problem?

---

### Post by Ufo on 2005-07-27
I have used cdrecord to write digital photos to cd:s.
I used it this way:

$cdrecord -v speed=4 dev=/dev/hdd -data cd_image

-v is for verbose output
speed=4 is slow, maybe you would like to use faster speed.
My cdwriter drive is /dev/hdd.
cd_image is the image file I made of photos with mkisofs.

Hope this helps :-)

---

### Post by vladuz976 on 2005-07-31
hey thanks  a lot,

that helped. works like a charm!!!

---

