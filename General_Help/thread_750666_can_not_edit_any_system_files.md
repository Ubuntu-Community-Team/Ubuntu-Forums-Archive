---
title: "can not edit any system files"
date: 2008-04-09
forum: General Help
---

### Post by weirdfate on 2008-04-09
Im a noob when it comes to linux but a pro in windows so this is getting me verry mad


ok i have,from what ive been told, a verry odd problem.  I cant edit any system files at all.  I need to add a command to cr or rc.local, i cant remember off the top of my head.  I tried in sudo -s,sudo nano, i tried to just edit it in mouse pad via the system file folder on the desk top bit heres what happens.  I get error can not open file to write when i try to save it when i edit it in mousepad.  When i try to do it with sudo or sudo -s,super nano--it tells me its a new file when i get it open (but its there)

This is pissing me off cause i got every thing else running fine i just have no permisions to edit any files 

i set up xubutu on a dell laptop
latitude cpi
300mhz pII
20 gig hd
cant remember the ram
I think the partition is ntfs

Im not sure what the issue is here i just cant figure it out

---

### Post by ibutho on 2008-04-09
You can edit system files by prefixing the commands you use to start the editor with sudo e.g.
```
sudo nano /path/to/file
```
You can also use graphical text editors by using gksudo e.g.

```
gksudo gedit /path/to/file
```

---

### Post by ScorpKing on 2008-04-09
very weird indeed (if i understand correctly). there are a few things you can try if sudo nano <file> or sudo vi <file> does not work. 
1) boot to recovery mode and edit files while you are root. 
2) make sure you are part of the "admin" group. run groups in the terminal to find out. if you are not part of the group run adduser <yourname> admin as root in recovery mode. 
3) check in /etc/sudoers (run cat /etc/sudoers as root from recovery mode) if the line %admin ALL=(ALL) ALL is present. if not run visudo /etc/sudoers as root and add that line to it. 

you can also boot from the livecd to see if sudo works then. if it does then there's something wrong with your installation. hope you get it working soon.

---

### Post by weirdfate on 2008-04-09
> **ibutho said:**
> You can edit system files by prefixing the commands you use to start the editor with sudo e.g.
```
sudo nano /path/to/file
```
You can also use graphical text editors by using gksudo e.g.

```
gksudo gedit /path/to/file
```

the gedit code gives me an error as well(not sure what it is im at my parents not near my linux)
the sudo nano code opens the file but it says its a new file,every file i open even the xconf file that i needed to change to edit my display resolution but i did that by using the code to rebuild it and set the resolution back then.

thankyou

---

### Post by weirdfate on 2008-04-09
> **ScorpKing said:**
> very weird indeed (if i understand correctly). there are a few things you can try if sudo nano <file> or sudo vi <file> does not work. 
1) boot to recovery mode and edit files while you are root. 
2) make sure you are part of the "admin" group. run groups in the terminal to find out. if you are not part of the group run adduser <yourname> admin as root in recovery mode. 
3) check in /etc/sudoers (run cat /etc/sudoers as root from recovery mode) if the line %admin ALL=(ALL) ALL is present. if not run visudo /etc/sudoers as root and add that line to it. 

you can also boot from the livecd to see if sudo works then. if it does then there's something wrong with your installation. hope you get it working soon.

how do i boot into recover mode?????

---

### Post by ibutho on 2008-04-09
> **weirdfate said:**
> the gedit code gives me an error as well(not sure what it is im at my parents not near my linux)
the sudo nano code opens the file but it says its a new file,every file i open even the xconf file that i needed to change to edit my display resolution but i did that by using the code to rebuild it and set the resolution back then.

thankyou
Are you entering the correct path names of the files. For example if you wanted to edit the X configuration file , you would have to do "sudo nano /etc/X11/xorg.conf".

---

### Post by weirdfate on 2008-04-09
> **ibutho said:**
> Are you entering the correct path names of the files. For example if you wanted to edit the X configuration file , you would have to do "sudo nano /etc/X11/xorg.conf".

this is what im tryn to do

```
mousepad /etc/rc.local

Add the following after the last commented out line and before "exit=0":

echo activate > /sys/devices/pnp0/00:10/resources
modprobe snd-cs4236 isapnp=0 port=0x530 cport=0x210 irq=5 dma1=1 dma2=0

```

when i open mouse pad with sudo it open a blank file
when i try to sudo nano it opens it as  a new file

:confused::(:confused:
gona try some of the sugestions here and let you guys know what happenes

thanks for the help

---

### Post by p_quarles on 2008-04-09
The exact line you need to type is:
```
gksu mousepad /etc/rc.local
```
If for some reason the file is still empty after typing this *exact* command, not to worry. That file does nothing by default. Just make sure that it begins with:
```
#!/bin/sh -e
```
and ends with 
```
exit 0
```

---

### Post by weirdfate on 2008-04-10
thankyou everyone for your help

the last post did it and now the soundcard drivers are loaded every startup :KS:)

this place is great people are hear to help out a fellow ubuntuer even if he/she is a noob(me)  

this OS runs great on my older laptop even if it takes for ever to start up

thankyou again for your help

:guitar:

---

### Post by weirdfate on 2008-04-11
now its back to crap again i uninstalled it and tried to re do it to see whay i have no admin/root access and now i find that the torrent for the alter. xubuntu disk is bad at the kernel?!!  WHY ME?
but i cant stop till i atleast give my self a hart attack or something to that effect:)

---

### Post by fguilhon on 2008-04-11
I didn't read all the replies but if you:
> I think the partition is ntfs
that's the problem... Ubuntu does not write to ntfs out of the box.. you have to install **ntfs-3g** package..

---

### Post by weirdfate on 2008-04-12
ok i have tried everything i can think of but i still get no access to my system files!!!!!  They open up in blank files with mousepad,gtedit wont run


I cant even gain access to my xorg.conf file to change my screen res.
only way i was able to change from 24 to 16 was to go  thru that whole xorg.conf reconfigure command......

I have now installed the older version of xubuntu and still have no root access to files (same problem as above)


Ive gone into the user settings and assigned my  user name to the admin,root..... and still no luck

only thing I can thing of is the copys im downloading from the net go bad somewhere and i just have crappy luck
what are the min sys requirements for xubuntu??  Dont even know why im asking cause it runs on my system cause ive seen many posts about my dell cpi D300XT running xubuntu!!!!

im giving it one more shot with this older(6) versioon and then im going back to windows or maby another linux release 
this sux but i got my self into this and im gona loose sleep tryn to get out :lolflag:

---

### Post by duncan.hawthorne on 2008-04-12
post the exact commands you run and the problem you encounter. the more accuracy in reporting the better :)

if you run
sudo gedit /etc/X11/xorg.conf

you should have now opened your xorg.conf file to edit. (but dont edit it, you seem quite new to ubuntu, and editing that file without knowing what you are doing breaks things)

if not post exact error messages from terminal, or from the windows

try running 
cd ~ && echo sampletext >> samplefile 
report output

then run
gedit samplefile

and post output. it should have the text "sampletext" inside it


there is no chance that the cd you downloaded was broken if it managed to install sucessfully

---

### Post by weirdfate on 2008-04-12
> **duncan.hawthorne said:**
> post the exact commands you run and the problem you encounter. the more accuracy in reporting the better :)

if you run
sudo gedit /etc/X11/xorg.conf

you should have now opened your xorg.conf file to edit. (but dont edit it, you seem quite new to ubuntu, and editing that file without knowing what you are doing breaks things)

if not post exact error messages from terminal, or from the windows

try running 
cd ~ && echo sampletext >> samplefile 
report output

then run
gedit samplefile

and post output. it should have the text "sampletext" inside it


there is no chance that the cd you downloaded was broken if it managed to install sucessfully

yes i am a noob and i wanted this to be easy for me but its not!!  I got it easy when i use windows and now im tryn to run xubuntu on my laptop and this is what i get a mess of things that wont work for ME
BTW the laptop is running strict xubuntu no partitions fof windows
i will try your helpfull posts in a little bit after a restart cause ive tried to get my sound card working using this thread [http://ubuntuforums.org/showthread.php?t=90869](http://ubuntuforums.org/showthread.php?t=90869) 
thanks

---

### Post by fguilhon on 2008-04-14
This is all very strange problems you're having... maybe your fs is read-only...
type ```
sudo mount
``` to list mountpoints and ```
cat /etc/fstab
``` to list the partitions and post back the results to us...
good luck

---

### Post by weirdfate on 2008-04-14
> **fguilhon said:**
> This is all very strange problems you're having... maybe your fs is read-only...
type ```
sudo mount
``` to list mountpoints and ```
cat /etc/fstab
``` to list the partitions and post back the results to us...
good luck

yes my FS is set to read only
i have tried to set my user as a root,admin.... wont open this up to read&write

```
weirdfate@weirdfate-laptop:~$ sudo mount
[sudo] password for weirdfate:
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
weirdfate@weirdfate-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=92a71502-7900-410b-a2d6-6384ac256a42 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=d7cf5471-178f-4177-b004-d4a5ad48f057 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
weirdfate@weirdfate-laptop:~$ 

```

---

### Post by fguilhon on 2008-04-14
From what I can see from the output it's normal... read-write...
I have no idea what it can be... try entering in rescue mode and modifying your sys settings..

---

