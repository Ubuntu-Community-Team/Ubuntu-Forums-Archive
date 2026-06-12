---
title: "[SOLVED] Logitech USB 250 Headset problems..."
date: 2007-09-30
forum: General Help
---

### Post by techknow on 2007-09-30
Hey guys,

I recently acquired a logitech usb 250 headset which I was hoping to use while gaming on Ubuntu, but I havn't been able to get the headset working properly.

After rooting around the forums for a while, I managed to get it to partially work, but only at full volume and with XMMS only, which is a bummer really, as I don't want to blow my ears out while listening to music.

I was wondering if any of you guys have had similar problems with this, and if you have any solutions.

Would really appreciate it

Cheers

-TechKnow

---

### Post by skip-br on 2007-09-30
Is your usb card being detected?
Do you have a onboard sound card enabled?

What does **cat /proc/asound/cards** output?

I'll tell you how I managed to get my usb card working, its a sennheiser PC155, it might work to you as well.

cat /proc/asound/cards outputs
```
 2 [Headset        ]: USB-Audio - Sennheiser USB Headset
                      Sennheiser Communications Sennheiser USB Headset at usb-0000:00:10.1-2, full sp
```
As my onboard sound is **disabled** in BIOS I only got one sound card.

Sound was fine, but the microphone wasn't working. Everytime I tried to record a sound I got an error about device #0 not found or not available (I dont remember the error exactly).

So I just edited the alsa-base file
```
sudo gedit /etc/modprobe.d/alsa-base
```
that line
```
options snd-usb-audio index=-2
```
to ```
options snd-usb-audio index=0
``` 

(* dont know if its necessary or not)
created a ~/.asoundrc file ```
sudo gedit ~/.asoundrc
```

with the content (I found it googling).
```
pcm.dmixed {
	type dmix
	ipc_key 1024
	slave {
	    pcm "hw:0,0"
	    period_time 0
	    period_size 1024
	    buffer_size 4096
	    rate 44100
	}
	bindings {
	    0 0
	    1 1
	}
   }
  
   #one called "dsnooped" for capturing
   pcm.dsnooped {
	type dsnoop
        ipc_key 5978293	# must be unique for all dmix plugins!!!!
        ipc_key_add_uid yes
        slave {
                pcm "hw:0,0"
		channels 2
		period_size 1024
		buffer_size 4096
		rate 44100
		periods 0 
		period_time 0
        }
        bindings {
                0 0
                0 1
        }
   }
  
   #and this is the real magic
   pcm.asymed {
       type asym
       playback.pcm "dmixed"
       capture.pcm "dsnooped"
   }
  
   #a quick plug plugin for above device to do the converting magic
   pcm.pasymed {
       type plug
       slave.pcm "asymed"
   }
  
   #a ctl device to keep xmms happy
   ctl.pasymed {
       type hw
       card 0
   }
  
   #for aoss:
   pcm.dsp0 {
       type plug
       slave.pcm "asymed"
   }
  
   ctl.mixer0 {
       type hw
       card 0
   }
```

After that, reboot.

After log in, go to System -> Preferences -> Sound
Set everything to  **USB Audio**

Then... System -> Preferences -> Multimedia System Selector
Choose Default Input/Output
Plugin: Alsa
Device: default or usb audio.

Now I got my audio output working (tested with xmms, VLC, Media Movie Player, youtube) and my input too (tested with Sound Record only).

If that doesn't work, just edit the alsa-base back to -2 and delete the ~/.asoundrc file.

---

### Post by techknow on 2007-09-30
Thanks, I ran through all that in my system and now its working.

I really appreciate i

Now for some FPS gaming :)

Cheers

---

### Post by shawnthecableguy on 2007-10-01
Is there any way to make the usb audio "plug and play" like windows?

I find it a pain to have to switch it in system pref's.

???????

---

### Post by poccino on 2007-10-03
HELP!

I followed your instructions and I hear VLC but  cannot hear Skype!

---

### Post by skip-br on 2007-10-04
> **poccino said:**
> HELP!

I followed your instructions and I hear VLC but  cannot hear Skype!

Since Im not a Skype user I can't be more specific, but if the sound is working with other applications that means you'll have to configure the skype program (some how) to use you sound card.

Does skype have any kind of sound setup?

---

### Post by poccino on 2007-10-05
Yes, and obviously i had set it up. Actually, it was working regularly.

---

### Post by skip-br on 2007-10-05
I just installed skype to see how it works and I was able to hear my own voice through that Option -> Sound Device -> Make a test call. And the **Make a test sound** works fine too.

Just uncheck the option **Allow Skype to automatically adjust my mixer levels** and click **Apply**
Then open the Menu System -> Preferences -> Sound and check if your sound device is selected, if not, select it again.
Next, open the System -> Preferences -> Multimedia System Selection and select you sound device again.

Go back and open the skype option again. Make both tests to check if your skype is working.
Note: I leave all options here under **Sound Devices** as **Default device (default)**

---

