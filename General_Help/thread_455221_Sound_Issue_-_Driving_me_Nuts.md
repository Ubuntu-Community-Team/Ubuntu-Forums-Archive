---
title: "Sound Issue - Driving me Nuts"
date: 2007-05-26
forum: General Help
---

### Post by brharri1 on 2007-05-26
I have scoured these forums for a problem similar to the one I'm having but have not found anything similar. My sound will work fine, but then stop working after a while (usually an hour or so of not using any sound). My speakers make a "pop" noise and the sound is gone. When I reboot, the sound works again.

I have tried sudo /etc/init.d/alsa-utils restart to no avail, I have made sure that pcm is not muted in alsamixer. I think this is the info for my sound card:

*-multimedia
             description: Multimedia audio controller
             product: VT8233/A/8235/8237 AC97 Audio Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.5
             bus info: pci@00:11.5
             version: 60
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: driver=VIA 82xx Audio latency=0
             resources: ioport:eb00-ebff irq:20

I wonder if something is wrong with my sound card. While it usually takes a hour or so for the sound to cut off, it only took 4-5 minutes on my last reboot. 

If anyone can offer any insight I would greatly appreciate it.

-Brian

---

### Post by misfitpierce on 2007-05-26
sudo aptitude (or apt-get) install alsa-base alsa-utils
sudo alsaconf

Perhaps try that... not sure if it works but you could try installing and tinkering with aslaconf and see if you cant get it workin?

---

### Post by dbott67 on 2007-05-26
After upgrading through Edgy & Feisty, I noticed that I was having some weird sound problems:

1. At the GDM login screen I would hear the "drum roll" sound.
2. After logging in, I would not hear the **startup.wav** file, although I could hear it if I played it in "Beep" or other music program.
3. In **SYSTEM > PREFERENCES > SOUND > SOUND tab**, the sounds would **not** play.
4. In **SYSTEM > PREFERENCES > SOUND > DEVICES tab**, the **TEST SOUND** worked.
5. Most applications with sound worked (Beep, Totem, Flash video, etc.)
6. No sound in the games "Cube" or "Sauerbraten".
7. All applications worked previously.

After fiddling with the sound settings trying various suggestions in the [Comprehensive Sound Problem Solutions Guide]("http://ubuntuforums.org/showthread.php?t=205449") thread, I totally buggered up my sound.  Oh well, a fresh install of Feisty never hurt anyone and I had my **/home** directory on a separate partition.

After the new install, I still had the 6 symptoms described above.

Thinking that it might be some sort of **.config** file remnant, I created a new user and everythng worked properly. A-HA! Comparing the user home directories, I noticed the presence of a **.asoundrc** file and another similarly named file.  After doing some research here about [what the file is for]("http://www.alsa-project.org/alsa-doc/doc-php/asoundrc.php") (and it's safe removal), I deleted it, logged out and returned to a system with full working sound.

My suggestion is this:

1. Create a new user account
2. Login using new user account
3. Check to see if sound works properly
4. If it does, then the issue is likely some sort of config file. Look for the .asoundrc file in your original home directory and move it to a backup folder (just in case)
5. Log back in as your original user and test.
6. If it fails to cure the problem, try the Comprehensive Guide above.

-Dave

---

### Post by brharri1 on 2007-05-26
Wow, thanks for the quick responses.

Misfitpierce, my alsa-base and alsa-utils are already at the newest version. When I typed in sudo alsaconf, it said "command not found." I have fiddled a lot in alsamixer but nothing works in there.

Dave, I forgot to mention that I had come across a post of yours in another thread and that I have tried removing the asoundrc file, but it did not change anything. I just tried creating a new user and logging into that account, but the sound did not work. Regarding the SYSTEM > PREFERENCES > SOUND > SOUND tab and devices tab, When I first boot my computer, the test sound buttons work. However, after the "pop" occurs and I have lost sound, they don't return any errors, just no sound. 

Does anyone have any other suggestions?

Thanks again,

-Brian

---

### Post by brharri1 on 2007-05-26
I read through the [Comprehensive Sound Problem Solutions Guide]("http://ubuntuforums.org/showthread.php?t=205449") and tried "aplay -l" and the output was:

**** List of PLAYBACK Hardware Devices ****
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 3/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


"lspci -v" gives the output that I posted in the original post.

I went to [http://www.alsa-project.org/alsa-doc/]("http://www.alsa-project.org/alsa-doc/") and saw that my card is supported by alsa, it is in fact the same one used by the writer of the guide. 

I tried "sudo modprobe snd-via82xx" - there was no output and nothing changed. I appened snd-via82xx to my /etc/modules, but it did not change anything after a reboot (that is, my sound dropped off after 5 minutes). 

I tried "sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils"
and then "sudo apt-get install linux-sound-base alsa-base alsa-utils" (I also had to install ubuntu-minimal and gdm which were automatically removed.)

Reboot, sound works, popped off after 5 minutes.

I am completely at a loss here. 

-Brian

---

### Post by dbott67 on 2007-05-26
Hi Brian,

I'm at a loss, too.  Sound troubles for me are a black art.  

The fact that the trouble happens regularly (but not quite predictably) leads me to believe that it's software related.  You may want to try checking your log files (I don't know for what, though).

You may also want to try a different sound card if you have one handy.

-Dave

---

### Post by brharri1 on 2007-05-27
I MAY have found a culprit. I would tend to agree with you that this is a software issue. So I decided to install a fresh copy of ubuntu on another partition, since my current install was an upgrade from edgy and might have had some unwanted junk on there. And I also figured, what the heck, I'll try a 64bit install too since I've heard that's improving a lot. Well, it was working fine on the fresh install for a while (a few hours, better than the 5 minutes I was getting). But it popped off again. And it wasn't too long after I installed vmware server through automatix (I know I know, smash automatix all you want, but I had vmware server installed manually on my last install). I just uninstalled vmware server, and we'll see how long I go before (if) it pops off again. 

I hope this fixes it, but that will also leave me wondering about my virtualization solution.

-Brian

EDIT: and I really wish I did have another sound card handy as that would make this diagnosis much easier. Thanks again for the help.

---

### Post by brharri1 on 2007-05-27
Scratch that. One hour after removing vmware, the sound cuts off again. Does anyone know what log file might offer any insight? I have browsed through /var/log but I don't have the first clue where to go from there.

EDIT: In /var/log/syslog here is the last hour's worth:

May 27 09:05:28 brian-desktop64 -- MARK --
May 27 09:11:35 brian-desktop64 kernel: [ 5207.344200] python[6240]: segfault at 0000000000000009 rip 00002b76a0ac5f2b rsp 00007fff0de20e90 error 4
May 27 09:17:01 brian-desktop64 /USR/SBIN/CRON[8524]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May 27 09:17:29 brian-desktop64 gconfd (root-8549): starting (version 2.18.0.1), pid 8549 user 'root'
May 27 09:17:29 brian-desktop64 gconfd (root-8549): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
May 27 09:17:29 brian-desktop64 gconfd (root-8549): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
May 27 09:17:29 brian-desktop64 gconfd (root-8549): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
May 27 09:17:29 brian-desktop64 gconfd (root-8549): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
May 27 09:17:29 brian-desktop64 gconfd (root-8549): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
May 27 09:17:59 brian-desktop64 gconfd (root-8549): SIGHUP received, reloading all databases
May 27 09:17:59 brian-desktop64 gconfd (root-8549): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
May 27 09:17:59 brian-desktop64 gconfd (root-8549): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
May 27 09:17:59 brian-desktop64 gconfd (root-8549): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
May 27 09:17:59 brian-desktop64 gconfd (root-8549): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
May 27 09:17:59 brian-desktop64 gconfd (root-8549): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
May 27 09:17:59 brian-desktop64 gconfd (root-8549): GConf server is not in use, shutting down.
May 27 09:17:59 brian-desktop64 gconfd (root-8549): Exiting
May 27 09:40:13 brian-desktop64 kernel: [ 6923.392545] python[9199]: segfault at 000000000000024d rip 00002b0360bdbfe3 rsp 00007fff4dd16db0 error 4

I immediately thought maybe the last line was a reflection of what happened, but its almost the same as the first line, at which point the sound was still working. And I don't know if GConf could have anything to do with it either.

---

### Post by brharri1 on 2007-05-27
I thought it might be a gconf issue, so I fiddled around with that for a while (not sure exactly what I did), but apparently I did not fix anything. My sound cut off again, and I checked the logs and there is no entry at all for that time in 

auth.log
daemon.log
debug
kern.log
messages
syslog
user.log
Xorg.0.log

all in the /var/log directory.

This must be a configuration issue as it has been working better than in my 32 bit install, but something is causing it to shut off.

---

### Post by TLM on 2007-06-03
While I am having different sound issues, I have seen something similar before, usually when I heard that pop sound and no more sound from the computer it was a threshold issue where the volume was below some sort of threshold, I would turn up the volume and it would come back. Why it did that I do not know but that was how I always solved it.

---

### Post by bunker on 2007-06-03
The VIA 82xx chipset has a heap of problems with alsa.  It's designed for 4 channel output so it has 4 sub devices instead of one; you're supposed to use the second on my 8235 chipset.  Run 
```
$ aplay -D hw:0,1 testfile.wav
```
and see if it solves your problem.  In this case, write the file /etc/asound.conf:
```

pcm.!default {
  type hw
  card 0
  device 1
}

ctl.!default {
  type hw
  card 0
}

```

This instructs things using alsa to use device 0,1 instead of 0,0.  You might want to try other sub-devices with aplay too (and edit the /etc/asound.conf as appropriate).

You'll probably need to play with it a fair bit more.  I vaguely remember there being some settings you need to use OSS emulation and the software mixer to allow multiple programs to use the sound card at the same time.  Look at alsa's wiki (the link in the 'Comprehensive Sound Problem Solutions Guide' is out of date by the way - [http://alsa.opensrc.org/](http://alsa.opensrc.org/) is what you need).

It's kind of surprising that Ubuntu doesn't configure all this for you really as most of the fixes are pretty formulaic per sound card.

---

### Post by kyphi on 2007-06-03
The problem described originally by Brharri1 seems like a capacitor failure to me.

As you may know, a capacitor smoothes electrical current flow.  It does this by storing electrical energy up to its specified level and then releasing it.  A disrupted capacity to store energy results in 'pops and clicks' and eventual total failure of the capacitor as well as other components in its feed chain.

If there is a separate sound card then a replacement should fix this problem.

If it is a chip in the motherboard then it means a new motherboard.

This may be a problem that the command line cannot fix.

---

### Post by brharri1 on 2007-06-03
Thanks for the info. I was finally able to get my hands on another set of speakers, and the problem hasn't occurred since. On the one hand, its nice to have such an easy fix. On the other hand, I spent so much time looking for a fix! 

Thanks to all who helped.

---

### Post by A. J. Rimmer on 2007-08-01
I know this doesn't exactly pertain to the original poster's problem, but I just wanted to say that the fix posted by dbott67 worked for me.

I recently upgraded from Dapper to Edgy and then Immediately to Feisty, and all sound worked fine except for login and logout "music."

I applied dbott67's fix and now I have the login and logout sounds.

---

### Post by speirint on 2007-08-16
I believe I have a similar problem as well, though I'm not sure:  My sound will work temporarily once in a while-it sometimes won't work at all from the gdm all the way through.  Rebooting doesn't change much either.  I've looked through at least eight threads and the most common problems seem mentioning an error in the alsa or kernal* (I'm an absolute beginner) that require the user to either purge and reinstall alsa, or kill a specific line of code.  I've tried purging already to no avail, and my understanding of terminal is not yet enough to try killing the suggested lines of code (putting kill in front of /usr/... doesn't work)-I'll post them here so that you may be able to give it a shot.

I also upgraded from edgy (where sound and everything was working fine) to feisty and I've been fighting with my distro ever since.

Edit: never mind, I see the problem has been solved.

---

