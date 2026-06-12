---
title: "how to make a customized live cd"
date: 2007-04-05
forum: General Help
---

### Post by Apollo101 on 2007-04-05
we can installed an os (i use kubuntu 6.10) to HDD by a live cd. then we customize it. install programs. and do kde settings.

is there a way to reverse this. 
by making a live cd from the 'installed' os we already have?

if not.
how to customize the live cd of kubuntu 6.10 or 7.04? some easy way?

(get a live cd. change settings, install/uninstall apps. then recompile the live cd) ?

---

### Post by Apollo101 on 2007-04-05
we can install an os (i use kubuntu 6.10) to HDD by a live cd. then we customize it. install programs. and do kde settings.

is there a way to reverse this. 
by making a live cd from the 'installed' os we already have?

if not.
how to customize the live cd of kubuntu 6.10 or 7.04? some easy way?

(get a live cd, change settings, install/uninstall apps. then recompile the live cd) ?

---

### Post by Apollo101 on 2007-04-05
we can install an os (i use kubuntu 6.10) to HDD by a live cd. then we customize it. install programs. and do kde settings.

is there a way to reverse this. 
by making a live cd from the 'installed' os we already have?

if not.
how to customize the live cd of kubuntu 6.10 or 7.04? some easy way?

(get a live cd, change settings, install/uninstall apps. then recompile the live cd) ?

---

### Post by gavinjb on 2007-04-05
Hi,

I did a quick google and came up with the following, not sure if it is what you want

[http://www.atworkonline.it/~bibe/ubuntu/custom-livecd.htm](http://www.atworkonline.it/~bibe/ubuntu/custom-livecd.htm)
[http://dsplabs.utt.ro/~juve/blog/index.cgi/01147559232](http://dsplabs.utt.ro/~juve/blog/index.cgi/01147559232)

---

### Post by Apollo101 on 2007-04-05
for ubuntu , reconstructor is best for making live cd
but i use kubuntu. kde.


i dont want to mess with gnome. any other options i have?
any body?

---

### Post by phidia on 2007-04-05
[http://uck.sourceforge.net/](http://uck.sourceforge.net/)

Check that link out-good luck &  let us know how it works for you.

---

### Post by mssever on 2007-04-05
Check out [Reconstructor]("http://reconstructor.aperantis.com").

---

### Post by Apollo101 on 2007-04-06
reconstructor is for ubuntu i guess. its not for kubuntu 6.10 or 7.04

i downloaded (after much difficulties) not by adept package manager. its not available there.   installed. when i run it . it says no glade module found. i installed glade too. but no use. same msg again.

---

### Post by mssever on 2007-04-06
I don't know much about Kubuntu, but it *shouldn't* make much of a difference once you get it installed. It basically asks you for an ISO, then asks you to modify it. As long as it's an Ubuntu derivative, it should work.

Glade, however is part of GNOME, so your install problems might be due to missing GNOME dependencies for reconstructor itself. Maybe the Reconstructor package doesn't properly list all its dependencies...

---

### Post by Apollo101 on 2007-04-06
1.i used reconstructor. but i think thats for gnome ubuntu . not for kubuntu. iam using kubuntu 6.10 or 7.04.        a message appears saying no glade module.

2.this is what i get using uck. 


X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Preparing build environment...
Creating X authentication cookie...
Running build process...
Starting CD remastering on  Fri Apr 6 13:26:46 PKT 2007
Customization dir=/tmp/tmp.hubqAq7448
Mounting ISO image...
Removing ISO remastering dir
Mounting SquashFS image...
mount: unknown filesystem type 'squashfs'
Cannot mount /home/loguser1/tmp/remaster-iso/casper/filesystem.squashfs in /home
/loguser1/tmp/squashfs-source, error=32
Trying to unmount X11 sockets directory (ignore errors)...
Checking if unmounting directory /home/loguser1/tmp/remaster-root/tmp/.X11-unix
is necessary...
mountpoint: /home/loguser1/tmp/remaster-root/tmp/.X11-unix: No such file or dire
ctory
Directory /home/loguser1/tmp/remaster-root/tmp/.X11-unix not mounted.
Checking if unmounting directory /home/loguser1/tmp/remaster-root/lib/modules/*/
volatile is necessary...
mountpoint: /home/loguser1/tmp/remaster-root/lib/modules/*/volatile: No such fil
e or directory
Directory /home/loguser1/tmp/remaster-root/lib/modules/*/volatile not mounted.
Checking if unmounting directory /home/loguser1/tmp/remaster-root/proc is necess
ary...
mountpoint: /home/loguser1/tmp/remaster-root/proc: No such file or directory
Directory /home/loguser1/tmp/remaster-root/proc not mounted.
Checking if unmounting directory /home/loguser1/tmp/remaster-root/sys is necessa
ry...
mountpoint: /home/loguser1/tmp/remaster-root/sys: No such file or directory
Directory /home/loguser1/tmp/remaster-root/sys not mounted.
Checking if unmounting directory /home/loguser1/tmp/remaster-root/dev/pts is nec
essary...
mountpoint: /home/loguser1/tmp/remaster-root/dev/pts: No such file or directory
Directory /home/loguser1/tmp/remaster-root/dev/pts not mounted.
Checking if unmounting directory /home/loguser1/tmp/squashfs-source is necessary
...
/home/loguser1/tmp/squashfs-source is not a mountpoint
Directory /home/loguser1/tmp/squashfs-source not mounted.
Checking if unmounting directory /home/loguser1/tmp/iso-source2 is necessary...
mountpoint: /home/loguser1/tmp/iso-source2: No such file or directory
Directory /home/loguser1/tmp/iso-source2 not mounted.
Trying to unmount X11 sockets directory (ignore errors)...
Checking if unmounting directory /home/loguser1/tmp/remaster-root/tmp/.X11-unix
is necessary...
mountpoint: /home/loguser1/tmp/remaster-root/tmp/.X11-unix: No such file or dire
ctory
Directory /home/loguser1/tmp/remaster-root/tmp/.X11-unix not mounted.
Checking if unmounting directory /home/loguser1/tmp/remaster-root/lib/modules/*/
volatile is necessary...
mountpoint: /home/loguser1/tmp/remaster-root/lib/modules/*/volatile: No such fil
e or directory
Directory /home/loguser1/tmp/remaster-root/lib/modules/*/volatile not mounted.
Checking if unmounting directory /home/loguser1/tmp/remaster-root/proc is necess
ary...
mountpoint: /home/loguser1/tmp/remaster-root/proc: No such file or directory
Directory /home/loguser1/tmp/remaster-root/proc not mounted.
Checking if unmounting directory /home/loguser1/tmp/remaster-root/sys is necessa
ry...
mountpoint: /home/loguser1/tmp/remaster-root/sys: No such file or directory
Directory /home/loguser1/tmp/remaster-root/sys not mounted.
Checking if unmounting directory /home/loguser1/tmp/remaster-root/dev/pts is nec                              essary...
mountpoint: /home/loguser1/tmp/remaster-root/dev/pts: No such file or directory
Directory /home/loguser1/tmp/remaster-root/dev/pts not mounted.
Checking if unmounting directory /home/loguser1/tmp/squashfs-source is necessary                              ...
/home/loguser1/tmp/squashfs-source is not a mountpoint
Directory /home/loguser1/tmp/squashfs-source not mounted.
Checking if unmounting directory /home/loguser1/tmp/iso-source2 is necessary...
mountpoint: /home/loguser1/tmp/iso-source2: No such file or directory
Directory /home/loguser1/tmp/iso-source2 not mounted.
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device


and the message says: building failed please examine file build.log (i cant find this file too) which has been created in directory where you run the script
if you still cannot find the problem, please send post a support request at : launchpad.net/products/uck/+addticket

---

### Post by Apollo101 on 2007-04-06
i installed glade too. and all other dependencies manully. but still i get this message., because i didnt found it in adept package manager.  (any easy way to install it?)




i also used uck. ubuntu customization kit
this is what i got from it .

X Error: BadDevice, invalid or uninitialized input device 168
Major opcode: 145
Minor opcode: 3
Resource id: 0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
Major opcode: 145
Minor opcode: 3
Resource id: 0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
Major opcode: 145
Minor opcode: 3
Resource id: 0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
Major opcode: 145
Minor opcode: 3
Resource id: 0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
Major opcode: 145
Minor opcode: 3
Resource id: 0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
Major opcode: 145
Minor opcode: 3
Resource id: 0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
Major opcode: 145
Minor opcode: 3
Resource id: 0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
Major opcode: 145
Minor opcode: 3
Resource id: 0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
Major opcode: 145
Minor opcode: 3
Resource id: 0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
Major opcode: 145
Minor opcode: 3
Resource id: 0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
Major opcode: 145
Minor opcode: 3
Resource id: 0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
Major opcode: 145
Minor opcode: 3
Resource id: 0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
Major opcode: 145
Minor opcode: 3
Resource id: 0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
Major opcode: 145
Minor opcode: 3
Resource id: 0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
Major opcode: 145
Minor opcode: 3
Resource id: 0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
Major opcode: 145
Minor opcode: 3
Resource id: 0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
Major opcode: 145
Minor opcode: 3
Resource id: 0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
Major opcode: 145
Minor opcode: 3
Resource id: 0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
Major opcode: 145
Minor opcode: 3
Resource id: 0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
Major opcode: 145
Minor opcode: 3
Resource id: 0x0
Failed to open device
Preparing build environment...
Creating X authentication cookie...
Running build process...
Starting CD remastering on Fri Apr 6 13:26:46 PKT 2007
Customization dir=/tmp/tmp.hubqAq7448
Mounting ISO image...
Removing ISO remastering dir
Mounting SquashFS image...
mount: unknown filesystem type 'squashfs'
Cannot mount /home/loguser1/tmp/remaster-iso/casper/filesystem.squashfs in /home
/loguser1/tmp/squashfs-source, error=32
Trying to unmount X11 sockets directory (ignore errors)...
Checking if unmounting directory /home/loguser1/tmp/remaster-root/tmp/.X11-unix
is necessary...
mountpoint: /home/loguser1/tmp/remaster-root/tmp/.X11-unix: No such file or dire
ctory
Directory /home/loguser1/tmp/remaster-root/tmp/.X11-unix not mounted.
Checking if unmounting directory /home/loguser1/tmp/remaster-root/lib/modules/*/
volatile is necessary...
mountpoint: /home/loguser1/tmp/remaster-root/lib/modules/*/volatile: No such fil
e or directory
Directory /home/loguser1/tmp/remaster-root/lib/modules/*/volatile not mounted.
Checking if unmounting directory /home/loguser1/tmp/remaster-root/proc is necess
ary...
mountpoint: /home/loguser1/tmp/remaster-root/proc: No such file or directory
Directory /home/loguser1/tmp/remaster-root/proc not mounted.
Checking if unmounting directory /home/loguser1/tmp/remaster-root/sys is necessa
ry...
mountpoint: /home/loguser1/tmp/remaster-root/sys: No such file or directory
Directory /home/loguser1/tmp/remaster-root/sys not mounted.
Checking if unmounting directory /home/loguser1/tmp/remaster-root/dev/pts is nec
essary...
mountpoint: /home/loguser1/tmp/remaster-root/dev/pts: No such file or directory
Directory /home/loguser1/tmp/remaster-root/dev/pts not mounted.
Checking if unmounting directory /home/loguser1/tmp/squashfs-source is necessary
...
/home/loguser1/tmp/squashfs-source is not a mountpoint
Directory /home/loguser1/tmp/squashfs-source not mounted.
Checking if unmounting directory /home/loguser1/tmp/iso-source2 is necessary...
mountpoint: /home/loguser1/tmp/iso-source2: No such file or directory
Directory /home/loguser1/tmp/iso-source2 not mounted.
Trying to unmount X11 sockets directory (ignore errors)...
Checking if unmounting directory /home/loguser1/tmp/remaster-root/tmp/.X11-unix
is necessary...
mountpoint: /home/loguser1/tmp/remaster-root/tmp/.X11-unix: No such file or dire
ctory
Directory /home/loguser1/tmp/remaster-root/tmp/.X11-unix not mounted.
Checking if unmounting directory /home/loguser1/tmp/remaster-root/lib/modules/*/
volatile is necessary...
mountpoint: /home/loguser1/tmp/remaster-root/lib/modules/*/volatile: No such fil
e or directory
Directory /home/loguser1/tmp/remaster-root/lib/modules/*/volatile not mounted.
Checking if unmounting directory /home/loguser1/tmp/remaster-root/proc is necess
ary...
mountpoint: /home/loguser1/tmp/remaster-root/proc: No such file or directory
Directory /home/loguser1/tmp/remaster-root/proc not mounted.
Checking if unmounting directory /home/loguser1/tmp/remaster-root/sys is necessa
ry...
mountpoint: /home/loguser1/tmp/remaster-root/sys: No such file or directory
Directory /home/loguser1/tmp/remaster-root/sys not mounted.
Checking if unmounting directory /home/loguser1/tmp/remaster-root/dev/pts is nec essary...
mountpoint: /home/loguser1/tmp/remaster-root/dev/pts: No such file or directory
Directory /home/loguser1/tmp/remaster-root/dev/pts not mounted.
Checking if unmounting directory /home/loguser1/tmp/squashfs-source is necessary ...
/home/loguser1/tmp/squashfs-source is not a mountpoint
Directory /home/loguser1/tmp/squashfs-source not mounted.
Checking if unmounting directory /home/loguser1/tmp/iso-source2 is necessary...
mountpoint: /home/loguser1/tmp/iso-source2: No such file or directory
Directory /home/loguser1/tmp/iso-source2 not mounted.
X Error: BadDevice, invalid or uninitialized input device 168
Major opcode: 145
Minor opcode: 3
Resource id: 0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
Major opcode: 145
Minor opcode: 3
Resource id: 0x0
Failed to open device


and the message says: building failed please examine file build.log (i cant find this file too) which has been created in directory where you run the script
if you still cannot find the problem, please send post a support request at : launchpad.net/products/uck/+addticket

---

### Post by Apollo101 on 2007-04-06
i re installed ubuntu instead of kubuntu
and the installed reconstructor. it worked
but it only have my three choices to change. i think like splash screen or something like that.

i wanted to change add remove softwares and desktop settings.
how is that possible?

---

### Post by Apollo101 on 2007-04-06
uck is giving errors in ubuntu too.


i re installed ubuntu instead of kubuntu
and the installed reconstructor. it worked
but it only have my three choices to change. i think like splash screen or something like that.

i wanted to change add remove softwares and desktop settings.
how is that possible?

---

### Post by Apollo101 on 2007-04-06
uck gives errors to me

i re installed ubuntu instead of kubuntu
and the installed reconstructor. it worked
but it only have my three choices to change. i think like splash screen or something like that.

i wanted to change add remove softwares and desktop settings.
how is that possible?

---

### Post by linear on 2007-04-06
Have you seen the instructions [here]("https://help.ubuntu.com/community/LiveCDCustomization/6%2e06")?

Written for Dapper, but you should be able to adapt them.

---

### Post by mssever on 2007-04-06
Isn't there such an option somewhere? I've never actually made a CD with Reconstructor, so I'm about as far from an expert as possible.

---

### Post by smartboyathome on 2007-04-23
If you are still wanting to do this, you can try reading this:
[https://help.ubuntu.com/community/LiveCDCustomization/6%2e06](https://help.ubuntu.com/community/LiveCDCustomization/6%2e06)

Or looking for an article on the list on this page:
[https://wiki.ubuntu.com//LiveCDCustomizationHowTo](https://wiki.ubuntu.com//LiveCDCustomizationHowTo)

---

