---
title: "Can't Copy CD"
date: 2007-01-24
forum: General Help
---

### Post by GoodPanos on 2007-01-24
Lately something weird is going on and I can't copy music CDs.  I was able to do that a few months ago and now it doesn't work right.

I have two Ubuntu distros on separate partitions, Ubuntu and Mint.  On both when I copy a music CD and then play back the CD it does not play.  For some reason the CD does not get burned right.  The music CDs are from the 80's so there is no copy protection and so forth.  I can make copies on my Windows XP fine.

Any suggestions or any good burning software out there for Ubuntu?

Please advise,

Thanks

---

### Post by dannyboy79 on 2007-01-24
well you need to troubleshoot this. is it the cd-writer? is it the burning software? what software are you using? are there any entries in dmesg or syslog prior or after burning. does the cd have anything on it after the burn, meaning can you put it in winxp and it sees something? you need to give us more info to help ya.

---

### Post by GoodPanos on 2007-01-24
The CD is fine.  When it does not burn I just boot into Windows and burn it right away.  I use Ubuntu to burn the CD.  Pop it in and then right click and select Copy Disc.

---

### Post by dannyboy79 on 2007-01-24
well what error do you get? what do you mean when you say, "when it does not burn"? you aren't really helping me help you! have you tried the cd burner in winxp to ensure that the burner didn't go bad? what do your logs say like I suggested.

---

### Post by GoodPanos on 2007-01-24
Actually it burns but the CD is useless.  Ubuntu goes through the whole process of caching the CD and then you put in the blanc CD and it goes through the burning process.  At the end though the CD is a dud - does not play back.

In WinXP I don't have to think about I just pop in the CD and make a copy of it using Nero.

I looked at the dmesg after burning the CD and I get two lines:
scsi: unknown opcode 0x01
cdrom: This disc doesn't have any tracks I recognize!
:confused: 

Where do you view the syslog?

---

### Post by dannyboy79 on 2007-01-24
i have that error in my dmesg all the time, despite the cd having a normal iso on it whatever. as far as readin the syslog, 2 way, either sudo gedit /var/log/syslog or open the log viewer under System, admin. how many different places have you tried the cd? you still haven't answered my question. have you tried THE BAD BURNER in winxp? or is this a dual boot system? we need to rule stuff out as the cause and troubleshoot this properly. taking items out of the equation is easier than trying the equation with tons of variables.

---

### Post by GoodPanos on 2007-01-24
Okay my misunderstanding.  Yeah this is done on a notebook, so yes it's the same burner in Ubuntu, Mint and WinXP...and nothing in syslog that looks suspicious.

---

### Post by GoodPanos on 2007-01-24
It looks like I am a victim of this post [http://www.ubuntuforums.org/showthread.php?t=217472&highlight=dev%2Fsr0](http://www.ubuntuforums.org/showthread.php?t=217472&highlight=dev%2Fsr0).

Here's how I discovered it:

I installed Gnomebaker and realized that I had to run it as root.  When I did that I was able to   copy the CD.  Hurray! :) 
However, every song came out messed up; it was like tunning in and out of a radio station.:confused: (anyways that's for another post another day).

So then after I read the above post I applied this solution:
Put the following line in /etc/rc.local file.
```
chown root:cdrom /dev/sg0
```

Now I can burn with Gnomebaker without running as root.  Since then though I haven't tried copying another CD in Gnomebaker or Nautilus; wasted too many CDs.

Will post results next time I do.

---

