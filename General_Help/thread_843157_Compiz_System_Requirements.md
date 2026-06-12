---
title: "Compiz System Requirements"
date: 2008-06-28
forum: General Help
---

### Post by 786souljah on 2008-06-28
This could turn out to be a lame question however with some searching resulting in no answers, I come to the forums.

I am currently in the process of backing up old windows documents to fresh install ubuntu linux 8.04. Now... I know the install will work well with linux running perfectly as I've tried the LiveCD already. Here's the old junk it'll run on:

IBM Thinkpad T23 Laptop (No built in wireless)
CPU: 1.13Ghz
HD: ~30GB
RAM: 512MB

Thats probably the most important information. Here's the deal though, I'd like to apply some nice effects like transparencies and the like to the ubuntu interface and wonder, is my hardware reasonable to run it? I'm not looking at the cube or anything I KNOW will need a 3D card etc, just the nice simple things. Will this still be too intensive for the laptop ill be running ubuntu on? 

Thank you very much for the help, and sorry in advance if this has been gone through already, my forum search skills must be lacking. Thank you once again!

---

### Post by overdrank on 2008-06-28
> **786souljah said:**
> This could turn out to be a lame question however with some searching resulting in no answers, I come to the forums.

I am currently in the process of backing up old windows documents to fresh install ubuntu linux 8.04. Now... I know the install will work well with linux running perfectly as I've tried the LiveCD already. Here's the old junk it'll run on:

IBM Thinkpad T23 Laptop (No built in wireless)
CPU: 1.13Ghz
HD: ~30GB
RAM: 512MB

Thats probably the most important information. Here's the deal though, I'd like to apply some nice effects like transparencies and the like to the ubuntu interface and wonder, is my hardware reasonable to run it? I'm not looking at the cube or anything I KNOW will need a 3D card etc, just the nice simple things. Will this still be too intensive for the laptop ill be running ubuntu on? 

Thank you very much for the help, and sorry in advance if this has been gone through already, my forum search skills must be lacking. Thank you once again!

Hi and I have a Acer laptop with 512 mb of memory and intel graphics and compiz runs nicely with Gutsy 7.10. I have a desktop with the intel graphics 32 mb dedicated and it uses the desktop effects but it is a little slow. :)
The point being that is depends more on the graphics in my opinion.

---

### Post by 786souljah on 2008-06-28
Ah I see. Even with little additions like a transparency, would there be a large slowdown in terms of speed?

Also, lets say I'm dual-booting leaving Ubuntu with only 10 or 15 GBs of HD rather than wiping windows; would it affect compiz much? (I'm still one of the newbie migrators from windows so i'd like to keep it just incase i leave myself with no working OS :P)

---

### Post by overdrank on 2008-06-28
> **786souljah said:**
> Ah I see. Even with little additions like a transparency, would there be a large slowdown in terms of speed?
Hi and I did not say that, I mean it depends on the graphics card and the amount of memory dedicated to the graphics. :)

> Also, lets say I'm dual-booting leaving Ubuntu with only 10 or 15 GBs of HD rather than wiping windows; would it affect compiz much? (I'm still one of the newbie migrators from windows so i'd like to keep it just incase i leave myself with no working OS :P)

Should have no effect as that is partitioning the hard drive and not effecting resources of the system as far as graphics.

---

### Post by 786souljah on 2008-06-28
Thanks a bunch! I guess I'll just install it and see how it runs. If it bogs the system down too much or doesn't run smooth i'll just remove it and that'll be the end of that =)

---

### Post by Kevbert on 2008-06-28
What video card are you using ?  You can see if compiz will run by using [compiz-check]("http://forlong.blogage.de/article/pages/Compiz-Check").

---

### Post by Forlong on 2008-06-28
Yeah, in fact, you left out the most important part in the hardware specs: the graphics chip.

And I'm afraid, it seems like all (?) [T23]("http://www.thinkwiki.org/wiki/Category:T23") came with a S3 -- which would be really bad in terms of Compiz.

---

### Post by 786souljah on 2008-06-28
I looked at my system information but it doesn't give information about a graphics chip. And well i guess if it is the S3 Super Savage which is with the t23's then I'm stuck? LOL, I knew it's an old laptop so i couldn't expect too much from it, just thought I could pump a little more out of it.

**EDIT**: Also, why is it that the S3 isn't too compatible with compiz; I read about a bug of some sort or has that been fixed but still doesn't have the 3d accelerators to do the job?

---

### Post by Forlong on 2008-06-28
Argh, sorry about the double post.

---

### Post by Forlong on 2008-06-28
> **786souljah said:**
> I looked at my system information but it doesn't give information about a graphics chip.
You can use this to check: [http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)
> **786souljah said:**
> Also, why is it that the S3 isn't too compatible with compiz
Because the people of S3 think Linux suck and did not support it properly.
> **786souljah said:**
> I read about a bug of some sort or has that been fixed but still doesn't have the 3d accelerators to do the job?
Things may have improved. S3 has been bought by VIA which is itself in the process of sucking less in terms of Linux.
There are also open source people who try to reverse engineer drivers.

So there might be a chance Compiz will work on your laptop (sometimes).

That is one of the reasons I wrote Compiz-Check. It will tell us what the chances are.

---

### Post by 786souljah on 2008-06-28
That's great! I just went to your blog explaining the script and all and it might work to tell me what i need. After I install ubuntu i'll be sure to get the script installed and see what it tells me.

---

### Post by hendoc on 2008-06-28
Google for a thing called "Compiz-check". Make it executable and run it and it will give you a checklist of 5 or 6 parameters and tell you if they are up to par for running Compiz Fusion.

---

### Post by 786souljah on 2008-06-28
Alright well i spend the afternoon getting the dual-boot up and running and here I am on ubuntu. All the upgrades completed (205 of them) and I decided to run that script and see how it'd fair out; heres the results: 

> Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         S3 Inc. SuperSavage IX/C SDR (rev 05)
 Driver in use:         savage
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [FAIL]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [WARN]

Something potential problematic has been detected with your setup:
 Warning: Detected driver is not on the whitelist. 

Would you like to know more? (Y/n) y

 Your driver is not widely known to work with Compiz and thus may be
 blacklisted on certain distributions.

 You can skip this blacklist -- but keep in mind that you did so.
 Do not complain if you encounter any problems with Compiz afterwards. 

Do you want to skip blacklist checks by Compiz? (y/N) y


I guess this basically shows I won't be able to run compiz well or at all even seeing as I fail in one part and am warned in another?

---

### Post by Forlong on 2008-06-28
Yes, I'm afraid that's the case.

---

### Post by 786souljah on 2008-06-28
LOL okay well thanks for the help, I'm glad at least now I know about that script to try out, which by the way is great and simple. Thanks again!

---

