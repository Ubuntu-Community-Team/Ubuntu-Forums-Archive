---
title: "Thunderbird lock ups with Hardy"
date: 2008-05-12
forum: General Help
---

### Post by sebbouckaert on 2008-05-12
Hello,

Does anyone have the same issue as I have with Thunderbird 2.0.0.14 crashing/locking up randomly in Hardy?

Never had any problems with TB in Gutsy before. 

I happen to manage multiple mailboxes with TB:

- my regular ISP pop mailbox,
- 2 Gmail accounts (I activated the POP settings in Gmail to send mail to TB)
-1 Hotmail account, for which I use 2 add-ons: WebMail 1.3.2 and WebMail and Hotmail 1.2.15. 

I wonder if these two last add-ons could be causing those crashes?

Most lockups occur after TB has been open for some time, and generally when new messages are coming in (doesn't matter from what account). 

When that happens a notification window appears on the bottom right of my Desktop (BTW, is this a Gnome thing or a TB thing?) after which TB freezes, blackens out, and has to be forced to shut down.

When I leave TB open for several hours, 9 out of 10 TB has crashed. 

I have already reinstalled TB, created a new profile, but I did copy my mail and my account settings (prefs.js) back to the new profile folder, but but all to no avail. :(

Any suggestions?

---

### Post by songshu on 2008-05-12
i had this once..

not 100% sure anymore but i think it was the sound when a new message arrived that borked my system (i was messing with the sound card at the time)

try to see if turning the notification messages and sound under preferences off helps.

---

### Post by sebbouckaert on 2008-05-15
Disabled the notification sound in TB, and this indeed seems to have fixed it. :-)

---

### Post by mickcalcara on 2008-07-07
So the fix is not have notification sounds? I have the same problem with Hardy ( never with Gutsy ). I have noticed Thunderbird locking with the notification sound and while I am playing music. Audacious is what I use for my streaming music.

---

### Post by sebbouckaert on 2008-07-08
Maybe this has something to do with Hardy's Pulseaudio? Dunno?

---

### Post by starcannon on 2008-07-08
Try some different settings in System-Preferences-Sound, be sure to take a screenshot of your original settings, it'll make restoring defaults easier later.

GL

---

### Post by sgleo87 on 2008-09-28
I can confirm that the crashing stops when turning off the sound notification. Is there any solution for this problem yet??? (so I can use the sound notification again)

---

### Post by sgleo87 on 2008-09-28
I can confirm that the crashing stops when turning off the sound notification (both the standard and custom sound leads to a random crash). This has only been happening recently to me (maybe a week) so I am guessing it was caused by a recent release of Thunderbird or an Extension (currently using Provider, Lightning, WebMail, Webmail - Yahoo). Is there any solution for this problem yet??? (so I can use the sound notification again)

---

