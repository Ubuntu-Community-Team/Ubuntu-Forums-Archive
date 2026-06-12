---
title: "I see lots of people with my problem but no real solution for why Modelines not read"
date: 2008-05-12
forum: General Help
---

### Post by dragonopolis on 2008-05-12
HP a530n -

AMD64 3200+ with Nvidia FX5200XT

Monitor - Optiquest V95

Been awhile for playing around in Ubuntu thought I check out the new LTS.  Problem

I have my modeline placed in the appropriate section of my xorg.conf file but the X log shows that Ubuntu just ignores the modeline and skips right over it.

I check the x logs ubuntu is looking at xconf file and not the failsafe

I am not running any 3d drivers.

I am not using vim (supposedly there was a modeline issue)

I do not have xserver-xgl installed as that seem to cause issues as well.

My modeline is save appropriately and should work but doesn't.


dpkg reconfigure xserver-xorg comand runs at first but kicks me out at the video configuration with a warning at the command line that it was trying to overwrite a auto-configuration. I guess I can't do that.

How do I gain control of my hardware thank you.  Xorg change quite a bit in the last year or two and it is definitely implemented differently in Ubuntu compared to other distros even debian based ones.

The logs does state Ubuntu is getting its information from my xorg file but seems to be skipping the modeline when loading

Can't use Ubuntu if my screen is jacked up. Also this auto configuration seems to mess up my ability to dpkg reconfigure as well.

Please Help and respond plus I'm sure there a plenty who would like a definite whats going on.

I did try to do a search but did not come up with any specific answers to the topic or solutions that matched mine (I am not running any fancy drivers or compositors).

So if it has been answered I apologize but please post the link to the solution

Modeline will fix it my monitor woes just need Ubuntu to see it.

How do I get Ubuntu to use it.

very frustrating.

---

