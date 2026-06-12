---
title: "kino and ieee1394"
date: 2005-05-04
forum: General Help
---

### Post by fsman on 2005-05-04
I'm trying to do some video editing in Ubuntu.
I installed Kino however I have run into some problems which I'd like some help

Firstly, the /dev/raw1394 device seems to only have root owner privilages by default. I have to manually change by 'sudo chmod 660 raw1394' on each boot. Shouldn't the device have group read and write access just like say a cdrom by default?
Is something wrong or is their a command to get the correct permissions loaded automatically.

Also, Kino itself seems to need to be run as root - otherwise it doesn't seem to always recognise the camcorder to set the AV/C controls in the perferences dialogue.


Anyone got kino working smoothly without having to resort to using sudo or root?

---

### Post by wwwolf on 2005-05-05
Interesting problem, after I installed my 1394 card and Kino I noticed the same thing. You probably have several options you can take:

1. You could probably edit the application menu and change the command to call Kino from 'kino %F' to something else that would allow you to execute 2 commands, something like:

'kino %F | sudo chmod 777 /dev/raw1394'

although this doesn't work because I don't know how to run sudo and satisfy the password in one step. If you can get the command syntax right then this would probably be the easiest way because then you could just forget about it and this added step of changing the permissions will be carried out automagically when kino is executed.

Another option is probably to modify the file MAKEDEV which lists the devices and their permissions at the beggining of the file. There are two MAKEDEV files in my system, one in .dev/ and one in sbin/
I have no idea which one needs to be edited though but this sounds like the script/file that will do it.

There are probably 193 other options/strategies you could employ but these are the only two I can think of at the moment.

HTH,

wwwolf
Oh, I just thought of another one, make a script to execute on startup that will change the permissions for you.  \\:D/

---

### Post by gstrock on 2005-07-14
give the group read-write permission on /dev/raw1394
and make sure you are a member of the group.

on my ubuntu 5.04 laptop that group is 'video'

> chmod g+rw /dev/raw1394

---

### Post by pixelnate on 2005-07-14
I am also interested in taking a crack at using Kino and Jahshaka. I am looking for a good 1394 card that work well with Ubuntu. Will this card work:
[Zonet VIA IEEE 1394 3+1 port PCI Card Model ZFN2600 - Retail](http://www.newegg.com/Product/Product.asp?Item=N82E16815106002) 

Thanks.

---

