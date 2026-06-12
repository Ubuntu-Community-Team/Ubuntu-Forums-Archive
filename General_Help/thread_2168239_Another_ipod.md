---
title: "Another ipod"
date: 2013-08-17
forum: General Help
---

### Post by dudemon2 on 2013-08-17
Windows crashed, my buddy loaded me up with ubuntu, have been really diggin' it, but my skills are limited to browsen the web and listening to music =) Here is my problem:

After reviewing numerous and specifically this thread, [http://ubuntuforums.org/showthread.php?t=1823227](http://ubuntuforums.org/showthread.php?t=1823227), (though i have a 7th gen nano) i am still at a loss. 

7th gen nano is recognized in banshie, rhythm box, and gtkpod. 
Music can be dragged to the device and appears as though it is there, however after disconnecting the device, no music is found.

I went through the steps in the thread (posted from here [http://downloadsquad.switched.com/2008/03/18/enable-support-for-7th-gen-ipods-in-ubuntu/](http://downloadsquad.switched.com/2008/03/18/enable-support-for-7th-gen-ipods-in-ubuntu/))

run "sudo lsusb -v | grep -i Serial" 
then copy the 16 digit code, 
run "sudo gedit /mnt/ipod/iPod_Control/Device/SysInfo," 
and lastly paste the 16 code after "FirewireGuid: 0x" in the text editor file which opens after running "sudo gedit /mnt/ipod/iPod_Control/Device/SysInfo"

when i hit save i am greeted with the error message "could not find the file /mnt/ipod/ipod_control/device/sysinfo..."

what am i doing incorrectly? 

funny thing, my iphone 3gs (which has not been updated from the original version/software) loads music no problem from banshie, rhythm box and gtkpod...\\:D/...but the headphone jack receiver cuts in and out.

---

### Post by dentaku65 on 2013-08-17
Hi, 
are you sure that the ipod is mounted on **/mnt** ?
If the device is automounted I supposed that resides on **/media** instead
Can you post the output of this?
```
df -H
```
of course with ipod plugged in

---

### Post by GreatDanton on 2013-08-17
For syncing mine (5th gen) I am using Clementine, since gtkpod was not working properly for me either.

Regards.

---

### Post by dudemon2 on 2013-08-17
[COLOR=#000000]greatdanton[/COLOR], thanks for the tip. clementine is nice. the side bar on the left makes navigating for music easy. the clementine icon is pretty cool too. however, when i went to add a song to my device i recieved the error message:

"Unsupported checksum type"

dentaku65, i am not sure. too begin with, i only followed those instructions because the problem seemed similar to mine....while entering the codes i am essentially blind, other than being able to guide myself through the steps.  

i believe you are correct that the device resides on /media as i ran the code you suggested, "[FONT=Ubuntu Mono, monospace][COLOR=#000000]df -H" with my nano plugged in and the output i received was:[/COLOR][/FONT]

Filesystem      Size  Used Avail Use% Mounted on
...
...
...
...
...
...
/dev/sr0        722M  722M     0 100% /media/Jan 08 2012
/dev/sdb1        16G  274M   16G   2% /media/dudemon

---

