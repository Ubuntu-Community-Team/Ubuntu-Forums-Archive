---
title: "Firefox Session Restore"
date: 2015-10-24
forum: General Help
---

### Post by ColdGoldLazarus on 2015-10-24
So tonight, my Firefox crashed. As it usually does that when the computer has been on too long, I rebooted the computer and opened up Firefox again, but it went to the home page instead of the session restore page. I went to the history tab and tried to restore it from the button there, but it just refreshed to the home page again. While I may be able to recreate the session data from my history, it won't be easy as I had quite a few tabs open at the time, not all of which I remember exactly. It would be preferable if I can still restore it more directly. If I can't anymore, I would like to have exhausted every alternative first. I'm running Lubuntu on a Dell computer with intel core i7, and am posting here via Chromium as I am hesitant to mess up Firefox's data any further.

---

### Post by Bucky Ball on 2015-10-25
Welcome. Can't help with putting together your tabs to get to where you were previously, but here's something that will help in future: Session Manager. 

In Firefox, go to Tools> Add-ons and search for 'Session Manager'. Install it. Tweak with the configuration and when Firefox crashes, Session Manager will save the session and when you re-open Firefox, you will be asked which session you would like to open (the previous session will be the first offered, but it keeps each session and you can manually save and name sessions). A real life saver. 

I would advise, though, posting a new thread to try and figure out why your Firefox is crashing in the first place. Good luck. :)

---

### Post by ColdGoldLazarus on 2015-10-25
Thank you very much! I'll install Session Manager ASAP, and then look at the crashing. (though that may have just been from the sheer amount of tabs I had open. Behavior to learn to avoid.)

---

### Post by Bucky Ball on 2015-10-25
> **ColdGoldLazarus said:**
> ... may have just been from the sheer amount of tabs I had open. Behavior to learn to avoid.)

Hehe. Possibly, depending on the specs of your machine, RAM specifically. I use groups for tabs, but not sure if FF reads that as still having all the tabs open or 'sleeps' the tabs in the not-visible groups. 

The groups button is in the top right hand corner of FF between the close/minimise/maximise buttons and the menu button (at the very right hand end of the line of tabs). It is a square made up of four rectangular 'blocks' (is one way of describing it!). Click that and you will see the groups. Click any tab in a group and that will open FF to that group. :)

Might help. Helps me organise things, I know that much.

---

### Post by ColdGoldLazarus on 2015-10-25
Oh, that's another thing I could do moving forward; thanks!

Additionally, I thought of another possible solution to my present problem. Do you know where the file containing the session restore data is? I might be able to see if I can rewind to a version from yesterday, before the crash, or something.

---

### Post by Bucky Ball on 2015-10-25
That's an idea. Open a file manager to your /home directory and hit control+h to show hidden files. Navigate to:

/home/<username>/.mozilla/firefox/********.default/sessions

... and see what you find. In the path above, <username> = your username and ******** will be a random alpha-numeric mix, like 'WX35HR93.default', which is your FF profile. I'd back that profile file up before you start fiddling with it, perhaps, as if you delete or mess it up you may be in trouble. If you delete it, FF will create a new profile when you relaunch FF, but it will be completely default, any changes you've made to your original profile, like customising FF, will be lost. 

I'm presuming the /session folder is default FF folder and not attached to Session Manager (there appears to be a 'sessionstore-backups' folder for that), but I could be wrong ... :-k

---

### Post by ColdGoldLazarus on 2015-10-25
Okay, I'm in the folder, and there's five text files; backup.session, backup-2.session, and onward. Unfortunately, looking at their properties, they're all dated to today. I did open firefox a couple of times to look at the history window. Unless there's anything else I don't know about, I may just have to try to recover things manually via that history. At least I have sessionmanager for the future, though.

---

### Post by dragonfly41 on 2015-10-25
The more you close and restart Firefox you are likely to lose opportunity to recover a crashed session.

I use quite a number of tabs and here are some guidelines I follow.

In your profile folder there is a file sessionstore.js which only appears _after_ you quit Firefox.

~/.mozilla/firefox/<profile-name>/sessionstore.js

There is also this folder .. ~/.mozilla/firefox/<profile-name>/sessionstore-backups/

and in there you will find recovery.js, recovery.bak

As soon as you experience a crash (if you don't have add-on sessionmanager installed) make a point of backing up these two files as soon as you can.

After first backing up these two files .. copy recovery.js into ~/.mozilla/firefox/<profile-name>/
and rename it as sessionstore.js

then try restarting Firefox.

It may be that this doesn't work since you've already restarted Firefox several times and each startup changes recovery.js and recovery.bak.

i.e. the recovery chain is 
sessionstore.js
recovery.js
recovery.bak


Regarding using multiple tabs I recommend try TabGroupsHelper add-on.

Also try installing addons ...

About Sessionstore
Norwell (for history view)
Save My Tabs (regularly saves tab URL's as txt files into profile directory to help in recovery)

---

