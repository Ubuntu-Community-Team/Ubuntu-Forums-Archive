---
title: "Automatically Logging Out, (Crashing?), Frustrating :/"
date: 2007-08-14
forum: General Help
---

### Post by vbgunz on 2007-08-14
I am using the latest Kubuntu 7.04 (fully updated).

This is so very frustrating. I walk away OR log into my sons account and as randomly as lightning strikes, my main user account just logs out. This **never** happens while I am using the account, it only happens when I either walk away OR my son is on his account.

I checked xorg.0.log and xorg contains no EE messages. I checked messages and the only suspicious thing I see is *GConf server is not in use, shutting down.* and almost immediately after that, *Received signal 15, shutting down cleanly*. I've checked */var/crash/* and find two files in there. one for Gaim and one for Firefox. I am trying to look into the logs sorted by date the best I can but I am unable to pinpoint the problem :(

I have tried changing my screensaver from *Euphoria (GL)* to *Blank Screen* and that didn't help. I really am stuck on what to do. I asked on #kubuntu about signal 15 and was told I should find out which app is sending the signal but I do not know how to figure that out :/

any help at all would be sincerely appreciated.

thank you!

---

### Post by vbgunz on 2007-08-15
I tried upgrading the Nvidia binary drivers from the one in the repos to the latest one on the official Nvidia site. This didn't work because I still found myself to automatically log out again later. I checked my xorg log again and found it crashed and sent a signal 11. I googled for this and found that commenting the 'Option "UseFBDev" "true"' should work. Well, I did that and so far so good. I need to look into this UseFBDev option but all seems well so I can only hope it really did the trick.

If anyone has any bright ideas, I am still all ears. Thank you!

---

### Post by vbgunz on 2007-08-27
well, just commenting out UseFBDev, didn't really do the trick. I noticed it still crashed or something as I came back once or twice and found myself logged out. What did seem to do the trick was commenting out this line (which I did about a week ago):
```
FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
```
For some reason, beyond me, this just seems to work or something. In a weeks time, I have not logged out automatically at all. I can only hope this really works.

---

