---
title: "March Madness on demand MMOD not working"
date: 2008-03-21
forum: General Help
---

### Post by oddworld on 2008-03-21
March madness on demand (MMOD) is not working in ubuntu.
The site is:  [http://www.ncaasports.com/mmod/welcome](http://www.ncaasports.com/mmod/welcome)
It says you need WMP9 or OSX, I cant get this to work.
I followed this, it still does not work  [http://ubuntuforums.org/showthread.php?p=4552930](http://ubuntuforums.org/showthread.php?p=4552930)
Specifically I did this:

> OK I've got it I believe. I am not totally sure on the order, but here goes.

1) in synaptic remove totem-mozilla
2) in synaptic install vlc mozilla-plugin-vlc vlc-plugin-esd
3) I am not sure if it matters but I do have the ubuntu-restricted-extras as well as w64codecs installed

at this point MMOD should work.

I was also able to install totem-mozilla again here, but the video, but when watching, vlc is obviously still the player.

hope this works for you guys.

As a note it appears that my problem was that I did not have vlc-plugin-esd installed.

Also while you test, it is annoying to have to wait in the waiting room for the MMOD to let you in. This link (from the ncaa website) has a video that seems to accurately test. If you can see and hear, you should be fine. [http://plugindoc.mozdev.org/testpages/wmp9.html](http://plugindoc.mozdev.org/testpages/wmp9.html)

Cheers!

---

### Post by ibuclaw on 2008-03-21
I recommend "mplayer-mozilla" for all your internet viewing needs.

But to the point, I can't seem to view it either. Have you tried it on another OS? cos it may be the MMOD site server is down atm.

I'm only guessing. I took a screenshot of what I was seeing.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=63340&stc=1&d=1206126228[/IMG]

Just the words "Connecting to Server" and the bouncing between different locations, but no connection...

:confused:

First try it on another OS, then we could perhaps come to one conclusion or the other.

---

### Post by oddworld on 2008-03-21
It works 100% on XP.
I had mplayer originally, but it didn't work so thats when I followed the thread I posted above.
Anyone got any ideas how we can get this to work?

---

### Post by sports fan Matt on 2008-03-21
Could it be that the bandwith  (Im a sports fan myself but have access to a tv) and the amount of users trying to connect to that site jam up the server?  I heard on tv that for every office that logs on to that site or does anything NCAA Nrelated..they lose something in the realm of 1.7 BILLION in productivity in 10 minutes...

---

### Post by oddworld on 2008-03-21
Well the problem is that it works 100% in xp here on a friends computer in my apartment.
I have had ubuntu for 4-5 months are really like it, but I am trying to make it my only OS.

Any ideas how to get this to work?

---

### Post by ibuclaw on 2008-03-21
Okay, I've found a temporary fix... Isn't perfect, but it will do!

My conclusion is that maybe MMOD has a vendetta for Firefox... don't ask why, it just seems that way.

Okay, follow these instructions:
(1) Go back onto the MMOD Player page.
(2) Choose the game that you want to watch (I used MPlayer to view this, not sure if it will work with any other).
(3) While the stream claims to be connecting, right-click on where the video should be embedded.
(4) Choose "Copy URL" in the opened tab.
(5) Open VLC (or any other Network Playable Media Players) in Linux
(6) Go into "File>Open Network Stream" or hit "Ctrl+N"
(7) In the newly opened window, choose the "HTTP/HTTPS/etc" option and paste your copied URL in the adjacent box.
(8) Click "OK"
(9) An error message will pop up about some AD that cannot load ??? Anyways, just close it.
(10) Watch with ease! No issues!

Here are some screenshots (if you get lost)
Right-Clicking on the MMOD Player Video
[[IMG]http://img504.imageshack.us/img504/2103/screenshotnd8.th.png[/IMG]](http://img504.imageshack.us/my.php?image=screenshotnd8.png)

Pasting the URL into VLC
[[IMG]http://img231.imageshack.us/img231/9790/screenshotopende3.th.png[/IMG]](http://img231.imageshack.us/my.php?image=screenshotopende3.png)

The Error message you get
[[IMG]http://img86.imageshack.us/img86/1097/screenshoterrorsxp0.th.png[/IMG]](http://img86.imageshack.us/my.php?image=screenshoterrorsxp0.png)

And the Final Result!!! It WORKS!
[[IMG]http://img86.imageshack.us/img86/8840/screenshotvlcmediaplayeyk3.th.png[/IMG]](http://img86.imageshack.us/my.php?image=screenshotvlcmediaplayeyk3.png)

---

### Post by IcemanV9 on 2008-03-21
Mine works beautifully on Dapper (6.06.2) & Hardy (8.04). On the Dapper box, the mplayer-plugin is being used to display the live game (SD vs UConn). And, on the Hardy box, totem-xine-plugin is being used to display the live game (UMBC vs Georgetown).

I have attached the screenshot of one game to "prove" that it does work.

---

### Post by oddworld on 2008-03-21
Well I did exactly that and it still didnt work.
I tried VLC and totem, both never showed any video.
Strange, what you said should have worked.

---

### Post by ibuclaw on 2008-03-21
Perhaps its a bug that got into Firefox on the Gutsy release. And it wasn't fixed until they release Beta3.0...?
And as for it not working in VLC... Who Knows!

We all feed off the same pie (repository) and yet our machines act vastly different to different tasks...

Strange, don't you think...

---

### Post by ibuclaw on 2008-03-21
There's a "Complete Streaming" guide for Ubuntu found [here.]("http://ubuntuforums.org/showthread.php?t=661833")

Don't know if it will be of any help.
But anything legible is worth a try.

---

### Post by IcemanV9 on 2008-03-21
Hm. I did not have a problem with Dapper for 2 yrs. I used totem-xine, NOT totem-gstreamer (never works for me since hoary). And, I never used VLC at all. 

General tip: If you install a plugin, make sure you restart the firefox.

Speaking of the firefox version, I have 1.5.0.13pre for the Dapper box and 3.0b4 for the Hardy box. I don't think it matters, but get the right plugin to display the live game.

For the Hardy box, I just installed ubuntu-restricted-extra, then (after found out that totem-gstreamer still doesn't work) totem-xine. That's it.

---

