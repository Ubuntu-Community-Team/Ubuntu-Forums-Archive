---
title: "3ddesktop/desktop cube effect not working"
date: 2008-04-26
forum: General Help
---

### Post by Micieri on 2008-04-26
Hey guys, this is probably just a very simple fix but here it goes:

Yesterday I installed Beryl and 3ddesktop on 7.04, and done the settings so it was all nice and sexy. The desktop cube worked fine when I done the default shortcut: <Control><Alt>Button1. Then totally randomly, without me touching the settings it just stopped working. I tried changing the shortcut but that didn't work either. I looked through the settings and everything seems to be how it was before, the desktop cube options were still there, it just wouldn't activate it. I do have 4 workspaces, desktop effects are enabled etc. I just really don't know what happened. I'm upgrading to 7.10 then hopefully to 8.04 if it's done in time, but I doubt that would be the problem seeming as it already worked fine on 7.04. Also when I do <Control><Alt>Left/Right, it doesn't rotate in the cube like it did before, it just changes windows so I'm guessing something has disabled the cube. Of course I've tried rebooting, and it doesn't let me uninstall Beryl because it's depended on by other applications (says Ubuntu).


Thanks for your time, I hope you can help.

Mike.

---

### Post by Zorael on 2008-04-26
I'm just guessing now, but you wouldn't happen to be using any foreign repositories, hmm? :>

Check your Software Sources and remove them (such as Treviño's eyecandy repo), then open up Synaptic and find Compiz, Beryl and Emerald packages. Mark them and choose **complete removal**. Or enter this in a terminal.
```
$ sudo apt-get autoremove --purge compiz* libcompiz* beryl* libberyl* libdeco* emerald* libemerald*
```

Then reinstall it. And remember the repos; you must disable them. (Can also be done by removing/commenting appropriate lines in /etc/apt/sources.list or removing/renaming *.list files in /etc/apt/sources.list.d/)

---

### Post by Micieri on 2008-04-26
Thank you for the time to reply, and well, to my knowledge I was using the default repositories, which seemed to be all of them.

I've done what you said, but when I look for Beryl or 3ddesktop in Synaptic or Add/Remove, they aren't there, even after ticking all the repositories again. I'm now on 8.04 and also there's no Desktop Effects app in System, I can change the Visual Effects though. I think I've installed compiz again because I got the file from Synaptic, but there's no System Tools option in Applications, like there was before.

Mid-post edit: Ok I've found compiz via Add/Remove apps. Comes up with the System Tools option, then inside that is Compiz Fusion Icon, which places a settings icon in the taskbar. Still no Desktop Effects app though.
Now I've got the options I had before, and it's set the same binding as Initiate the cube, <Control><Alt>Button1, which won't work. So I'm back to the situation I was in, in my first post.

Thanks again, sorry it didn't work :P

---

### Post by Zorael on 2008-04-26
I'm not sure what 3ddesktop is, but you don't want Beryl anymore, Compiz has superseded it. This is the case for 8.04; if you're on 7.04, stuff is much more complicated (you'd *need* foreign repositories to get Compiz-**Fusion**).

You may want to make sure you've gotten the Compiz Settings Manager installed, too. I'm not sure if it's listed in Add/Remove, but its package name is **compizconfig-settings-manager**, so you can install it via Synaptic or via a terminal.
```
$ sudo aptitude install compizconfig-settings-manager
```

If you're still on 7.04, none of this will likely apply. Gogo upgrade~

---

### Post by Micieri on 2008-04-26
I think we can disregard 3ddesktop now, it's just the cube effect for the 4 workstations, which seems to be included in compiz anyway. Ok I'll forget about Beryl then, I wasn't sure because I read somewhere that they were different then I read somewhere else that compiz was the successor of Beryl, which you confirmed.

Synaptic says compizconfig is installed.
The 3 hour or so delay in replying was the result of upgrading through 7.04,7.10, and finally 8.04 :P
When I went from 7.04 to 7.10 that's when the app Desktop Effects was removed, which doesn't help because I can't find any other option that would help me activate the effects.
I've set things like window shiver etc, but none of them are working, I just restarted to try and refresh everything but it got me nowhere. I must have missed something very small because looking through the other threads there doesn't seem to be anyone else with this problem.

Edit: I have a weird feeling there's just one setting to activate it all, because it's not right for every single effect to not work at the same time.

---

### Post by Micieri on 2008-04-26
Sorry for the double post, I just want to say I've solved it.

What I did was completely remove everything compiz, then reinstalled again like I was told at first.
Then I got the compiz fusion icon and simply clicked reload window manager, and everything works fine. Thanks for the help Zorael, I never even thought of reinstalling until you mentioned it :P

---

