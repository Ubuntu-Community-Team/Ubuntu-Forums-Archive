---
title: "Cancel on sound icon"
date: 2008-03-15
forum: General Help
---

### Post by Rafinator on 2008-03-15
I have just installed Ubuntu 7.10 and finally got my nvidia drivers working after many troubles.  I don't know too much about linux but am trying to learn, so please be easy on the help.  I can't get the sound to work, clearly I have to install a new driver, but should I look for a certain one or would anything do?  I read on another forum and someone asked for 'lspci' ran in console and the output posted.  Here is mine:

```
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:08.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a1)
00:09.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a2)
00:09.1 SMBus: nVidia Corporation MCP55 SMBus (rev a2)
00:09.2 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
00:0a.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:0a.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:0c.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:0d.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0d.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0d.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0e.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:10.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:11.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:12.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:16.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:17.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation G80 [GeForce 8800 GTX] (rev a2)
02:08.0 FireWire (IEEE 1394): Texas Instruments TSB82AA2 IEEE-1394b Link Layer Controller (rev 01)
02:0a.0 Multimedia audio controller: Creative Labs SB X-Fi
05:00.0 VGA compatible controller: nVidia Corporation G80 [GeForce 8800 GTX] (rev a2)

```

Any help is appreciated.

---

### Post by ibuclaw on 2008-03-15
> **Rafinator said:**
> 
02:0a.0 Multimedia audio controller: Creative Labs SB X-Fi


Creative Labs SB X-Fi by any chance?
And I see that you have a better graphics card than me too... (I have 8500GT :) )
Though the fact that it's newer may be the reason why you had problems with it to start (Newer Card = New Drivers = Bugs not quite rooted out yet from NVIDIA, though if it's from Ubuntu it should be stable enough).

Looked up the [ALSA-Project]("http://www.alsa-project.org/main/index.php/Main_Page")
And I quote:
[QUOTE=ALSA-Project] "[Unsupported] [PCI] Card delivered to developers. Completely new architecture. Creative actively preventing support due to no datasheets being released to ALSA developers. Reverse engineering work not started due to lack of time." [/QUOTE]

Checked out OSS though, and your in LUCK! Well, Kind of!

Good news is that **THERE IS A DRIVER!!!**
Bad news is that it is **NOT FREE** (in terms of install and never worry again).

You have a **choice**, either **get the free version** and** apply for a new license code every six months**, or** pay $49** for a full license and **never get bothered again**.

[Here is the Download.]("http://www.4front-tech.com/release/oss-linux_v4.0-1014_amd64.deb")
I presume that you installed the 64bit version of Ubuntu, your post said that you have an AMD Athlon64 or an Opteron CPU.
Else. [click here.]("http://www.4front-tech.com/release/oss-linux_v4.0-1014_i386.deb") for the x86 driver.

For info [http://4front-tech.com/linux.html]("http://4front-tech.com/linux.html")

Hope this helps.
Regards
Iain

---

### Post by Rafinator on 2008-03-15
Wow, very fast reply, I thank you for that.  I didn't install in 64 since i've had many problems in the past.  I'm currently installing the driver and will tell you what happens.

Okay, it did infact work, but it is VERY loud.  Was there a control panel by any chance? I still cannot use the ubuntu volume control because it says "No volume control GStreamer plugins and/or devices found."   Is there any way to fix this?

---

### Post by ibuclaw on 2008-03-15
I recognise that error...

It's one of quite a few things.

Okay, first, lets make sure we have the lastest and right stuff installed.
Now I would like you to open up a terminal.
On the upper panel its:
    Applications>Accessories>Terminal
now copy and paste the following command. (Paste is Shift+Insert).

```
 sudo apt-get install alsa-base alsa-oss alsa-utils gstreamer0.10-x gstreamer0.10-alsa 
```

Though I recommend adding Medibuntu to your repository list and get your Ubuntu up to speed with Codecs, DVD Playback and other lovely stuff that you take for granted in Windows that doesn't come as Standard in the default Ubuntu Install. [(Here's a nice tutorial in this forum post is here I recommend that you go through it as it just so happens to fix 90% of all sound problems from when you first start off!).]("http://ubuntuforums.org/showthread.php?t=661833")

And make sure all is up to date. Type in:
```
 sudo apt-get upgrade 
```

And restart your computer.

If problems persist, message back. I will reply in short time :)

Regards
Iain

---

### Post by Rafinator on 2008-03-15
Unfortunately that didn't work, I also did everything in that thread you linked me to.

---

### Post by ibuclaw on 2008-03-15
Okay, open up your Sound Preferences.

This is in your upper tab:
  System>Preferences>Sound

You will see "Sound Playback" and "Sound Capture" for a number of tasks.
Since you are using the OSS driver, set everything to "OSS - Open Sound System"

And set your Device to your soundcard. I can't give you the name, as that is specific to your system, but it should have "(OSS Mixer)" after it.

You can turn your speakers down and click "Test" If sound is coming out, that is good, half the job done!
[[IMG]http://img408.imageshack.us/img408/5544/vol3kc7.th.png[/IMG]](http://img408.imageshack.us/my.php?image=vol3kc7.png)
Next, close the Sound Preferences.
Open up your Volume Control Preferences (Volume Icon in the Upper Right hand corner, next to the Date and Time). Right Click it and select "Preferences".
Select Your SB X-Fi Card as the Device to Control, and select Master or Volume as the Track to Control. It's usually first name at the top of the scroll list.
[[IMG]http://img169.imageshack.us/img169/9255/volsc6.th.png[/IMG]](http://img169.imageshack.us/my.php?image=volsc6.png)
Next, open your Volume Control (Right Click Volume Icon and Select "Volume Control")
Go into:
  File>Change Device
And select your SB X-Fi soundcard, if it isn't already the default.
[[IMG]http://img169.imageshack.us/img169/1084/vol2kd9.th.png[/IMG]](http://img169.imageshack.us/my.php?image=vol2kd9.png)
Now, hopefully, (I'm going on blind faith here) you should have some control over your volume.

Iain

---

### Post by ibuclaw on 2008-03-15
If you still can't get it done.

It is neither Software, Nor Device Related...

Last thing it could possibly be is that you have been removed from the "Audio" group.
When I say this, I mean that you have (somewhere along the line of installing Ubuntu) have been revoked of your Audio Privileges.

Going into:
  System>Administration>Users and Groups

Select your user, and click properties.
Under the "User Privileges" Tab, check, uncheck and re-check the "Use audio devices" tick box.
[[IMG]http://img135.imageshack.us/img135/7513/accountug2.th.png[/IMG]](http://img135.imageshack.us/my.php?image=accountug2.png)
Logout and log back in.
If you are still having difficulties, try setting your audio back to ALSA, as you should have the ALSA OSS wrapper installed. (apt-get install alsa-oss).
But make sure that it all points to your SB X-Fi Soundcard, that is a must.

And lastly, if all else fails, I'm sorry, but I've ran out of time and here is the best link I know that can explain in detail on adding you back to the audio groups.
[http://linux.dsplabs.com.au/no-volume-control-gstreamer-plugins-and-or-devices-found-no-sound-or-voume-control-bug-on-ubuntu-p31/](http://linux.dsplabs.com.au/no-volume-control-gstreamer-plugins-and-or-devices-found-no-sound-or-voume-control-bug-on-ubuntu-p31/)
Hope you have been pleased with my responses, Ubuntu is a rocky journey to start for any new beginner, but all stays well when you get it up and good!

Regards
Iain

---

### Post by Rafinator on 2008-03-15
Wow! I have to say your help is really surprising.  Thanks for spending your time writing that whole thing up.  I did what you said but under default mixer tracks in sound preferances there is no device.  I tried to go to hardware manager, but the window closed as soon as it opened!  Hopefully someone else can answer this question if you can't.

---

### Post by ibuclaw on 2008-03-15
Okay, I'm back from work!

I'm sorry to hear. Sound still works, right?

Well, I may have found the answer!
While I was having you faff about with the alsa controls. I completely disregarded the fact that OSS may have their own.
This is my fault, and I'm sorry, I found a documentation of it here.
[http://www.opensound.com/release/oss-install.pdf]("http://www.opensound.com/release/oss-install.pdf")

The information you need is on page 4/5.

type in the terminal this command:
```
 ossdetect 
```
All this should do is detect your soundcard, if it does and loading of the modules seems fine.

Now to see if a working mixer pops up...
```
 ossxmix -d0 
```
or
```
 ossxmix -d1 
```
Both should show a GTK mixer, As to what they control, you'll have to find out.

Now I want you to turn the main volume to a low level, and play a song. If you hear a quieter sound. I'll be jumping up and down with glee :lolflag:
Now turn it up till the level is appropriate for you.
Try this for both by the way,  to determine which one (if not both) work.

If it does. I am pleased to hear! Now all we need to do is get rid of the faulty ALSA volume control.
Right-Click the "Volume Control" icon and select "Remove From Panel".
Make sure that you've selected the right applet before you do.

Now right click on a space in the panel (somewhere in the centre) and click "Add to Panel".
A new window will pop-up with a load of applets for your panel, but all what we are interested in is creating a "Custom Application Launcer".

Lets Name it OSSMixer for example.
The Command will be "ossxmix -d1" or -d2 depending on which one works for you.
And as for a picture, try this for /usr/share/pixmaps/gnome-mixer.xpm

Now fingers crossed, when you click on the icon, the program should load and give you access to control the volumue.
And make the upper panel presentable, Lets move it back to it's original place, between wireless and data/time.

I hope this (finally) solves your problem.

Regards
Iain

Goodnight!

---

