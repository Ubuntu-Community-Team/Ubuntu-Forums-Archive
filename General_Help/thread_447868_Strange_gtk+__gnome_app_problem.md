---
title: "Strange gtk+ / gnome app problem"
date: 2007-05-18
forum: General Help
---

### Post by Cene on 2007-05-18
Hi,

Searched a while these forums and didn't find any threads related to this. I could say that i'm pretty experienced in using Linux and solved most of the problems i've ran to myself, but this has caused me many problems.

So, I use Openbox with pretty many gtk/gnome apps (firefox, gnome-volume-manager, gdm, gnome-terminal, gaim, evolution etc...). These all work flawlessly (except firefox crashing randomly, but that is another story...), but most of the apps that come with gnome will slow down X so much that i cannot do anything but to restart X. These applications include Totem (but, surprisingly, not the totem player plugin for Firefox), Nautilus, gnome-settings-manager, Rythmbox, gnome-mouse-properties and so on.
So, basicly, I cannot start an gnome session (not even failsafe) without crash, and some of my favourite programs (totem mainly..) are unusable. Reinstalling these applications wont help, and logs show absolutely no errors or anything.

Myself, i think that this is caused by some corrupted gtk library what some programs use. I just got no ideas wich lib that would be. Any way to figure this out? Any other ideas? All welcome.

---

### Post by Cene on 2007-05-19
I hate to do this, but this problem is bugging me too much.. so: bump!

---

### Post by Cene on 2007-05-20
>_>

---

### Post by RedSquirrel on 2007-05-20
Sounds like a bug. I would try looking on launchpad to see if there's anything you could try. You could also create a bug report if you don't see a thread with your exact problem. 

Is it just GNOME applications? I know some people have to set pci=noacpi on the kernel command line or their system will freeze...

Launchpad:
[https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)


Good luck! :)


EDIT:

Here is a post from someone having strange problems with the desktop becoming slow:

[http://ubuntuforums.org/showpost.php?p=2687664&postcount=5](http://ubuntuforums.org/showpost.php?p=2687664&postcount=5)

No solutions presented there, but it sounds like a similar problem.

---

### Post by Cene on 2007-05-20
> **RedSquirrel said:**
> Sounds like a bug. I would try looking on launchpad to see if there's anything you could try. You could also create a bug report if you don't see a thread with your exact problem. 

Is it just GNOME applications? I know some people have to set pci=noacpi on the kernel command line or their system will freeze...

Yes, just gtk+ or gnome apps. What does pci=noacpi do? I don't think that's the problem, because everything worked fine a while ago.. Now to think of it, the problem appeared about the same time i tried Enlightenment E17.. Gotta try removing that.

> 
Here is a post from someone having strange problems with the desktop becoming slow:

[http://ubuntuforums.org/showpost.php?p=2687664&postcount=5](http://ubuntuforums.org/showpost.php?p=2687664&postcount=5)

No solutions presented there, but it sounds like a similar problem.

Looks about the same except that gkrellm works fine for me. :P
I haven't even got gvim installed, gotta try that later.

Edit: Haha, removing e17 did the trick! well, mostly.. Totem still uses more cpu than before, fonts look blurry in gtk+ apps now and my mouse configs got screwed up. :D
I think i can solve most of those and other than that, everything works like a charm.

Maybe i should file a bug about this to launchpad..

Edit2: Okay, more oddities. :D
I started an gnome session just to test everything was fine. All went good except that screen turned black for few seconds at login.. Nothing big.
Another problem now is that the mouse gets screwed (sensitivity changes and mouse acceleration turns on) only when i start some of the  programs that used to be bugged and fonts get bigger. I can solve the font problem by killing gnome-settings-daemon (wich didn't even start up with totem before.. dunno why it does now), but after it they look blurry.
The mouse is bugged like that no matter what i do until i restart X. Even if gnome-mouse-properties is turned off the problem presists.

---

