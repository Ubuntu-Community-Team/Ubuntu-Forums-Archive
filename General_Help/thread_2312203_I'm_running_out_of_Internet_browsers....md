---
title: "I'm running out of Internet browsers..."
date: 2016-02-02
forum: General Help
---

### Post by simple_impulse on 2016-02-02
Okay. I'm running two PCs with 12.04 LTS (one 64-bit, one 32-bit) with very good reasons. They are working fine. 

But now Firefox, which I have used so many years has become very unstable. Newest version crash way too often, usually in critical places (i.e. money involved...).

Then Chrome, which has worked quite well lately, announced it will not work in this system any more. I guess that includes Midori, Epiphany and Opera also stop working, because they all use Webkit.

What options I have? I know everybody says "upgrade" in chorus, but that would mean six-seven week work (believe  me, these machines are loaded with stuff and if the commercial ones stop working, it's huge loss for me...) Maybe I will have time to go through that hell during summer.

Hopefully only option is not through Wine or, even worse, dual boot or virtual machine solution.

But now I need a new browser. Any ideas?

---

### Post by Vladlenin5000 on 2016-02-02
You're misunderstanding what has been announced by Google. They're dropping support for 32-bit OS only and that affects their product (Chrome) only. Chromium, the open source base for Google Chrome will still get builds and updates for 32-bit. Ditto for all the others you mentioned.

Regarding Firefox some troubleshooting may be helpful. What requirements have those "critical places" where FF is allegedly crashing? Java, Flash, ...?

Regarding your systems... Upgrade definitely. You don't need to do it now and you shouldn't do it in a hurry but you'll haver to eventually because you have +/- 1 years of support left for 12.04 so... If I were you I would start right now testing live 14.04 LTS (and, in April, 16.04). By "live" I mean in a live session without actually installing.

---

### Post by simple_impulse on 2016-02-03
Thanks for reply! Those sites crashing Firefox are media-intensive, like Facebook, YouTube and so on. But for some reason also some PayPal functions crash too. I've patched FF. YouTube is now handled with separate add-on, it works mostly. There was some crashes with sound play (mostly due to Sound Cloud widgets). Also for Facebook I have some success with a fix (media.fragmented-mp4.enabled set to false). However there are way too much problems.

I guess the 32-bit support with Chromium and it's relatives is good news, however I'm a bit worried if the Google base goes to unportable direction... It feels funny that we only have so few Internet engines.

I'm definitely updating, but with this workload and this amount of stuff to update and upgrade, I feel a bit afraid. These systems have had already several Ubuntu versions before 12.04 LTS. If I could afford, it would be easier to buy new PC boxes and go gradually. But with current amount of income, impossible.

---

### Post by mörgæs on 2016-02-03
If you have the space you could create a new partition and install a later version here, giving the option to move your stuff step by step.

---

### Post by simple_impulse on 2016-02-03
Partitioning could be possible... It could be even possible to add a new hard disk drive to one machine. A possibility.

However, I'm still open if someone knows other usable browsers. I heard about someone who was in original Opera team making a new engine, but otherwise it seems strange that we have only Mozilla and Webkit-based browsers? (Microsoft and Apple browsers are not an option to Linux users.)

---

### Post by cholq on 2016-02-03
When I was getting frustrated with FireFox, I switched over to PaleMoon.  It is based on the same Mozilla code, so it is very similar, but it just seems a little quicker than FireFox did.  And, since it is based on the same Mozilla code, some of the FireFox extensions you are using may still work on Pale Moon.

---

### Post by mörgæs on 2016-02-04
> **simple_impulse said:**
> 
However, I'm still open if someone knows other usable browsers. I heard about someone who was in original Opera team making a new engine, but otherwise it seems strange that we have only Mozilla and Webkit-based browsers? (Microsoft and Apple browsers are not an option to Linux users.)

Using Buntu you have an excellent selection of browsers. In contrast, Apple is more or less squeezing out everything but their Webkit based Safari.

---

### Post by simple_impulse on 2016-02-04
Good call, that Palemoon! Much stabler than Firefox and got (with pepflash) Flash 20.x support! I'll test drive for some time, but this might be just what I was looking for! Thanks!

---

