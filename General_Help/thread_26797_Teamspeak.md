---
title: "Teamspeak"
date: 2005-04-13
forum: General Help
---

### Post by D_F on 2005-04-13
Teamspeak is a VoIP program that I use to talk to my friends with. It has work flawlessly for me on every distro except Ubuntu. I just did a clean install, but when I try to run Teamspeak, the program just doesn't come up. I am not sure where to go from here. :(

---

### Post by trash on 2005-04-13
I've looked into teamspeak, but couldn't figure it out... seems there are a lot of people using to, I hope it gets looked into for Ubuntu.

---

### Post by D_F on 2005-04-13
[QUOTE=trash]I've looked into teamspeak, but couldn't figure it out... seems there are a lot of people using to, I hope it gets looked into for Ubuntu.[/QUOTE]
 Yeah, it's really annoying me because I really like Ubuntu, but I really need Teamspeak. Someone who is using Ubuntu 5.04 said they had it working fine, but I can't even get it to work on a clean install.

---

### Post by trash on 2005-04-13
can't ya twist his/her arm to write a little howto? hehe

---

### Post by telmo on 2005-04-13
Love your bunny... lol

---

### Post by trash on 2005-04-14
naughty bunnies unite! hehe

---

### Post by crane on 2005-04-14
It's late and I need sleep. I will work on it tomorrow some and see if I can get it working on my hoary machine. I had it working fine under warty but could not play games and run teamspeak at the same time.
How about a little info on your system.

You said it won't start at all? What are some of your specs and what sound card are you running.

As I said I will install tomorrow and post if I have a problem and try to work through it.

If you come up with anything before then let me know :smile:

---

### Post by michealm on 2005-04-14
[QUOTE=crane]It's late and I need sleep. I will work on it tomorrow some and see if I can get it working on my hoary machine. I had it working fine under warty but could not play games and run teamspeak at the same time.
How about a little info on your system.

You said it won't start at all? What are some of your specs and what sound card are you running.

As I said I will install tomorrow and post if I have a problem and try to work through it.

If you come up with anything before then let me know :smile:[/QUOTE]
 I have TS running just did default install, and no problem

---

### Post by D_F on 2005-04-14
I tried running TeamSpeak from a clean install and it still wouldn't go.
I have onboard Intel (intel8x0) AC'97 audio.
It has worked flawlessly on other distros, why not for this one? :(

---

### Post by crane on 2005-04-14
[QUOTE=D_F]I tried running TeamSpeak from a clean install and it still wouldn't go.
I have onboard Intel (intel8x0) AC'97 audio.
It has worked flawlessly on other distros, why not for this one? :([/QUOTE]

Did you use sudo to install or install as user?

Oh try this.

click >>system > preferences > sound
Now uncheck the Enable Sound server startup box.

Now try to run Teamspeak again.

You should be able to run it alone. The only problem is with teamspeak running it will cause some game (like Quake3, ET and others) to hang up and not start.

I'm still working on that part.

---

### Post by D_F on 2005-04-15
Thank you crane. Disabling the sound server fixed everything. Now I'm just having problems running Battlefield 1942 (not with Teamspeak, just running BF1942 at all!). It starts, works fine, but when I go to load a map, it gets this error:
**MultiPlayerFreeCamera template not found**

This just isn't my day. :(

---

### Post by crane on 2005-04-16
[QUOTE=D_F]Thank you crane. Disabling the sound server fixed everything. Now I'm just having problems running Battlefield 1942 (not with Teamspeak, just running BF1942 at all!). It starts, works fine, but when I go to load a map, it gets this error:
**MultiPlayerFreeCamera template not found**

This just isn't my day. :([/QUOTE]

I think I have taht game as well. I'll see if I get the same error. you may want ot post [here](http://www.ubuntuforums.org/showthread.php?t=25723) it is a thread just for 3d gaming and maybe others will see it that have the same problem.

---

### Post by crane on 2005-04-16
OK I actually got teamspeak and quake3 to run together.

The how to link below will get it working for you.

[TeamSpeak How to](http://www.linux-gamers.net/modules/wfsection/article.php?articleid=34) 

You should read the whole thing and make sure you understand what your doing as you do it. 
There is one section about symlinking /dev/adsp and /deb/dsp
That is what needs to be done in Ubuntu to get it working.
The symlink has to be in place so the echo commands work correctly.

> echo "quake3.x86 0 0 direct">/proc/asound/card0/pcm1p/oss
echo "quake3.x86 0 0 disable">/proc/asound/card0/pcm1c/oss

echo "et.x86 0 0 direct">/proc/asound/card0/pcm1p/oss
echo "et.x86 0 0 disable">/proc/asound/card0/pcm1c/oss0 


 

I hope this help everyone out.

---

### Post by MajorNewby on 2005-04-17
I followed that guide, but it did nothing for me but trash the sound on my quake3 install... anybody got any idea what this line...
```
echo "quake3.bin 0 0 direct">/proc/asound/card0/pcm1p/oss
``` 
should be originally?

I am a complete n00b here... however, I'm not an idiot.  Something about that guide is wrong, but I can't figure out where it is - either that or my SoundBlaster Live ! 5.1 (emu10k1) card can't do both TS2 and Quake3...  help?

---

### Post by crane on 2005-04-17
[QUOTE=MajorNewby]I followed that guide, but it did nothing for me but trash the sound on my quake3 install... anybody got any idea what this line...
```
echo "quake3.bin 0 0 direct">/proc/asound/card0/pcm1p/oss
``` 
should be originally?

I am a complete n00b here... however, I'm not an idiot.  Something about that guide is wrong, but I can't figure out where it is - either that or my SoundBlaster Live ! 5.1 (emu10k1) card can't do both TS2 and Quake3...  help?[/QUOTE]

try
 quake3.x86 0 0 direct">/proc/asound/card0/pcm1p/oss

quake3 runs with the process name of quake3.x86
 That is what that command is doing. It is telling quake3 what to use.

---

### Post by MajorNewby on 2005-04-17
OK, got all my sounds working correctly again... unfortunately, after messing with that LinuxHOWTO guide for about 2 hours, I still cannot run quake3 when I'm running TS2 - please, do not make me go back to Windows... ](*,)

---

### Post by artinla on 2005-04-17
Actually, I think the line has a typo.

echo "quake3.bin 0 0 direct">/proc/asound/card0/pcm1p/oss

will replace the contents of /proc/asound/card0/pcm1p/oss with the line "quake3.bin 0 0 direct"

I think what they *wanted* to do was append the line to the end of the file.  The proper syntax for that would be:

echo "quake3.bin 0 0 direct" >> /proc/asound/card0/pcm1p/oss

Try that, however you have probably already trashed the original file by using the incorrect command.  You will have to figure out how to replace it, there may be a backup of it in the same folder.

Art

---

### Post by crane on 2005-04-17
from what I gathered from all the reading on this topic I have done. 
The idea is to tell which ever process you are running.

 The echo "quake3.bin ......" would not work if there was no process called quake3.bin.

I started quake3 the drop out of X (ctrl/alt/f1) then using the top command to see all running processes I found quake3 was running under quake3,x86.
After finding that out I went back to X (alt/f7) closed quake3 and used the echo command with the process name of quake3.x86.

That's where I came up with which command to use.

---

### Post by nautilus on 2005-04-18
[QUOTE=artinla]Actually, I think the line has a typo.

echo "quake3.bin 0 0 direct">/proc/asound/card0/pcm1p/oss

will replace the contents of /proc/asound/card0/pcm1p/oss with the line "quake3.bin 0 0 direct"

I think what they *wanted* to do was append the line to the end of the file.  The proper syntax for that would be:

echo "quake3.bin 0 0 direct" >> /proc/asound/card0/pcm1p/oss

Try that, however you have probably already trashed the original file by using the incorrect command.  You will have to figure out how to replace it, there may be a backup of it in the same folder.

Art[/QUOTE]

Actually, I highly suggest against attempting to move or remove proc node files...

You see, /proc is generally home to the Proc Filesystem, which most Linux systems use to give the user and other applications access to various driver and kernel internals, in this case, access to the ALSA sound subsystem.

The command as written instructs Alsa to use "DIRECT" mode on the first card's playback for all processes (programs) named quake3.x86, and the other line instructs Alsa not to attempt to capture from the device for that application.  This simply makes sense; quake3 doesn't work with a microphone, so we don't try to read from it.  This allows Teamspeak to use it, if you only have one capture channel, which most cheap sound cards only have.

The point of this is actually, the stuff in proc... it's not *real*.  It's created by the OS, and there are no files there.  They're a figment of Linux's imagination, there for your viewing pleasure.  So, using > or >> simply changes how the file is opened... nothing is overwritten, it's appended.  You must explicitly send an 'enable' to a disable or 'mmap' to a direct to negate the operation, you can't simply 'zero the file'.

I don't know, did that make any sense?  It's tough to describe, and I lack the technical lingo to say it properly, but just don't try to delete proc files.

---

### Post by MajorNewby on 2005-04-20
hrm... well, I reinstalled all the sound packages (just to make sure eveything is as it should be) then tried again... still no joy ](*,)   Anybody managed to get TeamSpeak2 and games like Quake3 Arena, Enemy Territory to work together?  Now that I have a stable linux setup, I'm quite happy with it... if I can avoid a reboot to run WinXP for my games, my life would be darn near complete! :-P

---

### Post by crane on 2005-04-20
[QUOTE=MajorNewby]hrm... well, I reinstalled all the sound packages (just to make sure eveything is as it should be) then tried again... still no joy ](*,)   Anybody managed to get TeamSpeak2 and games like Quake3 Arena, Enemy Territory to work together?  Now that I have a stable linux setup, I'm quite happy with it... if I can avoid a reboot to run WinXP for my games, my life would be darn near complete! :-P[/QUOTE]

 I was able to get mine working on my test computer \\:D/  I am running a sound blaster card. What type card are you using?

---

### Post by MajorNewby on 2005-04-21
I'm running a SoundBlaster Live! 5.1 (emu10k1), running gnome on hoary... someone is telling me it's because esd is running???

---

### Post by MajorNewby on 2005-04-27
bump?

any advice? :-|

---

### Post by crane on 2005-04-28
[QUOTE=MajorNewby]bump?

any advice? :-|[/QUOTE]

Sorry,

found this little tidbit on the [Wiki Page](http://www.ubuntulinux.org/wiki/RestrictedFormats)  that may help.
> 3. Sound and third party software

Ubuntu uses a program called esd to allow multiple applications to access the sound card at one time. However, many third party applications not in Ubuntu main aren't designed to use esd to access the card. On some sound cards, this causes these applications to not produce sound. To work around this problem, esd must be configured to release the sound card when it is not using it. To do this, edit /etc/esound/esd.conf and change the line that begins with spawn_options to begin with default_options. Finally, change the -as 5 to -as 2.

Note: this problem only occurs on the Ubuntu Hoary release and newer. Kubuntu and Ubuntu Warty are not affected by this.

---

### Post by kisain on 2005-04-28
i'm really new to linux and i don't even know how to install teamspeak just migrated from windows cause it sucks can anyone give me a step by step on how to install it? 
i already have the files and how do you run it once installed?

thanx for helpin

---

### Post by crane on 2005-04-28
[QUOTE=kisain]i'm really new to linux and i don't even know how to install teamspeak just migrated from windows cause it sucks can anyone give me a step by step on how to install it? 
i already have the files and how do you run it once installed?

thanx for helpin[/QUOTE]


It's pretty simple to install.
After you download it just unzip it. It will make a new directory call ts2_client.... or something like that.

Now open a terminal and cd to the directory it created,

[COLOR=Blue]cd /home/you/ts2_client....[/COLOR] <whatever the name of the directory is.
 Now you have two options.

 1st - you can install it as a user by just typing  [COLOR=Blue]sh setup.sh[/COLOR]
or 
 2nd - you could install as root [Color=Blue]sudo sh setup.sh[/COLOR]

I used the second option. This way it is installed as root and run as user. it will create a hidden file in your home directory called .teamspeak2 where all the configs are stored for the user. If you should ever screw up a config then you could just delete it and the root install is not harmed. When you run teamspeak again it just create a new .teamspeak2 file.

As far as running it, I believe it install a shortcut in the main menu or you can run it from a terminal by just entering [COLOR=Blue]teamspeak[/COLOR]

---

### Post by crane on 2005-04-28
Also as mentioned earlier. Be sure to go to 
system>preferances>sound in the menu and uncheck the enable sound server startup. If this is enabled it will cause troubles with teamspeak.

---

### Post by kisain on 2005-05-06
ok for some reason there seems to be a glitch in ubuntu with teamspeak....but i did however get it to run in kubuntu!!!! ^_^

here's what i did.......i extracted the files to it's own folder on the desktop
went in to console and typed : sudo ./setup.sh
and it was done!
now i haven't tryed this with ubuntu but i do know for a fact that it works in kubuntu why i do not know.

i hope that this helps all of you who are trying to install teamspeak.

kisain






























[QUOTE=D_F]Teamspeak is a VoIP program that I use to talk to my friends with. It has work flawlessly for me on every distro except Ubuntu. I just did a clean install, but when I try to run Teamspeak, the program just doesn't come up. I am not sure where to go from here. :([/QUOTE]

---

### Post by crane on 2005-05-06
[QUOTE=kisain]ok for some reason there seems to be a glitch in ubuntu with teamspeak....but i did however get it to run in kubuntu!!!! ^_^

here's what i did.......i extracted the files to it's own folder on the desktop
went in to console and typed : sudo ./setup.sh
and it was done!
now i haven't tryed this with ubuntu but i do know for a fact that it works in kubuntu why i do not know.

i hope that this helps all of you who are trying to install teamspeak.

kisain[/QUOTE]
 Could this be a Gnome problem?
Does anyone run Teamspeak in fluxbox or another desktop?

kisain, Have you run teamspeak and a game (quake3, ET) at the same time??

---

### Post by MajorNewby on 2005-05-08
Getting it to run in Gnome wasn't a problem.... Teamspeak installation was quite easy.  It's getting it to run with other games like Quake3, Enemy Territory.... :?

---

### Post by crane on 2005-05-08
[QUOTE=MajorNewby]Getting it to run in Gnome wasn't a problem.... Teamspeak installation was quite easy.  It's getting it to run with other games like Quake3, Enemy Territory.... :?[/QUOTE]

you right, I got it running with no problems, then I started quake3 :roll:

---

### Post by gazzie on 2005-05-08
Is it possible to use 2 different sound devices in TS linux? I have a USB microphone and I'd like to use that for input...

---

### Post by crane on 2005-05-10
[QUOTE=gazzie]Is it possible to use 2 different sound devices in TS linux? I have a USB microphone and I'd like to use that for input...[/QUOTE]


This I can't answer :-? 
Sorry I have no experience with usb mics.
You could try looking on teamspeaks site!

---

### Post by FX on 2005-05-10
Hate to say it, but just one of the reasons I still have a dual boot with XP is just for this.

---

### Post by esh on 2005-05-21
Hmm..me and many of my friends use TeamSpeak every day and it works very well with Hoary without any special settings.. :?
My soundcard is a SoundMAX 5.1 Digital and my friends use everything from old onboard AC'97 cards to Sound Blaster Audigy soundcards...

---

### Post by crane on 2005-05-21
[QUOTE=esh]Hmm..me and many of my friends use TeamSpeak every day and it works very well with Hoary without any special settings.. :?
My soundcard is a SoundMAX 5.1 Digital and my friends use everything from old onboard AC'97 cards to Sound Blaster Audigy soundcards...[/QUOTE]

Do your play games as well? Quake3 or ET?

---

### Post by esh on 2005-05-22
[QUOTE=crane]Do your play games as well? Quake3 or ET?[/QUOTE]
I've only tried with Steam, RtCW and Doom 3 - no problems.
Hope you getting it to work!

---

### Post by darkjedi8359 on 2005-05-28
[QUOTE=crane]Did you use sudo to install or install as user?

Oh try this.

click >>system > preferences > sound
Now uncheck the Enable Sound server startup box.

Now try to run Teamspeak again.

You should be able to run it alone. The only problem is with teamspeak running it will cause some game (like Quake3, ET and others) to hang up and not start.

I'm still working on that part.[/QUOTE]this seems to fix the team speak problem, but when I do this no other sounds work but team speak. ](*,) . Thanks for that solution. I also use a AC'97 onboard sound card :) I just switch it back to the way it was as I am not playing any games on linux atm.

---

### Post by TristanMike on 2005-06-19
Hi, this seems to be the only teamspeak help thread so I though I'd post my issue here too.

I've installed TS2 with no problems, but now, when I close the program, it just hangs there.  Any idea on what I can do to stop making it hang when I close?

I'm still a Linux/Command Line noob, so please bear with me.

Thank You
TristanMike

EDIT: P.S. About Teamspeak [Quote=trash]... seems there are a lot of people using to, I hope it gets looked into for Ubuntu.[/Quote]
I second that motion, great program, very popular.

---

### Post by mohaham on 2005-06-20
this might help solve this problem..
edit /etc/esound/esd.conf file
to change auto_spawn=0 to auto_spawn=1

here's my /etc/esound/esd.conf file:

[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 5
spawn_wait_ms=100

---

### Post by TristanMike on 2005-06-20
[QUOTE=mohaham]this might help solve this problem..
edit /etc/esound/esd.conf file
to change auto_spawn=0 to auto_spawn=1

here's my /etc/esound/esd.conf file:

[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 5
spawn_wait_ms=100[/QUOTE]

If you were refering to mine, it didn't.  Any other suggestions?

Thanx
TristanMike

---

### Post by mohaham on 2005-06-20
sorry, i was referring to the problems with the sound..

---

### Post by TristanMike on 2005-06-20
I thought so, but I also thought I'd double check, thanx anyway.....but anyone who might field my question, please give it a go....

Thanx
TristanMike

---

### Post by linuxwhatsthat on 2005-11-09
[QUOTE=crane]It's pretty simple to install.
After you download it just unzip it. It will make a new directory call ts2_client.... or something like that.

Now open a terminal and cd to the directory it created,

[COLOR=Blue]cd /home/you/ts2_client....[/COLOR] <whatever the name of the directory is.
 Now you have two options.

 1st - you can install it as a user by just typing  [COLOR=Blue]sh setup.sh[/COLOR]

or 
 2nd - you could install as root [Color=Blue]sudo sh setup.sh[/COLOR]

I used the second option. This way it is installed as root and run as user. it will create a hidden file in your home directory called .teamspeak2 where all the configs are stored for the user. If you should ever screw up a config then you could just delete it and the root install is not harmed. When you run teamspeak again it just create a new .teamspeak2 file.

As far as running it, I believe it install a shortcut in the main menu or you can run it from a terminal by just entering [COLOR=Blue]teamspeak[/COLOR][/QUOTE]

I installed just like u said here for option 2 but i cant get ts to run at all i checked in the menu's and cant find it and if i type teamspeak in the terminal it says command not found all suggestions more than welcome :)

---

### Post by crane on 2005-11-10
[QUOTE=linuxwhatsthat]I installed just like u said here for option 2 but i cant get ts to run at all i checked in the menu's and cant find it and if i type teamspeak in the terminal it says command not found all suggestions more than welcome :)[/QUOTE]

Try 
[color=blue]/opt/TeamSpeak2RC2/TeamSpeak
[/color]

That should start it. I believe when  you restart gnome panel there will be a link in the menu.

---

### Post by hav0x on 2005-12-10
Teamspeak does not use esd/arts or alsa. It really doesn't matter what kind of settings you have on both of them. it uses oss, and that is the problem.
It hogs the oss all for itself. still there are workarounds for this ... will install ET see if i can manage a solution and post back.

---

### Post by hav0x on 2005-12-10
well that was pretty simple.
what i did:
opened a terminal logged in as root did the echo thingie after checking the devices i had.
In short:
```

~$sudo -i
~#echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
~#echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss

```
Then i opened Teamspeak and connected to a public server.
Opened teh gamezor and checked if the sound was working ( it was ). And toke a picture of the whole thing.
Teh pic:
[[IMG]http://img529.imageshack.us/img529/2014/capturaecra1uh.th.jpg[/IMG]](http://img529.imageshack.us/my.php?image=capturaecra1uh.jpg)
It really hasn't changed  from other distros or from what i had to do in Hoary.
I'm packing a SB Live! 5.1. You might have to change the capture (/proc/asound/card0/pcm0c/oss) and playback (/proc/asound/card0/pcm0p/oss) device in other sound cards but that's the trick and it works fine. Basically what it does is tell the game to run using the alsa oss "emulation" thingie so it doesnt mess with the oss thingie Teamspeak uses.
You'll have to do it everytime you reboot, i used to have a thing/script to do it on boot back when i was using Fedora, but cant be bothered to think about it right now.
It works fine.;)

---

### Post by kisain on 2005-12-21
well i fixed it and got it to run ^^ thank you for all your help

---

### Post by happyponcho42 on 2006-03-07
Anyone able to get beep-media-player to work while TeamSpeak is running?

---

