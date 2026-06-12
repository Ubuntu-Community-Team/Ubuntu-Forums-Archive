---
title: "discovered the source of those goutputstream files"
date: 2014-07-15
forum: General Help
---

### Post by a-you on 2014-07-15
Hi all. I see that many people have been wondering, as I have, about those accumulating .goutputstream-blabla files, and then the other  day I happened to come across this in the apparmor profile for evince  (look in /etc/apparmor.d/usr.bin.evince):

# evince creates a temporary stream file like '.goutputstream-XXXXXX' in the
# directory a file is saved. This allows that behavior.
owner /**/.goutputstream-* w,

So now we know the source of those files!!!

Btw I'm using ubuntu studio trusty 64 bit but those files were piling up  in previous versions too, like definitely in quantal for example; I  don't recall whether I had that issue in natty, which was what I was  using before quantal, probably so though.

---

### Post by ibjsb4 on 2014-07-15
So what happens if you just comment it out?

---

### Post by a-you on 2014-07-16
Well I don't think the apparmor profile is the issue at all. It just happens to contain that comment that reveals that evince is what's creating those files.

---

### Post by ibjsb4 on 2014-07-16
Skimming through this long thread, it looks to be glib2 (post#102).

[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/984785](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/984785)

---

### Post by a-you on 2014-07-16
I don't agree. Skimming that it looks to me like everybody there is speculating about where they might be coming from whereas that apparmor file explicitely states that evince creates them, and indeed the apparmor lines are there to allow evince to create them. And the apparmor profile was written by a Canonical employee, so presumably it's not guesswork (he'd be informed I would think).

---

### Post by mc4man on 2014-07-16
The bug wasn't the creation of those files or what creates them (certainly more than evince), it was they weren't being removed
That was fixed in glib & lightdm some time ago & with the exception of 12.04 is no longer an issue. 
(- if you see in 14.04 studio then file a bug 

As far as evince it was mentioned in the report & not really the problem - 
[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/984785/comments/72](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/984785/comments/72)

---

### Post by a-you on 2014-07-16
I've read that long launchpad page before. Funny thing is that I didn't realize at the time that I was reading only the first and last 40 pages ;-). It's quite long and to be honest I didn't read the whole thing just now either; no time to do that at the moment. But in the first and last 40 pages at least nobody shows that apps other than evince are creating those files. For the most part the posts are wild speculations about possible sources.

But honestly never mind. I was just trying to offer something helpful to everybody by pointing out what seems to be the actual source of the files.

Btw I could've sworn that I did in fact delete sevaral of those files in this new install of trusty, but I'm now not absolutely sure because I never really minded just deleting them every now and then, so it got to be something I didn't make note of anymore. I'll keep checking back and if I see more than one I'll post that in the bug report, or file a new one.

---

### Post by ibjsb4 on 2014-07-16
> **mc4man said:**
> with the exception of 12.04 is no longer an issue.

So if I understand right, there is not going to be a fix for 12o4 and I might as well set up a cron job to take care of this as I do not want to manually delete these files for two more years.

---

### Post by a-you on 2014-07-16
I just thought of something: to check my backup drive, which has backups of various states of quantal use and I can definitively say that they were still being left behind by ubuntu studio quantal/12.10 64 bit in my home folder.

---

### Post by james_mcl on 2014-07-16
I've noticed that even though I use atril instead of evince, I still get these files, and /etc/apparmor.d/usr.bin.evince still exists. Perhaps Atril can/does use Evince's profile?

---

### Post by mc4man on 2014-07-16
> **ibjsb4 said:**
> So if I understand right, there is not going to be a fix for 12o4 and I might as well set up a cron job to take care of this as I do not want to manually delete these files for two more years.
The odds now of a fix n 12.04 are virtually none unless done locally or thru a test ppa
As far as 12.10 & 13.04 both are EOL so irrelevant, it was fixed in 13.10 & 14.04

---

### Post by a-you on 2014-07-17
Re comments by mc4man and ibjsb4: hmm but your point is well taken, that it can be an underlying lib that evince and other apps use. That's a good point. Probably true.

And to james_mcl: I don't think the fact that another app might or might not use the apparmor profile is an issue. Really all that's doing is that it allows the app to create those files, it doesn't mean that apparmor is creating the files. Probably, as others here have been saying, there's a lib that's shared by apps, including presumably evince, and that's the source. I was being a bit hasty in concluding that it could only be evince. Though in all fairness to me (haha) the info that I came across was explicit, while a lot of threads that comment on this issue have contained hardly more than vague speculation. Then again, vague speculation is fun too ;-).

---

### Post by a-you on 2014-07-23
If it's of interest: 

At the moment there are 4 of those .goutputstream-?????? files in my home directory. That's with Ubuntu Studio 14.4/Trusty. So it wasn't fixed.

---

