---
title: "Reset all Gnome 3 (3.8) settings to default? Ubuntu 13.04"
date: 2013-04-20
forum: General Help
---

### Post by Singtoh on 2013-04-20
Hello All,

I was wondering if someone could tell me how to do a complete reset of gnome 3.8 to default settings? As if I just installed fresh and logged in for the first time?? I adjusted some settings somewhere and fonts arent quite rite and other odds and sodds are not rite. So I was thinking if there were some commands to do a full reset back to scratch, that would be really good. There was no problems after the install, things were quite snappy, but play as I do with various settings, I have managed to mess things up a bit. I have searched around and have only found posts from a year or so ago and am afraid to use those for fear of making things worse. Thanks in advance for any help you could so graciously provide.

Cheers,

Singtoh

---

### Post by Dreamer Fithp Apprentice on 2013-04-23
I'm not an expert but you've gone 2 days with no answer so I'll give it a shot. I may be wrong, but I don't think there is anything like an all purpose, revert-everything-to-default-settings command. It's a good idea though. A darned good idea. It would probably be possible to script it. You'd need an additional script for the DE if you've changed it, or any other major component you've changed that might have settings you could have altered, like a window manager for instance.  If you hardware is such that you can conveniently install the same system again on another partition and update the new copy, it might work to copy all the system files (everything but folders you have your own data in) from /home/yourusername/ in the fresh installation to the same folder in your system. Depending on the circumstances that might be easier than reinstalling. However, if you try that, I'd make a copy of all the files in there now, before you copy over them. So if it makes things worse you'll be able to reverse it.  For future reference, I'd back up my system (as distinct from data) with something like Remastersys or fsarchiver everytime you tweak something and decide you like the change so that when you later tweak something you don't like and can't find your way back it will be easy to revert the changes. Done the best way, by restoring from an image stored on HD, while booted from another partition you can restore the system in 10 minutes or so without even having to interrupt whatever else you are doing on your computer.

You might get more effective responses if you could manage to remember anything about what sort of changes you made.

---

### Post by fantab on 2013-04-23
Are you sure that Ubuntu 13.04 is using Gnome 3.8? Or are you using Gnome PPA?

---

### Post by zombifier25 on 2013-04-23
This might help: [http://askubuntu.com/questions/56313/how-do-i-reset-gnome-to-the-defaults](http://askubuntu.com/questions/56313/how-do-i-reset-gnome-to-the-defaults)

---

### Post by Frogs Hair on 2013-04-23
12.10 & 13.04 have the Gnome Shell 3.6.3 in the repository and the only way to get a mostly complete version 3.8 is via three different  PPAs. I would make sure what version you have installed and see post 4.

---

### Post by Singtoh on 2013-04-23
Hello All,
Thanks for the replies. Yes I am using gnome 3.8.1 from the Gnome3 ppa. Yeah, I was just curious if there was a script floating about that someone knows about that could reset everything. I play around a lot and sometimes fiddle too much and screw things up. I am not a scripter/coder but I do try sometimes. I thought there might be a script that sets things back to default, floating about but I have searched high and low and haven't found it yet?? I have been looking at gsettings and trying to get something going with that in a script, but my head aches when trying the code thing. I'll look at that link zombifier25, thanks alot for the info. Man, a script that sets to default I thought was a good idea as well, but as I said, I haven't found it.

Thanks again,

Cheers,

Singtoh

---

### Post by Singtoh on 2013-04-23
I just looked at that link and I did see that before but I didn't want to do it because the post is a bit dated. I use fsarchiver for backups and can restore things back in 20 minutes or so, so I might give that post a try.

Thanks again,

Cheers,

Singtoh

---

