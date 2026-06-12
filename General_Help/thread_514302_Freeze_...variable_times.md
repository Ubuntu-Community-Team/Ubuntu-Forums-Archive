---
title: "Freeze ...variable times"
date: 2007-07-31
forum: General Help
---

### Post by newbun on 2007-07-31
Hi everyone




My reasons for seeking comprehensive diagnostic tools are that (at the moment) my AMD Athlon 1.15 ghz, 750mb ram, 40gb hard drive, machine is a bit temperamental as to WHEN it freezes.
My main PC is a laptop, but to try out UBUNTU (i'm liking it.....so far) on a machine that was just sitting there wondering whether to go the Vista route, or what.

Sometimes the desktop is up for a couple of hours - no freezes. Other times - its minutes. Can't pin down what's causing it. I've loaded an old copy of Windows xp (home edition), and it does the same with that - so it's not just picking on Ubuntu.

So, what I need is a diagnostic that pins down the reason....so I can fix it, and get on with this alternative to Windows.

I've tried all the suggestions, and am currently using the 'bootcd' diags for clues.....

Hope to hear some other suggestions (not im-sensors)

Thanks

---

### Post by AlexThomson_NZ on 2007-07-31
In my experience, most hard locks are caused by faulty ram modules, have you tried running memtest?

Does this happen when using XP under load?

---

### Post by figgles on 2007-07-31
Yep -- memtest is a must. You might also run sudo touch /forcefsck and reboot but I dobut that's the issue.

---

### Post by newbun on 2007-08-01
Funny you should say that AlexThomson_NZ' and 'figgles', I ran MEMTST on 2 occasions.  First it ran for over an hour, during which time I was looking for SOME error message....but then, it also just, hung.   So, as I'm new to UBUNTU will MEMTEST show up some sort of error?  It should if its call memtest?

It's an interesting point, as I've just (before installing Ubuntu) slotted in an extra 512 mb of ram - trouble is, I don't know if it's the original 256 bank, OR, the new 512 bank.  I checked that the new bank is the right kind of memory for my machine.

So, how do I know (if it IS the ram) which bank is causing the FREEZE??

Hope you guys are right, as it's getting to the annoying point..:(

Thanks - hope your suggestions don't dry up, as I've seen in other posts

---

### Post by AlexThomson_NZ on 2007-08-01
Can't really think of any reliable way, other than to swap the ram in and out and find the faulty one by trial and error.

Might be worth splashing out for a 1GB mem card anyway, you'll notice the difference

---

### Post by newbun on 2007-08-01
Well done guys !!  AlexThomson_NZ ,  I did exactly that - first swapped out the new bank of 512, and ran with the 256.  Sure enough, as soon as I booted up and connected to the net, it  'froze' in about 5mins flat.

So, out came the 256, in went the 512.....10mins.... an hour.....2 hours.....3 hours....ok, enough test surfing for now.  IT WORKED!!!    Thanks again for pointing me in the right direction.

I'll certainly step to to 1gb, when I've put Ubuntu through it's paces.

---

### Post by newbun on 2007-08-06
Oh No!!  what's happening....thought I had it fixed !!!!

HELP!!!   As you see from my posts above, I've been through this before.!!!


Before the current set of updates (Sat 4th Aug) I was running fine, with Feisty 7.04, but SINCE the updates, I ALSO noticed that the system is freezing at different points: whilst booting, whilst surfing between 5 and 30mins.  Sometimes even before I connect to the net via the ethernet cable.

I have an amd athlon 1.15 ghz, 40gb drive and 512mb ram.  My laptop connects wirelessly via xp, but the desktop (via cable to router) is having this recent problem.

The system is not freezing at any particular point, it's completely random. - screen freezes, mouse inactive, keyboard locked out - nothing responds until I do a power off, power on.

Can anyone tell me whats going on?  Any other on the forum having freezing problems, since the latest update of Feisty (Sat 4th Aug)??

Thanks

---

