---
title: "Load Programs into RAM on Startup"
date: 2008-04-03
forum: General Help
---

### Post by mlapaglia on 2008-04-03
How can I get my most used applications (firefox, thunderbird, pidgin, etc) to load into RAM at startup? I have 4 gb's of RAM, and even with windows virtualized, compiz-fusion running, and ton of programs I still have 3.4 gb's left...

Maybe a way to get programs to start loading into RAM a few minutes after the GDM is fully loaded?

Preload just isn't doing it for me, everything is still loading off of the hard drive when I attempt to run it.

---

### Post by kerry_s on 2008-04-03
you must want a really long startup. :)

preload can be configured.
"man preload" for more info

example:
/usr/bin/firefox --add preload

---

### Post by mlapaglia on 2008-04-03
well, no not a long startup..

what i mean is, can't ubuntu wait after gdm loads and say "hey, no one is using the computer and i have over 3gb of ram that pretty much never gets used because mlapaglia needed it to run vista but not ubuntu" and load stuff into RAM by default?

maybe this should be in the brainstorming site.

(thank you for your help though, I'm looking into configuration)

---

### Post by kerry_s on 2008-04-03
as far as i know there's nothing for that feature.

i just added preload to my custom install, the only thing i changed was the save time from 3600 to 120.

i looked at /var/lib/preload/preload.state
and does seem to be doing it's job it has everything i use in there.

still looking into it myself though, i'll let you know if i come across anything to tweak it.

---

### Post by mlapaglia on 2008-04-03
the /usr/bin/firefox --add preload makes my firefox startup completely from RAM.. after the <i>first</i> time i load it, which makes the hdd think.

it's currently got firefox thunderbird lastfm and pidgin done like this, they all act in the same way. which is awsome (firefox comes up maybe 2 seconds after i hit it, lastfm instantly.. am i doing something wrong that they aren't being... preloaded lol

---

### Post by ramkumail on 2008-04-03
Nice idea. I am sick of firefox taking long time to start. If experienced users can post a howto for using preload with firefox it will be great. I have tried swiftfox and didn't see any big difference. Keep up the good work.

---

### Post by mlapaglia on 2008-04-03
well i'm gonna have to correct myself. when i launch any application a second time after closing it, it always boots from ram..

so how can we pre-preload?

---

### Post by kerry_s on 2008-04-03
i don't think anything can be done, once you use the app it loads to ram, so starting after that is not a problem.
personally i don't reboot that often, except when i'm messing around and want to see the results, i never shutdown. i don't think i'm going to keep preload there's no real benefit for me.

---

### Post by forrestcupp on 2008-04-03
You're not going to be able to do it without having a long start up time.  In order for it to load into the RAM to be faster the 2nd time, it has to load it in the first place, which adds time to your start up.

If you don't mind having a long startup, you can put the programs you want in the Startup Programs in System->Preferences->Sessions.  You could even make a bash script to load the programs you want with preload and put that script in your Startup Programs so that all of those programs will stay in RAM.

You can also go to Sessions and in the Session Options tab click the box that says 'Automatically remember running applications when logging out'.

Also, using **alltray** is an option to keep programs running in RAM with a little icon in the notification area that you can click when you want to open it back up.

But seriously, it only takes about 2 seconds to open Firefox from the hard drive.  Is it really worth it?

---

### Post by Outworlder on 2008-04-03
> **forrestcupp said:**
> You're not going to be able to do it without having a long start up time.  In order for it to load into the RAM to be faster the 2nd time, it has to load it in the first place, which adds time to your start up.

If you don't mind having a long startup, you can put the programs you want in the Startup Programs in System->Preferences->Sessions.  You could even make a bash script to load the programs you want with preload and put that script in your Startup Programs so that all of those programs will stay in RAM.

You can also go to Sessions and in the Session Options tab click the box that says 'Automatically remember running applications when logging out'.

Also, using **alltray** is an option to keep programs running in RAM with a little icon in the notification area that you can click when you want to open it back up.

But seriously, it only takes about 2 seconds to open Firefox from the hard drive.  Is it really worth it?

Short answer: "Vista does it"

Long answer: it does not have to increase startup time. As long as it starts prefetching *after* the system  has started up already and it is idling.

---

### Post by Whiffle on 2008-04-03
NEvermind, I can't read.

---

### Post by forrestcupp on 2008-04-04
> **Outworlder said:**
> Short answer: "Vista does it"

Long answer: it does not have to increase startup time. As long as it starts prefetching *after* the system  has started up already and it is idling.

True, Vista does it.  But in my opinion, Vista's implementation of it is crap.  It slows normal performance down while it is loading things into memory.  But I don't have dual core, either.

---

### Post by philphil on 2008-05-14
How about XP? XP does it.  When I boot the PC at uni and then click on Word or IE or a number of programs they load INSTANTLY and I'm not talking about 2 seconds or 1 second, it's INSTANT.  I click it, it's there.  It's so quick it's as if I've alt+tabbed to it.  It makes me sick and it makes me wonder what am I doing with Ubuntu? XP is already quicker, why did I change again?

---

