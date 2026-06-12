---
title: "X/Ubuntu 14.04 You Tube Issues"
date: 2016-04-01
forum: General Help
---

### Post by verymadpip on 2016-04-01
Sorry, this probably needs deleting.  Seems to be a Firefox issue as YT is also broken in Windows 10
Hi everybody!
At some point during Wednesday You Tube on my Xubuntu 14.04 64 bit install freaked out on me.
At some point during Thursday evening You Tube on my Ubuntu 14.04 64 bit install did the same.
Also, video links from a news website I visit are not working - no controls available & no error message on screen.
This is while using Firefox 45, Google Chrome is fine.  Yes, I could just switch to Chrome, but I'm a creature of habit & FF is my generally preferred browser

I'm thinking something to do with flash player, but really have no idea what's happening.
Anybody got any ideas about what's going on?

---

### Post by ajgreeny on 2016-04-01
Youtube is working fine here on all browsers that I have installed, and don't forget that these days youtube generally uses html5 not flash.

Your screenshot of the youtube .com page seems to be showing something very different from what I see, as shown in my screenshot, with no images enabled in yours for some reason.

---

### Post by verymadpip on 2016-04-01
Hi ajgreeny.
It's a mystery to me.
I don't seem able to get video.  At one point yesterday I got audio from a clip, but no visuals.
Chrome is a-ok.
I'm having the same issue with Firefox on a Win 10 box too.
I can't even access the doodad to let me switch to html5.  The "Try something new" link is there, but gives me no html5 options.  I can't even turn it off to turn it back on aagin -assuming I'd enabled it anyway, which I don't think I had with this install.
Interestingly, all was well with youtube pages I already had open last night, but if I opened a new tab from my bookmark  high weirdness occurred. (Ubuntu 14.04 64 bit box, different house & different ISP).

It's freaking me out, & I clearly picked the wrong week to quit smoking.

---

### Post by Impavidus on 2016-04-01
I have occasionally seem somewhat similar effects on other websites (not on youtube, but on wikipedia) in recent weeks. It seemed like a problem loading style sheets. But only rarely and intermittently, so I never really cared.

For me youtube hasn't used flash in a very long time, also because I simply disable flash in firefox unless I really need it. Youtube and many other sites default to something else when your browser reports it doesn't support flash. Disabling flash also removes those nasty flash ads that steal cpu power and make the cooling fans spin like crazy.

---

### Post by ajgreeny on 2016-04-01
The only other thing I can suggest is to rename the hidden **.mozilla** folder in your home to see if that overcomes the problem.

If it does work properly with a new user profile, your current profile must be corrupt in some way.  Having renamed the old folder and not deleted it you can still restore bookmarks, etc, etc, if they are not already synced in the cloud.

---

### Post by fall2 on 2016-04-01
Did you check your modem/router and or wireless. Sometimes my pages look similar and I reset my modem/router, then its okay again.

---

### Post by verymadpip on 2016-04-01
Hi chaps.
ajgreeny, I'll give the renaming a go, probably tomorrow.  I can live with using chrome for now.
I don't really see why I'd be having the same issue with Windows though.  I'm not aware that I'm using the same Firefox profile for any of my machines, although I tend to save bookmarks from one machine & restore them to fresh Firefoxes elsewhere, if that makes sense.

fall2, I may try the router thing tomorrow too.  This happens in 2 different locations, which seems odd.

I'll let you guys know how I get on with your suggestions.

---

### Post by desesperado on 2016-04-01
I'm facing the exact same issue on my Xubuntu system with Firefox.
```
~$ lsb_release -a && uname -r
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.4 LTS
Release:    14.04
Codename:    trusty
3.13.0-53-generic
``````
~$ firefox -version
Mozilla Firefox 45.0
```

---

### Post by verymadpip on 2016-04-02
Hi everybody!
fall2 - router reset did not help, thanks for the suggestion nevertheless.
ajgreeny - renaming the .mozilla directory has done the trick on my Xubuntu box.  Thanks for the help.

On the Windows 10 box in question I used the "Refresh Firefox" feature & that cured the issue there.
This option is also available in Xubuntu, so it may be less hassle to try that before the rename.

I have to say, I'm still pretty baffled as to the "why?" of this, but what the hey, I'll take the win.

---

### Post by desesperado on 2016-04-02
> **verymadpip said:**
> Hi everybody!
fall2 - router reset did not help, thanks for the suggestion nevertheless.
ajgreeny - renaming the .mozilla directory has done the trick on my Xubuntu box.  Thanks for the help.

On the Windows 10 box in question I used the "Refresh Firefox" feature & that cured the issue there.
This option is also available in Xubuntu, so it may be less hassle to try that before the rename.

I have to say, I'm still pretty baffled as to the "why?" of this, but what the hey, I'll take the win.
Thanks for that tip, verymadpip. I refreshed Firefox and You Tube is showing up now as it should.

---

