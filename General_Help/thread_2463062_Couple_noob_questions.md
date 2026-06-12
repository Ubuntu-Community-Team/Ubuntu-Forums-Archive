---
title: "Couple noob questions"
date: 2021-06-02
forum: General Help
---

### Post by Durandall on 2021-06-02
Just installed 20.10 on my plex "server" build - (ubuntu desktop, not server.  Just being clear.)  PC's primary function is to host media around the house.

Anyway it's working well, VERY well.  However!

A) how do I enable capslock on boot?

B) somewhat more troublesome... is there such a thing as a screensaver?

If I walk away from the "server" long enough - I'll come back to my monitor (4ktv) being inactive.   Like it displays that there is NO input.  I cant "wake" the pc.  I have to full on restart.

I've gone through my power settings... it shouldn't go into sleep mode no matter how long I'm away.  But it does.

Can't find any screensaver or any settings other than "turn off display after..." (and mine is set to never)

Mainly use windows, but really loving this recent build of Ubuntu.

---

### Post by TheFu on 2021-06-03
20.10 support ends in less than 2 months.  Should have stayed with 20.04 which is an LTS release 
or 
you move to 21.04 ASAP.  Not worth trying to address anything on 20.10 at this point.  Non-LTS releases basically have support until the next release 6 months later with a few months of overlap.  We are in the overlap period for 20.10 now.  Media servers usually should run only LTS if you want a happy spouse/family.  Also, using a raspberry pi v4 as a 4k media player connected to a TV will provide a capable, silent, playback device. Then the full PC can be left in a place where noise doesn't matter.  My plex server is barely touched, except over the network.  There are plex clients for the raspberry pi. I dislike the plex interface, so use OSMC to access any DLNA server on the network.  I've been playing with jellyfin, which is very plex-like, but without the proprietary code and without all the spyware included in Plex. The good news is that plex is 10,000x better than any of the media streaming devices like a roku. I love our roku, but wish it didn't want to transmit every remote and keyboard entry, plus samples of all media watched, back to the mothership - constantly.  The top traffic blocked is for the Roku, but Plex traffic holes the #4, 5, 6 places for the top blocked domains too.

The settings for keys is usually in the BIOS for the system. I know NUMLOCK is.
There are lots of different screensavers. Use whatever package manager you like and install one.

---

### Post by Durandall on 2021-06-04
I had a usb installer with 21.04 on it - it was giving me trouble so I dusted off my DVD folder, most recent build I had burned was 20.10.  I *thought* if I installed it I would be able to do a release upgrade.  I was mistaken.

I'll check the bios for the setting and search for screensavers.  Thank you.

---

### Post by CatKiller on 2021-06-04
> **Durandall said:**
> If I walk away from the "server" long enough - I'll come back to my monitor (4ktv) being inactive.   Like it displays that there is NO input.  I cant "wake" the pc.  I have to full on restart. 

That's not powersave behaviour - particularly since you said that you'd turned power saving off. That sounds like a hang. 

> **Durandall said:**
>  I *thought* if I installed it I would be able to do a release upgrade.  I was mistaken.
You should be able to upgrade from one interim release to the next. Do it before the one you're on goes EOL, though. 20.04 LTS would have been a better choice, as TheFu says.

---

### Post by Impavidus on 2021-06-04
> **Durandall said:**
> I *thought* if I installed it I would be able to do a release upgrade.  I was mistaken.

It looks like release upgrades from 20.10 to 21.04 were enabled yesterday or so. At least, that's when I first saw that upgrade offered.

---

### Post by ActionParsnip on 2021-06-04
[https://securitronlinux.com/bejiitaswrath/how-to-toggle-the-caps-lock-key-with-the-command-line-in-linux-mint/](https://securitronlinux.com/bejiitaswrath/how-to-toggle-the-caps-lock-key-with-the-command-line-in-linux-mint/)

You can add an entry to /etc/rc.local to run the command at boot

---

### Post by TheFu on 2021-06-04
> **ActionParsnip said:**
> [https://securitronlinux.com/bejiitaswrath/how-to-toggle-the-caps-lock-key-with-the-command-line-in-linux-mint/](https://securitronlinux.com/bejiitaswrath/how-to-toggle-the-caps-lock-key-with-the-command-line-in-linux-mint/)

You can add an entry to /etc/rc.local to run the command at boot

Is rc.local always enabled?  I've had to turn it on via systemctl so it would work.

For GUI stuff, rc.local happens well before anyone logs in, so there isn't an X/Session. No X/Session = GUI not there, so those commands won't work.  Not sure about keyboard stuff.
[https://help.ubuntu.com/community/NumLock](https://help.ubuntu.com/community/NumLock) has the GUI way for per-user login. Also has CAPSLOCK settings.

If we prefer a non-DE specific way, then xdotool can be used at login. 
To _toggle_ the CAPSLock key:
```
/usr/bin/xdotool  key Caps_Lock
```
Put that into a file, chmod +x the filename, then add that file to your autostart list.

I'm 100% positive that **/usr/bin/xdotool  key Num_Lock** works like Caps_Lock does.  xdotool can be used to automate almost anything we'd mouse or type.  For typing, it is the easiest, by far.  For mouse stuff, I think there are better options.

For a list of symbolic names for the different keys: [https://gitlab.com/cunidev/gestures/-/wikis/xdotool-list-of-key-codes](https://gitlab.com/cunidev/gestures/-/wikis/xdotool-list-of-key-codes)

---

