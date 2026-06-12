---
title: "USB webcam only support windows..what can i do?"
date: 2007-10-30
forum: General Help
---

### Post by billy99 on 2007-10-30
hi guys..im new to ubuntu and i like it so far.

i do have a problem with my USB webcam.

thats the camera:

[http://www.smart-com.net/product_info.php?cPath=35&products_id=93](http://www.smart-com.net/product_info.php?cPath=35&products_id=93)

as u can see it sais it support windows.

is there a way i can make it work in my new linux ubuntu 7.04?

at the moment..when i start a ubuntu session the camera light turns on<on the camera itself..not on the screen>..but i dont know how to acsses it or see the broadcast.

any ideas?

thanks in advance.....

---

### Post by linuxwizard on 2007-10-30
[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

---

### Post by Vadi on 2007-10-30
File - Graphics - XSane Image Scanner. See if it works!

---

### Post by Purplecatty on 2007-10-30
I got both Logitech Quickcam 4000 Pro and Quickcam Fusion working.  You'll have to install Video4Linux2 (v4L2) from Synapic package manager and also Videoview software (free download, you'll have to google search).. I managed to get the video working!  The video is not exactly smooth but works. BUT I have not TRIED to use Kopete that have video chat option.  I personally am still learning.  I wish there are some way that allow us to test and view video and even broadcast it.  There is a compatibily on USB webcams that supports windows but supports Linux.  It's just the chipset issue that Some are compatible with Linux.  here is the website
[http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)

I'm using Ubuntu Gusty Gibbon 7.10
I hope this would help you.

Thanks
Catty

---

### Post by billy99 on 2007-10-30
thanks guys for helping!

vadi - i try that...but it didnt work.

purplecatty - thanks for your help...it was a bit comfusing to me being a newbie but ill try it later if the problem will not be solved.

linuxwizard -  that link might help but i didnt find my webcam model there...do u think it can still work?

also - i had some trouble installing easycam.im on ubnutu 7.04 and couldnt find how exactially do i add the Repositories...is that in the "third party software" tab?

or maybe in the "authentication" tab?

and after i add the adress  - deb [http://blognux.free.fr/debian](http://blognux.free.fr/debian) unstable main

how do i update the  packages?

what should i do with the line "sudo apt-get update"?

sorry for the dumb questions..im new and trying to learn..:)

thanks again

---

### Post by linuxwizard on 2007-10-30
in terminal copy & paste > sudo apt-get update > enter password > press enter

---

### Post by billy99 on 2007-10-30
thanks wizard...and in which tab in  "software sources" do i paste the adress "deb [http://blognux.free.fr/debian](http://blognux.free.fr/debian) unstable main"  ?

and do u think it might work with my camera model?

---

### Post by linuxwizard on 2007-10-30
click on add tab > than their should be custom tab > click on > paste there

All you can do is try EasyCam see if it works.

---

### Post by billy99 on 2007-10-31
well i tried..installed the program easycam..but it didnt fix my webcam.too bad.

i guess its hopeless.

at least i learned a few things.

thanks for trying

---

### Post by Vadi on 2007-10-31
Well, could you give a review for the cam on ubuntuhcl.com then, so others know? And post your email too - maybe someone will get it working, so then they'll contact ya.

---

### Post by billy99 on 2007-10-31
yes i already sent a email to the easycam programmer with all the details..hopefully they could make it work in the future.

---

### Post by Purplecatty on 2007-11-06
Wish you a good luck for someone to build driver for your webcam.  

    Or you could find another webcam that is compatible with Linux.  If you see what's listed there, It should work.   Try Logitech or Creative webcams (or whichever webcams brand on list that works with Linux well).  Most Logitech webcam works.  But there are some certain Logitech webcam may have some issue with Linux driver.  I have Logitech Fusion (2006 model) and it works but some adjustments are "shaded out".  Also It have issue with Frame Per Second speed which is a problem with my Fusion webcam (I don't know what it's fps but it look like 15fps instead of 30 fps..it's the chipset itself) I use Videoview that I downloaded (you only need to extract it to new folder and run it from there, very straightfoward program).  You must download Video4Linux2 driver or other driver that will work with webcam and run Videoview,  This program allow you to take snapshots and AVI video. As for Kopete built in videochat. The fps is too slow for me to use sign language to chat with other deaf video chatter, it worked great on Windoz using OOVOO videochat software (wishin' oovoo.com build one for linux!!).  But if you use VirtualBox or any Virtual Machine inside Linux,  It'll work but fps is sloowww)....  Newer Logitech Webcam do not have problem with it on linux driver. 

I borrowed my friend's Logitech Quickcam 4000 Pro and it worked and able to adjust most settings  FPS is pretty much the same as Fusion (but the sensor are different, 4000 Pro use CCD while Fusion use High Quality CMOS).  Problem is that when my son play Miniclip.com game that uses webcam to play game,  The screen inside little flash player window showing resolution that was too high and can't see pix (just like old tv with vertical phase problem).  There's nothing much I can do because I'm just plain noob on hacking webcam's drivers, I don't want to mess with it anyway.  I sure hope in future that webcam driver developer will find a way to make it compatible and allow full use. 


Catty

---

### Post by Vadi on 2007-11-07
Check this out: [http://www.linuxdriverproject.org/twiki/bin/view/Main/DriversNeeded](http://www.linuxdriverproject.org/twiki/bin/view/Main/DriversNeeded)

---

