---
title: "Keyboard layout - it keeps reverting to the wrong settings!"
date: 2008-06-18
forum: General Help
---

### Post by Harvs on 2008-06-18
Hi

Each time I boot, the keyboard layout reverts to getting #@ and " the wrong way around.

To fix it, I go System, Preferences, Keyboard and set the layout to one of the Generic settings which works fine.

All is well until I re-boot and find that the @# and " keys are the wrong way around again. (Even though the keyboard layout setting remains the same.)

Any ideas how to fix it permanently?
Thanks

---

### Post by Silpheed2K on 2008-06-18
Try what I tried in this thread:
[http://ubuntuforums.org/showthread.php?t=832411](http://ubuntuforums.org/showthread.php?t=832411)
Nobody was able to help me so see if that tool can fix it.
just type xkeycaps in the terminal after installing it to execute it.

---

### Post by Harvs on 2008-06-24
Thanks Silpheed2K

That programme looks like it should fix it. I've put in the details of what I want, and the keyboard on the screen is what I expect.

It says I need to add something to my start up script - do you know what this file is, or how to create a new script and make it run at start up??

Cheers
Harvs

---

### Post by pgdave on 2008-06-25
I have the same problem after an update a while back. After the update, the keyboard keeps reverting to a US-style keyboard (Upper case '2' is an 'at'; sign, rather than the expected double quotes).  I chose UK at installation 2 years ago, and it's been fine until the update. After a restart, I have to select a different keyboard, then revert to mine (Microsoft Internet keyboard). Although I have deleted the US keyboard, the system reverts to US, 104 key. Sometimes the '104 key keyboard' actually appears as the device set up when you select 'system->preferences->keyboard', although usually 'Microsoft Internet keyboard' appears. I cannot set the UK keyboard to be the default (the default radio button cannot be set, even if it is the only keyboard in the list.). 

I assume that the properly set keyboard should be in some sort of config file?

EDIT: This was due to monitor/graphics driver problems. When using the recovery kernel at startup, and fixing X11, the /etc/X11/xorg.conf file is overwritten to defaults, which include US keyboard. The Gnome keyboard setting program doesn't update this file (bug - it should do so!), so Ubuntu reverts to US 104-key keyboard next boot. Edit your xorg.conf file to have the following, or similar:

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

(this example for my UK 105 key keyboard).

---

### Post by Harvs on 2008-06-30
Thanks Dave

My xorg was set to "uk", but I changed it to gb so the the settings were exactly like yours, and re-booted. But it still doesn't work.

It's getting frustrating now. Especially as I can't get the pound sign which I use a lot!!!!

I don't mind fiddling about with settings / the terminal etc to get stuff working in the first place. But when something's been working fine for ages and then suddenly stops working, and there's not quick fix for it, I get pretty annoyed.....!

Anyway, I'll keep looking out for a fix....
Harvs

---

### Post by Silpheed2K on 2008-07-02
> **Harvs said:**
> Thanks Dave

My xorg was set to "uk", but I changed it to gb so the the settings were exactly like yours, and re-booted. But it still doesn't work.

It's getting frustrating now. Especially as I can't get the pound sign which I use a lot!!!!

I don't mind fiddling about with settings / the terminal etc to get stuff working in the first place. But when something's been working fine for ages and then suddenly stops working, and there's not quick fix for it, I get pretty annoyed.....!

Anyway, I'll keep looking out for a fix....
Harvs

It should automatically add the file when you hit write output like i mentioned in that post... do that and you're done.. you can manually program the keys in the right positions but I at least recommend trying one of the preset layouts in it before programming everything in manually.

---

### Post by Harvs on 2008-07-14
Ah, it's worked!

Fantastic - many thanks. Will enjoy using £, " and @ now that I can type them properly!

---

