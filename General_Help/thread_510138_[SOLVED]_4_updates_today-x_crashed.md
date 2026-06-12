---
title: "[SOLVED] 4 updates today-x crashed"
date: 2007-07-26
forum: General Help
---

### Post by DougieFresh4U on 2007-07-26
Using Feisty live-cd at this time.
This morning, update icon showed 4 updates on my Feisty box. I ran updates from terminal and then it wanted a system restart. When I restarted, I was presented with, " x failed to  start " , or some thing to that effect.
Not sure of the command for reconfigure x and also how can I get back up x, as I do recall backing it up a couple of days ago
If any one is willing to help me out, I need it put in real simple terms as I am still learning. I do not know how to mount hard drive using this live cd. I would like to try to rescue rather than do fresh install  :)
Thanks

---

### Post by srt4play on 2007-07-26
What graphics card do you have?  The command to reconfigure X is

sudo dpkg-reconfigure xserver-xorg

But that needs to be executed from the "broken" system not from the live cd.

---

### Post by Archmage on 2007-07-26
> **srt4play said:**
> What graphics card do you have?  The command to reconfigure X is

sudo dpkg-reconfigure xserver-xorg

But that needs to be executed from the "broken" system not from the live cd.

So he should boot, wait till he sees the "x-server failed", than press CTRL+ATL+F1, log in, and than type in the command.

---

### Post by srt4play on 2007-07-26
Yeah, the CTRL-ALT-F1 is not necessary, saying no to the xserver log being displayed will drop you to a CLI, but those would be the steps.

---

### Post by DougieFresh4U on 2007-07-26
> **Archmage said:**
> So he should boot, wait till he sees the "x-server failed", than press CTRL+ATL+F1, log in, and than type in the command.

Thanks for all the replies, made me feel good about the whole situation.
when I boot and eventually it brings me to a login of some sort, I enter my user name and password when prompted but it does not accept my password. 
It is my understanding, that in order to reconfigure x using command, I need to boot and get to grub menu and go to command line from there, is this correct? Once I'm sure of this I shall leave live cd and attempt reconfigure x. also I should just go with default configuration and just hit enter as I go through the x reconfigure. Thanks every one!!

---

### Post by DougieFresh4U on 2007-07-26
Ok, I have managed to reconfigure x. I am using live cd again as when i boot machine I can see Ubuntu and progress bar move then screen goes black BUT I can here login screen come up but can not see it. So for the heck of it I type my user name and password. I can HEAR it go to desktop (I hear the start up jungle music) but I can not see any thing on screen So I do know that my reconfigure of x was some what successful :) But I have not a clue as to why screen goes black out during the start up before login screen. When I put live cd back in and boot all is seen. Can some one please tell me what is happening?
Thanks to all replies as they did help.

---

