---
title: "SSH and USB"
date: 2013-03-06
forum: General Help
---

### Post by georgesgiralt on 2013-03-06
Hello !
I've two computers running 12.04 LTS.
One called tower has an USB scanner (Epson 2450) attached. The other, a laptop.
On the tower computer to use the scanner I open a terminal and launch vuescan scanning software by using /opt/Vuescan/vuescan.
Yesterday, my wife was using the tower computer. Instead of lockin her session and opening a new one, I decided to use the laptop. So I ran, on a terminal on the laptop :ssh -X tower.
Then I typed /opt/Vuescan/vuescan and the software complained that there where no scanner attached it can open. 
So I checked dmesg and lsusb to see that the scanner was actually here. 
I then modified the X settings on the laptop and ran on the tower the software as root (sudo su -) then set the DISPLAY correectly and ran /opt/Vuescan/vuescan to see that, now, the scanner was here and that the software was apt to use it.

Question :
Why can I access the usb scanner when I ran "Application -Accessories -Terminal " and not when I use ssh -X <machine> ? As far as I know, I use the same credentials, and the same devices/access methods ? 


Many thanks in advance for your help and advice !

---

### Post by TheFu on 2013-03-06
I don't use "vuescan", but I suspect this is a group permissions issue.  Check that you are in the group (id) that the scanner device in /dev/ is. Also make certain that the /dev/{scanner} allows group "rw" permissions.

If you used **sudo -s** instead of sudo -i, then you would have retained your **ssh -X** DISPLAY settings.  **man sudo** explains all.

BTW, i use **gscan2pdf** to scan documents.  Reasonable OCR (multiple methods) and conversion to many different formats built into the GUI. Of course, it uses multiple, proven, F/LOSS tools under the covers.

---

### Post by georgesgiralt on 2013-03-06
Hello !
Thanks for your answer.
But, how do you explain that the whole thing works when I start the shell using the applications menu and not while using ssh -X to connect to the machine ? I retain the same identity, such the same rights both ways... Or is the graphical interface doing something unclear and not done by the login process ?

---

### Post by albandy on 2013-03-06
Don't know where is the problem, but
Why don't you use sane to create a network scanner?
Look "Sharing a Scanner Over a Network" in [https://help.ubuntu.com/community/ScanningHowTo](https://help.ubuntu.com/community/ScanningHowTo)

---

### Post by TheFu on 2013-03-06
> **georgesgiralt said:**
> Hello !
Thanks for your answer.
But, how do you explain that the whole thing works when I start the shell using the applications menu and not while using ssh -X to connect to the machine ? I retain the same identity, such the same rights both ways... Or is the graphical interface doing something unclear and not done by the login process ?

I cannot explain that - I do not use the GUI.  If you specified the exact GUI you are using and OS, then someone else* _might_* be able to help.  
It could be a "feature" of vuescan too.  Commercial software often does things like this to prevent unlicensed uses.

---

### Post by georgesgiralt on 2013-03-06
The GUI is Gnome 2D no effects. The version is 12.04 LTS. And I've checked with Vuescan team, it's not vuescan... 
All software (except vuescan of course) come from the standard Ubuntu repositories and the software are kept up to date.

---

### Post by TheFu on 2013-03-06
> **georgesgiralt said:**
> The GUI is Gnome 2D no effects. The version is 12.04 LTS. And I've checked with Vuescan team, it's not vuescan... 
All software (except vuescan of course) come from the standard Ubuntu repositories and the software are kept up to date.

[LIST]
[*]What command does the menu run?
[*]Can you run that exact command in an ssh -X session? Does it work or not? Any error messages?
[*]What are the device permissions for the scanner in /dev/?
[*]Is your userid in the correct group?
[*]Running as root may reset permissions for some files and config files.
[*]
[/LIST]

---

### Post by kuifje09 on 2013-03-06
I also think it is a permissions issue. You could try as a test the same,  on the laptop run a ssh to the tower and start the vuescan.
But when no-one has logged in on the tower. It must be possible to do what you want, because as root it works. And root, as you already saw, has a lot more permissions then a regular user. My guesss, if someone logged in on the tower, all devices become owened by that user.
So you could also test, login on the tower, ( all devices are yours ) and then log in from the laptop and run vuescan.
It isn't an X problem, then it would not run as root either. This also confirms, your vuescanner is X-Display aware.

Edit, you could easily see who owns the scanner by ls -l /dev/{Scandevice}

---

### Post by kuifje09 on 2013-03-06
I have tried the same as you are using ( even an epson 2400 )

Which user is logged in is not an issue, mabe when he/she is using the scenner ;)

When the remote user is trying to use the scanner, that user has to be allowed to use the scanner ( user profiles )
Then it must be possible to do what you want. ( I tested it with scanimage -x 100 -y 100 --format=tiff >out.tiff )

The user logged in local had uid 1000  and the remote had 1001.  Have a look at the permissions , menu-Other,user-groups.
Dont forget , its about the numbers, not the names.

update : you can check local and after the ssh....   with ls -l /dev/bus/usb/002/002 ( in my case )  and getfacl /dev/bus/usb/002/002 
Exact path could be found in dmesg after plugging the scanner.

---

### Post by georgesgiralt on 2013-03-06
So, 
I've played a bit with this : 
My wife is connected to the tower.
I do an "ssh -X tower" from the laptop and got a shell with my ID :
```
georges@tower:~$ id
uid=1000(georges) gid=1000(georges) groups=1000(georges),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),109(lpadmin),124(sambashare)
georges@tower:~$ 

```
Then I started the scanner :
```

georges@tower:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 2001:f103 D-Link Corp. DUB-H7 7-port USB 2.0 hub
Bus 002 Device 002: ID 046d:c30a Logitech, Inc. iTouch Composite
Bus 002 Device 003: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel Mouse
Bus 001 Device 005: ID 04b8:0112 Seiko Epson Corp. Perfection 2450
georges@tower:~$ ll /dev/bus/usb/001/005
crw-rw-r--+ 1 root root 189, 4 mars   6 19:07 /dev/bus/usb/001/005
georges@tower:~$getfacl /dev/bus/usb/001/005
getfacl: Removing leading '/' from absolute path names
# file: dev/bus/usb/001/005
# owner: root
# group: root
user::rw-
user:nicole:rw-
group::rw-
group:scanner:rw-
mask::rw-
other::r--

georges@tower:~$

```
Then, I locked my wife's session and logged in on the tower. Just log-in. Done nothing. 
Guess what ? 
```

georges@tower:~$ getfacl /dev/bus/usb/001/005
getfacl: Removing leading '/' from absolute path names
# file: dev/bus/usb/001/005
# owner: root
# group: root
user::rw-
user:georges:rw-
group::rw-
group:scanner:rw-
mask::rw-
other::r--

georges@tower:~$ id
uid=1000(georges) gid=1000(georges) groups=1000(georges),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),109(lpadmin),124(sambashare)
georges@tower:~$ 

```
The rights on the shell given by ssh have changed.... 
What does the session manager ? Why ? Why this action is not made *also*  by the pam system when I log-in with ssh ??? 
All your help will be appreciated !
P.S. : If I log out from the tower and let the locked session live it's life, I get this for the usb device file :
```

georges@tower:~$getfacl  /dev/bus/usb/001/005
getfacl: Removing leading '/' from absolute path names
# file: dev/bus/usb/001/005
# owner: root
# group: root
user::rw-
user:lightdm:rw-
group::rw-
group:scanner:rw-
mask::rw-
other::r--

georges@tower:~$

```

---

### Post by kuifje09 on 2013-03-06
I have to check for the permisions I have in bothe cases, but I get the idea 12.04 does something different then 11.10 I use.
Unfortunedly I cannot check it right now, but I will post them!

---

### Post by TheFu on 2013-03-06
Console users have special permissions to local devices.  Start there.  I've seen this with audio playback.  I used to be able to ssh in and control speakers connected to the server. At some point, that stopped and I honestly never had a need to research it further.

Strangely, I was in the /etc/fuse.conf file and noticed a setting there #user_allow_other - seems that local users can fuse mount drives. 

I bet all the code used to make this happen was seen as a great solution to some other problems.  Perhaps if you add both your IDs to the scanner group?  The plugdev group might have something to do with this too, but I'm 100% guessing on that.

---

### Post by kuifje09 on 2013-03-07
Well, if read the story well, then georgesgiralt is running in a gui, on both machines, and just wants to scan from the commandline.

I did the test and see the same permissions as you do, but I can scan ! Maybe its an issue with vuescan, I do'nt know.
This is what I did and saw :
```

Bus 002 Device 002: ID 04b8:011b Seiko Epson Corp. Perfection 2400 Photo
wim@grey:~$ ls -l /dev/bus/usb/002/002
crw-rw-r--+ 1 root root 189, 129 2013-03-07 12:51 /dev/bus/usb/002/002
wim@grey:~$ getfacl /dev/bus/usb/002/002
getfacl: Removing leading '/' from absolute path names
# file: dev/bus/usb/002/002
# owner: root
# group: root
user::rw-
user:wim:rw-
group::rw-
group:scanner:rw-
mask::rw-
other::r--

wim@grey:~$ ssh -X browser@localhost
browser@localhost's password: 
Welcome to Ubuntu 11.10 (GNU/Linux 2.6.38-16-generic i686)

 * Documentation:  https://help.ubuntu.com/

32 packages can be updated.
32 updates are security updates.

New release '12.04.2 LTS' available.
Run 'do-release-upgrade' to upgrade to it.

Last login: Wed Mar  6 16:13:23 2013 from 192.168.123.117
browser@grey:~$ ls -l /dev/bus/usb/002/002
crw-rw-r--+ 1 root root 189, 129 2013-03-07 12:51 /dev/bus/usb/002/002
browser@grey:~$ getfacl /dev/bus/usb/002/002
getfacl: Removing leading '/' from absolute path names
# file: dev/bus/usb/002/002
# owner: root
# group: root
user::rw-
user:wim:rw-
group::rw-
group:scanner:rw-
mask::rw-
other::r--

browser@grey:~$ scanimage -x 100 -y 100 --format=tiff >out.tiff
browser@grey:~$

```

I ran it indeed from the localhost to the localhost using ssh -X, because there is no difference with a reel remote host.
May be, to be shure, you could test with scanimage?  I don't see a clue to why it does not work at your site.

---

### Post by kuifje09 on 2013-03-07
Wow, just an update, I oversaw this,

To use the scanner you must be a member of the group scanner or the owner of the device.
So root can do all, but in the last pane, george is not in the group scanner while lightdm is owner.

I think you have to add george to the scanner group.

When I try to use the scanner over ssh, with a user not in the scannergroup, i get the error:
scanimage: no SANE devices found

So that must be your solution.


( I think lightdm becomes owner of the device, because it is locked by lightdm for the already logged-in user )

---

### Post by georgesgiralt on 2013-03-07
Hello !
I did not make myself clear. 
If I log in using the graphical console, and then, start a shell and launch Vuescan, I can access the scanner and do my job. Even if someone else is *already* logged on on the console. 
If I log in using ssh I get the shell directly. Why the heck can't I access the scanner ? Am I a second class user ? What is different in the login process between the graphical user interface and ssh ? And why is there THIS difference ? (if there is one, and actually there is, what else is different? .....)
And why are the ACL on the device file change so often.... (in this case, before I log in, the device file belongs to root with an acl to nicole, then when I log in on the graphical interface, the acl gives me the right to use the scanner. Then, when I log out, the device acl does not revert to nicole but to lightdm.... Nonsense.)
Since then, I've found a workaround, but .... intellectually, this is not good enough.

---

### Post by kuifje09 on 2013-03-08
Hi georgesgiralt,

Thats exact the problem...

You never are member of the scannergroup, so if you are the first to log in, you are the owner of the scanner.
When you login as second or via the network you must exist in the scanner group.
So you must be the owner of the scanner, check with "getfacl", or must be member of the scannergroup, check with  "id".

---

### Post by georgesgiralt on 2013-03-08
No, I *do* disagree.
The system behind the graphical login does idiot things. It changes acl of devices files without mercy nor rationality. I would understand if the acl gives ownership of the scanner to "nicole", the first logged user. I am dubious of the fact that the owner change to "georges" when I log in graphically. But this whole things becomes stupid when it revert the acl to "lightdm" when I log out. Worse than stupid. Add to this that this mechanism is not triggered at all when logged through ssh and you have an useless and stupid thing.  
And this is not related to scanner also. This behavior is the same for a whole bunch of devices....

---

### Post by kuifje09 on 2013-03-09
I understand what you mean but I think it is a little different organized.
It may look as strange behaviour, but also it is just a way it is designed. And I am shure, I couldnt do it better.
And last but not least, if you are in the scanner group, you can alway access the scanner, so what's the point.
Over the network you never become the owner of the scanner, so take it or leave it. ( I dont mean this in a bad way. )
I would say , better al devices are from root or the display manager. Although I don't know what the display manager has to deal with devices at all.
It could be considered as a bit more secure when you can oly use a device when it is stricly given to you. As now by the group permission.
But either way , it is a choice.

Maybe add yourself to the scanner group and tell if thats a working solution. It can be at help for others.

---

