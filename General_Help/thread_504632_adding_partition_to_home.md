---
title: "adding partition to /home"
date: 2007-07-19
forum: General Help
---

### Post by liorc666 on 2007-07-19
> "Yes resizing is what I meant I thought that's what you were asking. I hope it works for you. If you have any problems with resizing or using gparted post back here or create a new thread with the specifics of what is happening. Good luck "

thats was post from my last post ([http://ubuntuforums.org/showthread.php?p=3045042#post3045042](http://ubuntuforums.org/showthread.php?p=3045042#post3045042))
i used Gparted from liveCD to resize the my main linux partition (from 24 to 20 gb) now i have got 4 GB i want to add to /home folder ,

i tryed to add it via mount command
sudo mount /dev/sda4 /home
but its replace my home folder ... 
since the orginal /home folder and the new parttion are not on the same HD i can use GParted to stick em togther ?

what sould i do to make my new partition go on /home without umount my current /home folder


thanks for helpers ^^

---

### Post by Nythain on 2007-07-19
since they are on different hard drives the best you are gonna be able to do is mount it within your /home.
first make a place to mount it... something like this
```

mkdir ~/stuff

```
will make a folder inside your home directory called stuff
then you have to tell fstab to mount the partition there everytime you boot
first we will find out what partition it is
```

sudo fdisk -l

```
will list every partition in your computer... find the 4 gig one you want to mount and note its /dev/xxyz
then
```

gksudo gedit /etc/fstab

```
to open up your fstab file
look for an entry for the 4 gig partition... if its already there then just change it to look something like this
```

/dev/xxyz    /home/yourusername/stuff    ext3    defaults    0 2

```
and if its not there then just add a line thats something like that... making sure to replace xxyz with the actually device and changing yourusername to your actual username... replace ext3 with ext2 or vfat or ntfs, depending on the filesystem its formatted in.

then to mount the partition without rebooting type
```

sudo mount -a

```

report any errors and we'll see what went wrong

---

### Post by ahaslam on 2007-07-19
I'd do:
sudo mount /dev/sda4 /wherever
sudo cp -a /home/youruserid /wherever
Add an entry to your fstab, mounting the new partition to /home
Reboot
Remove your previous directory

---

### Post by liorc666 on 2007-07-19
ok i did it 
its all went great 

~/Files
is now mounted

i got 1 problem 1 question 

the problem that my user cant write to this folder , only root can

and i useally install things with apt-get or synaptic can i tell apt-get to install things into there ? i mean useally its install it on 

~/.wine
~/.gimp
or such ... can it be : ~/Files/.<program name> ?

thanks

---

### Post by liorc666 on 2007-07-19
i didnt got your way ahaslam

you sueggest mount sda4 - to any folder
then copy the home folder to the folder 

and then what ?

---

### Post by bodhi.zazen on 2007-07-19
You should move your current home to a new partition and then add the space to that new home partition.

[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

---

### Post by Nythain on 2007-07-19
in terminal type
```

sudo chown 1000:1000 ~/Files

```
will change ownership from root to your user and group... at least thats how i have done and would do it...

---

