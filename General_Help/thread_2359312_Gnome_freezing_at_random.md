---
title: "Gnome freezing at random?"
date: 2017-04-22
forum: General Help
---

### Post by Roasted on 2017-04-22
Hi friends. With the recent news of Ubuntu switching to Gnome, I decided to spin up 17.04 Ubuntu Gnome on several systems for sake of getting in on the changes early. I have three installations so far.

3rd gen Intel i5 Macbook Pro
4th gen Intel i5 Dell Latitude
2nd gen Intel i3 Desktop

The desktop acts as our home theatre PC in the living room.

I don't recall having any freezing on the Macbook, however I've had this happen on the Dell and the desktop multiple times. The mouse cursor remains active, but I cannot click on anything. Keyboard is unresponsive. Dropping to a TTY is not possible.

On a hunch I checked network connectivity via a second system and could see it was online. I SSH'd to it and ran killall -3 gnome-shell, as per the recommendation of someone on a bug report online. It gracefully restarted Gnome and I was back to working. Thing is, had I not been able to SSH to it, I would have had to do a force restart.

Unfortunately the desktop installation is not even 24 hours old. It's been in use maybe 4 hours so far, and it's locked up twice.

I looked around online and was quite alarmed at the magnitude of bug reports and user discussion regarding this topic. BSD, Mint, Ubuntu, Fedora, Red Hat, Debian, across a whole array of Gnome versions (3.2 on up to present), and still this appears to be an issue.

Has anybody seen this? Is there anything a user can do besides force-restarting a system, in some cases, multiple times a day?

Thanks for any and all insight!

UPDATE/EDIT:
I may have spoken a bit soon. The Macbook and Dell have not exhibited any lockups following updates. It's hard to say when that took place as I grab updates constantly when they are available, but it's been at least a few days (close to a week almost?) since then. The desktop on the other hand I realized something. The system itself was not locking up, but what I was seeing on the screen was locking up. I had a video up on fullscreen and could hear the audio. With the keyboard command to kill the player, I heard the audio stop, but the visuals remained locked with the video on fullscreen at a static image from that video. On the desktop (again the desktop is my HTPC) this happened twice in a short amount of time. Over SSH I took snipets of syslog each time and began to look for common traits from the syslog and found this:

/usr/lib/gdm3/gdm-x-session[924]: (WW) NOUVEAU(0): flip queue failed: Device or resource busy

Oddly, I forgot I even had an Nvidia chip in this HTPC. It's an older GPU, Nvidia GT440, but I now remember installing it when my HTPC was on 16.04 with Unity. Nvidia with proprietary drivers was faster than Nouveau when using Ubuntu Unity with everything scaled up. To Gnome's credit, Gnome was much faster with Nouveau when scaled up to the point I didn't even realize I wasn't using the proprietary driver. I installed the proprietary driver and so far I have yet to exhibit a lockup using the HTPC. The day before it locked up a total of 3 times within a 1-2 hour time frame. Since adding the proprietary driver it's ran for half a day without issues. Perhaps that was the issue, in conjunction with regular system updates to the other two systems.

Time will tell, but so far it's hard to shake a finger at working systems. Seems better so far.

---

