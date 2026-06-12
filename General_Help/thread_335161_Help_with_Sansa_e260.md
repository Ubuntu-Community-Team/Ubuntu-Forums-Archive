---
title: "Help with Sansa e260"
date: 2007-01-09
forum: General Help
---

### Post by DeathOnJuice on 2007-01-09
I just got a brand new Sansa today, and it seems to be a very solid player. However, I'm having a bit of Linux trouble. The first thing I did was turn it to MSC mode and deleted some of the preloaded songs in Ubuntu, then disconnected it by right-clicking the icon on the desktop and selecting eject. After this, it still said "Connected" and had some arrows moving on the screen, but I unplugged it regularly and it restarted and worked. How can I fix this disconnecting problem? I tried this advice:

Open a terminal window. Type sync. Wait for it to finish. This command flushes the file buffers so your player has everything written to it. Then right click on the icon and select "Eject" this unmounts the player, but it will still say Connected. Finally, back in the terminal I type "sudo eject /dev/sg0" You may need to use a different device. This actually ejects the USB device and your player will now say Disconnected.
Instead of sg0 (which didn't work), I tried sdb1 which the command "mount" told me was associated with the Sansa, but it said something about it not being a valid device.

Anyway,  I charged the player on the USB port on my Wii for a while, then connected it to my Ubuntu box again.

Then, I loaded on some songs and disconnected it the same way. I noticed that two of the songs on one album were listed twice. I cleared the album from the player, but it was still there with each of those songs listed once. What's up with that?

Finally, if I turn the volume down to minimum on the player (mute it), then put it one up, it remains muted until I move it up and back down again. Also, it the volume is at this problem setting when the song changed but it's not muted, it will become muted again. This isn't a big deal, but does anyone know how to fix it?

Thanks so much!

---

### Post by DeathOnJuice on 2007-01-10
Anyone?

---

### Post by SZF2001 on 2007-01-11
For one thing, about the "mute" problem, seems like an older version of Firmware if you ask me. Maybe you should get the latest Firmware?

And about the ejecting thing - I've had my Sansa for about a month now, every time I go through the procedure of disconnecting from the computer I do this:

Go to the Desktop, right click, unmount/eject (I say unmount because I'm still in Breezy).

Yes, it still says Connected, but I unplug it anyway. If the icon on the desktop is gone, then you usually are good to go.

Just make sure you have other programs that could be using it off, like Rhythmbox, XMMS, Opera (any bittorrenting stuff), etc - before trying to unmount.

I also wrote a big 'ol guide [here](http://www.ubuntuforums.org/showthread.php?t=312196&highlight=sansa). I know it doesn't answer *every* question, but it covers the basics in installing firmware and stuff.

---

### Post by DeathOnJuice on 2007-01-11
Thanks; I have actually been keeping an eye on that great thread, and I posted in there. I contacted Sandisk support and they were great (as competent and friendly as any other tech support I've come across) and they may e-mail me the firmware directly. If not, where on the ABI forums can I find the latest?

---

### Post by Zwack on 2007-01-12
The "eject /dev/sgX" part only seems to work on the Rhapsody players (e2X0R).  Sorry about that.  I've been assuming that they were the same until I hear otherwise.

Removing the database (/system/data/*) and letting it rebuild it might resolve the double album problem. but I don't know for sure.

It certainly shouldn't harm your player.

Z.

---

### Post by agustin.g on 2007-01-23
just removed all the files in the /system/data folder, gave the unit some time to "refresh database", but most of the songs are missing... i'm going to try contacting customer service to see if there's anything i can do. In the meantime I wouldn't really reccomend it.

---

### Post by LukeDJedi on 2007-03-07
I have an e280 Rhapsody and it doesn't seem to have the USB Mode in the Settings menu.  Any suggestions?

---

