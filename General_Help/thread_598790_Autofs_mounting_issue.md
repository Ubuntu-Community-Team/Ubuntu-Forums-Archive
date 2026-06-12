---
title: "Autofs mounting issue?"
date: 2007-10-31
forum: General Help
---

### Post by becatlibra on 2007-10-31
I am having an issue mounting using autofs

Originally this command would work from the command line:

sudo mount 192.168.1.225:/SharedThings/music /home/benito/Desktop/Shared


But then I thought autofs to automount (if the system goes on and offline) would be good

I installed autofs - now the question stands - what am I doing wrong?

/etc/auto.master:
benito@nighthawks:/misc$ cat /etc/auto.master #
# $Id: auto.master,v 1.4 2005/01/04 14:36:54 raven Exp $
#
# Sample auto.master file
# This is an automounter map and it has the following format
# key [ -mount-options-separated-by-comma ] location
# For details of the format look at autofs(5).
#/misc  /etc/auto.misc --timeout=60
#/smb   /etc/auto.smb
#/misc  /etc/auto.misc
#/net   /etc/auto.net
/misc   /etc/auto.misc

/etc/auto.misc:
benito@nighthawks:/misc$ cat /etc/auto.misc
#
# $Id: auto.misc,v 1.2 2003/09/29 08:22:35 raven Exp $
#
# This is an automounter map and it has the following format
# key [ -mount-options-separated-by-comma ] location
# Details may be found in the autofs(5) manpage

cd              -fstype=iso9660,ro,nosuid,nodev :/dev/cdrom

# the following entries are samples to pique your imagination
#linux          -ro,soft,intr           ftp.example.org:/pub/linux
#boot           -fstype=ext2            :/dev/hda1
#floppy         -fstype=auto            :/dev/fd0
#floppy         -fstype=ext2            :/dev/fd0
#e2floppy       -fstype=ext2            :/dev/fd0
#jaz            -fstype=ext2            :/dev/sdc1
#removable      -fstype=ext2            :/dev/hdd
SharedMusic  -rw,soft,intr,rsize=8192,wsize=8192   192.168.1.225:/SharedThings/music



What is wrong?  I followed a howto I found which said the directory I was mounting to could have NO subdirectories and the mounting directory (SharedMusic) should not exist on the client machine.  Nothing is showing up in the /misc directory.  I chmod'd it so that it is 777 (just in case)


Help?

Thanks

Benjamin

---

