---
title: "Trouble... cannot boot to anything"
date: 2008-05-03
forum: General Help
---

### Post by shrodes on 2008-05-03
Hi, so I thought I'd give this Ubuntu thing a try after reading a bit and hearing of the new release.

Couldn't be bothered waiting for a partition resize, so I thought I'd try out Wubi, off the Ubuntu .iso

Worked great, could boot into Ubuntu first shot, but then when I went to get back into Windows, I got a black screen. No hard drive activity, nothing.

So, reading a bit, I've tried most, if not all of the recommendations, fixmbr, fixboot, chkdsk /r, etc.

None of them are working. So then, stupidly, I edited my boot.ini file to take the Wubi line out, so now I can't even get into that.

And I've been trying desperately for the last 3 days to boot into Windows. I realise now, that probably won't be an option, so I'm really just trying to find a way to get my files off my HD (I can still access them OK).

I have an external hard drive that runs off Firewire or USB, but I can't access that through any boot methods (tried copying with programs on Hiren's Boot CD), and even booting into temp. Ubuntu from the CD won't let me mount the hard disk, because it wasn't 'safely ejected' from Windows. GREAT.

I'd be much obliged if anyone had any ideas on where to go next, I'm fine to reformat once I get my files off, I just need a way to do that.

I'm running a Dell Latitude D400, 512MB RAM, and I was running XP SP3 before all these problems arised :(

---

### Post by tinybit on 2008-05-03
Could it be SP3 who caused the failure? I suppose SP3 would create many more incompatibilities and nothing else.

Don't mind if it is not the case. I just want to help you to find out the possible reasons why it fails.

---

### Post by shrodes on 2008-05-03
Well, I should probably mention a few more things...

Scandisk did nothing. Every time I run it (from my XP CD - XP SP2 CD, that is), it gets to 25%, stops for a long while, keeps going slowly until 75%, goes back to 50% then finishes. Sometimes, it tells me there is an unrecoverable error, and that Scandisk can't run.

I should also mention that my hard drive was pretty heavily fragmented before I installed Wubi, which probably wasn't a good idea to begin with.

I did read somewhere that fragmentation can affect the boot partition, but given I have no way of getting into Windows, I can't actually defrag it now anyway (unless someone knows of a bootable method?)

Thanks for the reply, though I'm not sure whether it is or isn't SP3.

---

### Post by tinybit on 2008-05-03
You may try fixing it by booting off the XP installation CD.

You can select to fix it, or install it once more onto the previously installed drive and dir(don't change them), which could also fix the problems.

---

### Post by shrodes on 2008-05-03
Ah, forgot to mention I did this too. I booted my XP CD, then went through the repair process which only made another problem... next time I booted it told me a ntoskrnl.dll or something similar was missing or corrupted.

So I booted the recovery console, copied that off the CD onto my HDD, then I'm back to square one with the black screen and nothing else.

Trying an XP USB edition now to try and get my files off.

---

### Post by tinybit on 2008-05-03
> 
install it once more onto the previously installed drive and dir(don't change them), which could also fix the problems.


Have you tried this one? If not, you may try it. Of course it is better if you get your files out before the install.

---

### Post by shrodes on 2008-05-04
Hmm, not sure what you mean... I can't Wubi it again, cause I can't get into XP.

And the only option I can see to install Ubuntu is to write over my existing partition. That said, I am a bit of a newbie to this whole franchise, so let me know if I'm missing something.

---

### Post by tinybit on 2008-05-04
By
```

install it once more onto the previously installed drive and dir(don't change them), which could also fix the problems.

```

I mean you could use your XP SP2 CD to "upgrade" your current Windows SP2. The "upgrade" won't destroy anything in your current system, but can repair the lost system files.

---

### Post by shrodes on 2008-05-04
[QUOTE=shrodes;4875168]Ah, forgot to mention I did this too. I booted my XP CD, then went through the repair process which only made another problem... next time I booted it told me a ntoskrnl.dll or something similar was missing or corrupted.
[QUOTE]

So yeah, I did this 'upgrade' process. To no avail, unfortunately.

I've managed to boot into a flash drive running a modified Windows, so I can now copy to my external HD.

I guess I'll just reformat now. Not the most desirable solution, but the only one under the circumstances I guess... thanks for your help (and wish me luck with my new Ubuntu PARTION :))

---

