---
title: "Lubutnu 16.04 - Chrome not working on the laptop, but works in a Virtualbox Lubuntu"
date: 2017-01-03
forum: General Help
---

### Post by donsevilla on 2017-01-03
Dear wise and great gurus

Have been running Lubuntu 16.04.1 on this machine (one of the first DellXPS13s, snapshot below) for several weeks now. Generally all good except for Chrome. 

Chrome starts, displays a window with an address bar, and then pretty much just freezes. Can't even close it. Longer detailed description here:

[HR][/HR][INDENT]If I open a window from another program on top of it, then minimize that second program, I get a 'ghost trail' of the second program, like the machine can't repaint the screen with Chrome and just fills it with the intermediate images of the second program minimizing. I'd screenshot it for you, but that function doesn't seem to be working.

So Chrome just sits there. Its visible as multiple processes in Task Manager, although I have never seen it occupying the highest memory or CPU. It has 13 separate processes called 'chrome', all using 0% CPU and between 110-64MB in the RSS column. 

Sometimes the fan kicks in gently but the system as a whole is not unresponsive or slowed (usually running ~20 Firefox windows, password manager and then e.g. file browsers and Virtualbox). I can click on the Chrome session in the task bar - it 'invisibly paints' the whole screen with Chrome, i.e. the view doesn't change but you can't click on anything on the window underneath it.

Then every so often, it works for a second. E.g. I have set it as the default browser, so when I followed an [www.lxde.org]("http://www.lxde.org") link in the 'help' section of Task Manager, up popped chrome with lxde.org in the address bar - and then it froze solid again.

It will not close. Right click on the tab in the task bar gives you the usual options including 'close window', but that does nothing. The function xkill doesn't work. Last time, manually killing every one of those 13 processes in the task manager did the job. This time, I just had to kill the biggest and all the others closed. 
[/INDENT]
[HR][/HR]

I have purged Chrome with apt-get and reinstalled. Same behaviour - this underlines its none of the plugins x lubuntu, because I didn't have the chance to install them. 


Web searches didn't show a lot (any?) of people with the same issue.

On a whim, I installed Virtualbox and then followed the prompts to create a VM with the identical lubuntu 16.04 - as in, from the same disc (checksum was fine, btw). Perfect, no problem. Played with that for a week, then updated it to 16.04.1. Again, no problem. 

So what gives? Last distro was Ubuntu-Mate, and I had a few problems that I can't even remember now, but not like this. I have a disc with the new Mate LTS waiting for me down at the post office (internet only 10GB per month :( ), and I think its best I change it over, but this nags me... What's going on? Is this a hardware thing? Is this evidence of interference on my machine? (Hence, am I safe?) What am I not understanding here?

Your insights would be gratefully received.

DS


*I've used a variety of distros over a couple of years now but I'm really not well versed in computers. Any requests for more information I'll be happy to comply, but you'll have to give me some pointers on e.g. what commands to run.*


Processor               : 4x Intel(R) Core(TM) i5-2467M CPU @ 1.60GHz
Memory                  : 3929MB (3413MB used)
Operating System   : Ubuntu 16.04.1 LTS
Date/Time              : Wed 04 Jan 2017 10:56:25 AEDT
-Display-
Resolution              : 1366x768 pixels
OpenGL Renderer    : Unknown
X11 Vendor             : The X.Org Foundation

---

### Post by dragonfly41 on 2017-01-04
Sounds vaguely similar to this ..

[http://en.community.dell.com/techcenter/os-applications/f/4613/t/19993614](http://en.community.dell.com/techcenter/os-applications/f/4613/t/19993614)

Note: I'm running 14.04 on a Jurassic version of Dell laptop so this is just a guess, not from any experience.

---

### Post by vasa1 on 2017-01-04
> **donsevilla said:**
> ...
I have purged Chrome with apt-get and reinstalled. ...
Your profile will be unaffected by that. Have you tried with a new user? That'll leave your original profile intact but give you another pristine profile.

Also, have you disabled hardware acceleration? Does starting Chrome this way```
google-chrome-stable --disable-gpu
```help?

---

### Post by donsevilla on 2017-01-04
Ok, I am scratching my head.

Tried making a new user account as you suggested, vasa1. Gave it the same privileges as my usual (hitherto, my only) user account. Tried to switch users via lubuntu power menu and it only offers me my original user account as an option, i.e. clicking the dropdown box on the login menu did nothing. 

Restarted the machine - a vague and desperate homage to my Windows days - and got the same belligerent behaviour. Log in via my original user name and check the settings - can't see anything different in the settings between the two accounts. Searched google and nothing jumps out.

Again, to test, I tried the same on the Virtualbox installation and I got through to the new user account just fine. 

I don't know if it makes a difference, but I should note I am running full disc encryption and LVM on the host. (Nothing special, just walked through the Lubuntu installation wizard). 

_However_ - Chrome is now working smoothly after the restart. (I have restarted several times before and *not* had this result).

 I haven't logged in to my Google account, I can see it isn't running with any of my extensions... Okay. Just logged in to my Google account, and it still hasn't run with my extensions. I thought that was automatic. Anyway, for no good reason that I can discern, Chrome is up and running again after several weeks of malfunction. 

I just don't seem to have the ability to access a new user account. 

Is there a deeper problem here? (Other than a clueless operator, that is).

---

