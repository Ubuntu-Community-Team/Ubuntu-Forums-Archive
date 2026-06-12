---
title: "How did my Ubuntu get so crippled?!"
date: 2007-09-26
forum: General Help
---

### Post by DAE_JA_VOO on 2007-09-26
My regular Ubuntu Desktop looks like this:

[IMG]http://i29.photobucket.com/albums/c267/DAE_JA_VOO/more2/newscreen2.png[/IMG]



But tonight, when i logged in, it looked like this:

[IMG]http://i29.photobucket.com/albums/c267/DAE_JA_VOO/more2/wth.png[/IMG]



This is now the second time that this has happened in the last 3 days. Restarting doesn't help. The first time it happened, i just booted into windows and used that, and then a few hours later, when i came back into Ubuntu, it was fine again. Now i sign in and i see this crap. 

It doesn't even detect my other HDDs.

What the hell is going on here?

---

### Post by Skerit on 2007-09-26
First of: that's quite a nice desktop.. err, when it works of course (don't want to rub it in, though :)) Very clean (my desktop usually looks like a war-zone, like that windows-wars skit)

anyway, I'm afraid we're gonna need a bit more data to get you on your way ... 

You say it doesn't even detect your other HDDs, did you see any special notices on boot-up? Can you access your other drives in nautilus, or no luck there, too?

---

### Post by rsambuca on 2007-09-26
That has happened to me in the past when there were errors mounting certain hard drives during the boot process.  It is quite strange that it comes and goes though.  I might be a little worried that one of your drives is failing.  You might also want to check for loose cables inside your rig.

---

### Post by DAE_JA_VOO on 2007-09-26
Thanks for your compliment :)

It doesn't pick up my disks at all, as if they're not plugged in. No difference in bootup whatsoever. 

I can access other drives, yes, but not the two that have EVERYTHING on them.

---

### Post by DAE_JA_VOO on 2007-09-26
The odd thing is that i never have this issue in XP, ever.

---

### Post by Prefader on 2007-09-26
What happens if you try to mount the drives after boot up?  Try opening a terminal and type ```
sudo mount -a
```.  Post the output from that here.  It might also be worth checking the output from ```
dmesg
``` for any errors.  Those are the first two places I'd look.

---

### Post by Skerit on 2007-09-26
Oh wait ...

Do you access your ext partitions INSIDE windows? Or did you shutdown windows in any "unproper" manner?

Sounds idiotic, but it does matter.

I used the ext2fs tool to access my drives in windows but because it's such a fragile thing windows "corrupted" a few stuff when I failed to shut down in a proper way. 

If this IS the case, the easiest fix is to go back to windows, see if you can get on the drives there, and then shut down the *right* way. Everything should be fine.

You can also check your disks in linux but that'll take a while ...

---

### Post by DAE_JA_VOO on 2007-09-26
I dound the problem guys :D

I didn't shutdown (in windows) properly, so the disks had an "unclean record". Why the hell is Ubuntu so iffy about crap like this?

Needless to say, it's back to normal now. Thanks for your help :)

---

### Post by Skerit on 2007-09-26
Hehe, I thought so...

But was it your ext2 partitions or not?

I do believe, eventually, it's a good thing that linux behaves like this. Ofcourse, when the problem occurs you'd think "what the hell is this" (a bit more communication with the user wouldn't hurt) but it's a small price to pay for the safety of your data :)

---

### Post by strabes on 2007-09-26
[QUOTE=DAE_JA_VOO;3431498I didn't shutdown (in windows) properly, so the disks had an "unclean record". Why the hell is Ubuntu so iffy about crap like this?[/QUOTE]

You shouldn't be storing your data on an NTFS partition in the first place.

---

