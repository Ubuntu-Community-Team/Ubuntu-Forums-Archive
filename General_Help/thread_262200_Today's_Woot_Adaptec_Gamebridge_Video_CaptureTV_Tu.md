---
title: "Today's Woot: Adaptec Gamebridge Video Capture/TV Tuner - should I buy one?"
date: 2006-09-21
forum: General Help
---

### Post by TeeAhr1 on 2006-09-21
Will it work under Linux?  The price is right... Anyone have one of these?

---

### Post by abstractism on 2006-09-25
well my order arrived...I'm hoping it *does* work :)

---

### Post by TeeAhr1 on 2006-09-28
I opted to not.  Let me know if it does work out for you, though, I may have to go out and (/sigh) pay full price for one...

---

### Post by sk8dork on 2006-10-23
i got mine today. (avc-1400) the software cd that comes with it is windows only and it doesn't play nice in wine as far as i can tell. it doesn't do anything by default...i hope to see someone crack this thing to work. i guess in the meantime i'll be booting to windows to use it.

---

### Post by BillyBudd on 2007-04-01
I've got one of these too, and it worked fine in Windows XP.   I've spent the past couple of hours trying to get it installed into WinXP in VirtualBox, without success.  VBox has the USB sockets enabled, but WinXP apparently can't find them.  The GameBridge installation program starts OK in the VBox session, but then announces that there are no USB 2.0 ports. 
I've been experimenting and will leave a message here if I get this thing working in VBox.

---

### Post by TiCL on 2007-04-26
I have talked with developers in #v4l@irc.freenode.net. After examining a usbsniff dump, they told me it is not currently supported. However, one of the developers assured that he would start working on the driver on May'07 (no promises though).

---

### Post by ergosteur on 2007-06-10
> **TiCL said:**
> I have talked with developers in #v4l@irc.freenode.net. After examining a usbsniff dump, they told me it is not currently supported. However, one of the developers assured that he would start working on the driver on May'07 (no promises though).

any updates? i want to get rid of my dual-boot. :p

---

### Post by loudnlownoma on 2007-08-19
Anyone have any luck with this?  I've got one too, and it's one of the few things holding me back from making the plunge to run from Windows without looking back!

---

### Post by tuckie on 2007-09-19
any updates on this?

---

### Post by likwidoxigen on 2007-09-19
This isn't quite good news, but I have gotten it installed in win xp as guest in vbox. However the stupid intervideo software fails miserably. Apparently it uses some form of compositing in the graphics card to overlay the video and some of the controls, makes the UI totally flake out and i can't even choose to use composite instead of svide. I'll try with svideo when i get the cable and hookups to see if i have any progress, though i'll need a composite s-video converter. 


If you want to get done what I did. Open up the Drivers folder on the cd. Copy the .sys files to c:\windows\system32\drivers  then copy the files to a temporary directory. Rename the .IN_ files to .inf then copy the whole shebang into c:|windows\system32 directory. Then connect the gamebridge through the menu for your guest (you see a light come on and complaints about it not getting the right bandwidth) then tell it to install automatically and continue anyway. You may need to do this twice. Then disable the gamebridge in the vbox menu, re-enable it so that it goes all green lighted and has the right drivers, then install the intervideo software. And you'll be as far along as  I am. If you make any progress definately post. Enjoy all!

---

### Post by loudnlownoma on 2007-09-20
> **likwidoxigen said:**
> This isn't quite good news, but I have gotten it installed in win xp as guest in vbox. However the stupid intervideo software fails miserably. Apparently it uses some form of compositing in the graphics card to overlay the video and some of the controls, makes the UI totally flake out and i can't even choose to use composite instead of svide. I'll try with svideo when i get the cable and hookups to see if i have any progress, though i'll need a composite s-video converter. 


If you want to get done what I did. Open up the Drivers folder on the cd. Copy the .sys files to c:\windows\system32\drivers  then copy the files to a temporary directory. Rename the .IN_ files to .inf then copy the whole shebang into c:|windows\system32 directory. Then connect the gamebridge through the menu for your guest (you see a light come on and complaints about it not getting the right bandwidth) then tell it to install automatically and continue anyway. You may need to do this twice. Then disable the gamebridge in the vbox menu, re-enable it so that it goes all green lighted and has the right drivers, then install the intervideo software. And you'll be as far along as  I am. If you make any progress definately post. Enjoy all!

Very interesting to hear!  I was just starting to get my USB working in VirtualBox and ready to start trying it this way, thanks for the heads up.  Will definitely try this a little later on and see if I have any better luck....will post as well.

---

### Post by loudnlownoma on 2008-01-21
> **likwidoxigen said:**
> This isn't quite good news, but I have gotten it installed in win xp as guest in vbox. However the stupid intervideo software fails miserably. Apparently it uses some form of compositing in the graphics card to overlay the video and some of the controls, makes the UI totally flake out and i can't even choose to use composite instead of svide. I'll try with svideo when i get the cable and hookups to see if i have any progress, though i'll need a composite s-video converter. 


If you want to get done what I did. Open up the Drivers folder on the cd. Copy the .sys files to c:\windows\system32\drivers  then copy the files to a temporary directory. Rename the .IN_ files to .inf then copy the whole shebang into c:|windows\system32 directory. Then connect the gamebridge through the menu for your guest (you see a light come on and complaints about it not getting the right bandwidth) then tell it to install automatically and continue anyway. You may need to do this twice. Then disable the gamebridge in the vbox menu, re-enable it so that it goes all green lighted and has the right drivers, then install the intervideo software. And you'll be as far along as  I am. If you make any progress definately post. Enjoy all!

Been a little while and figured I would check in.  Still haven't forgotten about this yet.  I somehow lost the driver/install CD that came with mine.  I managed to find an archive somewhere that had the drivers at least.  Through some playing around, I was able to find a Winamp plugin that allows TV input, and managed to get the GameBridge working again on my Windows boxes successfully.  So I figured it was time to take a shot with Ubuntu again.  In VirtualBox, I have similar issues.  Winamp and the drivers install fine, the plugin installs, but as soon as the video tries to start up, the virtual WinXP just freezes up and hangs.  So I figured I'd play a little bit and see about getting it to work natively.  Through ndiswrapper, I was able to get the two drivers installed, and get the device recognized at least.  So when I plug it in, it is recognized, ndiswrappers list shows it enabled, and it shows up in the hardware list (System > Preferences > Hardware Information) as "Adaptec Gambridge 1400/1500".  Tried opening it with TVTime in just about any way I can imagine, but it still doesn't seem to pick up on it.  This was on my laptop with Feisty, may try tomorrow on the desktop that's running Gutsy, just to see if anything different happens....

---

### Post by galatasarai on 2008-01-25
Interesting topic, I have a GameBridge too I couldn't make it capture in Linux (kubuntu). I wish there were more people to help, and only this makes me commend your efforts loudnlownoma!

To resume, do you try instead of making it work under Linux, to install VirtualBox and install the windows application in this "shell"?

Did you try to run the whole windows application under this VirtualBox? In case you still lack the stuff from the install CD, although mine Gamebrige is 1410, and I don't see a real concern about compatibility. Let me know if can help you with the cd content.

Cheers.

---

### Post by loudnlownoma on 2008-01-26
> **galatasarai said:**
> Interesting topic, I have a GameBridge too I couldn't make it capture in Linux (kubuntu). I wish there were more people to help, and only this makes me commend your efforts loudnlownoma!

To resume, do you try instead of making it work under Linux, to install VirtualBox and install the windows application in this "shell"?

Did you try to run the whole windows application under this VirtualBox? In case you still lack the stuff from the install CD, although mine Gamebrige is 1410, and I don't see a real concern about compatibility. Let me know if can help you with the cd content.

Cheers.

Been a little busy lately, so I haven't had much more chance to mess with it just yet, and I'm definitely not the only one working with it, but I do want to get it running.  I don't have the included capturing software, but was able to find a plugin for winamp(that I have successfully setup in both XP and Vista otherwise in actual installs) to use.  Unfortunately, it seems to get the same results as others, in that the virtualization of the hardware doesn't seem to play very nice with the video rendering.  It loads fine and recognizes the adapter without trouble, Winamp even picks up the adapter and gives the options as it should, but as soon as you start the playback it freezes up the virtual machine or start spitting out errors.  Tried a few different settings, but not an in-depth struggle with it virtually as I was making some progress on the native Linux run of it.  But still stuck in the same spot there, in that I can get Linux recognizing the device and drivers as it seems it should, but still no luck finding any software to recognize it's input and display the video...  Hopefully this weekend I may have some time to play with it, but no guarantees yet.  Not to mention I'm still fairly new in the grand scheme, so I'm probably missing most of what I'd need to get it working anyway...lol.

Edit:  Didn't mean to forget - Thank you for the kind words!  Happy to help as much as I can, even in my "newbie" status...hehe.

---

### Post by galatasarai on 2008-01-26
In all my research this is what found most relevant:
[http://www.tomsguide.com/us/gamebridge-transforms-pcs-into-entertainment-centers,review-688-2.html](http://www.tomsguide.com/us/gamebridge-transforms-pcs-into-entertainment-centers,review-688-2.html)
and:
[http://www.ussg.iu.edu/hypermail/linux/kernel/0604.2/1795.html](http://www.ussg.iu.edu/hypermail/linux/kernel/0604.2/1795.html)

a lsusb will show:
```

**Bus 005 Device 004: ID 03f3:009b Adaptec, Inc.**
Bus 005 Device 002: ID 5986:0200
Bus 005 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 004 Device 002: ID 045e:0084 Microsoft Corp.
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000

```

I tried then:

```

~$ sudo modprobe cx25840
[sudo] password for xxxx:

```

almost there... (I mean I got no errors)
then...

```

~$ lsmod
Module                  Size  Used by
**_cx25840 _               26640  0**
i2c_core               26112  1 cx25840
....
yenta_socket           27532  1
v4l1_compat            15364  2 uvcvideo,videodev
**_v4l2_common            18432  3 cx25840,uvcvideo,videodev_**
rsrc_nonstatic         14080  1 yenta_socket
....
fan                     5764  0
fuse                   47124  1
apparmor               40728  0
commoncap               8320  1 apparmor


```

BINGO!

Now, I am a newbie too, so:
1. What application can I use to capture the video? Will MythTV do it?
2. How can be automagically detected this USB device when is just plugged (like the USB flash drives)?

Maybe more experienced people would jump in...? What else can I try to confirm that actually ubuntu deals well with GameBridge? (at this point I didn't capture any video)

---

### Post by loudnlownoma on 2008-01-26
Interesting....  Will have to do some reading it looks like!  I have been trying to use TVTime, although I have no real experience yet with it or MythTV, as my tuner card in my desktop is still on the verge of working as well.  For the second question - I'm not sure I understand.  When I plug mine in, it immediately lights up, although it is a red light instead of the green, and starts showing in the list given with lsusb, as well as in the hardware manager.  I haven't tried the modprobe command tho, so not sure if that will change anything on my end.  Will have to try that and post my findings..

---

### Post by Devi 710 on 2008-01-27
Oh man!

Are you saying that if I type in the above mentioned code in galatasarai's post I may be able to get the Adaptec Gamebridge working in Ubuntu???

It is the seriously the only reason I ever boot into windows anymore. I only need it to play games, I don't care about the tv tuner. Please let me know if you guys get it going and what I need to install ie: myth tv, drivers, etc.

:):):):):):)

Thanks,

Devi

---

### Post by galatasarai on 2008-01-30
What I said is that there is a driver compiled for the current kernel.

From here there is still a long way (at least for me) to get recognized automagically when is plugged to USB port, to be registered as a valid video dev and then to test with applications like MythTV.

And that was the reason I asked for some help from people with more knowledge...

---

### Post by Devi 710 on 2008-01-30
Well I didn't think it would be easy. It is great to hear that people are trying to get it to work in Ubuntu. I am sure there isn't a large number of people who have one.

Anyway, good luck and if you or anyone ever does get it going, I'll be sure to setup my gamebridge in Ubuntu :)

Thank you,

Devi

---

### Post by galatasarai on 2008-01-31
A quick MythTV install didn't do a thing...

However, I see at [http://ivtvdriver.org/index.php/Firmware](http://ivtvdriver.org/index.php/Firmware) there is support for CX25840.
Are you asking what is ivtv? I'm dizzy now...

EDIT:
In my dizziness I found: [www.isely.net/pvrusb2/setup.html](www.isely.net/pvrusb2/setup.html)

It's a long story there but it looks is having the answers.
Good news: I found there is in ubuntu pvrusb.ko already.
Just news: it looks there is a way to use windows drivers to be used in ubuntu. I might be wrong (I didn't read through all article) but hey, I want you to have fun by reading it...

---

### Post by wolfen69 on 2008-01-31
ivtv drivers and ivtv-utils are available in synaptic.

---

### Post by galatasarai on 2008-02-11
Since kernel 2.6.18 ivtv & all are included by default.
With 2.6.22 the current kernel I run, I have them all: drivers, firmware, tools, name them...
Now back to the square one: how to use them? Anyone?? Help...
[-o<

---

### Post by galatasarai on 2008-02-16
OK, maybe more specific questions.
For now just one:

If I have a firmware file (.fw), what do I do with it? how can I dump it in GameBridge?

Regards

---

### Post by fishypants on 2008-02-24
These are still dirt cheap wherever you can find one, the picture quality is decent as well.

---

### Post by yjhuoh on 2008-04-21
anybody have any success yet? i've been dying to use my gamebridge again. i can't dualboot because i run software raid.

---

### Post by remu on 2008-06-01
I'm interested in this as well.

---

### Post by loudnlownoma on 2008-06-04
Still been crazy busy here and haven't had much of a chance to mess with this, although the laptop has now been updated to Gutsy and my desktop is running Hardy64 now, so hopefully I'll have a chance to sit down and play with it again with some better luck.  

Was using this for my PS2 so I didn't have to rip apart the entertainment center to hook it up and I'm kinda missing that, so I'm almost motivated enough to get back on it...lol.

---

### Post by remu on 2008-06-05
I'm hoping we can get this figured out as well. I've got Ubuntu 8.04 64bit, and was hoping to get this working in Ubuntu

---

### Post by vkkim on 2008-06-25
[IMG]http://www.ricesigns.com/real_pictures/bump_signs.jpg[/IMG]

---

