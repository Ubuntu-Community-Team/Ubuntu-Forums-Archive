---
title: "Writing to fat32 partition with full permission"
date: 2007-08-19
forum: General Help
---

### Post by jonathon678 on 2007-08-19
Hi!  

My /etc/fstab looks like this :

/dev/hda11   				  /media/datajon2  vfat  iocharset=utf8,umask=000  	0    0

I can copy files to my data partition however when i open a text file with gedit on my data partition** i can't save to it** and thus i have to save to the /home directory and then copy the file to my data partition. This is really frustrating. How can can obtain full access to my fat32 partition. johnny

---

### Post by cwillu on 2007-08-19
/dev/hda11 /media/datajon2 vfat iocharset=utf8,uid=<your user name> 0 0

i.e., I'd use /dev/hda11 /media/datajon2 vfat iocharset=utf8,umask=000,uid=cwillu 0 0

---

### Post by jonathon678 on 2007-08-20
thanks for your help. Your suggestion worked also both of the options below worked although it is the same as what i had before:  


dev/hda11   				  /media/datajon2  vfat   defaults,umask=000  		    0    0

instead of 

/dev/hda11   				  /media/datajon2  vfat  iocharset=utf8,umask=000  	0    0

I received a message on the boot saying 'iocharset=utf8 was not recommended' or something along those lines. 

Also this command worked as well:

dev/hda11   				  /media/datajon2  vfat  defaults,utf8,umask=007,gid=46,           0       1

(The '0' in the second last field indicates that the file system does not need to be backed up when the dump command is executed . The '1' in the last field indicates the consistency of the file system should be checked on boot and a '0' would indicate a check is not required.)

and your option:

/dev/hda11 /media/datajon2 vfat iocharset=utf8,umask=000,uid=jonathon 0 0 

(The 'uid=jonathon' refers to the user id which is 1000)

jonathon@jonathon-laptop:~$ id
uid=1000(jonathon) gid=1000(jonathon) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),104(scanner),112(netdev),113(lpadmin),115(powerdev),117(admin),1000(jonathon)

'The 'gid=value' refers to the group id

The 'defaults' means that -async, auto, exec,nouser, rw, suid commands are used.  

The 'umask' indicates initial file permissions on a newly-created file.

jonathon@jonathon-laptop:~$ umask
0022



I don't know what '0' means though? 


I can't really explain why it works now anyway i went with the first option. Maybe their is some kind 

of bug.  Also I turned off gedit> edit > preferences> editor > create a backup copy... so the 'could not create backup file while saving to' error message no longer occurs. 

All is well cheers

---

