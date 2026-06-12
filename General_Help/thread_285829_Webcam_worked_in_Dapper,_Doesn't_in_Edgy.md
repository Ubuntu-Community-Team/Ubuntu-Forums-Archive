---
title: "Webcam worked in Dapper, Doesn't in Edgy"
date: 2006-10-27
forum: General Help
---

### Post by Ambimom on 2006-10-27
I've had the most horrible time upgrading. 

My Logitech quickcam pro 4000 webcam worked in Dapper, but doesn't in Edgy.  The device manager recognizes it.  Camorama loads with it, but it just has gray screen...no picture.  I can take picture, but it is gray too.

I'm beginning to hate Edgy.  

I've searched the forums for solutions, but I'm relatively noobie....nothing makes sense.  Anyone got a suggestion?

---

### Post by Psychobudgie on 2006-10-28
I'll second this

---

### Post by fragos on 2006-10-28
Since a new kernel was installed, any driver you compiled for use in Dapper must now be recompiled for Edgy.

---

### Post by ~LoKe on 2006-10-28
I've got a different problem.  It'll show my webcam, but if I change the view from medium to large, it crashes saying it can't capture the image. o_O

---

### Post by trash on 2006-10-28
same deal with the logitech quickcam 3000 pro, i haven't really had time to look into it much yet though, but i think the drivers were preinstalled with dapper(maybe?) so they should be in edgy.

---

### Post by Psychobudgie on 2006-10-29
> **fragos said:**
> Since a new kernel was installed, any driver you compiled for use in Dapper must now be recompiled for Edgy.

the driver was installed with dapper. Nothing to recompile as far as I'm aware.

regards,

pb

---

### Post by KoolPenguin on 2006-10-29
I also have problems.  Logitech Quickcam for notebooks works in Dapper and in Edgy the audio works but I get an error for the video. I have tried everything with no luck.  Anyone have a suggestion?  Specs:

usb Logitech Quickcam for Notebooks
Dell Latitude CPx laptop
kernel 2.6.17-10-generic

lsusb:

Bus 001 Device 005: ID 046d:08ae Logitech, Inc. 

lsmod: (not listing all, just what I think is useful)

Module                  Size  Used by
spca5xx               637648  0 
zc0301                 42244  0 
snd_usb_audio          80416  0 
snd_usb_lib            18816  1 snd_usb_audio
snd_hwdep              10756  1 snd_usb_audio
v4l2_common            17280  1 zc0301
videodev               10752  2 spca5xx,zc0301
usbcore               134912  9 spca5xx,zc0301,snd_usb_audio,snd_usb_lib,usb_storage,libusual,usbhid,uhci_hcd

When using Ekiga, the audio test works however the video test fails. I get an Error While Opening /dev/.static/dev/video0

Thanks.

---

### Post by fragos on 2006-10-29
You may want to the following driver.  Its an spca5xx replacement for newer kernels like the one in Edgy.  This is the developers site and has a lot of interesting information, like compatability, and a number of viewer options.

[http://mxhaard.free.fr/spca50x/Download/gspcav1-20060925.tar.gz](http://mxhaard.free.fr/spca50x/Download/gspcav1-20060925.tar.gz)

---

### Post by KoolPenguin on 2006-10-30
Using the link provided did the job, thanks!

[http://mxhaard.free.fr/spca50x/Download/gspcav1-20060925.tar.gz]("http://mxhaard.free.fr/spca50x/Download/gspcav1-20060925.tar.gz")

---

### Post by Wesseli on 2006-10-31
How do I install that driver mentioned above? I couldn't get it done. Using Edgy 6.10. What do I have to type to konsole? Gettin' frustrated to this ](*,) 

Thanks

---

### Post by fragos on 2006-10-31
Open up a terminal window, cd to the directory you expanded the archive in  and run the shell script gspca_build as root.

---

### Post by trash on 2006-10-31
anybody got any advice, i can't get past make... just hangs at 'leaving directory `/usr/src/linux-headers-2.6.17-10-386'

---

### Post by fragos on 2006-10-31
What are you trying to compile.  If its the package I mentioned about you should execute gspca_build.  The developer took the time to create a shell script that does it all for us.  Its always best to stick with the directions.

---

### Post by trash on 2006-10-31
I am executing that file... could i be missing something gnome has that is needed, i'm using xfce.
I don't see any other directions  than what you posted, not even on their website

EDIT: i forgot to mention that before this i tried easycam nd it also hung at makeinstall.. not sure if this helps clarify anything.

---

### Post by fragos on 2006-10-31
I have no experience with xfce.  I looked at the shell script.  Bash is bash regardless of the window manager but perhaps the directory usage is different which would result in files not being found.  Ubuntu has a package called build-essentials that most of what you need to compile.  I don't know how that relates to xfce.  You might also need a copy of the kernel source.  I'm running Ubuntu 6.10 Gnome and used Synaptic to install the packages I mentioned.  I don't know how Synaptic relates to xfce.  Hopefully something I said will help you find your problem.

---

### Post by trash on 2006-10-31
seems i have everything i need, i even found spca5xx-source in the repos and all dependencies were satisfied. thanks anyway, i just keep tinkering till somethin happens lol

---

### Post by funbags on 2006-11-03
This is what fixed it for me 

[http://ubuntuforums.org/showthread.php?t=282748](http://ubuntuforums.org/showthread.php?t=282748)

---

### Post by trash on 2006-11-03
> **funbags said:**
> This is what fixed it for me 

[http://ubuntuforums.org/showthread.php?t=282748](http://ubuntuforums.org/showthread.php?t=282748)

fixed my logitech 3000 pro too:)

---

### Post by cyber_bushi on 2007-01-12
I use ubuntu Edgy, but only get a black screen when i use camorama with my logitech qc for notebooks. Any Ideas?

regards,

cb

---

### Post by fragos on 2007-01-12
Try adjusting the brightness and or contrast.  Image from the camera may not agree with what the software calls anormal image.  This was the case with my new Logitech QC chat.

---

### Post by cyber_bushi on 2007-01-12
> **fragos said:**
> Try adjusting the brightness and or contrast.  Image from the camera may not agree with what the software calls anormal image.  This was the case with my new Logitech QC chat.

I tried everything in camorama but it didn't work out... :( only black screen... cept for if i use the invert filter - then white screnn... ;)
i think i'm gonna give it up for now... ](*,) 

with win i had the same probs with brightness but i managed to set it correctly but here it doesn't work... :(

---

### Post by cyber_bushi on 2007-01-13
it was not the brightness and so on... just plugging the cam in a seperate usb-port did the job...  guess it doesn't like to be one among many on the hub... ;) thanks for all the help!

regards,

cb

---

### Post by fragos on 2007-01-13
> **cyber_bushi said:**
> it was not the brightness and so on... just plugging the cam in a seperate usb-port did the job...  guess it doesn't like to be one among many on the hub... ;) 
cb

Just curious, was the hub powered separately?

---

### Post by cyber_bushi on 2007-02-01
yes - the hub is actually a quite expensive usb switch and is powered separately...

---

