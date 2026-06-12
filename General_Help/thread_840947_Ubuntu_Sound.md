---
title: "Ubuntu Sound"
date: 2008-06-25
forum: General Help
---

### Post by LoneWolfXAxis on 2008-06-25
I have racently had Ubuntu put on my computer. Though it is working amazingly well, I have a bit of a sound problem. I don't have the Gstreamer plugins that it needs to run sound. What king of Gstreamer do I need to look for?

---

### Post by Vivaldi Gloria on 2008-06-25
> **LoneWolfXAxis said:**
> I have racently had Ubuntu put on my computer. Though it is working amazingly well, I have a bit of a sound problem. I don't have the Gstreamer plugins that it needs to run sound. What king of Gstreamer do I need to look for?

Start synaptic and install

```
ubuntu-restricted-extras
```

which contains gstreamer plugins and other goodies. 

Or you can search gstreamer in synaptic and install the ones you want.

---

### Post by LoneWolfXAxis on 2008-06-25
What would be the name for the Gstreamer for volume control? Could you help me out, I can't find it.

---

### Post by Vivaldi Gloria on 2008-06-25
> **LoneWolfXAxis said:**
> Gstreamer for volume control?

There is no such thing. I think you are confusing things. Sound should work out of the box. 

Can you please give some more info. 

1) Does any sound work in your computer or you can't play a particular file? What is your exact problem?

2) When you login do you hear the login-sound? 

3) Can you play and hear the files in your examples folder? 

4) What error messages are you getting and when?

---

### Post by LoneWolfXAxis on 2008-06-26
Say if I want to hear a video on youtube or listen to a song on itunes, I can't turn my volume up because the volume menu keeps saying there is no gstreamer for the volume control on the desktop volume control button.

---

### Post by AmericanYellow on 2008-06-26
Looks like your sound card was not detected correctly and the audio drivers didn't install correctly. You should first check the forums to see if people with your same computer/sound card have the problem and how they fixed it. If you don't find anything, then I suggest you downloading the current ALSA driver and compile it yourself.


This guide will help you with your problems

[http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449")

---

### Post by LoneWolfXAxis on 2008-06-26
This is very confusing to me. I can't find the "shell" that I need to look for in the link you gave me, American Yellow. Could you help me through this step by step? Or anyone with suggestions...I have 3 Logitech speakers hooked up to my computer. But they will not work. They work in windows but not on Ubuntu for some reason.

---

### Post by Vivaldi Gloria on 2008-06-26
To open a Terminal (shell) do as follow:

Choose Applications &#8594; Accessories &#8594; Terminal;

Or press Alt+F2 and type gnome-terminal.

You'll write the commands here.

See 

[https://help.ubuntu.com/8.04/basic-commands/C/](https://help.ubuntu.com/8.04/basic-commands/C/)

to learn the basics of the terminal.

---

### Post by LoneWolfXAxis on 2008-06-26
I am stuck on part three of this link.

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

I am sorry for being a burden but I am still trying to get used to computers. I have no idea what exactly I am looking for and where to go. I did all the steps up to three. But the link it gave me brings me to two different other links instead of a drop box that it tells me that I will see. can someone direct me to where I need to be? I feel like I am almost done with this. I just need a little more help.

---

### Post by Nepherte on 2008-06-26
Look up your sound card here: [http://www.alsa-project.org/main/index.php/Matrix:Main](http://www.alsa-project.org/main/index.php/Matrix:Main)

---

### Post by LoneWolfXAxis on 2008-06-26
Ok, I have made it to the file that my driver is supposed to be in. But I have no idea what to do with it. I see it in my terminal with different commands that I can't seem to perform unless I am doing it wrong.

---

### Post by ghalia on 2008-06-26
I am having the same problem. Installed Heron, had sound (e.g. at login), installed updates and now sound is gone, with a red circle over the volume control. There are about a zillion posts related to this topic, but with everyone giving different, and confusing, advice. What is going on? Why can't Ubuntu find my sound card and how can this be EASILY remedied?!

Please help :confused:

---

### Post by LoneWolfXAxis on 2008-06-27
I've done the best on my part, but I still need help. I need directions and advice. Refer back to my last quote for where I am at now.

---

### Post by guiliker on 2008-06-27
I'm not sure how much my reply will help but I had this issue. Sound working fine one minute and then gone the next...I never found out what caused it though. 

My solution was: I dual boot with Win XP Sp3 and Ubuntu Hardy so I checked sound in XP and that was gone too. Tried all kinds of windows fixes and it was still not working. Tried reformatting the dual boot with no success. In the end I formatted whole HDD with Windows 98, which is a different file system and sound worked ok. Reformatted with the dual boot and sound was OK. I suspect what happened was either the sound chip driver got corrupted or the bios was corrupted. Either way it's a drastic solution but it worked for me.

I'd also suggest the most productive way to get gstreamer plugins and other related packages is using the following rather than "ubuntu-restricted-drivers":
open terminal type:

```
sudo gedit /etc/apt/sources.list
```

Copy and paste following in the end of the file the below:

```
## Medibuntu - Ubuntu 8.04 "hardy" 
## Please report any bug on https://bugs.launchpad.net/medibuntu/ 
deb http://packages.medibuntu.org/ hardy free non-free
```

save the document and close, then in the terminal type:

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - 
```

in order to receive the appropriate key. 

Finally at the terminal type one command at a time:
```
sudo apt-get update
sudo apt-get install gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-bad-multiverse
sudo apt-get install gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly
sudo apt-get install gstreamer0.10-ffmpeg libxine1-ffmpeg libdvdread3
sudo apt-get install gstreamer0.10-pitfdll
sudo apt-get install w32codecs
sudo apt-get install libdvdcss2
sudo apt-get install sun-java6-plugin
sudo apt-get install flashplugin-nonfree
sudo apt-get install mozilla-plugin-vlc
sudo apt-get install liblame0
sudo apt-get install msttcorefonts
sudo apt-get install rar unrar
sudo apt-get install p7zip-full
sudo apt-get update
sudo apt-get upgrade
```

instructions compiled from: 
1. [http://ubuntuguide.org/wiki/Ubuntu:Hardy]("http://ubuntuguide.org/wiki/Ubuntu:Hardy")
2. [http://ubuntuguide.org/wiki/Ubuntu:Gutsy]("http://ubuntuguide.org/wiki/Ubuntu:Gutsy")
3. [http://packages.ubuntu.com/hardy/ubuntu-restricted-extras]("http://packages.ubuntu.com/hardy/ubuntu-restricted-extras")

---

### Post by Vivaldi Gloria on 2008-06-27
> **LoneWolfXAxis said:**
> Ok, I have made it to the file that my driver is supposed to be in. But I have no idea what to do with it. I see it in my terminal with different commands that I can't seem to perform unless I am doing it wrong.

LoneWolfAxis, 

At step 2 you find your audio device in the output of "lspci -v". At step three you find whether there is an alsa driver for it or not. If there is a driver then there isn't anything else to do in step three. Move to step 4.

---

### Post by LoneWolfXAxis on 2008-06-27
I have made it to a screen that gives me the file, what do I need to do next? I am still stuck in step 4.

---

### Post by Vivaldi Gloria on 2008-06-27
Write 

```
sudo nano /etc/modules
```

not

```
sudo nano /etc/hda-intel
```

Actually, editing a file is easier with gedit. Press Alt+F2 and start

```
gksudo gedit /etc/modules
```

And add your module's name snd-hda-intel at the end and save.

---

### Post by LoneWolfXAxis on 2008-06-27
Now that I have the hang of the screenshot feature I can further your thoughts on what the problem might be. Every time I click on the volume control button that is next to the date and internet connection icons, this sign pops up!

---

### Post by LoneWolfXAxis on 2008-06-27
Ok, is this the way it needs to look? Just making sure so I don't mess anything up.

---

### Post by Vivaldi Gloria on 2008-06-27
> **LoneWolfXAxis said:**
> Ok, is this the way it needs to look? Just making sure so I don't mess anything up.

That's right. The guide says that add snd-hda-intel under the last line and save. 

But before that, have you tried 

```
sudo modprobe snd-hda-intel
```

in a terminal as the guide says? It tells in step 4 before "success". Does writing that line in a terminal makes sound work?

---

### Post by LoneWolfXAxis on 2008-06-27
No, my sound still doesn't work. I don't get it, my sound works for windows but not for ubuntu. Maybe I did something wrong. Let me go back to where I am supposed to find the chipset for the soundcard. I will show you a screenshot of what was given to me. 

But this sign still keeps popping up when I click on the sound icon...

---

### Post by Vivaldi Gloria on 2008-06-27
What happens when you write

```
ls -la /dev/snd 
```

in a terminal?

---

### Post by LoneWolfXAxis on 2008-06-27
For what you asked me to do, I was given this...

---

### Post by Vivaldi Gloria on 2008-06-27
What are the results of the following commands:

```
dpkg --get-selections | grep modules-2.6
```

```
uname -r
```

You can copy from the terminal and paste here btw.

---

### Post by LoneWolfXAxis on 2008-06-27
I get something like this...

---

### Post by Vivaldi Gloria on 2008-06-27
> **LoneWolfXAxis said:**
> I get something like this...

How about writing the following in the terminal:

```
lsb_release -a
```

and

```
uname -a
```

---

### Post by LoneWolfXAxis on 2008-06-27
This...where exactly are you leading me with all this?

---

### Post by Vivaldi Gloria on 2008-06-27
> **LoneWolfXAxis said:**
> This...where exactly are you leading me with all this?

Well, all this time I assumed that you had the latest ubuntu. It turns out you have an older one (7.10). I should have asked earlier. Sorry for that. So we lost a bit of time. Now back on track. I found a bug report related to your problem:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/164598/](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/164598/)

Let's try the solution given there. In terminal try:

```
sudo apt-get install linux-ubuntu-modules-2.6.22-15-386
```

If it gives no errors then restart your system.

---

### Post by LoneWolfXAxis on 2008-06-27
Will I still have to restart with this response?

---

### Post by Vivaldi Gloria on 2008-06-27
> **LoneWolfXAxis said:**
> Will I still have to restart with this response?

You didn't write the command correctly! There is a typo. Why don't you copy and paste to the terminal?

To copy select the text and right click and then copy. To paste right click the terminal and choose paste.

---

### Post by LoneWolfXAxis on 2008-06-27
Ok, I have restarted my computer and it has been updated. But I now have another problem...My screen has suddenly changed to super size! How do I fix this to where everything is small in my last ubuntu?

---

### Post by Vivaldi Gloria on 2008-06-27
> **LoneWolfXAxis said:**
> Ok, I have restarted my computer and it has been updated. But I now have another problem...My screen has suddenly changed to super size! How do I fix this to where everything is small in my last ubuntu?

In the upper panel, click the system > preferences > screen resolution and choose a higher resolution.

What about sound? Is it fixed?

---

### Post by LoneWolfXAxis on 2008-06-27
Ok, Vivaldi, I appreciate your help. I really do. But help me with my screen first. The thing is...I can't get back on ubuntu without my screen saying it is "out of signal" and it needs to switch to "1680x1050 @ 60Hz.

I can't get anywhere when that pops up. I am on windows right now and I am having the same problem here too. Am I able to fix my screen problem from windows or the start up menu?

---

### Post by Vivaldi Gloria on 2008-06-27
> **LoneWolfXAxis said:**
> Ok, Vivaldi, I appreciate your help. I really do. But help me with my screen first. The thing is...I can't get back on ubuntu without my screen saying it is "out of signal" and it needs to switch to "1680x1050 @ 60Hz.

I can't get anywhere when that pops up. I am on windows right now and I am having the same problem here too. Am I able to fix my screen problem from windows or the start up menu?

Am I understanding this correctly:

You have an LCD screen with native resolution 1680x1050 @ 60Hz. Right?

If the resolution is different than 1680x1050 @ 60Hz the screen itself says "out of signal". But it continues to work anyway after it pops up that message. Or what happens after you get that message?

Does this work: Try right-clicking the windows desktop, choose properties and the settings tab. Then make the resolution 1680x1050. Then click the advanced button and the monitor tab and choose 60Hz. Click Ok.

---

### Post by LoneWolfXAxis on 2008-06-27
Yes your advice works. Now will this work for Ubuntu since I changed it for windows? Or do I need to do that somewhere else? The thing is, when I do get that message, I can't really change anything at that time...unless you know a way I don't. The best I can do is restart. But please continue...

---

### Post by Vivaldi Gloria on 2008-06-27
> **LoneWolfXAxis said:**
> The thing is, when I do get that message, I can't really change anything at that time

I don't understand what you say. What happens when you get that message? Can't you still move your mouse and click the menus etc.?

Where exactly did you that get that message when you are booting ubuntu? Do you remember? Before the login window? After the login window?

---

### Post by LoneWolfXAxis on 2008-06-27
I am sorry for confusing you. Heres the deal.

When click on Ubuntu at the menu that has Ubuntu, Windows, etc. Its where you pick which system you want to load. When I click on ubuntu, it take a little bit for it to load. Then the message pops up. I can't see anything but the message. I have no mouse to move with or click. After that I have to turn off my computer because there is nothing else for me to do or see. Thats unless you know something that I don't.

---

### Post by Vivaldi Gloria on 2008-06-27
> **LoneWolfXAxis said:**
> I am sorry for confusing you. Heres the deal.

When click on Ubuntu at the menu that has Ubuntu, Windows, etc. Its where you pick which system you want to load. When I click on ubuntu, it take a little bit for it to load. Then the message pops up. I can't see anything but the message. I have no mouse to move with or click. After that I have to turn off my computer because there is nothing else for me to do or see. Thats unless you know something that I don't.

OK. I get it know. I'll try something and get back to you in 20 mins.

---

### Post by enchesss on 2008-06-27
it sound like your video card drivers or xorg settings are set to a low resolution.

if you have a grub menu to dual boot then you should also have an option to boot in safe graphics mode.

login as root and type the following command

sudo dpkg-reconfigure -phigh xserver-xorg

when you get a new prompt type

startx

---

### Post by enchesss on 2008-06-27
check this too it may be easier

[http://ubuntutip.googlepages.com/nodisplay](http://ubuntutip.googlepages.com/nodisplay)

i found it here:

[http://ubuntuforums.org/showthread.php?t=842847](http://ubuntuforums.org/showthread.php?t=842847)

---

### Post by Vivaldi Gloria on 2008-06-27
Sorry. I'm back.

You need to edit c:\wubi\boot\grub\menu.lst and do two things:

1) Increase the timeout 

2) Comment out the hidemenu option by deleting the # sign before it. 

Then reboot. Select ubuntu. Now you will see a second boot menu. Choose the one with recovery near to the top.

Now you'll reach a menu which contains an item "fix X-server" or something like that. It should fix it automatically.

---

### Post by LoneWolfXAxis on 2008-06-27
Where do I go to do that? Can you provide me with steps?

---

### Post by Vivaldi Gloria on 2008-06-27
> **LoneWolfXAxis said:**
> Where do I go to do that? Can you provide me with steps?

OK. There are two different ways of installing ubuntu and windows together. It depends whether there is a c:\wubi folder in windows or not. So is there a c:\wubi folder in windows?

---

### Post by LoneWolfXAxis on 2008-06-27
I am sorry for being a total newbie at this, but where do I find the folder that the file is supposed to be in?

---

### Post by Vivaldi Gloria on 2008-06-27
> **LoneWolfXAxis said:**
> I am sorry for being a total newbie at this, but where do I find the folder that the file is supposed to be in?

Double click on my computer and double click on C drive. Is there a wubi there?

---

### Post by LoneWolfXAxis on 2008-06-27
No I do not see a wubi file there.

---

### Post by Vivaldi Gloria on 2008-06-27
OK. Restart your computer. 

Do you immediately reach a boot menu which has a line containing "recovery" in its name or do you reach a menu which says "press Esc to enter menu" at the bottom or something like that. In the first case choose the recovery line near to the top. In the second case press Esc to reach the menu and choose the recovery line near to the top.

After you choose recovery it'll boot a few seconds and you'll reach another menu which contains an item "fix X-server" or something like that. It should fix it automatically.

You may need to use the tab key and the arrow keys to navigate that last menu.

---

### Post by LoneWolfXAxis on 2008-06-27
So in the boot menu, where it says: ubuntu (recovery)

Click that?

---

### Post by Vivaldi Gloria on 2008-06-27
> **LoneWolfXAxis said:**
> So in the boot menu, where it says: ubuntu (recovery)

Click that?

Yes. And then wait for the other menu and choose fix X-server there.

---

### Post by LoneWolfXAxis on 2008-06-27
When I click on the ubuntu (recovery mode), all it does is bring up a scrolling list of things that its doing and then it gives me a line to put in a command. I can't find the recovery button you are wanting me to find. Can you list me possibilities of where to find it?

---

### Post by Vivaldi Gloria on 2008-06-27
> **LoneWolfXAxis said:**
> When I click on the ubuntu (recovery mode), all it does is bring up a scrolling list of things that its doing and then it gives me a line to put in a command. I can't find the recovery button you are wanting me to find. Can you list me possibilities of where to find it?

Hmm. Then that feature is new in ubuntu 8.04 and your ubuntu version gives just a command line. Then type this when the command line appears:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

It'll reconfigure and fix things. Then you'll be in command line again. You need to learn how to shutdown the system from the command line. Use

```
sudo shutdown -h now
```

to shutdown and 

```
sudo shutdown -r now
```

to reboot. 

Then see if ubuntu is fixed.

---

### Post by LoneWolfXAxis on 2008-06-27
Ubuntu is still not fixed. I still get the monitor message.

---

### Post by Vivaldi Gloria on 2008-06-27
> **LoneWolfXAxis said:**
> Ubuntu is still not fixed. I still get the monitor message.

That's bad news. I'll write what to do now, wait 5 mins.

---

### Post by LoneWolfXAxis on 2008-06-27
Are you still online? Its been 30 minutes...

---

### Post by Vivaldi Gloria on 2008-06-27
The screen and resolution settings of ubuntu (among other settings) is kept in this file:

```
/etc/X11/xorg.conf
```

You have to manually edit and fix it from the command line. But first make a backup copy incase we need it later:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_old
```

Now open that file with nano:

```
sudo nano /etc/X11/xorg.conf
```

Unfortunately you'll have to use the nano editor because nice editors like gedit don't work in the command line.

You move around with arrow keys and make the changes and to save it you need to 

1) Press Ctrl+X
2) Answer yes to save
3) Press enter to save on top of the original file.


So what to change in xorg.conf?

You must find the section that starts with Section "Screen" and change it to look as follows:

```
    
Section "Screen"
Identifier     "Default Screen"
    Device         "???????????????? keep whatever is written here"
    Monitor        "???????????? keep whatever is written here"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1680x1050" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
```

When you save you'll be back in the command line. Restart using the commands in the above post and check if things are fixed. 

If it still doesn't work then try putting "1680x1050_60" in place of "1680x1050" in the above line.

---

### Post by Vivaldi Gloria on 2008-06-27
LoneWolfXAxis,

It's 6am in the morning here and I haven't slept yet. I am going to bed know. See you later.

---

### Post by holiday on 2008-06-27
Here's the thing:

You've got a weird sound card or some configuration quirk that Ubuntu doesn't cover out of the box. You could try googling about Linux sound and see if you get interested, but if you don't, and if you don't have a Sunday or two to spare, then either buy another sound card - maybe a good idea - (checking the Ubuntu compatibility lists) or get another operating system.

Happy Linux users are a bit like crossword puzzle people. They like solving puzzles. They get very excited about it, so much that they will try to get you excited too. Good people. 

However - if you have something important to do and Linux isn't working for you then I suggest a Mac. They're pricey, but reliable.

---

### Post by LoneWolfXAxis on 2008-06-28
Ok, Vivaldi I am back online and I am ready to finish this problem. Hopefully it can be done today. Out of the codes you gave me, one of them worked in the command line. After that was entered it brought up a "new file". I had no clue what you wanted me to do at that point because I was sure that you were expecting me to find a list of some kind.

This code could not be found: /etc/x11/xorg.conf
and: sudo cp /etc.x11/xorg.conf /etc.x11/xorg.conf_old

---

### Post by Vivaldi Gloria on 2008-06-28
> **LoneWolfXAxis said:**
> Ok, Vivaldi I am back online and I am ready to finish this problem. Hopefully it can be done today. Out of the codes you gave me, one of them worked in the command line. After that was entered it brought up a "new file". I had no clue what you wanted me to do at that point because I was sure that you were expecting me to find a list of some kind.

This code could not be found: /etc/x11/xorg.conf
and: sudo cp /etc.x11/xorg.conf /etc.x11/xorg.conf_old

You have typos in the code. it's /etc/X11/ not /etc.x11/ and be careful, linux is case sensitive so x11 and X11 are NOT the same.

So have a look at my post above and type them exactly.

---

### Post by LoneWolfXAxis on 2008-06-28
I was in the right area "section screen". But I don't know why it wouldn't work. I even tried putting Hz after the 60, for 60Hz. Is it an absolute must to have the code like this: 1680x1050_60 (with the underscore?)

The original mode had @ instead of an underscore.

I am still getting the message saying that my display needs to be set to 1680x1050@60Hz

---

### Post by Vivaldi Gloria on 2008-06-28
> **LoneWolfXAxis said:**
> I was in the right area "section screen". But I don't know why it wouldn't work. I even tried putting Hz after the 60, for 60Hz. Is it an absolute must to have the code like this: 1680x1050_60 (with the underscore?)

The original mode had @ instead of an underscore.

I am still getting the message saying that my display needs to be set to 1680x1050@60Hz

I have seen it both ways actually so try try with @ also. You have saved the file and restarted right?

Don't puz Hz at the end. Never seen it like that.

Also try leaving only 1680x1050 part and delete the other resolutions. But first try adding @ and then this.

---

### Post by LoneWolfXAxis on 2008-06-28
Before I leave, do I need to get rid of the quotes? ""
Or do I keep those?

---

### Post by Vivaldi Gloria on 2008-06-28
> **LoneWolfXAxis said:**
> Before I leave, do I need to get rid of the quotes? ""
Or do I keep those?

Try

```
Modes      "1680x1050@60" "1280x1024" "1024x768" "800x600" "640x480"
```


and

```
Modes      "1680x1050"
``` 

and

```
Modes      "1680x1050@60" 
```

---

### Post by LoneWolfXAxis on 2008-06-28
I've tried all of them and nothing works. Could there be something else thats contributing to the monitor problem?

---

### Post by Vivaldi Gloria on 2008-06-28
> **LoneWolfXAxis said:**
> I've tried all of them and nothing works. Could there be something else thats contributing to the monitor problem?

Damn. I've have run out of ideas. I suggest one of two things:


1) Open a new thread 

[http://ubuntuforums.org/forumdisplay.php?f=334](http://ubuntuforums.org/forumdisplay.php?f=334)

at the hardware subforum. There are more experts there. Don't forget to link this thread. I am pretty sure that someone will come with a better idea. 


2) Download and intall the new ubuntu from

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

This will fix all your problems. It's easy to install ubuntu once you watch the videos here:

[http://screencasts.ubuntu.com/](http://screencasts.ubuntu.com/)

Download Ogg/Vorbis/Theora - Large ones if your connection speed allows (the links are at the top right). Especially watch installing ubuntu parts 1 and 2. The part you need to watch carefully is the part about partitions. You don't want to install the new ubuntu on top of windows but rather on the old ubuntu. There is also a video on how to burn ubuntu to cd there.

If I were in your shoes then I would go with option two. It's really not hard to install it. Besides, it's the new version of ubuntu. 


I'm sorry but I can't think of anything else now. Don't give up ubuntu. You have already learned a lot, if only it worked... 

Please let me know what option you'll choose.

---

