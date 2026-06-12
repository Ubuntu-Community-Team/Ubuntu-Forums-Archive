---
title: "k3b only copies/backs up using DUAL LAYER DISCS"
date: 2007-06-19
forum: General Help
---

### Post by GMachine_24 on 2007-06-19
Ok, first, I am completely frustrated. I have attempted for several months - on and off - to find a way to burn my music collection (65GB more or less) onto DVDs. I already have two hard drive back ups so I don't need a third. I do, however, need a backup that is not subject to power surges, burglaries, etc. I've tried with Edge Eft and the version before this one whatever that was called - Dapper Drake I guess.

To that end, I have attempted several programs; gnomebaker, graveman, and the much ballyhoed k3b.  k3b appears to be the only one capable of a multisession DVD back up - however with the warning the program spits out about how many / most / all? multisession DVDs CANNOT be read by most DVD players/burners/etc. I have my doubts. If something doesn't work, they should just come out and say: "It doesn't work. Don't waste your time."

I remember six months ago or so there was a CD burning problem with k3b. I guess someone fixed that. But if you attempt to make a multisession DVD back up you will come to a message that says you need to insert a dual layer blank DVD in your DVD burner - whether or not your DVD burner is single/double/triple/quadruple layer compatible.

ALL THE 'FIXES' I'VE READ DON'T WORK.

I am looking for a real answer to this problem. If you choose that your disk is 4.7 (really 4.4 gb in k3b) it doesn't matter; the computer will accept the setting and then when you hit 'burn' you will still be asked for a dual-layer DVD.  I have many dual-layer DVD burners. However, I do not have any dual-layer disks. They are expensive and I don't - with this one exception apparently - need them. And, there is no reason why k3b should not be able to record a single-layer disk.

I searched numerous, numerous Web sites, posts, threads, subjects, k3b installation guides etc. and tried whatever I could and still wound up where I began. My final effort was to remove an older, single-layer DVD burner from the computer I'm typing on now, install it in the offending Ubuntu computer with k3b software and, sure enough, even though the DVD writer is not compatible with dual-layer disks - and even though k3b software shows under its configuration that it KNOWS the dvd burner does not 'do' dual layer disks....  it still asks for a dual layer disk and says it can't write to the one in the drive.

This occurs with DVD +, DVD - , name brand, generic, new, old, whatever you like - I would love to hear from someone - ANYONE - who has found a fix for this. I installed extra software, removed current versions of  various packages upon the advice of yet another genius on the Internet and, surprise surprise, nothing changed.

So, there. That felt pretty good to get that off my chest. I worked at this for more than four hours today and don't plan on spending any more time on it unless someone can give me an answer they know works because they've used it themselves.

Sorry if I seem abrupt and annoyed - but I am.

gmachine

Oh, just to cover the bases, I tried to back up the music file to CDs - k3b wrote one 700 mb disk and spit out a bunch of error messages suggesting I try TAO (track at once, I presume, not, like, the Tao of Physics.)

---

### Post by kuja on 2007-06-19
K3b is MASSIVELY improved in Kubuntu 7.04. Especially with regards to dealing with things like multi-session DVDs. I definitely recommend giving it a try.

Oh, also, as per the 4.4 vs 4.7 thing:

4.4 GiB = 4.7GB. 

4.4 GiB = 4.4 * 2 ^ 30
4.7 GB = 4.7 * 10 ^ 9

---

### Post by GMachine_24 on 2007-06-19
thanks for your post. it's funny, i have avoided upgrading versions unless absolutely necessary because my first upgrade (from breezy to whatever) was a disaster. so i've kept to just updating current versions as long as they work.

i'll d/l kubuntu 7.04 and give it a whirl. it can't be as painful as anything i did today.

yeah... i understand the 4.4 / 4.7 gb thing. it was just one more thing to annoy me today and i still wonder why someone hasn't posted a fix for k3b and edgy but hey if they don't care... why should i?

i'll post results of my latest foray.

[as an aside, one reason i am so perturbed is that four of my computers decided to start disintegrating at roughly the same time - i think it's because of all the power surges we get that zap the hardware and my surge protectors and battery back ups probably need replacing. i've had hard drives, memory, mbs, monitors .... etc. go bad in the past two weeks. it's been a little overwhelming]

thanks again.

gmachine

---

### Post by GMachine_24 on 2007-06-24
Hi:

Ok, so, .... I loaded the computer with Kubuntu 7.04 Feisty Fawn ... updated everything and still cannot do a multisession back up using Kubuntu - I get the same message to insert a dual/double--layer blank DVD - even though, once again, the DVD burner in the computer is a single-layer drive.

Perhaps my problem is that I just don't know how to do a multisession back up - at least not with Linux. I'm accustomed, when working with another OS whose name shall not be mentioned, to just dragging/dropping/marking whatever I want to back up in the DVD burner software and the burner automatically burns what it can per disk until all data is copied. The only thing I have to do is add a blank DVD now and then when the previous one is full.

I can, and do, use K3b to back up data to a single disk - 4.3GB or less... whatever. That works fine. It's projects above single-disk capacity that I can't seem to manage.

Any ideas are apprediated.

---

### Post by kuja on 2007-06-25
... Perhaps you're misunderstanding what multisession does. Multisession means that you can burn things to the disk once, then, in another session, update removing/modifying/adding things. I don't think it'll handle using more than one disk. 

:rolleyes:

---

### Post by GMachine_24 on 2007-06-25
Hi:

Thanks for your post. I kind of came to the conclusion that I was thinking multisession is one thing when in fact it's just being able to add data/music whatever to an existing project/disc.

So, I guess I'm back to just backing up to external hard drives - which is very simple and works great - I'd just hate to lose what has taken me years to gather because of a hurricane or some other thing . . .

Anyway, thanks for your help. I like Kubuntu - I'm looking forward to trying out the OCR software that comes with Feisty. I hope it actually works......

Take care.

---

