---
title: "Login Screen to Desktop taking a while in Gutsy"
date: 2007-11-12
forum: General Help
---

### Post by shavenlunatic on 2007-11-12
Hi,

Since upgrading to Gutsy (did an upgrade AND a clean install after that but it didn't rid me of the problem) I seem to have a long wait between logging in and getting to my desktop.

We're talking nearly 20 seconds, used to be probably about 5 seconds in feisty.  It basically sits on a completely blank screen with the default "Human" color (which is also an annoyance as I have changed the background color several times in various places and it STILL persists to default to the Human color.. but if I remove my wallpaper it appears as my chosen color!? strange, don't know if it's related but thought I'd mention it).

POST => Grub and Grub => Login Screen are both reasonable fast.  I haven't installed a shedload of software which will run at startup (clean install) and it still happens.

AWN is installed, I didn't have this issue in Feisty and I don't think it loads until late in the process anyway so I don't 'think' its AWN causing the problem (but I haven't tested running without it, silly me, i promise to as soon as I get home)

It's late in the day and I've ran out of Coffee so apologies for bad grammar, terrible sentance construction and any typos (and lets be honest, even on a good day I am below average!)

Thanks in advance :)

---

### Post by reckless2k2 on 2007-11-12
it's most so because of compiz default setup. try disabling desktop effects completely. that might help.

---

### Post by shavenlunatic on 2007-11-12
hmm could be.. 

i don't use many desktop effects but I do like expo and one or two other little things.. so I'd rather not totally disable compiz (for one thing, AWN requires it)

If there any way to get a terminal output of what is happening, and when it's happening while it's logging in? So maybe I can see for definite which items may be causing the delay

---

### Post by reckless2k2 on 2007-11-12
from terminal you want to issue

```
ps aux
```

but i'm not sure on how during login. maybe someone can chime in. do you have mount points to network drives in fstab that might be causing the slowdown as well?

i was asking you to disable compiz temporarily just to see if that was the link.

---

### Post by shavenlunatic on 2007-11-13
> **reckless2k2 said:**
> from terminal you want to issue

```
ps aux
```

but i'm not sure on how during login. maybe someone can chime in. do you have mount points to network drives in fstab that might be causing the slowdown as well?

i was asking you to disable compiz temporarily just to see if that was the link.

The PC isn't on a local network so no slow mounts.

I will disable compiz tonight to test the speed, if it does end up being Compiz being the issue, do we know if there is a fix for it? (other than downgrading back to feisty)

but as mentioned, if anyone could provide a way of viewing "real time" terminal scrolls of what processes are running, it would be greatly appreciated

---

### Post by reckless2k2 on 2007-11-13
well i know a way it can be done somewhat but i'm not sure it would be easy for you. don't mean to be rude at all. i'll briefly explain in overview.

you would switch over to another terminal and login as normal but then sudo ps aux to start the process veiwer. i just can't remember how to push the output to a file in real time while you flip back to other terminal and log into your GUI as regular user. since you say it's slow, you can flip back to the other terminal and view the ps output though to see what the hog is. 

i'd be surprised if it wasn't compiz. i don't know your vcard but there is a setting somewhere that i forget to offload video to the vram/processor rather than the regular processor. that's probably the only way to circumvent the slow down if that's the issue. or upgrade the vcard with more ram.

---

### Post by shavenlunatic on 2007-11-13
> **reckless2k2 said:**
> well i know a way it can be done somewhat but i'm not sure it would be easy for you. don't mean to be rude at all. i'll briefly explain in overview.

it's ok, you can never be sure of someone else's level of knowledge or intelligence.  Best to be safe than sorry. (fairly new to linux, but been working with computers all my life)

> 
you would switch over to another terminal and login as normal but then sudo ps aux to start the process veiwer. i just can't remember how to push the output to a file in real time

wouldn't
```
sudo ps aux >> temp.txt
``` work?

> 
while you flip back to other terminal and log into your GUI as regular user. since you say it's slow, you can flip back to the other terminal and view the ps output though to see what the hog is. 

either way, i'll give this a go now


> . i don't know your vcard Nvidia 7600GS (512MB DDR2)


going to have a go now.. thanks for the advice so far :)

---

### Post by reckless2k2 on 2007-11-13
well your vcard should not be the hangup then. that really blows the whole thing out of the water considering your vcard specs. i wouldn't be surprised if it was the "buggy" compiz but you will see. i know i have a 256MB PCIe nvidia and had similar buggy issues with compiz. i completely turned off desktop effects and have been fine since. 

"real time" output wouldn't be using that command. that's static at the point. only thing i can think is get to a gui desktop on the other console like fluxbox and pop open the terminal along with istanbul to record it. then flip over to the other console with GDM and start it. 

you can just be a fluxbox convert and rule out the slowness. hahaha. flux grows on ya. hahaha.

---

