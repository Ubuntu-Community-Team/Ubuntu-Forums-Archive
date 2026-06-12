---
title: "K9Copy Error"
date: 2015-12-22
forum: General Help
---

### Post by Darth4212 on 2015-12-22
When I try to rip the DVD it gives me the error: Unable to run mencoder.
What is exactly is mencoder and if it is a program how do I install it. I am running Ubuntu 15.10

---

### Post by Vladlenin5000 on 2015-12-22
Well, as I said in your other thread, there are reasons for a given software to be deprecated. Unsatisfiable dependencies is one of them. 
May I suggest you use HandBrake instead? You don't want to be burning DVD-Video in 2015, do you? ;-)

---

### Post by Darth4212 on 2015-12-23
Wait what do you mean> You don't want to be burning DVD-Video in 2015, do you?;) I'm confused?

---

### Post by Vladlenin5000 on 2015-12-23
I mean, your goal is to backup some (video) DVDs you already own, right? Copying them to another DVD - the purpose of K9 - is soooo 2005.
HandBrake can backup all your DVDs in small MKV or MP4 files.

---

### Post by cbraxton on 2015-12-28
> **Vladlenin5000 said:**
>  
May I suggest you use HandBrake instead? You don't want to be burning DVD-Video in 2015, do you? ;-)

I can't speak for the OP, but I do continue to burn DVD video in 2015 and will continue to do so for years to come! \\:D/  Handbrake does the opposite of what I need.

---

### Post by lisati on 2015-12-28
> **cbraxton said:**
> I can't speak for the OP, but I do continue to burn DVD video in 2015 and will continue to do so for years to come! \\:D/  Handbrake does the opposite of what I need.
Likewise. Some of the people I know are still getting used to the idea of using DVD instead of tape.

---

### Post by cbraxton on 2015-12-29
> **lisati said:**
> Likewise. Some of the people I know are still getting used to the idea of using DVD instead of tape.

We still use tape as well, it is convenient for time-shifting broadcast TV shows. In fact I have such a time-shifted show playing on VHS tape right now. ):P

I know many if not most people have switched to just viewing mp4 or avi files or whatever, but with our old TV sets we still use DVD on a regular basis and that is not likely to change any time soon.

---

### Post by lisati on 2015-12-29
> **cbraxton said:**
> We still use tape as well, it is convenient for time-shifting broadcast TV shows. In fact I have such a time-shifted show playing on VHS tape right now. ):P

I know many if not most people have switched to just viewing mp4 or avi files or whatever, but with our old TV sets we still use DVD on a regular basis and that is not likely to change any time soon.

I switched from VHS to DVD for stuff I've recorded on camcorder some years ago, and for a while I used a DVD recorder with an HDD for timeshifted viewing of TV shows until analogue TV stations here in New Zealand were completely replaced with digital TV a couple of years ago, but we digress........

---

### Post by cbraxton on 2015-12-29
> **lisati said:**
> I switched from VHS to DVD for stuff I've recorded on camcorder some years ago, and for a while I used a DVD recorder with an HDD for timeshifted viewing of TV shows until analogue TV stations here in New Zealand were completely replaced with digital TV a couple of years ago, but we digress........

Yes, that's getting a bit off-topic, will just say that tape works fine with a digital converter box here in the U.S., and some later VCRs had built-in digital tuners (I have one of those).

Back on topic, for myself and presumably for the OP, not having something like K9Copy available is a problem. For the moment I'm still running Xubuntu 12.04 where it works just fine. If it won't be available in newer versions of Ubuntu, not sure what I'll do when support ends and it becomes necessary to update.  (Maybe run 12.04 in a VM just for dealing with DVDs.)

I did some poking around and it looks like k9copy development has been picked up, it is now available as "k9copy-reloaded" with unofficial packages available for newer versions of Ubuntu and Debian:

[http://tomtomtom.org/k9copy-reloaded/en.html](http://tomtomtom.org/k9copy-reloaded/en.html)

I have Xubuntu 14.04 running on an old laptop, even though I don't normally use that machine for DVD work I'll have to give this a try.

(Rereading the original post it looks like the problem being experienced was mencoder not installed - hopefully installing that via synaptic or "sudo apt-get install mencoder" will get things working for Darth.)

---

