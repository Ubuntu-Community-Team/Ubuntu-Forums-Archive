---
title: "audio recording issues"
date: 2007-05-22
forum: General Help
---

### Post by chris.olsen on 2007-05-22
I was having problems getting skype to work, and later found that I am also unable to record over the mic with the standard sound recorder.

When I goto System -> Preferences -> Sound, in the Sound Conferencing section by default (?) "ALSA - Advanced Linux Sound Architecture" is set, but if I click the test button beside it I get the following error message
-----
gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not open resource for writing.
-----

I get the same message if I change it to many of the other options as well.

Thanks for any help.

---

### Post by zolireds on 2007-05-23
I have exactly the same problem.

---

### Post by treblesix on 2007-05-24
I am having these problems too.

---

### Post by icechen1 on 2007-05-25
I am having this problem too,even compiling alsa 1.0.14rc4.
I have a HDA-INTEL card with sigmatel STAC 92XX

---

### Post by treblesix on 2007-05-27
Surely somebody must be recording though Line In ? Can't believe no-one is.

---

### Post by ramjet_1953 on 2007-05-28
1.Right click on the speaker icon in the top menu bar.

2. Select [COLOR="Blue"]Open Volume Control[/COLOR]

3. When the window opens, click [COLOR="Blue"]Edit.Preferences[/COLOR]

4. When the window opens, scroll down and put a tick in the [COLOR="Blue"]Capture Box[/COLOR].

5. Close the window.

6. There should now be a [COLOR="Blue"]Capture Tab[/COLOR] in the Volume Control window. Click on it.

7. Wind the volume up to max and click on the microphone icon to remove the red X on it.

8. Now try again. Hopefully, it should all work.

Regards,
Roger :cool:

---

### Post by piopier on 2007-05-30
What worked for me was to do exactly the following :
Double click on the volume icon (or right clic and "open volume manager"
Unmute "Capture Mux"
On recording tab, activate recording (click the little microphone icon) but don't unmute it (don't click the  other icon).

---

### Post by icechen1 on 2007-05-30
I unmuted everything,the microphone icon in capture tab is activated and it still don't work.

---

### Post by treblesix on 2007-06-02
I still get the line-in coming through the speakers, but can't record it

---

### Post by nickwu2000 on 2007-06-05
I'm getting exactly the same problem.

---

### Post by euchrid on 2007-06-06
Me too. I'm using Ubuntu Studio, upgraded from Feisty Fawn. Can't make much music without being able to record stuff!

---

### Post by euchrid on 2007-06-07
**_*** SEE UPDATE BELOW - THIS NO LONGER SEEMS TO HAVE WORKED ***_**

SOLUTION! (hopefully):
After a LOT of searching, I finally got this sorted out on my system.

Please read ALL of this post before trying out the code, in case it messes something up for you!

I went here: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/88570/comments/19](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/88570/comments/19), and, taking the advice, tried out updating the Alsa driver.

All you have to do is put in following code into a terminal (line by line):

```
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2
tar -xjf alsa-driver-1.0.14.tar.bz2
cd alsa-driver-1.0.14
./configure
sudo make
sudo make install
```

Then REBOOT. 

I was worried that updating the Alsa driver might cause a problem, as I am aware that the driver is somehow connected to the kernel (I am a long way off being a Linux expert). I'm guessing it could cause problems for some people, depending on what they've done to their system (although it's unlikely they've got as much mess installed as I have). So far, it's all fine for me.

I have seen a lot of advice about selecting 'Capture' in alsamixer; this was not an option for me, as I did not have anything labelled 'Capture', and everything else was 'on' - except for the Analog/Digital Jack, which seems to do nothing more than disable all sound.

While I was having the problem, when I hit the 'test' button for recording in System>Preferences>Sound, I got an error message, and I got an error whenever I tried to record with Audacity or Sound Recorder (or anything else). Nothing I came across about microphone recording or Feisty/Alsa problems seemed to help.

In case it helps someone else, here is some information about my system: I started out with Edgy Eft. I upgraded to Feisty Fawn when it came out, and then upgraded to Ubuntu Studio when that was released. I use the low latency kernel (2.6.20-15-lowlatency) that came with Ubuntu Studio, and I have a lot of programs installed, some of which may be installed incorrectly (not sure what I did to my Java installation, but that's another story). I use a Soundblaster Audigy (external model), and am also using a Wacom Volito and a Logitech Cordless Trackball, without any noticeable problems at the moment. If you want any more information, I'm happy to post it.

Further hints and tips I picked up along the way:
[LIST]
[*]Following advice here: [http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/]("http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/") did nothing except stop JACK working. Maybe it will work for other people.
[/LIST]
[LIST]
[*]I read on another post that a Logitech Cordless Mouse can cause xruns in JACK (basically it'll  mess up recording with clicks and glitches) - might be worth connecting something else when you're recording.
[/LIST]
[LIST]
[*]There seems to have been several other people with related problems:
[https://answers.launchpad.net/ubuntu/+question/6414]("https://answers.launchpad.net/ubuntu/+question/6414")
[https://answers.launchpad.net/ubuntu/+question/7629]("https://answers.launchpad.net/ubuntu/+question/7629")
[https://bugs.launchpad.net/ubuntu/+bug/80531]("https://bugs.launchpad.net/ubuntu/+bug/80531")
You can find a lot more!
[/LIST]

I am absolutely convinced that there is either a problem with the Alsa driver (version 1.0.13) that comes with Feisty or with Feisty's (and therefore Ubuntu Studio's) handling of it. I had not problems in Edgy, and there are too many posts relating to Feisty with microphone, recording and/or general sound problems, and in each case the solution is either through Alsamixer or some dramatic reconfiguration.

It would be great if this and the X-server problems that plagued this latest update could be sorted out for the next release, so that 'newbies' don't get scared off!

I hope this has helped someone. Reply here if it worked for you, and I'll put it up as a How-To. Good luck!


**_*** UPDATE ***_**

Sorry folks, but it all went wrong again.

After I did the above, everything was fine. I did not turn the computer off or change anything. A few hours later, I came back, and Audacity wouldn't record. I re-installed the drivers, re-booted, and it was still all wrong - no recording anywhere. 

The only thing that changed on the system was that the power manager detected my Wireless trackball was down to 14% of its power. It was after this that I couldn't record again. It seems that the power management, the Logitech Trackball and Alsa all have some sort of problem working together - but what is it?

I have left the above information up in the hope that it will shed some light on this infuriating problem.

I hope someone can work this out, because otherwise I am going to have to rip Ubuntu Studio out and go back to Edgy - I had no problems there.

---

### Post by RichPicker on 2007-06-07
I've been using the "Mic" exclusively. The "Line" has never worked.

---

### Post by euchrid on 2007-06-07
OK, I don't want to look like I'm spamming this thread, but I have now found out that my above attempts DID work; now, Alsa only stops working when I start up JACK. Before, it didn't work with or without JACK.

This issue seems to get weirder and weirder - there must be something underlying it all. This now makes me think that it cannot be Alsa itself, but something in Ubuntu that prevents Alsa from working.

Now, how do I get JACK running so I can use Ardour, Rosegarden, etc.? I'll report back when I find out.

Is anyone else getting the same issue as me?

I CAN record with 'Line in' AND 'mic' on my Audigy, but I guess each soundcard is going to react differently.

---

### Post by RichPicker on 2007-06-07
Each soundcard must be configured differently - yes. I believe this is true. I'm asking a few places now how I can configure Jack for my computer/sound card. But so far no luck. You're way ahead of me ;)

But if I should expect more mic problems if/when I do get Jack connected and running, I'll be prepared for more.

---

### Post by euchrid on 2007-06-08
This is about the last time I'm going to come back to this issue. If it carries on, I'll open a new thread. I hope someone is finding this useful or at least thought-provoking so far.

I can now record in Ardour and Rosegarden, with JACK (qjackctl) running on either Alsa or Oss, although choosing the 'Realtime' option is no good (despite the fact that I am on a Realtime kernel). However, I cannot run Audacity while JACK is running. 

Everything worked differently in Edgy Eft. I could put JACK on and do whatever I liked (or so it seemed), and still record and everything - but now, I find I have to update the Alsa drivers to get anything to work at all and JACK no longer works with Audacity. Thankfully, my needs are relatively simple for recording, so I haven't - yet - tried out all the other programs that came with Ubuntu Studio (doing this has been work enough).

If someone can work out why there seems to be such a mess with JACK, Alsa and Feisty/Ubuntu Studio, it would be great to know what is going on and how to fix it. Is *someone* interested in sorting this out for the next release, or, if not, getting together with other users to write up a useful How-To? 

If I can help, I will, but I am an end-user with no worthwhile programming experience. I have a penchant for experimenting with stuff now and again, but I do not really understand how everything works - a typical ex-Windows user, I suppose. I am happy to work on writing up instructions on how to sort this recording issue out, if someone can just pass on the instructions!

Lastly, if these issues *can* be sorted out, Ubuntu Studio will blow the pants off many commercial equivalents. What I have achieved so far (mainly in Edgy Eft) greatly outstrips anything I have been able to do (or afford) in Windows. Also, as a musician, by using free software to create music, I am happy to release it for free (when I finish something) - paying £500+ for commercial software that doesn't produce any better results (and is often just as difficult to use) does not encourage such community spiritedness. Let's sort this out!

---

### Post by klondike0 on 2007-06-09
I had sound until I went to the 2.6.20-16-generic kernel.  Alsamixer did load once right after that, and sound worked nicely through those volume controls and not through my Fn keys.  

I am attempting to install the alsa-utils-1.0.14 from that same ftp site, alsa-project.org, in the same way as the alsa-driver-1.0.14 so that I can get a fresh install of alsamixer, etc, but when I run ./configure it says that I need a ncurses or curses library , and the documentation also suggests as much.  

anybody got a line on a library of curses? anybody know how it's used or the legacy thereof?:-&

---

### Post by mynis on 2007-06-11
i did this and at first i had completely no sound. then i realized that upgrading to alsa 1.0.14 you need to install the lib and util packges too found here:[http://www.alsa-project.org/alsa/ftp/lib/alsa-lib-1.0.14rc4.tar.bz2](http://www.alsa-project.org/alsa/ftp/lib/alsa-lib-1.0.14rc4.tar.bz2)
and here:
[http://www.alsa-project.org/alsa/ftp/utils/alsa-utils-1.0.14rc4.tar.bz2](http://www.alsa-project.org/alsa/ftp/utils/alsa-utils-1.0.14rc4.tar.bz2)

> **euchrid said:**
> **_*** SEE UPDATE BELOW - THIS NO LONGER SEEMS TO HAVE WORKED ***_**

SOLUTION! (hopefully):
After a LOT of searching, I finally got this sorted out on my system.

Please read ALL of this post before trying out the code, in case it messes something up for you!

I went here: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/88570/comments/19](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/88570/comments/19), and, taking the advice, tried out updating the Alsa driver.

All you have to do is put in following code into a terminal (line by line):

```
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2
tar -xjf alsa-driver-1.0.14.tar.bz2
cd alsa-driver-1.0.14
./configure
sudo make
sudo make install
```

Then REBOOT. 

I was worried that updating the Alsa driver might cause a problem, as I am aware that the driver is somehow connected to the kernel (I am a long way off being a Linux expert). I'm guessing it could cause problems for some people, depending on what they've done to their system (although it's unlikely they've got as much mess installed as I have). So far, it's all fine for me.

I have seen a lot of advice about selecting 'Capture' in alsamixer; this was not an option for me, as I did not have anything labelled 'Capture', and everything else was 'on' - except for the Analog/Digital Jack, which seems to do nothing more than disable all sound.

While I was having the problem, when I hit the 'test' button for recording in System>Preferences>Sound, I got an error message, and I got an error whenever I tried to record with Audacity or Sound Recorder (or anything else). Nothing I came across about microphone recording or Feisty/Alsa problems seemed to help.

In case it helps someone else, here is some information about my system: I started out with Edgy Eft. I upgraded to Feisty Fawn when it came out, and then upgraded to Ubuntu Studio when that was released. I use the low latency kernel (2.6.20-15-lowlatency) that came with Ubuntu Studio, and I have a lot of programs installed, some of which may be installed incorrectly (not sure what I did to my Java installation, but that's another story). I use a Soundblaster Audigy (external model), and am also using a Wacom Volito and a Logitech Cordless Trackball, without any noticeable problems at the moment. If you want any more information, I'm happy to post it.

Further hints and tips I picked up along the way:
[LIST]
[*]Following advice here: [http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/]("http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/") did nothing except stop JACK working. Maybe it will work for other people.
[/LIST]
[LIST]
[*]I read on another post that a Logitech Cordless Mouse can cause xruns in JACK (basically it'll  mess up recording with clicks and glitches) - might be worth connecting something else when you're recording.
[/LIST]
[LIST]
[*]There seems to have been several other people with related problems:
[https://answers.launchpad.net/ubuntu/+question/6414]("https://answers.launchpad.net/ubuntu/+question/6414")
[https://answers.launchpad.net/ubuntu/+question/7629]("https://answers.launchpad.net/ubuntu/+question/7629")
[https://bugs.launchpad.net/ubuntu/+bug/80531]("https://bugs.launchpad.net/ubuntu/+bug/80531")
You can find a lot more!
[/LIST]

I am absolutely convinced that there is either a problem with the Alsa driver (version 1.0.13) that comes with Feisty or with Feisty's (and therefore Ubuntu Studio's) handling of it. I had not problems in Edgy, and there are too many posts relating to Feisty with microphone, recording and/or general sound problems, and in each case the solution is either through Alsamixer or some dramatic reconfiguration.

It would be great if this and the X-server problems that plagued this latest update could be sorted out for the next release, so that 'newbies' don't get scared off!

I hope this has helped someone. Reply here if it worked for you, and I'll put it up as a How-To. Good luck!


**_*** UPDATE ***_**

Sorry folks, but it all went wrong again.

After I did the above, everything was fine. I did not turn the computer off or change anything. A few hours later, I came back, and Audacity wouldn't record. I re-installed the drivers, re-booted, and it was still all wrong - no recording anywhere. 

The only thing that changed on the system was that the power manager detected my Wireless trackball was down to 14% of its power. It was after this that I couldn't record again. It seems that the power management, the Logitech Trackball and Alsa all have some sort of problem working together - but what is it?

I have left the above information up in the hope that it will shed some light on this infuriating problem.

I hope someone can work this out, because otherwise I am going to have to rip Ubuntu Studio out and go back to Edgy - I had no problems there.

---

### Post by eggdeng on 2007-06-11
Some of us have managed to get working microphones following the fix at [http://ubuntuforums.org/showthread.php?t=342681](http://ubuntuforums.org/showthread.php?t=342681)
Basically it means editing esd.conf
```
sudo gedit /etc/esound/esd.conf
```
to read as follows
```
[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 1
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=
```

---

### Post by dannyboy79 on 2007-06-12
i couldn' even do a sudo checkinstall because it said something about a file called modules.dep couldn't be overwritten or something like that. there was a log file but the only logf file I can find now within the alsa compiling folder is config.log and that looks ok. I am going to try sudo make install now?

---

### Post by oxalá on 2007-06-12
aaaaaarrrrgh!!!!

mustrememberthisispartofthecharmofLinux
mustrememberthisispartofthecharmofLinux
mustrememberthisispartofthecharmofLinux

sigh.  I can't get Ardour or Audacity to work.  Hopefully eggdeng's fix will work for me.
otherwise, Ubuntu Studio isn't much of a studio.

---

### Post by IkimashoZ on 2007-06-14
No apparent problems with the update of my drivers to 1.0.14.

Still no recording.  Everything seems pretty much unchanged.

Stupid ICH6...

---

### Post by icechen1 on 2007-06-17
> **IkimashoZ said:**
> No apparent problems with the update of my drivers to 1.0.14.

Still no recording.  Everything seems pretty much unchanged.

Stupid ICH6...
i tried updating too,it just removes some options(i have a front mic and no mic anymore)
i hate ich7 with sigmatel.

---

### Post by rabideau on 2007-07-04
In the stupid solutions realm, I had the same problem and here's how I fixed it....

I reinstalled GDM from scratch and voila... everything worked perfectly! Hopefully this will help someone.:popcorn:

---

### Post by dannyboy79 on 2007-07-05
> **rabideau said:**
> In the stupid solutions realm, I had the same problem and here's how I fixed it....

I reinstalled GDM from scratch and voila... everything worked perfectly! Hopefully this will help someone.:popcorn:

when you say from scratch, could you please be more specific? did you compile it from source? did you just remove it thru synaptic, purge it, then reinstall it? doesn't it want to uninstall gnome-desktop with it as well? I know it's just a metapackage so it's ok, I am merely asking for other's benefit. 

Hardware:
card 0: OPL3SA23 [Yamaha OPL3-SA23], device 0: CS4231 [Yamaha OPL3-SA23]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I have tried changing the capture to line and mic, see here:

[http://img341.imageshack.us/my.php?image=alsamixerlo6.png](http://img341.imageshack.us/my.php?image=alsamixerlo6.png)

you can just barely see the capture is set to Line for in the picture but I have tried both MIC and line.

I have xubuntu and I already recompiled alsa with what's suggested and I still can't get audacity to record anything. I don't even know where to look now? I have three ports on my laptop, a line in, a line out, and a mic jack. When I plug it in the mic jack, I can actually here the music coming thru my speakers when I plug it in, very weird! (I am trying to record from a mixer, you know, dj tables kind of thing) so it has a line out on it, rca plugs, then on the other end it has the little "headphone jack thingy". When I plug it in the line in, I can still hear the music coming thru my speakers but it's WAY  lower in volume where as when I plug it in the mic jack, it's super loud. I would like to point out that on page 2 of this thread eggdend points out that esd.conf should be modified but I notice that within audacity, my input recording device is the Yamaha card and the other choice is something along the lines of  ESD or was it OSS, not sure but I have NOT tried that yet.

I hate it because I am trying to convert the owner of the mixing tables to linux and when I tried to show him the versatility of linux something as simple as recording a source of sound (either mic or line in), it doesn't even work!!! Then he opens winbloz, open's this little app, hit's record and it just works for him. So how can I argue to him that he should use linux???? I have been trying for a while now to get this to work. 

and when I try sound-recorder in xubuntu, there's no gui, so I have no idea what syntax to use to record either the mic input or the line input? Any help anyone????

---

### Post by rabideau on 2007-07-05
Hi Danny,

I unistalled ALSA from synaptic and that caused a lot of things to unistall themselves including Agavae and GDM.

When I saw unistalls of everything including GDM, I killed my PC (shut it off with the power button).  I turned the PC back on and all I got was command line Linux (not my favorite view of the OS;) ).  Anyway it was there that I followed all the commands to reinstall GDM.  Once that was complete my machine was back in tip-top shape, minus one or two apps, which were simple enough to reinstall.

A totally ugly systems management approach but it yielded a good result (thus far).

---

### Post by dannyboy79 on 2007-07-05
> **rabideau said:**
> Hi Danny,

I unistalled ALSA from synaptic and that caused a lot of things to unistall themselves including Agavae and GDM.

When I saw unistalls of everything including GDM, I killed my PC (shut it off with the power button).  I turned the PC back on and all I got was command line Linux (not my favorite view of the OS;) ).  Anyway it was there that I followed all the commands to reinstall GDM.  Once that was complete my machine was back in tip-top shape, minus one or two apps, which were simple enough to reinstall.

A totally ugly systems management approach but it yielded a good result (thus far).
again, could you please specify what you mean when you say, "followed all the commands to reinstall GDM" What is Agavae? So you're saying that after all this, you can record sound? Is the sound thru the MIC port or the line in port? What program do you use to record the sound?  Also, did you do any other modifications previously? Like maybe edit the asound file or any other files? Thank you for any more info you can provide.

---

### Post by rabideau on 2007-07-05
Hi Danny,

I guess you're asking questions that go beyond my meager knowledge.  Agave is a graphics package (that I do know, why it unistalled when I used synaptic to remove ALSA, I have no idea; for that matter I don't know what synaptic removed GDM, either).

What I can tell you is that when you loose GDM, Linux comes up looking like a 1970's DOS OS.  However it is wonderful in that it assumes you don't really want to see that and so offers a set of command suggestions to help you reinstall GDM.  I followed those (I have no idea what they were... "I am a bear of too little brains" to remember all that I guess).

Anyway, once I completed their instructions and restarted the machine... everything was fixed.

As for my use I am using mic line in on my headset for Skype etc.  I am not using it to record fancy stuff.  Now I can both hear and talk with clarity that was non-existant before on my Dell e1505n.  I hope this helps.

---

### Post by dannyboy79 on 2007-07-05
OK, I have to be honest and say that you gave us all VERY FALSE hopes!!! You posted, "I had the same problem and here's how I fixed it...." immediately following a person who quoted the fact that he still couldn't get his mic or line in to record sound. You told us that you reinstalled GDM and then "it" worked. The THREADS entire purpose is to get recording working with either a MIC or a Line In and you aren't doing either so I am curious as to why you posted here in the first place?

I wish I hadn't wasted my time with the last 2, now 3 posts.

---

### Post by rabideau on 2007-07-05
I guess I could say the same... it's tough trying to be helpful sometimes I guess.

---

### Post by dannyboy79 on 2007-07-05
if you're trying to be helpful, than do it in a thread that your help is actually related to. more like this one: [http://ubuntuforums.org/showthread.php?t=490580&highlight=skype+mic](http://ubuntuforums.org/showthread.php?t=490580&highlight=skype+mic)

---

### Post by kvonb on 2007-07-18
Post #6 of this thread worked for me, also you might want to look through this rather long thread below, it solved my problem of continually shuffling sound cards.

A lot of useful stuff here:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

It seems to me that there are way too many obscure options in the mixer, it get's very confusing and the labels make little or no sense!

Theoretically you should be able to simply select which sound input you want to record from, and if you have an "advanced" sound card (ie not the cheap built in things!), then you should (theoretically) be able to select multiple sources with the "capture" buttons!

---

### Post by renzokuken on 2007-08-02
> **euchrid said:**
> **_*** SEE UPDATE BELOW - THIS NO LONGER SEEMS TO HAVE WORKED ***_**

SOLUTION! (hopefully):
After a LOT of searching, I finally got this sorted out on my system.

Please read ALL of this post before trying out the code, in case it messes something up for you!

I went here: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/88570/comments/19](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/88570/comments/19), and, taking the advice, tried out updating the Alsa driver.

All you have to do is put in following code into a terminal (line by line):

```
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2
tar -xjf alsa-driver-1.0.14.tar.bz2
cd alsa-driver-1.0.14
./configure
sudo make
sudo make install
```

Then REBOOT. 

I was worried that updating the Alsa driver might cause a problem, as I am aware that the driver is somehow connected to the kernel (I am a long way off being a Linux expert). I'm guessing it could cause problems for some people, depending on what they've done to their system (although it's unlikely they've got as much mess installed as I have). So far, it's all fine for me.

I have seen a lot of advice about selecting 'Capture' in alsamixer; this was not an option for me, as I did not have anything labelled 'Capture', and everything else was 'on' - except for the Analog/Digital Jack, which seems to do nothing more than disable all sound.

While I was having the problem, when I hit the 'test' button for recording in System>Preferences>Sound, I got an error message, and I got an error whenever I tried to record with Audacity or Sound Recorder (or anything else). Nothing I came across about microphone recording or Feisty/Alsa problems seemed to help.

In case it helps someone else, here is some information about my system: I started out with Edgy Eft. I upgraded to Feisty Fawn when it came out, and then upgraded to Ubuntu Studio when that was released. I use the low latency kernel (2.6.20-15-lowlatency) that came with Ubuntu Studio, and I have a lot of programs installed, some of which may be installed incorrectly (not sure what I did to my Java installation, but that's another story). I use a Soundblaster Audigy (external model), and am also using a Wacom Volito and a Logitech Cordless Trackball, without any noticeable problems at the moment. If you want any more information, I'm happy to post it.

Further hints and tips I picked up along the way:
[LIST]
[*]Following advice here: [http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/]("http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/") did nothing except stop JACK working. Maybe it will work for other people.
[/LIST]
[LIST]
[*]I read on another post that a Logitech Cordless Mouse can cause xruns in JACK (basically it'll  mess up recording with clicks and glitches) - might be worth connecting something else when you're recording.
[/LIST]
[LIST]
[*]There seems to have been several other people with related problems:
[https://answers.launchpad.net/ubuntu/+question/6414]("https://answers.launchpad.net/ubuntu/+question/6414")
[https://answers.launchpad.net/ubuntu/+question/7629]("https://answers.launchpad.net/ubuntu/+question/7629")
[https://bugs.launchpad.net/ubuntu/+bug/80531]("https://bugs.launchpad.net/ubuntu/+bug/80531")
You can find a lot more!
[/LIST]

I am absolutely convinced that there is either a problem with the Alsa driver (version 1.0.13) that comes with Feisty or with Feisty's (and therefore Ubuntu Studio's) handling of it. I had not problems in Edgy, and there are too many posts relating to Feisty with microphone, recording and/or general sound problems, and in each case the solution is either through Alsamixer or some dramatic reconfiguration.

It would be great if this and the X-server problems that plagued this latest update could be sorted out for the next release, so that 'newbies' don't get scared off!

I hope this has helped someone. Reply here if it worked for you, and I'll put it up as a How-To. Good luck!


**_*** UPDATE ***_**

Sorry folks, but it all went wrong again.

After I did the above, everything was fine. I did not turn the computer off or change anything. A few hours later, I came back, and Audacity wouldn't record. I re-installed the drivers, re-booted, and it was still all wrong - no recording anywhere. 

The only thing that changed on the system was that the power manager detected my Wireless trackball was down to 14% of its power. It was after this that I couldn't record again. It seems that the power management, the Logitech Trackball and Alsa all have some sort of problem working together - but what is it?

I have left the above information up in the hope that it will shed some light on this infuriating problem.

I hope someone can work this out, because otherwise I am going to have to rip Ubuntu Studio out and go back to Edgy - I had no problems there.

there shouldnt be a "sudo" in front of the make command (i'm 99% sure anyway) it should read

```
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2
tar -xjf alsa-driver-1.0.14.tar.bz2
cd alsa-driver-1.0.14
./configure
make
sudo make install
```

---

### Post by treblesix on 2007-08-03
Oddly enough, I have plugged the cable I had in my Line-In, into the Microphone socket, installed Audacity, and now I can record anything through the microphone socket. 

I had no joy in getting it working through the Line-In though.

---

### Post by dannyboy79 on 2007-08-03
this has to do with the aslamixer "capture" thingy being on the correct one. If you already tried that than I am not sure. Glad it's working for you none-the-less.

---

