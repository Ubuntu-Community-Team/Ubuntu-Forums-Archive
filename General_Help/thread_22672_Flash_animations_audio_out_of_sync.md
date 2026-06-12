---
title: "Flash animations audio out of sync"
date: 2005-03-29
forum: General Help
---

### Post by NeoChaosX on 2005-03-29
Is it me, or is anybody else having audio sync problems when viewing Flash animations? If I view a Flash animation either off the web or opening a file on the hard drive, the audio (if any) starts to slowly play a bit slower than the video in the Flash. I've also noticed this behavior in Mandrake 10.1. Is there any way to fix this problem?

---

### Post by NeoChaosX on 2005-04-04
*bump*

So no one else is having audio issues with Flash?  :|

---

### Post by TravisNewman on 2005-04-04
Totally. I REALLY wish this would work.

Using the Windows flash plugin in Ubuntu's firefox (through crossover) really likes to bork some things. Flash bleeds through tabs, it steals focus so you can't type in the address bar, etc. I didn't have that particular issue with the Linux flash plugin, but I watch a lot of Homestar Runner (speaking of which, I wonder if they've updated yet ;)) so I need the video and audio to sync up.

Surely someone other than us is having this issue. I posted about this ages ago and got no replies either. Searching Google barely turns up anything EXCEPT that this was supposed to be fixed in 7. It's not.

---

### Post by NeoChaosX on 2005-04-13
One more time:  do you people seriously notice no audio sync problems in the Flash plugin? Or are PT and I the only ones have this problem?

---

### Post by jasonmallison on 2005-04-14
Yes, I am having these same issues as well. Could it be an ALSA issue? Or ESD?

---

### Post by NeoChaosX on 2005-04-14
I know that switching to either ALSA or ESD doesn't fix the problem. I dunno how to get OSS to work so I can test that, either.

---

### Post by poofyhairguy on 2005-04-14
[QUOTE=panickedthumb] I didn't have that particular issue with the Linux flash plugin, but I watch a lot of Homestar Runner (speaking of which, I wonder if they've updated yet ;)) so I need the video and audio to sync up.[/QUOTE]

Homestar Runner. Kickass, never heard of that have to try it out.

I don't have flash problems. If I had to guess why, its because of the things I did to Firefox according to this howto:

[http://ubuntuforums.org/showthread.php?t=25850](http://ubuntuforums.org/showthread.php?t=25850)

---

### Post by NeoChaosX on 2005-04-15
I don't think that HowTo is the answer. It's informative, but it has nothing regarding tweaking sound. I tried installing Flash Player from the Macromedia installer (instead of the mozilla-flashplayer package) but it didn't change a thing, either.

I'm a big fan of [Nanaca Crash](http://homepage.mac.com/pockyrevolution/nanaca_crash.html), and the audio sync problem really throws off my timing in that game. I'd love to get this problem fixed ASAP.

---

### Post by misterlizard on 2005-04-15
I get sync problems with flash in Firefox too. It starts pretty much in sync but slowly drifts out, becoming quite noticable by about half a minute.

I'm using KDE and used to use the Arts engine with Firefox, which was really bad as the sound would start, then restart after about half a second and continue to drift out. Once I disabled Arts and got Firefox running with esound (going into ALSA) instead things improved greatly. Still not quite there though.

As this involves the sync getting worse as the animation goes on, I'd guess that this is a timing problem within the flash player, rather than an audio problem.

Are there any other Linux flash players that work with Firefox?

---

### Post by psoleko on 2005-04-15
Is this a Firefox specific issue? I have noticed some weirdness in some Flash games, but nothing too distracting yet. Does Konqueror have similar issues with Flash to anyones knowledge?

---

### Post by misterlizard on 2005-04-15
Just tried flash under Konqueror and I get the same problem as under Firefox.

Under Firefox, I've tried the following plugins (just tried 2. under Konqueror):

1. Flash downloaded from within Firefox (getting put in ~/.mozilla/plugins). Starts OK, but drifts out.

2. flashplayer-mozilla 7.0.25-woody0.0 from Synaptic. Same results as above (probably as it's the same code).

3. swf-player 0.3.2-2 from Synaptic. Pauses for about 10s with a black box before playing the animation. Starts in sync, but drifts out pretty much the same as the above ones.

4. libflash-mozplugin 0.4.11-2 from Synaptic. Couldn't get this to work. FIrefox just crashes out with the following error:

The program 'Gecko' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadShmSeg (invalid shared segment parameter)'.
  (Details: serial 30 error_code 169 request_code 148 minor_code 2)

---

### Post by misterlizard on 2005-04-15
OK. Here's a fix. You'll need to open a shell window and then:

1. Kill esd with:
    killall esd
2. Install alsa-oss if you don't already have it
    sudo apt-get install alsa-oss
3. Tell Firefox to use the aoss wrapper
    FIREFOX_DSP=aoss
    export FIREFOX_DSP
4. Start Firefox **on the command line using the same shell as you did above** (just type 'firefox') and try a flash animation. Hopefully it'll work.

Reading around a bit on various other forums, it looks like the problem is to do with the esound daemon not being very good with sync. Firefox will run with the esddsp or artsdsp wrapper by default since it's an OSS only application. However, by specifying 'aoss' as the DSP, we can get it going directly into ALSA without the extra mixing stage of esd. esd running at all seems to cause the sync problem, even if Firefox is going through aoss.

You may run into trouble trying to play more than one sound at once. Not sure if there's a way round this since it's a restriction of OSS.

You may need to setup alsa for software mixing, this thread has some good info on this:
[http://www.ubuntuforums.org/showthread.php?t=8882](http://www.ubuntuforums.org/showthread.php?t=8882)

If you must use esd, you can make the plugin get its sync back by right clicking it, deselecting 'Play' and reselecting it.

Hope this helps, let me know if it's still bad.

---

### Post by anopenscroll on 2005-04-15
[QUOTE=misterlizard]OK. Here's a fix. You'll need to open a shell window and then:

1. Kill esd with:
    killall esd
2. Install alsa-oss if you don't already have it
    sudo apt-get install alsa-oss
3. Tell Firefox to use the aoss wrapper
    FIREFOX_DSP=aoss
    export FIREFOX_DSP
4. Start Firefox and try a flash animation. Hopefully it'll work.

Reading around a bit on various other forums, it looks like the problem is to do with the esound daemon not being very good with sync. Firefox will run with the esddsp or artsdsp wrapper by default since it's an OSS only application. However, by specifying 'aoss' as the DSP, we can get it going directly into ALSA without the extra mixing stage of esd. esd running at all seems to cause the sync problem, even if Firefox is going through aoss.

You may run into trouble trying to play more than one sound at once. Not sure if there's a way round this since it's a restriction of OSS.

You may need to setup alsa for software mixing, this thread has some good info on this:
[http://www.ubuntuforums.org/showthread.php?t=8882](http://www.ubuntuforums.org/showthread.php?t=8882)

If you must use esd, you can make the plugin get its sync back by right clicking it, deselecting 'Play' and reselecting it.

Hope this helps, let me know if it's still bad.[/QUOTE]
 I sure, sure hope your setup is default, because it fixed everything :)

---

### Post by mesocool on 2005-04-15
[QUOTE=misterlizard]OK. Here's a fix. You'll need to open a shell window and then:

1. Kill esd with:
    killall esd
2. Install alsa-oss if you don't already have it
    sudo apt-get install alsa-oss
3. Tell Firefox to use the aoss wrapper
    FIREFOX_DSP=aoss
    export FIREFOX_DSP
4. Start Firefox and try a flash animation. Hopefully it'll work.

Reading around a bit on various other forums, it looks like the problem is to do with the esound daemon not being very good with sync. Firefox will run with the esddsp or artsdsp wrapper by default since it's an OSS only application. However, by specifying 'aoss' as the DSP, we can get it going directly into ALSA without the extra mixing stage of esd. esd running at all seems to cause the sync problem, even if Firefox is going through aoss.

You may run into trouble trying to play more than one sound at once. Not sure if there's a way round this since it's a restriction of OSS.

You may need to setup alsa for software mixing, this thread has some good info on this:
[http://www.ubuntuforums.org/showthread.php?t=8882](http://www.ubuntuforums.org/showthread.php?t=8882)

If you must use esd, you can make the plugin get its sync back by right clicking it, deselecting 'Play' and reselecting it.

Hope this helps, let me know if it's still bad.[/QUOTE]

The flash does have sound after the setup. But my Music Player cannot play music anymore and the sound when clicking on a program is disappearing.. ](*,)

---

### Post by NeoChaosX on 2005-04-15
I just tried misterlizard's instructions, and the audio is still out of sync. Changed to ALSA and everything.  :???:

---

### Post by misterlizard on 2005-04-16
Well, it helped someone :)

NeoChaosX: did you start Firefox from the command line or from the start menu? I should have put that it needs to be started from the command line after the 'export FIREFOX_DSP'. I've edited the post now.

If that doesn't work then try opening another shell and doing 'pgrep esd'. If this produces some output (1 or more numbers) then the esound daemon has kicked, and Firefox is probably still going through that.

mesocool: do you get any sound out of Music Player after you've exited out of Firefox? (make sure all Firefox windows are closed) Does Music Player work normally after restarting your computer?

---

### Post by NeoChaosX on 2005-04-16
[QUOTE=misterlizard]NeoChaosX: did you start Firefox from the command line or from the start menu? I should have put that it needs to be started from the command line after the 'export FIREFOX_DSP'. I've edited the post now.[/quote]
I didn't the first time. but I did now, and it still hasn't changed a thing. Flash audio is still drifting out of sync.

> If that doesn't work then try opening another shell and doing 'pgrep esd'. If this produces some output (1 or more numbers) then the esound daemon has kicked, and Firefox is probably still going through that.
I just did this and it didn't produce a line of output.

Now I'm stumped.

---

### Post by misterlizard on 2005-04-17
I'm stumped too. Tried out polypaudio instead of esd, and it was no better with the drifting, and it kept taking up 100% CPU when idle, causing a strange whining noise to come from the computer (not from the speakers, which was weird).

Then I tried getting rid of the OSS modules in the kernel, in an attempt to get the flash sound going to ALSA via aoss. Sometimes the page with the flash wouldn't load, or the flash would start but stop as soon as the sound started, or it would run in silence.

Anyway, I've gone back to esd now. I'll just have to put up with things going out of sync, or watch flash on another, non-ubuntu computer.

Does anyone know if later versions of Firefox or flash will feature direct ALSA output?

---

### Post by caoac on 2005-05-19
Hey everyone.  I'm having the same sync problems with a flash mx file.  My problem, though, stems from a project that I'm working on.  I'm doing a cartoon and, though the animation is right in stride with the audio at start, the audio gradually begins to lag behind the visuals as the file progresses on playback.  This is not media dependent.  I encounter the same problem in flash's "test movie"; netscape and IE; quicktime, etc.  This leads me to believe it's NOT something that can be fixed by tweeking FireFox, IE, etc. 

I noticed, however, that when I playback my movie, if I STOP/PLAY the file mid-run, it seems to sync up again.  That is, if I have a file and I STOP the playback when things start going astray, wait for a second, then resume playing the file everything's happily lined up.  You'll pardon my ignorance here, but is this a processing issue?  Is the audio gradually becoming too hefty to process simultaneously with the animations?  This would explain other users' problems when trying to view things like Homestarrunner (What a great cartoon!), regardless of what medium they use.  

I should say, though,  that I have a great computer with plenty of speed and plenty of space.  It really SHOULD be able to handle all of the code thrown at it from just about any flash file. 

Here's the really confusing part.  The cartoon I'm doing is about 30 minutes long and it has something like 10 individual files that I'm going to put up together as scenes in one large, flash movie.  When viewing them independently,  I had NO PROBLEMS with audio sync in the first six files.  Then, all of a sudden, the file I was working on last night refused to line up.  Everything's the same from the authoring standpoint.  Audio format and rates are all the same;  I'm using the same files from the same library.  It all syncs up when I play it within the authoring window, but the minute I export it to "Test Movie," we're audio dragging once again.

If anyone would like to knock heads about this, I'm all for it.  There has to be something that we're missing. 

Good Times...

---

### Post by TravisNewman on 2005-06-04
OK I've officially done everything in this thread, and nothing has helped.

How many of us with sound issues have SB Live! cards?

---

### Post by NeoChaosX on 2005-06-04
This issue seems to be universal with Linux. I have a SigmaTel C-Major Audio on my laptop, and I'm still suffering from this problem.

---

### Post by TravisNewman on 2005-06-04
Thing is, I've been talking with Kassetra and she doesn't have ANY problems. Never has with version 7 of the plugin. So I have no clue.

---

### Post by TravisNewman on 2005-06-05
OK I posted this problem on the macromedia forums and emailed macromedia.

Hopefully we can get this crap worked out.

---

### Post by BKonkle on 2005-06-06
I just wanted to raise my hand and say I've been having the same problem.  I'm running an AMD64 3200+ system with Hoary i386 and the backport repositories enabled.  My sound card is an SiS SI7012.  I have ALSA selected as my default Sink and Input source.  I use the Beep Media Player RC2 to play music through ALSA.  (How can I make this my default player instead of Totem, by the way?)  I have implemented the configuration file changes suggested in this and other threads.  At first my sound was really choppy and garbled, but then I got everything switched over to ALSA and now I'm just having the flash delay / out of sync problem.  The FIREFOX_DSP export works perfectly, but then no other sounds on my system work.

I just wanted to add to the ranks of everyone who is having a problem.  Should I go ahead and fire off an email to Macromedia as well?

---

### Post by TravisNewman on 2005-06-06
hehe, absolutely. If we flood them, they HAVE to reply to one of us.

I also posted this question to the mozillazine forums.

[http://forums.mozillazine.org/viewtopic.php?p=1518977#1518977](http://forums.mozillazine.org/viewtopic.php?p=1518977#1518977)

---

### Post by TravisNewman on 2005-06-06
Oh, and here's the link to the macromedia forum post: 
[http://www.macromedia.com/cfusion/webforums/forum/messageview.cfm?catid=184&threadid=1011442&enterthread=y](http://www.macromedia.com/cfusion/webforums/forum/messageview.cfm?catid=184&threadid=1011442&enterthread=y)

---

### Post by BKonkle on 2005-06-06
I just wanted to report that for some reason, the FIREFOX_DSP export trick is no longer working for me.  I've rebooted and tried it several times, but even though it worked before it no longer solves the problem.

Sure is hard to watch the trailer for Peasant's Quest: The Movie with all that audio lag!    :-(

---

### Post by TravisNewman on 2005-06-06
I love that trailer ;)

---

### Post by NeoChaosX on 2005-06-07
Okay, I think I've found one fix for the sync problem: **don't run any other programs that use ESD while running Firefox**. Normally, I have Gaim and probably Beep Media Player opened while surfing the Internet. Just now, I tried playing a Flash animation without any other programs opened. The Flash sync problem was gone!   :)  Now our problem is getting the program to work properly while other apps that are using the sound card are open.

EDIT: Okay, try not using ESD apps while Flash is running. I just tried Flash again with Beep running outputted to ALSA, and Flash isn't going out of sync either. As you can guess, I had Gaim output to ESD, but not anymore.  :wink:

EDIT2: And I have FIREFOX_DSP set to AOSS, so trying that (along with having libesd-alsa0 and alsa-oss installed) might help.

---

### Post by kiddo on 2005-06-12
Same problem here, on a 2.4ghz desktop (with an Nvidia geforce fx5200 and a Sound blaster live thingyaudigy platinum blah blah) and on a laptop with a mere 8mb radeon and maestro sound.

I think by closing gaim (the only app open) it made the synch on the [advent children]("http://www.square-enix.co.jp/dvd/ff7ac/") trailer 4 a bit better, but it went desynching over time still. 

I wanted to add the fact that the sound is too high in flash files. It's choppy. Listen to a music from a flash file, and listen from a music (yeah I know, not the same compression) from your media library, you may notice that it blows off the peaks.

I really hope macromedia could do some patching there.
2nd testing: on the 2.4ghz desktop, it makes not difference.

---

### Post by joelito on 2005-06-17
Ok i've managed to make a little script with the solution that was posted before
```

#!/bin/bash
killall esd;
FIREFOX_DSP=aoss;
export FIREFOX_DSP;

```
Now, what i NEED to know is how to set it up so it would run automatically (maybe as a service)

---

### Post by NeoChaosX on 2005-06-18
You don't need a script to do that.

"killall esd" = Go into System > Prefrences > Sound and uncheck "Enable sound server startup".

"FIREFOX_DSP=aoss" = Just edit /etc/mozilla-firefoxrc and set the variable there.

---

### Post by joelito on 2005-06-22
What I finaly did was setting the esd.conf to release the sound hardware as soon it's not using it and setting oss as the default sound system.

What I wanted was a setting that would work for all users automagically

---

### Post by NeoChaosX on 2005-06-23
Okay, lemme try again on how I got it to work. Getting Firefox sound to work again after reinstall Hoary clued me in on what to do.

1. sudo apt-get install libesd-alsa0 alsa-oss (Installs OSS-to-ALSA packages)
2. ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1 (Enables sound in Firefox)
3. Enabled sound mixing as detailed [here](http://ubuntuforums.org/showthread.php?t=26567) (This enables sound mixing via dmix)
3a. In addition to that, add these lines to /etc/asound.conf
```
pcm.dsp0 {
	type plug
	slave.pcm "dmixer"
}

ctl.mixer0 {
	type hw
	card 0
}
```(This allows dmix to process OSS calls to ALSA.)
4. sudo gedit /etc/mozilla-firefox/mozilla-firefoxrc
Change value of FIREFOX_DSP to "aoss" (this tells Firefox to use OSS routed through ALSA)
5. Go into System > Preferences > Sound and uncheck "Enable sound server startup" (disables ESD, which messes with Flash for some reason)
5a. killall esd (just to make sure that ESD is gone)
6. Now start Firefox and go to a Flash-based diversion of your choice. Sound should now be in sync!

---

### Post by NeoChaosX on 2005-08-15
Um, sorry to bump this back up, but now I've got Flash in sync with ESD on.

You have to install esound-clients

```
sudo apt-get install esound-clients
```then edit **/etc/esound/esd.conf** and change this line

```
auto_spawn=0
```to "auto_spawn=1".

You still have to have Firefox set up to use OSS emulated by ALSA  (FIREFOX_DSP=aoss) as described above.

---

### Post by Corlian on 2005-08-25
[QUOTE=NeoChaosX]Okay, lemme try again on how I got it to work. Getting Firefox sound to work again after reinstall Hoary clued me in on what to do.

1. sudo apt-get install libesd-alsa0 alsa-oss (Installs OSS-to-ALSA packages)
2. ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1 (Enables sound in Firefox)
3. Enabled sound mixing as detailed [here](http://ubuntuforums.org/showthread.php?t=26567) (This enables sound mixing via dmix)
3a. In addition to that, add these lines to /etc/asound.conf
```
pcm.dsp0 {
 type plug
 slave.pcm "dmixer"
}

ctl.mixer0 {
 type hw
 card 0
}
```(This allows dmix to process OSS calls to ALSA.)
4. sudo gedit /etc/mozilla-firefox/mozilla-firefoxrc
Change value of FIREFOX_DSP to "aoss" (this tells Firefox to use OSS routed through ALSA)
5. Go into System > Preferences > Sound and uncheck "Enable sound server startup" (disables ESD, which messes with Flash for some reason)
5a. killall esd (just to make sure that ESD is gone)
6. Now start Firefox and go to a Flash-based diversion of your choice. Sound should now be in sync![/QUOTE]

My flash sound was out of sync with the animation, so I followed these steps (except for 5, killall esd always says "no process killed"), and now I get NO sound with flash.  Other sound from Kubuntu and music remains unchanged after switching the sound system from oss to alsa.

Any idea why the flash sound would go away after this rather than be fixed?

---

### Post by Corlian on 2005-08-25
Okay, if I have FIREFOX_DSP="aoss", that gives me flash with no sound, and a Firefox that likes to crash a lot.

If I switch FIREFOX_DSP back to "auto" (with a reboot), I return to choppy sound and no crashes.

Can anyone help?

Incidentally, now that I setup alsa-oss via this thread, I get all system sounds except for the startup music.  Annoying but not life-threatening...still, is that fixable?

---

### Post by elempoimen on 2005-08-27
I've been following this thread with great interest, as I love the videos at [www.living.com](www.living.com).

I've followed all the instructions here (and in the other thread referred to, about running esd through arts), and I've tried every possible DSP wrapper with Firefox--and it's actually worse now than when I started.

Just for craps and giggles, I decided to log in from a basic terminal (Failsafe Terminal under Sessions, for those "not in the know") and run Firefox.  I headed to [www.living.com](www.living.com)...and what do you know?  Everything works PERFECTLY.  The video was right in-sync.

What do you make of that?  I'll check my processes and see what's all running...but this is basically single-task mode (or at least I'm not smart enough to figure out how to do it multi-task)--so I can't get a process list.

Edit: so, I exited Firefox and ran gnome-system-manager to take a look at what was running.  Of course, OSS and ALSA load as modules, so they were running.  What's more interesting is that ESD was also running--so the problem is apparently NOT a conflict among these 3 systems.  It's also worth mentioning that Firefox is running with the AOSS wrapper.

So, what's the deal, I wonder?  Why does it run great outside of GNOME, but like crap inside of GNOME?

---

### Post by elempoimen on 2005-08-27
I know...bad form replying to my own post.

I've figured it out.  It is, indeed, ESD that is the problem.  Apparently GNOME spawns a second instance of ESD when started.  For some unknown reason, even when FIREFOX_DSP="aoss" is set, as long as this second daemon is running, Firefox runs all sound through it.  Note also that I have my system sound set to ALSA in the multimedia selector.  ESD is all but out of the loop--but Firefox still uses it.

So, I killed this copy of ESD (which ended up killing them both) while Firefox was running.  I restarted Firefox...and viola!  Flash audio was in sync.

Now, NeoChaosX, you said you got this to work with ESD on.  My settings match yours, but it still doesn't work.  Would you please post your entire /etc/esound/esd.conf?  I'd like to see if we have some different settings elsewhere.

Thanks!

---

### Post by Corlian on 2005-08-27
The thing is though, I use KDE, and I'm just catching on to the fact that KDE doesn't try to use ESD like GNOME does.  And yet, I still have all the same problems as the GNOME people.

---

### Post by elempoimen on 2005-08-27
The plot sickens...

You're right.  The *only* way I can get Flash to stay in sync is to use the FIREFOX_DSP="aoss" setting.  If I try any other DSP setting for Firefox, Flash goes out of sync.  This would seem to me to be a problem with Macromedia's implementation--as I have the same problem with Opera.

The problem is, that the aoss wrapper introduces some instability, as earlier mentioned.

You should maybe try editing /etc/mozilla-firefox/mozilla-firefoxrc to read as above and report your findings.  Be sure that you have the alsa-oss package installed first, otherwise it won't do any good.

---

### Post by NeoChaosX on 2005-08-27
Argh, sorry elempoimen for not responding sooner...classes started for me and I haven't been online as much.

Anyway, unfortunately, the ESD thing was a temporary fix, as I found later that it just went out of sync again. The fix you described in killing the second ESD process, then restarting Firefox was how I got it working, so I think the only option, really, is to stop using ESD.  :mad: 

But for reference, here's my esd.conf:
```
[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 0 -d dmixer
spawn_wait_ms=50
# default options are used in spawned and non-spawned mode
default_options=
```
Corlian, did you check buffer_size in /etc/asound.conf? I've found that the sound is actually prettly clear when buffer_size is set 8192, but YMMV.

---

### Post by elempoimen on 2005-08-27
Bummer, dude.  I miss sounds--and I have to have to kill ESD everytime I want to watch flash.

The big question is: how do we keep ESD from grabbing Firefox while running?  The whole gnome environment depends on ESD.

Does anyone know about polypaudio?  Maybe that's the solution.  The howto here isn't very good, with the author saying later in the thread that he switched back to ESD.

---

### Post by elempoimen on 2005-08-27
I THINK I'VE GOT IT!!!

1. open a terminal and enter ```
sudo apt-get install alsa-oss
```
2. then ```
sudo gedit /etc/mozilla-firefox/mozilla-firefoxrc
```
3. edit the file to read: ```
FIREFOX_DSP=aoss
```save the file, then exit gedit.

4. you may have made a link from libesd.so.0 to libesd.so.1 to get flash sound working.  **delete it.**  it is a big source of problems, because it forces the flash plugin to talk to ESD.  use: ```
sudo rm /usr/lib/libesd.so.1
```
5. **this is important:** edit (or create) your asound.conf to reflect the following--this minimizes latency on the system (credit goes to [http://phaeronix.net/asoundrc](http://phaeronix.net/asoundrc)).  in the terminal, enter ```
sudo gedit /etc/asound.conf
```then, replace the file contents with the following:
```
pcm.card0 {

  type hw

  card 0

  mmap_emulation true

}

pcm.!output {
type dmix
ipc_key 1234
ipc_key_add_uid 1
slave {
pcm "card0"
period_time 0
period_size 1024
buffer_size 8192
rate 44100
}
bindings {
0 0
1 1
}
}

#
# DSNOOP output device
#
pcm.!input {
type dsnoop
ipc_key 4321
ipc_key_add_uid 1
slave {
pcm "card0"
period_time 0
period_size 1024
rate 44100
}
}

#
# ASYM duplex device
#
pcm.!duplex {
type asym
playback.pcm "output"
capture.pcm "input"
}

#
# Make the duplex device default
#
pcm.!default {
type plug
slave.pcm "duplex"
}

#
# OSS Compability

pcm.!dsp0 {
type plug
slave.pcm "duplex"
}

ctl.!mixer0 {
type hw
card 0
}

```save and close gedit.

6. this step may not be necessary, but what the hey...it works for me and doesn't seem to hurt anything.  in the terminal: ```
sudo gedit /etc/esound/esd.conf
```replace the contents of that file with the following:
```
[esd]
auto_spawn=0
spawn_options=
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=-terminate -nobeeps -as 1

```
7. To make sure everything sticks, reboot your computer and then give it a whirl!  My favorite testing site is [www.living.com](www.living.com) (check out the hamburgers section--the mini man burgers are awesome, but make sure you cut the seasoning in half *grins*)

---

### Post by Corlian on 2005-08-28
NeoChaosX:

I've tried 8192 (and other suggested values), but it doesn't change the behavior.

Elempoimen:

Using your asound.conf and removing the libesd.so.1 link made no difference.  And then, like always for me, switching to FIREFOX_DSP=aoss stopped all my flash sound.

---

Since everyone talks so much about ESD, I tried on KDE doing killall artsd, which in my ignorance just kills all sound across the system and doesn't help flash.

They say so many sound issues have been fixed in Breezy...do we know if flash sound is part of that?  I think I gotta give up on fixing this for now.  Thanks for the suggestions.

---

### Post by elempoimen on 2005-08-28
[QUOTE=Corlian]Elempoimen:
Using your asound.conf and removing the libesd.so.1 link made no difference.  And then, like always for me, switching to FIREFOX_DSP=aoss stopped all my flash sound.[/QUOTE]Are you 100% sure you have the alsa-oss package installed?  If you don't then, no, this won't work.  The aoss wrapper is what is contained in the alsa-oss package.  In retrospect, you may also need to have libsdl1.2debian-all installed.  By default, Hoary only includes the alsa component--OSS programs won't give you sound w/o the OSS component as well--so it's easiest to just install the full package, which will also make ESD use ALSA.  Make sure you have those two libraries.

Try running Firefox from a terminal using "firefox --verbose" and see what happens.  You should see something like this: ```
FIREFOX_DSP=aoss
APPLICATION_ID=firefox
CMDLINE_DISPLAY=
DISPLAY=:0.0
REMOTE=0
TRY_USE_EXIST=0
OPTIONS=
DEBUG=0
DEBUGGER=
Running: /usr/lib/mozilla-firefox/firefox-bin -a firefox -remote 'ping()'
PING_STATUS=2
Cleaning user profile
Running: aoss /usr/lib/mozilla-firefox/firefox-bin -a firefox
```You especially need to see that last line.  If you don't see the "aoss" command, then you don't have alsa-oss, or it's not configured right.

Please do try this and let me know your findings.  If this does it, then I'll need to update my howto above.

---

### Post by NeoChaosX on 2005-08-28
[QUOTE=elempoimen]4. you may have made a link from libesd.so.0 to libesd.so.1 to get flash sound working.  **delete it.**  it is a big source of problems, because it forces the flash plugin to talk to ESD.  use: ```
sudo rm /usr/lib/libesd.so.1
```[/QUOTE]
YES! This did the trick for me.  :)  Firefox is going through AOSS again! You have to post this whole thing in the HOWTO section, elempoimen, this is incredibly helpful, especially since a lot of the sound FAQs tell you to do the /usr/lib/libesd.so.1 link to get Firefox sound just to function.

Note that I already did step 5, I already have ALSA set up through dmix and everything. You may want to change that /etc/asound.conf you posted, though, as the config you have listed there breaks quite a few things.

---

### Post by Corlian on 2005-08-28
[QUOTE=elempoimen]Are you 100% sure you have the alsa-oss package installed?  If you don't then, no, this won't work.  The aoss wrapper is what is contained in the alsa-oss package.  In retrospect, you may also need to have libsdl1.2debian-all installed.  By default, Hoary only includes the alsa component--OSS programs won't give you sound w/o the OSS component as well--so it's easiest to just install the full package, which will also make ESD use ALSA.  Make sure you have those two libraries.[/QUOTE]

Thanks so much for trying to help me.

I had followed the instructions in the forums to install alsa-oss, and Kynaptic confirms it's installed.

I added libsdl1.2debian-all just now, made sure the bad file link was removed, changed back to FIREFOX_DSP=aoss, and rebooted.  I get the same output as you from firefox --verbose.  Now I get no flash sound at all, but the animations run smoothly (not always the case before with some sound configurations), but then on homestarrunner, clicking on anything freezes firefox.

I'm pretty sure I haven't done anything except the instructions out of this thread...I reinstalled fresh just before finding this thread too...but it's hard to keep up after a while, and perhaps I did something to it that I didn't recognize at the time.

Thanks again for all the help.

A note -- I installed libsdl1.2debian-all through Kynaptic instead of the terminal, and before installing it, I saw it only had the oss part installed already.  However, my sound system is set up specifically through alsa (after installing alsa-oss), and all sounds from all programs come through.  Is that how it was supposed to be?

---

### Post by NeoChaosX on 2005-08-28
Corlian: can you paste the contents of your /etc/asound.conf here?

---

### Post by elempoimen on 2005-08-28
[QUOTE=NeoChaosX]You may want to change that /etc/asound.conf you posted, though, as the config you have listed there breaks quite a few things.[/QUOTE]What did it break for you?  For me, I've not noticed any problems yet...but if you can be specific about what troubles you've had, then perhaps I can test on my machine.  The asound.conf file may not be the "silver bullet" here--it may be that the rerouting of libesd.so.1 is the issue.  However (and I'll need to test more to make this conclusive), if I recall correctly, I needed to have this asound.conf in order to get it to work.  I backed up the old file (recommended elsewhere in the forums), so perhaps I'll switch back and see if it still works.

Your help is invaluable--if I can get all the bugs worked out of the howto, then I'll post it.

**Corlian** - you're on KDE, right?  I think this will have to be a GNOME-specific fix.  I'm sorry I can't help you.  I'm sure the solution for you is similar, however, except that you'll need to keep the Flash plugin from talking to artsd instead of esd.  Admittedly, I gave up on KDE (that's why I'm using Ubuntu)--I had more problems than fixes, and more extra configuring to do than I cared for.  That's why I'm running GNOME now--and liking it much better.

On Linux, it seems that KDE appeals to the Windows users better, and GNOME (especially Ubuntu's setup, as it's very similar in functionality) appeals more to the Macintosh crowd.  I just joined the Mac crowd this year--and I'm running Ubuntu so I can have a good OS on my laptop.  POSIX rocks!  (Boy, that sounded immature... *g*)

Edit: Corlian, I just had a thought.  Is ALSA talking directly to your sound hardware, or is it still passing through ARTS to get to your sound card?  Here's how you tell: open up kpm and find artsd in the process list.  Start an app that uses sound--preferably something that you can make use ALSA directly (not a KDE app), maybe Mplayer or Xine or something.  Play some audio and watch the CPU on artsd.  If artsd has activity whilst you're playing audio, then ALSA is still passing through the ARTS pipeline, and that's probably your problem.  ARTS, like ESD in GNOME, add latency to the system.  Beyond that, I don't have a fix for you--but at least it will get you pointed in the right direction.  For giggles, install some minimal WM, like OpenBox, and log into it--having your setup like I have here.  Try out flash--and see if it's better.  Using a different WM should stop ARTS from running.  If things work, then you'll know for certain what you need to do.  Then, it's just a matter of finding out how to do it.  :wink:

---

### Post by NeoChaosX on 2005-08-28
[QUOTE=elempoimen]What did it break for you?  For me, I've not noticed any problems yet...but if you can be specific about what troubles you've had, then perhaps I can test on my machine.[/QUOTE]

Actually, never mind. I thought you have configured your pcm.!default section the wrong way, but I was actually looking at pcm.!duplex. Your config file's fine, and the problems don't have anything to do with Flash.

---

### Post by Corlian on 2005-08-29
NeoChaosX:

For /etc/asound.conf, I've used both the one you suggested in this thread, and the one elempoimen recently suggested, but it made no difference.

[QUOTE=elempoimen]Edit: Corlian, I just had a thought.  Is ALSA talking directly to your sound hardware, or is it still passing through ARTS to get to your sound card?  Here's how you tell: open up kpm and find artsd in the process list.  Start an app that uses sound--preferably something that you can make use ALSA directly (not a KDE app), maybe Mplayer or Xine or something.  Play some audio and watch the CPU on artsd.  If artsd has activity whilst you're playing audio, then ALSA is still passing through the ARTS pipeline, and that's probably your problem.  ARTS, like ESD in GNOME, add latency to the system.  Beyond that, I don't have a fix for you--but at least it will get you pointed in the right direction.  For giggles, install some minimal WM, like OpenBox, and log into it--having your setup like I have here.  Try out flash--and see if it's better.  Using a different WM should stop ARTS from running.  If things work, then you'll know for certain what you need to do.  Then, it's just a matter of finding out how to do it.  :wink:[/QUOTE]

Well, you're right about artsd.  Amarok made artsd spike, and testing sound in the sound system config made artsd go up a little.

I'll try another window manager...I'm curious about them anyway, and I'll do anything to get to the bottom of this.  I'm so happy with my Linux experience so far, I don't want to let a little thing like this ruin the whole affair.

As far as KDE and GNOME...;)...well, I have my reasons for using KDE, and I've been very happy with it so far, and I've made it look pretty un-Windows.  But I'm certainly open to other ideas, and I'll look into different managers and packages.  I just had intended to do it after I got the first one working. ;)

---

### Post by NeoChaosX on 2005-08-29
Hey Corlian, FIREFOX_DSP can be set to "arts". Try changing /etc/mozilla-firefox/mozilla-firefoxrc and see if that setting works.

---

### Post by Corlian on 2005-08-29
[QUOTE=NeoChaosX]Hey Corlian, FIREFOX_DSP can be set to "arts". Try changing /etc/mozilla-firefox/mozilla-firefoxrc and see if that setting works.[/QUOTE]

I was so hopeful for this, but it didn't help.

I tried xfce, but almost no sounds at all worked there, let alone flash.

I guess I may reinstall everything and try again.

Again, thanks for everyone's advice.

---

### Post by elempoimen on 2005-08-30
Corlian, all I can say is "I'm sorry."  I'd really hoped this would work for you, too.  KDE is just a strange beast, sometimes.

At least I'm 50% there.  This seems like it will work with standard Ubuntu.  I'll work on tweaking it and getting that HowTo posted.

---

### Post by Corlian on 2005-08-31
I reinstalled with Breezy colony 3 and updated everything.  Flash sound now stays totally in sync (but with some cracks and pops that I'll have to try and fix).  Once again, thanks for everyone's help.

...but, since it was brought up... ;)

Now that I've spent a little time in GNOME, I really do like KDE much more.  I'm glad I have GNOME installed now, because there are aspects of it I think are really interesting, and I like some of the programs a lot more, and it does seem "tighter" somehow.  But generally everything worked just as well in KDE, and most importantly for me, KDE is a lot more configurable.  Everyone talks about configurability being the biggest strength of Linux, and KDE continues that idea in a deeper way.  Plus, I think two panels are kind of wasteful (unless they have a specialty purpose like on a Mac), and I know you can consolidate them in GNOME, but...on KDE I can have it precisely as I want, simple as that.  If I've missed something, let me know, but I've looked all through GNOME-look.org.  I think the answer for me is KDE, and then stripping down all the menus to be much more simple, and then making it look cool (via transparent panels and other add-on goodies).

Just a newcomer's perspective.  Not trying to beat the apparently *very* dead horse. ;)

---

### Post by elempoimen on 2005-09-01
I'm glad to hear that things are better for you!

And as far as beating a dead horse goes...hey, it's whatever works for you.  I've been down both roads, and even though I've found that there are some KDE apps that work better for me, I prefer the GNOME environment.  YMMV.  :-P

---

### Post by Corlian on 2005-09-03
Hmm...well...I spoke a bit too soon.  I added KDE to my Breezy, and I have the exact same flash problems as with Kubuntu Hoary.  But Kubuntu Breezy apparently has had almost no testing, so at this point I 'll just have to wait and see.

I got a copy of the free Linspire that's going around this weekend, hopeful that I'd finally have a KDE desktop with working flash, but Linspire barely worked at all once I had it going, it continually hung and crashed, and even though it auto-detected some things better than Ubuntu, I couldn't even keep the sound setup box from crashing long enough to get sound working.  Not to mention that it took around two minutes to boot (compared to 50 sec for Ubuntu and 30-ish sec for XP), or that on first boot it auto-loads a tutorial that hung for me every time.  Luckily I remembered the key combination for killing programs in Linux.

I'm sure this is common for new Linux users, but -- it's so frustrating to consider yourself "good at computers", and apt with technology in general, and all of a sudden find yourself helpless when trying to fix something in Linux.  I wish I had the tools to dig in and figure these problems out for myself.

---

### Post by elempoimen on 2005-09-04
Then the problem is most certainly ARTS.  Sorry, I've become a pretty dedicated GNOME user lately, so I can't help you.

As far is the troubles with Linux--you're not alone.  This is my 4th or 5th stab at it, and I'm finally here to stay now.  The major prerequisite is that you have to learn to think differently about how an OS works.  And since the majority of OS's currently in use besides Windows are POSIX-based (or at least POSIX-inspired), I'd say that Windows is probably the OS with the broken mindset.  When Apple based OS X on Mach/BSD, they were the last major OS (other than Windows) to move to a POSIX kernel.  It's a great system, really, because your OS can be so customized for whatever you need.  The downside: it's a bit more technical, and there are hitches here and there (as you've seen).  Overall, more stable--and potentially more integrated.  I can use a BASH script to to powerful things in Linux that I can only dream of in Windows...with just a few lines of code.

An example: there have been a few times that I've experimented with software that froze my GUI (GNOME).  In Windows, there's only one solution: reboot.  But I had documents open!  So...you lose it all.  But in Linux, I've been able to switch over to a text mode terminal, log in, and issue a kill command to the offending software.  Then, switch back to my GUI, and all is well...without having to restart anything or losing data.

Anyway, I'm a Windows refugee, so I know how you feel.  But I have truly come to appreciate Linux.  And really, Ubuntu is one of the best, most stable, and fastest distros I've used.  And I've used several (let's see...Mandrake, SuSE, Mepis, Linspire, Kanotix, Xandros PE).

---

### Post by Corlian on 2005-09-04
I'm sold on Linux, and I have been since my first day with (K)ubuntu, for many reasons.  That's why I'm fighting so hard, and why it's so heartbreaking.

I just have to get it to perform basic functions, and I'll be set. ;)

I've have no problem in XP (but in no Windows before that) with killing errant programs without upsetting the system...but one thing that's so nice about Linux, often when one program has frozen, it's seperate enough from everything else that other programs still function, and the GUI still works, even though the one program is a little hosed.  That wouldn't happen in a million years in XP.

---

### Post by elempoimen on 2005-09-04
We're getting OT now, but...

I have no problem killing an offending program on XP, either--unless the GUI freezes.  If the GUI freezes, then you're out of luck and have to restart.  Ctrl-Shift-Esc doesn't work if your GUI is locked up.  In Linux, there are alternatives even if the GUI is in bad shape (which I had happen).

---

### Post by usergentoo on 2005-09-09
Im also having these problems in KDE and still no luck

---

### Post by Corlian on 2005-09-09
[QUOTE=usergentoo]Im also having these problems in KDE and still no luck[/QUOTE]

Yeah, I mean, I don't want to badger the point, but where else can we go to find out about this?  Is there any way to go farther up the Kubuntu food chain to find out if this is a bug, a user-specific problem, a problem with KDE but not Ubuntu, a problem that Macromedia has to fix, or whatever?  Is there anyone involved with the development that I can beg to set this straight?

I'm dying to make the move to full-time Kubuntu now, and I realize Flash is proprietary and a closed format, but until someone convinces the world to use something different, Flash is a very basic component of today's internet environment, and something I can't compromise on.  I'm eager and willing to do extra work to get it to function on my system, but at this point I'm at a loss, and either this thread is a lost corner of the forums, or the developers don't read it, or no one has bothered to check if Flash works in Kubuntu, and it's a little unsettling to me.  Even if someone who knows for sure told me, "Flash just doesn't work properly in KDE in any situation yet," I'd feel much better knowing where I stand.

I'm going to try to get Flash to work properly in KDE under SUSE and Mepis, and after that, I guess I have to scratch the whole thing for now.  Which I genuinely would be really sad and disappointed about.

---

### Post by Haiyadragon on 2005-09-13
The linux flash plugin sucks. It's slow and the video runs out of sync. Been that way forever and for everyone I ever talked to about this problem. My guess is it will only run good on a lot of horsepower, I'm talking dual 3.4 gigs or whatever.

The only thing that kinda worked for me was the standalone player. But I just gave up on flash.

---

### Post by joelito on 2005-09-13
I just tried flash in Breezy and it worked OK...

I used the flashplayer package from the repositories

---

### Post by kiddo on 2005-09-13
I sure hope that's fixed. However, there is no such package... Did you get that from a multiverse? Oh well anyways I'll have plenty of time to play with that when final comes out.

---

### Post by joelito on 2005-09-15
I can't remember but I think it was from either universe or multiverse...

look for a package named flashplayer-nonfree or flashplayer-mozilla, i recommend flashplayer-nonfree

---

### Post by rylando on 2005-09-16
I just found a simple fix that works for me, without having to install any other drivers or wrappers:
in the /etc/mozilla-firefox/mozilla-firefoxrc file, change
FIREFOX_DSP="auto"
to
FIREFOX_DSP=esd
that's all i had to do, flash sound stays in sync fine now.  for info, i'm using a kubuntu breezy installation with the macromedia plugin for firefox.  the "auto" setting was defaulting to artsdsp, but now that it's using esd instead of arts it seems to work.

---

### Post by Corlian on 2005-11-25
I haven't had internet at home since the end of September, so I wasn't able to play with Linux again until now.

I just installed fresh from a Kubuntu Breezy CD, updated with universe and multiverse, and installed flashplayer-mozilla and Firefox.  I had audio lag in Flash.

I changed FIREFOX_DSP to arts, and now I have Flash sound in sync, but with (minimal) clicks and pops.  It works the same way set to esd.

I guess this means I finally fixed my issue, but not perfectly, so I'll keep my fingers crossed for improvements in the future.

---

### Post by ajmacca on 2006-04-30
I realise this is a bit of a dead thread, but I have a suggestion.  I just encountered this problem myself, however I'm using Gentoo and an install of Firefox (version 1.5.0.2) straight from mozilla.com.  I'm also using alsa with all the OSS emulation options compiled in my kernel.  

Anyways, my video and audio was getting out of sync when I watched flash videos in firefox (e.g. homestarrunner.com and youtube.com).  I noticed when reinstalling the plugin from macromedia.com that the plugin files were stored in ~/.mozilla/plugins, which is not my firefox install directory.  By copying the plugins from this directory to my firefox install directory (in this case /usr/local/firefox/plugins) the problem was solved.  This is probably too late to be of use, but I thought I'd post on the off chance this worked for others.

---

### Post by vem0m on 2006-07-05
elempoimen's guide rather how-to seems to have worked for me :D

will let u all know if anything changes :)

---

### Post by siennalizard on 2006-09-10
If you want to use the aoss sink for every run of firefox, you can export that variable in your profile. Try putting this in your ~/.bashrc file:
```
export FIREFOX_DSP="aoss"
```

Then when you run firefox, it will always see that variable and use the right sink.

Hope this is handy. There's probably a nicer way (using /etc/firefoxrc?) but this works for me.
J.

---

### Post by ropers on 2006-10-03
I am also suffering from significant audio lag when watching Flash movies (e.g. youtube, Google video). In my case this may be aggravated by the fact that I "only" have a PIII 1000MHz machine.

Is there a recommended and/or supported solution now for Dapper 6.06 LTS? 

I tried setting FIREFOX_DSP="aoss" or FIREFOX_DSP="esd" in /etc/firefox/firefoxrc, but to no avail. The latter actually crashed Firefox at launch, which is pretty much what the words of wisdom in the /etc/firefox/firefoxrc file warned about. 

I would really love to get this to work in a way that doesn't make my machine or browser crash-prone. 

Do people have any solution?

---

### Post by andrea_c on 2006-10-06
Just my experience: I followed the instructions in this thread. I thought they didn't solve the problem because I simply closed firefox and restarted to check if the video was in sync. 

After I rebooted the computer, the video and audio were OK.

So, according to my experience, the instructions in this thread solve the problem but be aware that you should reboot the computer and not simply logout or restart firefox to check if they worked.

Thanks to everyone for those instructions!

---

### Post by ropers on 2006-10-06
Thanks for the reply andrea_c.

Could you detail precisely which instructions you followed? (Because there are several suggested solutions in this thread.)

Did you just set FIREFOX_DSP="aoss" in /etc/firefox/firefoxrc and reboot or did you do something else? Also, are you using Ubuntu "Dapper" 6.06 LTS and Firefox 1.5.0.7?

Thanks and regards,
--ropers

---

### Post by andrea_c on 2006-10-06
Hello Ropers!

I just did all the procedure once again to be sure to give you information at least tested twice. It works in my environment.

Yes, I'm using Ubuntu "Dapper" 6.06 LTS and Firefox 1.5.0.7 

I followed the procedure described by elempoimen in his post dated August 27th, 2005 post no.44 page 5 in this thread.

All correct in that post except one thing. In point 2 of instructions instead of writing sudo gedit /etc/mozilla-firefox/mozilla-firefoxrc you should write (and edit) sudo gedit /etc/firefox/firefoxrc

And remember to reboot to test and follow carefully the elempoimen's instructions. 

If all woked please comfirm it in this thread (it can be useful to others).

Good luck and thanks for your reading!

---

### Post by Ambimom on 2006-10-06
Yes, the audio is slightly out of sync but it's not a major issue for me...my biggest problem is that I prefer using Opera over Firefox and when Flash does work (java too) it works in Firefox and not Opera (though they share the same libraries for plugins).  

Don't get me started on the Flash version 7; though I understand that is about to be updated for Linux.

UPDATE:  Things are back in-sync.  I discovered inadvertently that I had included too many paths for plugin links in Opera.  All I needed were Opera and Firefox plugin paths (but for some reason Mozilla and Netscape were also there).  As soon as I removed them, things were relatively normal, including java, flash and the sync issues.

---

### Post by ropers on 2006-10-07
andrea_c: Thanks for your reply.

Sadly I'm unconvinced that worked. I'm still seeing lag in quite a few flash films (specifically Youtube/Google video). I'm not even sure if the lag problem really has improved since doing these changes. If there is anything else you did and that I should look at, I'd be curious to hear it, but other than that I'm close to giving up on this one -- probably all I can do is wait and see how things look with the next release of Ubuntu/Flash.

---

### Post by Cronjob on 2006-10-09
This has been something which has frustrated me for a long time. Things tend to be out of synch by a couple full seconds, at least. I would hope this is not going to be an issue when the official linux Flash player is released (though I'm not convinced a linux flash player is any more likely than Duke Nukem Forever).

---

### Post by ropers on 2006-10-09
I'm not sure what you mean by "the official linux Flash player". Adobe's player (version 7,0,68,0 ; cf. [http://www.adobe.com/shockwave/download/index.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/index.cgi?P1_Prod_Version=ShockwaveFlash) ) or the open source one ( [http://www.gnu.org/software/gnash/](http://www.gnu.org/software/gnash/) )?

---

### Post by Cronjob on 2006-10-09
> **ropers said:**
> I'm not sure what you mean by "the official linux Flash player". Adobe's player (version 7,0,68,0 ; cf. [http://www.adobe.com/shockwave/download/index.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/index.cgi?P1_Prod_Version=ShockwaveFlash) ) or the open source one ( [http://www.gnu.org/software/gnash/](http://www.gnu.org/software/gnash/) )?

[http://blogs.adobe.com/penguin.swf/](http://blogs.adobe.com/penguin.swf/)

By the way, note that their September 11th post suggests that the audio synch problems may not have anything to do with the flash player. So maybe this means we'll see the exact same problem when they release the up-to-date linux player (again, hopefully before DN3 ships).

[quote="Adbobe"]Audio/Video Synchronization: This is also something that the core Flash Player worries about, believe it or not. The notorious A/V sync problems with Player 7 on Linux were not a result of some fundamental inability of the Player to maintain sync.

. . .snip . . .

There are still plenty of fascinating problems involved in making the official Flash Player run well on Linux (Tinic writes of one we just discovered). The problems listed above are not among them.
[/quote]

---

### Post by ropers on 2006-10-09
Ah. Thanks! :)

---

### Post by lochnaes on 2006-10-10
Install ies4linux, it comes with flash 9 and runs thru wine.  I know it isn't the ideal solution, but if you enjoy homestar or youtube this will work until the problem gets fixed.  

Just follow the instructions here:
[http://www.tatanka.com.br/ies4linux/page/Installation:Ubuntu](http://www.tatanka.com.br/ies4linux/page/Installation:Ubuntu)

---

### Post by etherised on 2006-10-20
> **Cronjob said:**
> [http://blogs.adobe.com/penguin.swf/](http://blogs.adobe.com/penguin.swf/)

By the way, note that their September 11th post suggests that the audio synch problems may not have anything to do with the flash player. So maybe this means we'll see the exact same problem when they release the up-to-date linux player (again, hopefully before DN3 ships).

Cronjob,

excellent find!  i've been suffering the loss-of-sync in flash as well, and having tried all the various remedies, none of them worked for me--  until now.  the link you provided led to the [flash player 9 beta]("http://labs.adobe.com/downloads/flashplayer9.html"), which i downloaded and installed.  i'm happy to say, the problem is finally solved.

thanks to everyone else who posted helpful info also! :biggrin:

---

