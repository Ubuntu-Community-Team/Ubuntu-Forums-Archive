---
title: "Failed to connect bluetooth headset HDH DS-970"
date: 2007-01-05
forum: General Help
---

### Post by RikoW on 2007-01-05
Hi all,

I have the Sony HDH DS-970 bluetooth headset, which came with my mobile phone.
I tried to connect it to my laptop to listen to music without cable but so far failed.

I started kbluetoothd, which recognized the headset with the correct HW adress (same I get when using "hcitool scan". However, the icon shown in konquorer window is a DVD icon (type: audio/video bluetooth device)???
Anyway, I choose to ignore the wrong icon, click on it and expected to be asked for a pin (the headset being in pairing mode of course). Unfortunately, I only get a pop-up window, asking me:

[I]open sdp://hdh-ds970?
save as... open with ... cancel
[/I]

Open with pop up a new konqueror window, with a few icons for some services I guess found on the headset. But no matter which one I select, I always get something like:

[I]Open 'sdp://[00:11:b1:07...70&rfcommchannel=1'?
Type: Unknown Bluetooth Profile
[/I]

Any ideas, how to proceed on this?

Thanks,

            Riko

---

### Post by canard on 2007-01-07
hi,

you should try to look at these two pages:
[http://www.ubuntuforums.org/showthread.php?t=75978&highlight=bluetooth+headset](http://www.ubuntuforums.org/showthread.php?t=75978&highlight=bluetooth+headset)
[http://nicolas.delerue.org/en_tips.html](http://nicolas.delerue.org/en_tips.html)

i got a bt headset work under ubuntu edgy with it and i'm using it with no problems with openwengo....

good luck!

ps: you might also take a look here, as things can act little weird.....
[http://www.ubuntuforums.org/showthread.php?p=1982278#post1982278](http://www.ubuntuforums.org/showthread.php?p=1982278#post1982278)

---

### Post by RikoW on 2007-01-10
Hello again,

finally managed to get to play with the headset again. Seems like I'm only a step away!

> **canard said:**
> 

you should try to look at these two pages:
[http://www.ubuntuforums.org/showthread.php?t=75978&highlight=bluetooth+headset](http://www.ubuntuforums.org/showthread.php?t=75978&highlight=bluetooth+headset)
[http://nicolas.delerue.org/en_tips.html](http://nicolas.delerue.org/en_tips.html)

i got a bt headset work under ubuntu edgy with it and i'm using it with no problems with openwengo....
[http://www.ubuntuforums.org/showthread.php?p=1982278#post1982278](http://www.ubuntuforums.org/showthread.php?p=1982278#post1982278)

The second link let me connect to the BT headset, asking for a pin and everthing. The headset leaves the pairing mode and in the display I see it is bluetooth connected.
```

> sudo hcitool cc 00:11:B1:07:A6:19
> sudo btsco -v 00:11:B1:07:A6:19
btsco v0.4c
Device is 1:0
Voice setting: 0x0060
RFCOMM channel 2 connected
recieved AT+GCLIP=1
speaker volume: 14 mic volume: 1
i/o needed: connecting sco...
connected SCO channel
Done setting sco fd
recieved AT+VGS=14
Sending up speaker change 14
recieved AT+VGS=15
Sending up speaker change 15

```

The last "speaker" entries appear, when I change the volume on the headset. Under the System -> Preferences -> Sound tab, I have now in addition to the on-board sound card an entry for the "BT Headset". Selecting that turns off the sound through the speaker/cable headset, however, I don't hear anything on the BT headset :(
I played a bit with the rfcomm channel, but it seems "2" is the only one I can connect to.

Any more ideas, how to get sound out of this thing?

Thanks,

               Riko

---

