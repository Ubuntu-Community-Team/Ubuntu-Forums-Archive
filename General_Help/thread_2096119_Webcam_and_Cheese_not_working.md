---
title: "Webcam and Cheese not working"
date: 2012-12-19
forum: General Help
---

### Post by DinghyMan on 2012-12-19
Sirs,
I have a webcam on Ubuntu 11.10 which was working well in Cheese, Skype and Motion.

I rebooted the PC, and now the webcam doesn't work. Cheese hangs with a blank screen and no menus or elements on the screen. VLC doesn't display anything.

With motion, there is no output and no webcam output.

With lsusb I get:
Bus 002 Device 003: ID 0c45:60c0 Microdia PC Camera with Mic (SN9C105)

What is wrong? How do I get it working again?

Many thanks for your help.

---

### Post by Rockstarever on 2012-12-19
open a terminal and type in [PHP]gstreamer-properties[/PHP]

this will pop up some msg and open up a window named "Multimedia systems selector" go to video tab and check the default input plugin 
set it to your camera and you are done. now check if its working by pressing the test button and opening the cheese. good luck. :popcorn:

---

### Post by mörgæs on 2012-12-19
Is there a particular reason for running 11.10? 

The webcam drivers have improved a lot the later releases.

---

### Post by DinghyMan on 2012-12-20
Dear Rockstarever and morgaes,

Thank you for your help.

Firstly, I am using 11.10 as I wanted to be using a stable system, and that works - and has been working, and I don't like the more recent releases. I had everything I needed working in 11.10, so I don't understand why it has stopped working!


Also I tried the gstreamer-properties and got:-

(gstreamer-properties:14396): Gtk-WARNING **: Unknown property: GtkDialog.has-separator

(gstreamer-properties:14396): Gtk-WARNING **: Unknown property: GtkDialog.has-separator
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lsrc'


which explains why I get a blank Cheese screen, but I don't know why, or the solution [IMG]http://ubuntuforums.org/images/icons/icon9.gif[/IMG] !

Thank you for your help.

---

### Post by mörgæs on 2012-12-20
If you somehow manage to get it working, you will have only four months of support in 11.10. 

You will be better off with a fresh install of 12.10 right away.

---

### Post by dannyboy79 on 2012-12-20
if you like stable releases I would suggest installing 12.04, it's an LTS release, meaning a long support life. You could test out your webcam using a 12.04 live cd to see if it works out of the box. have you checked out this page?
[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

---

### Post by DinghyMan on 2012-12-21
Dear Dannyboy79 and morgaes,

Thank you for your help. The link [https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam) gave me a page 500 error.

As for 12.04 or 12.10 - I take the point that at some point I will have to upgrade, but I had a working system, and I know it takes so much effort to upgrade (or has in the past), and the webcam was working - and had been working really well for many months. If possible I would like to get it working, then I can upgrade knowing it's working rather than having a partially working system, and have an additional set of unknowns! Is that possible, or should I upgrade and risk lots of stuff not working?!! (That does make me nervous leading up to the holidays!)

Many thanks for your help!

---

### Post by mörgæs on 2012-12-21
You don't have to decide now. Better to do a live boot of 12.10 and see how it works.

---

### Post by dannyboy79 on 2012-12-21
> **DinghyMan said:**
> Sirs,
I have a webcam on Ubuntu 11.10 which was working well in Cheese, Skype and Motion.

I rebooted the PC, and now the webcam doesn't work. Cheese hangs with a blank screen and no menus or elements on the screen. VLC doesn't display anything.

With motion, there is no output and no webcam output.

With lsusb I get:
Bus 002 Device 003: ID 0c45:60c0 Microdia PC Camera with Mic (SN9C105)

What is wrong? How do I get it working again?

Many thanks for your help.have you verified that you have a /dev/video0 device? also, you said this all used to work, have you tried booting into an older kernel? it's possible a kernel upgrade has caused this.

i don't know why you get error 500 with that link, works fine for me. It's the official ubuntu help page for webcams. Try to google "ubuntu webcam help", for me it's the first returned search result, click that link
I would run 12.04 if it were me.

---

### Post by DinghyMan on 2012-12-21
Dear dannyboy 79,

Thank you for your help. The webcam was working a few days ago, and I do not recall installing any updates in that time (hence my reluctance to change another set of variables).

I also have a TV card and a satellite card so in the past the webcam has been /dev/video2 - so nothing has changed as far as I am aware.

I did find the following in dmesg:-
 INFO: task motion:22856 blocked for more than 120 seconds.
[139800.352072] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[139800.352075] motion          D 00003a51     0 22856      1 0x00000000
[139800.352079]  f4151c7c 00000086 00000000 00003a51 00000000 dc3019a0 c1768060 c1874ec0
[139800.352083]  c1874ec0 862ff1b5 00007efc f77c6ec0 dc3019a0 e9fb19a0 f77c6ec0 00000000
[139800.352087]  00000000 c153e520 f77c6ec0 c153e520 f4151c58 c1032b82 e9fb19a0 f77c6ec0
[139800.352091] Call Trace:
[139800.352098]  [<c1032b82>] ? check_preempt_curr+0x72/0x90
[139800.352101]  [<c1032bc8>] ? ttwu_do_wakeup+0x28/0x130
[139800.352105]  [<c1530f35>] schedule+0x35/0x50
[139800.352107]  [<c1531ad6>] __mutex_lock_slowpath+0xc6/0x120
[139800.352109]  [<c1531784>] mutex_lock+0x24/0x40
[139800.352126]  [<f810b64f>] videobuf_streamoff+0x4f/0x70 [videobuf_core]
[139800.352133]  [<f9f0df36>] saa7134_streamoff+0x36/0x70 [saa7134]
[139800.352138]  [<f9f0df00>] ? video_release+0x270/0x270 [saa7134]
[139800.352144]  [<f82ba276>] __video_do_ioctl+0x1d56/0x6460 [videodev]
[139800.352147]  [<c102e997>] ? __wake_up_common+0x47/0x70
[139800.352150]  [<c103012c>] ? __wake_up_sync_key+0x4c/0x60
[139800.352155]  [<c1253e35>] ? apparmor_socket_sendmsg+0x15/0x20
[139800.352159]  [<c142b45c>] ? sock_sendmsg+0xec/0x110
[139800.352162]  [<c146f32d>] ? ip_finish_output+0x12d/0x300
[139800.352165]  [<c146f5d0>] ? ip_local_out+0x20/0x30
[139800.352167]  [<c153294d>] ? _raw_spin_lock+0xd/0x10
[139800.352170]  [<c1117b73>] ? add_partial+0x43/0x70
[139800.352173]  [<c128b53f>] ? __copy_from_user_ll+0x1f/0x40
[139800.352178]  [<f82b82f4>] video_usercopy+0x234/0x2d0 [videodev]
[139800.352183]  [<f82b8520>] ? v4l2_norm_to_name+0x50/0x50 [videodev]
[139800.352186]  [<c142ac98>] ? sock_destroy_inode+0x28/0x30
[139800.352188]  [<c111988a>] ? kmem_cache_free+0xea/0x100
[139800.352191]  [<c113c419>] ? __d_free+0x39/0x60
[139800.352193]  [<c11414da>] ? iput_final+0xaa/0x150
[139800.352195]  [<c113c419>] ? __d_free+0x39/0x60
[139800.352197]  [<c113c419>] ? __d_free+0x39/0x60
[139800.352200]  [<c115ddd8>] ? fsnotify+0x198/0x250
[139800.352204]  [<c12258f4>] ? security_file_permission+0x24/0xb0
[139800.352206]  [<c114493d>] ? vfsmount_lock_global_unlock_online+0x4d/0x60
[139800.352212]  [<f82b83a7>] video_ioctl2+0x17/0x20 [videodev]
[139800.352216]  [<f82b8520>] ? v4l2_norm_to_name+0x50/0x50 [videodev]
[139800.352221]  [<f82b73aa>] v4l2_ioctl+0x10a/0x110 [videodev]
[139800.352225]  [<f82b72a0>] ? v4l2_mmap+0xa0/0xa0 [videodev]
[139800.352228]  [<c113a029>] do_vfs_ioctl+0x79/0x2d0
[139800.352230]  [<c13356d0>] ? read_null+0x10/0x10
[139800.352233]  [<c113a2ef>] sys_ioctl+0x6f/0x80
[139800.352235]  [<c1532d64>] syscall_call+0x7/0xb

Sadly, it has meant nothing to me, and I couldn't see a reference to the webcam.

If I have no option, I will try 12.04 or 12.10 but as I mentioned, to me it seems if it was working before, I should be able to get it working - and then upgrade.

Many thanks for all your help, it's really appreciated.

---

### Post by DinghyMan on 2012-12-21
Mmmmm - interesting - I just plugged the webcam into another USB socket, and I can now see the output using motion, and VLC, but Cheese still hangs. I remain puzzled - so maybe now I can chance an upgrade to 12.04/12.10.

Many thanks,

---

### Post by dannyboy79 on 2012-12-21
have you tried launching cheese from the command line to see what it may be reporting back to you as it tries to open the program?

---

### Post by DinghyMan on 2012-12-21
Dear dannyboy79,

When I run cheese from the CLI, I get:-

 cheese

(cheese:17230): Gtk-WARNING **: Attempting to add a widget with type GtkImage to a GtkToggleButton, but as a GtkBin subclass a GtkToggleButton can only contain one widget at a time; it already contains a widget of type GtkLabel

(cheese:17230): Gtk-WARNING **: Attempting to add a widget with type GtkImage to a GtkToggleButton, but as a GtkBin subclass a GtkToggleButton can only contain one widget at a time; it already contains a widget of type GtkLabel

(cheese:17230): Gtk-WARNING **: Attempting to add a widget with type GtkImage to a GtkToggleButton, but as a GtkBin subclass a GtkToggleButton can only contain one widget at a time; it already contains a widget of type GtkLabel

(cheese:17230): Gtk-WARNING **: Attempting to add a widget with type GtkHBox to a GtkButton, but as a GtkBin subclass a GtkButton can only contain one widget at a time; it already contains a widget of type GtkLabel

(cheese:17230): Gtk-WARNING **: Attempting to add a widget with type GtkImage to a GtkButton, but as a GtkBin subclass a GtkButton can only contain one widget at a time; it already contains a widget of type GtkLabel

(cheese:17230): Gtk-WARNING **: Attempting to add a widget with type GtkHBox to a GtkToggleButton, but as a GtkBin subclass a GtkToggleButton can only contain one widget at a time; it already contains a widget of type GtkLabel

(cheese:17230): Gtk-WARNING **: Attempting to add a widget with type GtkImage to a GtkButton, but as a GtkBin subclass a GtkButton can only contain one widget at a time; it already contains a widget of type GtkLabel

and there is no GUI component displayed.

Does this help?

I did try reinstalling cheese without success, and I ensured that it is configured to access the right video device (in case it mattered), but nothing seems to help!

Many thanks,

---

### Post by dannyboy79 on 2012-12-21
which version of cheese are you using?

---

### Post by Rockstarever on 2012-12-22
can u tell is it poping some external app if not so give me your result for the following to be typed into terminal.

lsmod | grep videodev

---

### Post by Rockstarever on 2012-12-22
also wanted to ask have u installed the restricted extras if not so first install them by 


sudo apt-get install ubuntu-restricted-extras

and after that try the command issued by me. and tell me if that works.

---

### Post by DinghyMan on 2012-12-22
Many thanks for the help.

I followed the guidance from Rockstarever and got:-

videodev               85626  14 cx88_blackbird,cx2341x,wm8775,saa7134,tuner,gspca_main,cx8800,cx88xx,v4l2_common

Cheese looks as though it is 3.2.0 (from the Software Centre).

I also tried to load it again in case the restricted extras made it work. I noticed that in the System Monitor, Cheese is waiting for v4l2_ioctl.

Does any of this help?!

I am most appreciative of all your help.

---

### Post by Rockstarever on 2012-12-23
sry for my late replays i am kind of stuck with my network provider service problems. Ok focusing on you proble it seems your system have detected the video device. the only thing you have to do now is to manually by typing in the following in "gstreamer-properties" this will pop up some msg and open up a window named "Multimedia systems selector" go to video tab and check the default input plugin 
set it to your camera and you are done. now check if its working by pressing the test button and opening the cheese and tell me if get you to work.

---

### Post by Outlooker on 2012-12-23
Try here - [http://ubuntuforums.org/showthread.php?p=12393918#post12393918](http://ubuntuforums.org/showthread.php?p=12393918#post12393918)

Then after all that, reboot a couple of times

---

### Post by DinghyMan on 2012-12-24
Dear Rockstarever,

Thanks for the reply - using gstreamer-properties, I still get:-

(gstreamer-properties:28502): Gtk-WARNING **: Unknown property: GtkDialog.has-separator

(gstreamer-properties:28502): Gtk-WARNING **: Unknown property: GtkDialog.has-separator
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lsrc'

This may relate to why Cheese isn't working. Does this help?

Many thanks for your help.

Outlooker - thank you for the help - but the webcam now works, it is only cheese that isn't!

I even got motion working - and was puzzled as to why it was constantly triggering with the same settings as before - until I realised it was the Christmas lights causing the triggering! Doh! [IMG]http://ubuntuforums.org/images/icons/icon10.gif[/IMG]

---

