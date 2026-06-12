---
title: "Mapping a network drive"
date: 2008-06-07
forum: General Help
---

### Post by Johnsie on 2008-06-07
On Windows its pretty simple... just click "map network drive", select the folder you want to map and choose a drive letter. You can decide if you want it mapped at boot time jsut by checking a box. It's all easy to do and has a pretty intuitive and simple gui. 

Say I want to do something similar in Linux (mounting a samba share using a gui), how would I go about doing this? Is there an easy way like there is on Windows? In terms of intuitiveness and ease of use which operating system is better for easy share mapping?

---

### Post by Johnsie on 2008-06-13
hmmmm... I havent had any reponse to this post. So far the only way I've seen to do it on Linux is by playing around with a config file (fstab). I think this is something that needs to be simplified in Linux as most homes have multiple computers these days.

---

### Post by mdurham on 2008-06-13
I just use Nautilus to connect and 'bookmark' it.
Seems not too complicated.
Cheers, Mike

---

### Post by paulhart on 2008-07-09
Same question.. I have a dual boot (WinXP32Pro and UbuntuStudio64) on this station, with three networked WinXP stations used as render farm clients primarily and secondary storage. I asked over on the Blender Forum, as I can't get Blender to even "see" any of the other drives (2SATA, 2IDE) on this station using Ubuntu, as it only sees the /home/(username) folder. At least when in Blender on the WinXP32Pro boot, I can see all of the local drives but none of the networked drives (even "mapped") ones. Other programs have no problem. When I go to "Places" in Ubuntu, it sees the networked stations, and I can even TightVNC them into Ubuntu, but Blender "sees" nothing. I will do some research on 'Nautilus' but this shouldn't be that hard, as Linux has always been noted for it's strong network support. What am I missing.???
Paul

---

### Post by bluepowder7 on 2008-07-09
dunno if this helps too much, but...

do you need nfs-common installed?  on my home "network", which is a linux file server and a linux desktop, i have the server drivers 'broadcast' using nfs (which i guess takes care of the first half of connecting stuff), and on the desktop (client) side, i mount the server's drive to a local spot on the directory (which takes care of the second half of connecting).

i can either do this (the second half) manually, or i can enter a line in fstab to have it done automatically.  the first half is automatically done each time the server boots up.

mind you, that's linux to linux.  i guess that for a windows machine, you'd need to set up samba as well.  the server guide should be able to help.

[http://doc.ubuntu.com/ubuntu/serverguide/C/](http://doc.ubuntu.com/ubuntu/serverguide/C/)

---

### Post by bodhi.zazen on 2008-07-09
It should work out of the box.

Go to places and navigate to the windows server.

Otherwise go places -> server and input the ip address and share name.

If it is not working, it is most likely a problem on the windows server or workgroup.

---

### Post by paulhart on 2008-07-10
The problem seems more systemic, in that Blender and Open Office can not see anything other than the "/home/username" folder. Interestingly enough, when I navigate using the Ubuntu file browser, no problem, sees all of the drives, even sees the networked stations, which I even "bookmarked," but clicking the "P" button in Blender or the double arrows below don't go any where. In Open Office, same issue, so it's no Blender specific. If I open the file manager in Ubuntu, navigate to another drive, and click on a Open Office document, it opens fine, just can't go there from inside of programs. My "noobishness" with Linux is definitely showing. I did go ahead and load the NTFS config tools, no difference. Overall I am pleased to be up on Ubuntu. Thanks for the help.
Paul

---

### Post by jimv on 2008-07-10
The closest thing that I think you will get to a mapped drive that automounts is adding the share to your fstab file.  It will look something like this:

```
//server/share	/some/folder	smbfs	user=someuser,password=somepassword
```

---

### Post by paulhart on 2008-07-12
Thank you...
I tried the /server/share command, first trying
 //server/share /home/paulhart smbfs user=username,password=userpasswrd
but only got "No such file or directory"
Tried the same thing to try to connect to a main data drive..local station
 //server/share /media/D1-P1_Data2 smbfs user=username,password=userpasswrd
got the same response "No such file or directory"
It shouldn't be this difficult. Try this in Open Office, File>Open, click on the Icon to go "Up" and I can only go up two levels to where the folders are /bin /boot /cdrom, etc. but beyond this to see other actual folders on the same drive, no go. And I can not "see" any of the data drives on the same local station, and no idea about networked drives. If I navigate to then using the File Browser in Ubuntu, no problem, sees all the drives, even the networked drives. I can click on a file and open it in Open Office, but this doesn't change how Open Office then views folders. Same problem in Blender. With so much of Ubuntu working right "out of the box" this mystifies me. You all can't be loading everything into your "/home/username" folder, that's "brain dead" in this day
Sorry for the (/rant) mode but I don't think this should work like this.
Thank you for any assistance, it is appreciated.
_________________________________
Here is the output of fstab
paulhart@ubuntu64:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config --
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sdc5 :
UUID=5e423e7e-50c2-4033-a40e-92eb7e2f946e / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sdc6 :
UUID=6054f57c-87fd-4c1c-8f85-facdd8d518dd none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sdc1 /media/Scsi1_Sys ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sdb1 /media/Scsi2_Data ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda5 /media/D1-P2_Archv ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda1 /media/D1-P1_Data2 ntfs-3g defaults,locale=en_US.UTF-8 0 0

Paul

---

### Post by bodhi.zazen on 2008-07-12
Samba mounts are not that difficult.

You can mount samba shares graphically :


[list]
[*]Places -> Network -> browse to server, enter users and password
[*]Places -> connect to a server -> Enter server, share, user , and password
[/list]


Or with the command line. 

From the command line, install smbfs first :

```
sudo apt-get install smbfs
```

next make sure the mount pint exists.

```
mkdir <directory>
```

Also smb is depreciated for cifs

Then :

```
sudo mount -t cifs //server/share /mount/point -o user=xxx
```

Enter password when asked.

If it is working you can add an entry to fstab

---

### Post by djkilgus on 2008-08-16
bodhi.zazen, thanks for the help.

i've added entries to my fstab, but the two ntfs shares they reference are not mounting on boot.

would the fact that my ubuntu box is a laptop that solely leverages my home wireless network have anything to do with my problem?  my wireless connection doesn't seem to finish establishing itself until the end of the boot process, and i have to assume that fstab is executed much sooner.

thoughts?

---

### Post by Nhorning on 2011-02-08
I have the solution to this. It's so simple and it took me FOREVER to find it. 2 years late for the original poster but maybe it will help others with this problem. 

Network shares mounted through the UI are mounted in a hidden hidden directory in your home folder: ~/.gvfs

Find that in your home directory using show hidden files, bookmark it by dragging it over to to the side in Nautilus, and you're done!

---

### Post by mosaic2s on 2011-08-16
yes, that is good.

---

