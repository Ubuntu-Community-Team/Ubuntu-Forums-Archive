---
title: "could not start the x server"
date: 2008-03-12
forum: General Help
---

### Post by nzadLithium on 2008-03-12
Hey I gots a new processor today. 32bit like the last one. I had a celeron replaced with pentium. Initial startup went fine. Played a bit of rtcw noticed i still had the sudden drop in fps that i get had with the celeron. I don't know why that happens so i restarted went into bios and turned up the cpu clock (default is 200 i set to 300 i think) and dram ratio. When i restarted it brought up a weird message saying 
"Could not start the x server (your graphical environment)
due to some internal error
please contact your system administrator
or check your syslog to diagnose.
In the mean time this display will be disabled. Please restart GDM when the problem is corrected."

i hit ctrl alt f6
and it comes up with (none) login:

then when i goto login i get "-bash: /dev/null: Permission denied" a couple of hundred times. I hit control + c then login.

i nano /var/log/syslog
i have things about
syslogd ubuntu(version numbers stuff round this): restart
then job 'cron.daily' terminated
normal exit (1)
then a bunch of messages with varying tty numbers all saying 
tty(no) main process killed by TERM
then avahi-daemon got SIGTERM
leaving mDNS multicast group on eth0.IPv4 with address 192.168.1.3
Caught signal 15, unregistering and exiting
nfsd: last server has exited
nfsd: unexporting all filesystems
cmaster32bit-desktop exiting on signal 15

i seem to have the same problem as this [http://ubuntuforums.org/archive/index.php/t-576435.html](http://ubuntuforums.org/archive/index.php/t-576435.html)
but that thread the person ends up with complete reinstall. I want to fix without doing that preferably as i would have to wait till end of the broadband month to download ubuntu again.

---

### Post by nzadLithium on 2008-03-12
hmm i just restarted computer again after leaving it for like half an hour. It just started up fine. could overheating cause this???

---

### Post by nzadLithium on 2008-03-12
did another restart and now i have the stupid message again :sad:

---

### Post by nzadLithium on 2008-03-12
it seems removing quiet and splash from grub has fixed it.

---

