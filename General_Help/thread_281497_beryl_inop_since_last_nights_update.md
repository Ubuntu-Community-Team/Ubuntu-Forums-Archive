---
title: "beryl inop since last nights update"
date: 2006-10-21
forum: General Help
---

### Post by swp6499 on 2006-10-21
beryl was working fine on my pc until last nights update to 0.1.1 now when i load beryl the window border flickers IF beryl doesnt crash when i load it....anyone else having this problem? another thing that was weird was when the window border started flickering i clicked on the beryl-manager icon and did quit.. but the wobbly windows and the cube were running in metacity it seemed like...any suggestions?

---

### Post by tribaal on 2006-10-21
I have a similar problem: Beryl doesn't see to be started automatically like it used to before the updates.
I had to re-do my setting for beryl plugins too, so you might need to do that too.

- trib'

---

### Post by swp6499 on 2006-10-21
what did u do in beryl-plugins to get it right? are u have the weird metacity things or flickering window border problems??

---

### Post by tribaal on 2006-10-21
Well I just had to set the settings to my likings again, like if my config file was deleted.

I experienced a few flickering menus, yes. My main issue now is Beryl's refusal to start. I have to start it manually every time I log in.

- trib'

---

### Post by JunySan on 2006-10-21
same problem here.....

---

### Post by neymac on 2006-10-21
the same here

How do I restore my previous version of beryl and emerald?

---

### Post by roger99 on 2006-10-21
Same with me, beryl starts alright on login but uses 100% of my processor continually.  Plus flashing menus, windows, sticky notes refusing to leave the screen etc.  I've disabled it for the time being.

---

### Post by neymac on 2006-10-21
I downgraded beryl and emerald to 0.1.0-1. All working fine again.
I'll wait the next version to update.

---

### Post by swp6499 on 2006-10-21
how did you downgrade the version?

---

### Post by Dual Cortex on 2006-10-21
lol crap I just upgraded it... I don't want to restart my computer now!

---

### Post by shanepardue on 2006-10-21
i just updgraded..restarted my computer and it works great. no problems at all.

---

### Post by PriceChild on 2006-10-21
i deleted ~/.beryl* & ~/.emerald*

then restarted beryl.

---

### Post by hanzomon4 on 2006-10-21
My window decorations refuse to show, tried purging then reinstalling, and deleting my ~/.beryl ~/.emerald dirs...

---

### Post by swp6499 on 2006-10-21
fixed mine it was trying to load my window theme and it wasnt installed...weird...anyway...in response to a couple of the above posts about beryl autostarting if u man beryl from terminal it says at the top autostart not available anymore...hope this helps...

---

### Post by gorded on 2006-10-21
Does any one know how i can revert all my beryl and emerald packages back to their previous vesions, my windows decorations are showing up but.

Thanks

---

### Post by hanzomon4 on 2006-10-21
I figured it out kinda....

First I uninstalled everything again. I was about to reinstall, shutdown, and try again.. But I decided to make sure beryl was really uninstalled.

I popped  open a terminal a typed "beryl"... I got the "command not found" message, just what I expected. I then typed emerald and it spit out some error indicating that emerald was still installed.

I checked to make sure I uninstalled it and I had, so I ran a locate emerald. I found that I had emerald dirs and a bin file located in /usr/local, like I installed from svn or something.

I removed all the /usr/local emerald files reinstalled all my beryl stuff and it worked. However what I don't get is how emerald got in /usr/local and /usr/. I haven't installed from svn and this only appeared after updating, via the repos, to v0.1.1. Is this a packaging error?

---

### Post by Nojatron on 2006-10-21
Thanks Hanzomon4, same thing fixed my problem. Only issue left is it seems to be looping the mouse over of the min/max/close buttons.

---

### Post by smeager on 2006-10-21
Well I've tried every suggestion listed here and it's still not functioning correctly. I can't even use the command:

```
beryl-manager --force-window-manager
```

All I get back when I enter it in the terminal is:

```
Usage: beryl-manager [-d] [--force-window-manager] [--force-decorator] [--help] [--version]
```

I can launch it using the standard beryl-manager and that is the only way I can get it to launch at startup, but when it does I get the flashing window boarders. 

Any other suggestions???

---

### Post by Nojatron on 2006-10-22
> **Nojatron said:**
> Thanks Hanzomon4, same thing fixed my problem. Only issue left is it seems to be looping the mouse over of the min/max/close buttons.

Figured it out. If you have this problem and it annoys you too, just go to Emerald Theme Manager and click on Emerald settings uncheck the button fade pulse, it seems this is on by default

---

### Post by m.musashi on 2006-10-22
The only problem I had was that beryl would no longer auto load. It also changed some settings but that wasn't too much of a problem. This morning, there was another update to the beryl manager so I installed it hoping that it would fix the problem. It did. But it created more. Now it auto loads but runs the cpu at 100%](*,)

---

### Post by KingArthur10 on 2006-10-22
> **m.musashi said:**
> The only problem I had was that beryl would no longer auto load. It also changed some settings but that wasn't too much of a problem. This morning, there was another update to the beryl manager so I installed it hoping that it would fix the problem. It did. But it created more. Now it auto loads but runs the cpu at 100%](*,)

Same issue here.  It's getting to be a pain.  I upgraded to edgy and had the exact same problems (clean install).  Hopefully they roll out another update soon enough.  How does one downgrade to an older version of the file?

---

### Post by thesmartace on 2006-10-22
I had problems when I booted this morning. Beryl starts running at 100% and the window borders would randomly flicker on and off.

I managed to open Emerald and set it back to a built-in theme. This fixed the flickering and 100% problem. I could then set it back to my custom theme and all was good.

---

### Post by KingArthur10 on 2006-10-22
[HERE]("http://bugs.beryl-project.org/ticket/588") is a link to a bug report on this.  Please post and let them know how many of us are affected.

---

### Post by shanepardue on 2006-10-23
I recant my statement of it working fine. It's now giving me the same 
problems that everyone is mentioning here. I have noticed that if I just exit
 beryl-manager from the tray, the problem is fixed and i still have my XGL/compiz working.

---

### Post by tribaal on 2006-10-24
A very strange thing I noticed: on my laptop, the fickering and 100% CPU seem only to happend when the power plug is unplugged during boot (when it's not booting off the battery). Booting on the battery and then plugging the power supply back in seems to be the way for me. 
I know, it's pretty strange, but it works.

Anybody else experiencing this?

- trib'

---

### Post by cogsprocket on 2006-10-24
There's an update that came down today that may fix this problem but I'm unsure.  When I started up this morning I had the flicker problem.  After installing the libGUI update it runs fine.  I'm not 100% that this has fixed it though. I've not restarted X yet to be certain.

*edit - Negative on that.  I'm sure someone else has had this experience and probably would have informed me I was wrong had I not checked for myself.*

---

### Post by linuxmad on 2006-10-24
any updates on this issue?

---

### Post by m.musashi on 2006-10-24
> **linuxmad said:**
> any updates on this issue?

I don't know if there have been any official updates. After updating to 0.1.1 and experiencing the problems of flicker and 100% CPU, I removed beryl-manager from start up and rebooted. Then I manually started beryl-manager and it worked fine. I have not tried to set it back to auto start. However, it seems to work fine if you wait until everything else loads and then starting beryl. It's more of a hassle but until their is another update it isn't too bad.

---

### Post by linuxmad on 2006-10-24
Ok .. problem solved .. it is a hack ... but we all love hacks :)
[http://forum.beryl-project.org/topic-5682-titlebar-blinks](http://forum.beryl-project.org/topic-5682-titlebar-blinks)

---

### Post by ronmarley1 on 2006-10-24
> **linuxmad said:**
> Ok .. problem solved .. it is a hack ... but we all love hacks :)
[http://forum.beryl-project.org/topic-5682-titlebar-blinks](http://forum.beryl-project.org/topic-5682-titlebar-blinks)
This works for me also.

---

### Post by Syd_Crowe on 2006-11-27
Since the beryl forums are currently down, can anyone list this hack to fix the problem? Thanks.

---

