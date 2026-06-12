---
title: "Palm TX (usb) issues"
date: 2007-05-30
forum: General Help
---

### Post by bmeyer on 2007-05-30
I've searched the forums extensively and haven't come across anything to fix this, so any help is appreciated!  I have a Palm TX connected through USB.  I followed the Palm Setup instructions, including adding to /etc/udev/rules.d/10-custom.rules and adding the visor module.  jpilot sync works only once per restart.  When I push the sync button any more times after the first, the Palm is not recognized.

I have NEVER gotten gnome-pilot to recognize it.

Any ideas?

Also, this may be an extreme newbie question, but how do I go about installing applications on the palm or uploading media to the SD card through jpilot?  I can't seem to figure it out.

---

### Post by Pdennis on 2007-05-31
I just got my TX today, and I'm in the exact same boat...
I'll report back if I figure anything out, but until then I'm  interested to see what people have to say.

---

### Post by niteshifter on 2007-06-01
I spent a lot of time on this same problem. I did finally get Edgy and gnome-pilot to Hotsync via USB working ...

By any chance are you connecting the TX to an external USB hub? If so, try connecting the TX directly to a USB port of your PC - that was the final fix for me.

I have this content in etc/udev/rules.d/10-custom.rules

```
BUS="usb", SYSFS{product}="Palm Handheld*", KERNEL="ttyUSB*", NAME{ignore_remove}="pilot", MODE="666"

```

and this content in ~/.gnome2/gnome-pilot.d/backup.conduit (reference: [https://wiki.ubuntu.com/PDADeviceList](https://wiki.ubuntu.com/PDADeviceList))

```

[Pilot_25947]
backup_dir=/home/dlk/MyPDA
updated_only=true
remove_deleted=false
no_of_backups=0
**exclude_files=WiFiCoreLib**

```

... but it never worked via USB until a I quit connecting via an external hub.

HTH

---

### Post by azdragon on 2007-06-04
I have a Palm TX and I never have any of these issues.   Here is the simple solution.   Set up your PDA to sync over the network and simply have it connect to your computer over your wireless router.   I even connect to my PC at my work to sync over the internet when I travel.   It works great every time, and with no issues.

Now all I need is a good PIM for linux.

---

### Post by defishguy on 2007-06-04
I have a TX working swimmingly too.  Try removing the custom rule and add visor to the /etc/modules file.  

Stop the gpilot daemon and remove the icon from the panel.

 After that I would remove /home/yourusername/.gnome2/gnome-pilot.d and I would remove /home/yourusername/.gpilotd  you can just rename the folders if you don't want to remove them.  

Plug in your TX via the usb cable.

Add the Pilot applet again to the panel.

Follow the wizard just like you normally would.

This setup works for me perfectly with multiple syncs per session if need be.

Good luck and let me know if this helps!

---

### Post by azdragon on 2007-06-06
Well I only have it syncing correctly.  I have checked and all of the data is in my home directory in a sub called MyPDA.    So at least that works.   My problem is now that I have this data here none of the programs seem to look there and I still don't have any way to view/edit my PDA data on my ubuntu box.   

Can anyone tell me what to do once the data is on my hard drive.    I don't care at all about email, I use web based email.

---

### Post by le_jawa on 2007-06-11
Azdragon,

What "data" are you trying to read specifically?  Depending on what you want, Evolution may still be the best GTK-based tool.


And of course, if no one else has said it, welcome to Ubuntu forums!  :-)

Jason

---

### Post by azdragon on 2007-06-11
Well I have contacts, memos and calandar items.  Mostly I only care about my contacts, I have over 5000 of them I have built up over 8 years, 5 palms and 4 computers.   I use this HOURS per day and doing it on my PDA is much slower.   

I sync over the network, I no longer have the cable and been using networks syncs for over a year with no problems.    I have noticed that when I sync using Gpilot all of my data, even my programs, are stored in /home/jason/MyPDA     I just need some program that can access and use this data.   I also heard that some older programs can duplicate or trunicate your data, so I don't want that.

Thanks in advance for any help you may have.

---

### Post by le_jawa on 2007-06-12
Jason,

I've got good news and bad news.  The good news is, Evolution will do all those with out any additional configuration.  The bad news is, Evolution will do all those with out any additional configuration.  Basically, it's all a matter of your point of view.  If you like (or even don't mind) using Evolution for Calendar, Memo and Contacts, it will do all those seamlessly; it's integrated with gpilotd (since they are both part of GNOME) so you don't have to tell it about /home/jason/MyPDA.  It already knows.  (You may also notice that any tasks you have will show up in your GNOME calendar.)   However, I do understand if you don't want to use something that is usually viewed as an email client as your PIM.  It's a little weird feeling, but it actually does work very well.  Evolution turns out to be a very good PIM.  If it helps you, you can start Evolution in Calendar view; just change the command in your Evolution launcher to say [FONT=Courier New]evolution --component=calendar[/FONT] (It should be [FONT=Courier New]evolution --component=mail [FONT=Tahoma]by default.)[/FONT][/FONT].  That may make things more useful for you.

As for other alternatives, you could use KPIM or other KDE-based solutions, but then you need to shutoff gpilotd and use their KDE Palm Pilot daemon(s).

I don't know if that's what you were hoping for or not, but I do hope it helps.  Let us know if you need further info or if this just didn't quite answer your question.

Good luck and enjoy!

Jason

PS -- If you're not already familiar with Evolution, it's the Linux equivalent to Outlook; it has all the same core features.

---

### Post by azdragon on 2007-06-12
Thanks, you are correct, they are there.   They were not there last time I checked so that is very odd.   I have noticed two things.   It did not import my catagories, that is bad as I have everything sorted.   Second I use the MEMO field alot, I keep notes on my contacts, but in evolution is is only like 15 pixels tall and displays only one line.    Do you know of other PIM software that may do a better job other than the KDE version because the KDE one does not support hotsync over a network.   Why has PALM not made a linux version?

I never used outlook either, I was always a Eudora person.

---

### Post by le_jawa on 2007-06-12
> Thanks, you are correct, they are there.   They were not there last time I checked so that is very odd.   I have noticed two things.   It did not import my catagories, that is bad as I have everything sorted.   Second I use the MEMO field alot, I keep notes on my contacts, but in evolution is is only like 15 pixels tall and displays only one line.Hmmm... The best avenue I can think of is to contact the Evolution team via their bug database or a feature request email and let them know of those limitations.  That is kind of nasty and I suspect those things could be resolved in a version or two.  I know that doesn't help you now, but it could be a good long-term solution.   You may also find a workaround in the process from someone who knows more about it than I.


> Do you know of other PIM software that may do a better job other than the KDE version because the KDE one does not support hotsync over a network.   There is J-Pilot; Ubuntu has packages in Universe.  It will solve your category issue, and probably your memo problem too, but I'm not sure about network sync.  I'd have to look  more into the pilot-sync daemon it relies on to be sure.  It's definitely worth your time to look into.

I also took a peek at running Palm Desktop through wine.  Don't bother.  In the end, the desktop itself doesn't work, which defeats the whole purpose.

> Why has PALM not made a linux version?I'd love to know the answer to that one myself.  ;)  About a year or so ago, they started talking a lot about a "renewed commitment to Linux" or some such.  My impression from all the puffing and dancing was that they intended to use the Linux kernel, not actually support Linux as a desktop OS for syncing.   Now they've released a new laptop-like device named Foleo, and I'm willing to bet it's Linux under the hood.  In any case, I don't see a Linux Palm Desktop coming in the future, near or otherwise.

> I never used outlook either, I was always a Eudora person.Good man.  :) Eudora's a nice application.  Hopefully, you can get Evolution to meet your needs on Linux, or get J-Pilot to do it.   In my experience, PDA support has been a sore spot for Linux for a long time.  GNOME 2.18 and Evolution 2.10 have fixed a lot, but it still has a ways to go.  Hopefully upcoming releases will finally smooth things out.

Unfortunately, that's about all I can give you.  Maybe others who have dug more into this can offer more.  If you learn more yourself, please share it with the community here; I'm sure others would benefit from your learning.

If you give J-Pilot a try and need help, I or others here can certainly be of assistance.

Best of luck,

Jason

---

### Post by eustace on 2007-06-15
> **bmeyer said:**
> I've searched the forums extensively and haven't come across anything to fix this, so any help is appreciated!  I have a Palm TX connected through USB.  I followed the Palm Setup instructions, including adding to /etc/udev/rules.d/10-custom.rules and adding the visor module.

I just solved this problem for myself. It appears, none of the above steps are actually necessary. There are only two things to do: 

1. Add the "Pilot Applet" to the panel.
2. Set the device to "usb:" in the applet's configuration dialog. 

That's it. From there it should already work. 

Now, before I discovered this, I also looked desperately for a working configuration, and found a few, which usually involved messing with udev rules and enabling visor module. All for the sake of supporting the old /dev/ttyUSB* or /dev/pilot way of communicating with Palm. It even forced me to blacklist ehci_hcd module, which was a stupid thing to do. I think I actually broke more than fixed with it. 

After rolling my changes back and simply using 'usb:' as the Palm device the syncing worked wonderfully.

---

