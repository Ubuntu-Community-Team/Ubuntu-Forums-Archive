---
title: "Corrupt Filesystem?"
date: 2006-12-07
forum: General Help
---

### Post by cjserio on 2006-12-07
Hello,

I'm running Dapper Drake. This morning i was playing a YouTube video and for the first time ever on linux, my PC froze completely. Mouse/Keyboard didn't work at all. I had no choice but to shut the computer down by killing the power. Since then when I turn it on, it boots fine however i can't seem to perform any administrative functions.

If i try to go to users and groups, nothing happens...If i try to perform a system update, nothing happens. If i try to execute a sudo command, i get this error "/etc/sudoers is owned by gid 16777216 should be 0".

If i go to /etc/ and view a list of the files, there are several files whose group is some seemingly random numbers. I don't ever remember it being like that before.

What do i do?

Thanks,
Chris

---

### Post by bscbrit on 2006-12-07
Boot up in Recovery Mode and change the owner of the /etc/sudoers back to 0.  Then you should be able to log on again as usual and use sudo to begin to correct the errors.  

Alternatively, recover to your most recent backup - you do make backups, don't you? ;)

---

### Post by cjserio on 2006-12-07
When you say "correct the errors" how would i do that? If it is in fact filesystem corruption (I'm just guessing it is) then how do i know exactly what's broken and how to fix it?

Will running fsck from a liveCD help or hurt? If it's corruption can it usually fix it?

Chris

---

### Post by bscbrit on 2006-12-07
If the errors aren't obvious then I suspect you will be either looking at a re-install or continue with what you have and, if something stops working, tracking down the cause and fixing it.

I'm not trying to be sarcastic, but this is one of those times when a recent backup would be very useful...!  If, you re-install, make a backup once you have the system reconfigured just the way you like it.

---

