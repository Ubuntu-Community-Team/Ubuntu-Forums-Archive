---
title: "Ubuntu Server Hard Lock"
date: 2007-07-24
forum: General Help
---

### Post by rfdeshon on 2007-07-24
I have an installation of Ubuntu Server 7.04 running on a Dell Optiplex 240 with the 20-16-server kernel with a major problem. Basically, about 15 minutes after booting it hard locks. Every time without fail. I am running samba on it as it is being used to do over-the-network Windows installations. This is proving to be a major headache for me. What good is a remote install server if it dies halfway through the install? /var/log/messages yields nothing. I have not noticed any suspicious messages during the boot process either. When it dies, it does not respond to network requests (i.e. it's not just the shell that is locked), no response to keyboard commands, NumLock and CapsLock do not respond, it's a true hard lock. Any suggestions?

---

### Post by rfdeshon on 2007-07-25
No one has any suggestions? Can anyone suggest where I would begin to look at least?

---

### Post by rfdeshon on 2007-07-25
I booted this machine up and ran top until it froze. Both times it froze with an uptime of 14 minutes. I tried this with both the 2.6.20-16 and 2.6.20-15 kernel image. Same deal with both images. I did a recursive grep through the /var/log directory for the time that the server froze (I checked a range of a couple minutes just to be safe) but saw no errors. What could hard lock a system after the same amount of uptime consistently, across kernels, and leave no log? I've run the Dell diagnostics 3 times and found no faults in any of the hardware, I'm at a loss, will someone PLEASE help?

---

### Post by srt4play on 2007-07-25
I'm sure you've seen the reports of Feisty locking up for people, although most reports are for the desktop version.  I use 6.06 for my server (nfs, gnump3d) and it's solid as a rock.   Reverting back to Dapper may be your best option.

---

### Post by rfdeshon on 2007-07-25
Thats what I was afraid of. It's odd though, it was running fine two weeks ago then it suddenly started doing this. It is literally 14 minutes then lock. Every time, 14 minutes of uptime then locked. I checked the crontab and there is nothing scheduled to run, I checked atd and same thing. This is really out there.

---

### Post by tanman77 on 2007-11-21
> **rfdeshon said:**
> Thats what I was afraid of. It's odd though, it was running fine two weeks ago then it suddenly started doing this. It is literally 14 minutes then lock. Every time, 14 minutes of uptime then locked. I checked the crontab and there is nothing scheduled to run, I checked atd and same thing. This is really out there.

I get this as well but its every 4-6 days..looks like i am going to revert to Dapper.

---

