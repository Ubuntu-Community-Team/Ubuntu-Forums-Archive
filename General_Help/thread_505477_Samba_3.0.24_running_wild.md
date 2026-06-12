---
title: "Samba 3.0.24 running wild"
date: 2007-07-20
forum: General Help
---

### Post by Cr0n_J0b on 2007-07-20
I'm not sure what is going on here, but I have noticed that if I leave my system on for a while, Like over a couple days it starts slowing to a crawl.  Looking in process list there are a TON like 50-100 spawned smbd processes.  I've never seen smbd spawn so many times.  I can't seem to shut it down either.  In this state I can stop samba, but the processes are still alive...the only solution is a reboot.  I'm a little worried that this might be some type of attack on the system, but my ISP doesn't allow smb traffic out...still it's odd.  any help would be appreciated.

thanks

---

### Post by Cr0n_J0b on 2007-07-23
anyone!

---

### Post by erland on 2007-09-13
Did you find any resolution to this ?

I had the exact same behaviour this morning and I think I've also had it 2 or 3 times before during the last months. The server where I have this problem is running Ubuntu Dapper and have been very stable before, but this problem has happend a few times during the last months.

I wasn't even able to kill the processes using:
sudo killall -9 smbd
As in your case, a reboot was the only solution.

I looked in /var/log/dpkg log files and a new version of samba was installed 2007-05-18, so the problem might have started already then but it wasn't until now I actually realized that samba was the problem.

If anyone have a solution to this or some ideas what to check, please let me know.

EDIT: I have the problem with samba 3.0.22, so the problem seems to exist in several samba versions.

---

