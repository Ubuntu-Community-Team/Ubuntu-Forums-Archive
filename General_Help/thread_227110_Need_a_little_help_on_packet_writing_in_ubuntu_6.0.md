---
title: "Need a little help on packet writing in ubuntu 6.06"
date: 2006-08-01
forum: General Help
---

### Post by fghubusdfs on 2006-08-01
cd-dvd packet writing is very useful and suitable feature (for me).

under the ms windows i am using nero incd.
at this site i found that packet writing is also available under ubuntu.

i found here 2 good topics on this theme:
"Nero InCD Equivalent for UBUNTU" and "Packet Writing without tears".
i set my system up as described in these topics.
and this works. but i have some problems and need help.

if i use cdrw disk that has been formatted with nero incd under the windows.
i can read and write this disk via gnome nautilus.
and files that been wrote under linux are visible under windows. Other words i can use incd disks in both, windows and linux systems.
but.
when i tried to format new disk under linux with
sudo cdrwtool -t 10 -d /dev/hdc -q -v 0x0150
or
sudo mkudffs --udfrev=0x0150 --media-type=cdrw /dev/pktcdvd/0
this makes new disk but i can't write this disk under linux.
when i try write this disk under linux (at nautilus) i always get:
"you have no permissions to write this".
Moreover, after i format cdrw with
sudo mkudffs --udfrev=0x0150 --media-type=cdrw /dev/pktcdvd/0
i can't use this disk under windows also - no free space at this disk.
And only if i use
sudo cdrwtool -t 10 -d /dev/hdc -q -v 0x0150
i can use this disk under windows, but not under linux.

i tried:
sudo chown 777 /media/udf/ (/media/udf/ is my mount point for /dev/pktcdvd/0)
sudo chown 777 /media/udf/.
and even
sudo chmod 666 /media/udf/
sudo chmod 666 /media/udf/.
sudo chown 777 /media/udf/*
sudo chmod 666 /media/udf/*
sudo chown -hR alex /media/udf
but nothing helps.


finally.
1) i can use udf disk under both linux and windows only if disk been formatted by nero incd.
2) i can use udf disk under windows if it has been formatted under linux with cdrwtool.
but i can't use this disk under linux.
3) i can't use disk under windows if it has been formatted with mkudffs.
4) i have 2 recorders at secondary pata channel: master is cdrw (/dev/hdc) slave dvdrw (/dev/hdd).
how can i use both of them with the packet writing?

can somebody help me?

my environment:
kernel 2.6.15-23-386
gnome
/etc/default/udftools: DEVICES="/dev/hdc /dev/sr0"
/dev/pktcdvd: root-root drwxr-xr-x
/dev/pktcdvd/0: root-root -rw-r-----
/dev/pktcdvd/pktcdvd0: root-cdrom -rw-rw----

---

### Post by mchatel on 2006-08-01
Hope you get this working like you want.  :)  I always find the people on these forums helpful.

Just a word of caution...  I hope you don't want to use packet-writing for files or anything too important, as it does tend to konk out at the worst possible time sometimes.  I've lost data before with packet writing.  Read the data fine once, 2nd time, it was gone, never to be seen again.  It's okay to use as a scratch disk, for just temporary stuff, but just realize it's not a reliable method of writing to re-writable media.

---

### Post by fghubusdfs on 2006-08-06
1 problem resolved with
sudo chmod -R 777 /media/udf
now i can r w disk that been formatted under linux.

---

### Post by Cariboo1938 on 2006-08-28
> **mchatel said:**
> Hope you get this working like you want.  :)  I always find the people on these forums helpful.

Just a word of caution...  I hope you don't want to use packet-writing for files or anything too important, as it does tend to konk out at the worst possible time sometimes.  I've lost data before with packet writing.  Read the data fine once, 2nd time, it was gone, never to be seen again.  It's okay to use as a scratch disk, for just temporary stuff, but just realize it's not a reliable method of writing to re-writable media.Hi mchatel, 
I believe I'm a bit slow, but I don't understand the warning. What is the reason for the instability? Is this a Linux specific problem. I never ever had any problems using packet writing under Windows XX! How did these guys solve the problem if there is one?

---

### Post by orb9220 on 2006-08-28
I have problems with packet writing in general mainly because of the media.

rw media is notorious for alot of the media crapping out 1,2,3,6 month's  down the line. And other systems with incd having problems reading them   from fresh burns.

Go to any video burning forum and they will tell you not to use rw media   . For serious archiving.

For the price +r or -r media are cheaper than rw and support multisessions.

So for me It seems redundant to do the inCD thing with rw's.

I have seen at least a couple of dozen people try it out and they came  away with a sour taste in thier mouth.

Just my opion if it works for you go for it.

---

### Post by trents on 2006-11-07
I use packet writing all the time under InCD/Windows. It is my main file storage option. I have found it to be pretty reliable with the  proviso that every several months I make a new disk. The media does tend to get scratched with constant use and the dye breaks down over time as well.

Looking at the string here, it seems as though packet writing in Linux is not yet user friendly drag and drop. I look forward to the time when it is all graphical and mouse controlled. Its on that list of things that keep me from being able to abandon Windows. In my opinion there are far too many Linux distros that have arisen and the open source community's energy and resources are too spread out. This has also discouraged hardware manufacturers from devoting resources to developing device drives for Linux. There are just too many varieties to have to cater to. A driver written for one distro will not work on the others. Sorry, I strayed from the original topic. 

Steve

---

