---
title: "Uninstalling nvidia drivers disrupted beryl"
date: 2007-05-02
forum: General Help
---

### Post by dizzle on 2007-05-02
First, let me start off by saying I installed Ubuntu last week and I LOVE it!

However, there are a few issues with it, some minor, this one major.

I installed Beryl from the Add/Remove prompt, and it was amazing.  Then I installed the Nvidia drivers from the Add/Remove prompt (the binary ones I believe).  Things were good, then I realized the windows were missing title bars!  Ack!  I set the window manager to Metacity (I believe that's what it's called) and uninstalled the Nvidia drivers.  After that I set the window manager back to Beryl and that's when the problems started.

The screen went white, and I panicked and hit the reboot button.  Well, it brought me into a prompt that said X11 wouldn't load, would i like to see a log or something like that.  After that I rebooted into the recovery mode, and just saw a prompt, with no welcome screen or anything.

I didn't really create or save any documents, but if I could save this installation I would rather do that than reformat that partition.  That being said, I will if i have to, because Ubuntu is worth it!

Thanks in advance!

---

### Post by spankymasterc on 2007-05-02
ok First te missing windows isnt nvidia problems all you have to do is add some things to your xorg.conf ask me if u dont want to look (im to lazy to look right now lol)

Next in recovery mode type

sudo dpkg-reconfigure xserver-xorg and leave things on default 

and it will reconfigure your xserver

now restart the computer and try again 

if you need further help hit me up

---

### Post by mozetti on 2007-05-02
Try running ```
dkpg-reconfigure xserver-xorg
``` from the recovery console (it's supposed to drop you at a root prompt, and not the "Welcome" screen -- it's for recovering a broken system).

From there, pick the "nv" driver when it prompts you (assuming you have an nvidia graphics card).

That being said - Beryl & Compiz are pretty graphics-intensive. Installing/uninstalling core components like video drivers and Beryl willy-nilly isn't the best way to go about it. Research exactly what you're doing, and the right ways to do it, before you begin to avoid having an installation that won't load up and you should be fine.

---

### Post by dizzle on 2007-05-02
The dpkg command worked very well, thank you.  I tried enabling Beryl once again, but the same issue cropped up, so I think I'm going to uninstall it, or at the very least not use it.

And let me say that I am very impressed with the speed and quality of the answers I received.

Thank you.

---

