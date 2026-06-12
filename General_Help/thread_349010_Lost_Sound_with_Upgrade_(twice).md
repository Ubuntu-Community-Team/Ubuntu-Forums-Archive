---
title: "Lost Sound with Upgrade (twice)"
date: 2007-01-29
forum: General Help
---

### Post by KrazyPenguin on 2007-01-29
I just did a fresh install of Edgy a couple of days ago on my new laptop.

I had sound on the live cd and I had sound after installing.

Then I did an upgrade, did a reboot.  When I tried to play some music , i had no sound!!!

I read the sound guide and fixed the problem by unstalling and reinstalling the also packages.

After rebooting , LET THERE BE SOUND!!!

Then there was another upgrade today, and I lost sound again. 
So I went back to the guide, copied and pasted the lines, rebooted,
AND LET THERE BE SOUND again!!!!

So it seems upgrades are causing the problem.

Does anybody know why???
It seems somebody filed a bug.

sound driver: hda-intel

Thanks

---

### Post by Puschkin on 2007-01-30
Do you have multiple soundcards in your laptop?

If so: Ubuntu sometimes swaps the device names (I think it depends on in what order ubuntu loads the kernel modules)

try the following:

```
sudo asoundconf list
```

It will provide you with a list of available soundcards, then do

```
sudo asoundconf set-default-card YOURSOUNDCARD
```

and reboot for test.

maybe it helps

Greets,
Puschkin

---

