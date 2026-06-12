---
title: "Boot stops at &quot;Starting Samba daemons&quot;"
date: 2008-07-01
forum: General Help
---

### Post by alingham on 2008-07-01
Hey guys

I recently had problems with mounting Windows Samba shares.
Having read [this post]("http://ubuntuforums.org/showthread.php?t=88206&highlight=netbios"), I managed to fix it.

However, now when I try to boot into my beloved Ubuntu, the system hangs on running all the startup apps, and stops at the line
"Starting Samba Daemons"... all the other's have [OK] next to them, and I wait ages yet still no sign of any [OK] next to the Samba Daemon's line. 

Have had the horrible experience of having to boot into Windows to make this post. Please save me!
Any help is much appreciated

---

### Post by nikgare on 2008-07-01
Are you sure it's actually stopped - while mine check the disks (which can take a **long** time) it displays "starting samba Daemon" as well.
How long have you waited for?

---

### Post by alingham on 2008-07-01
Having read your post on another machine, I switched it on...
Currently sitting at 1 hour 2mins of wait time...

---

### Post by alingham on 2008-07-01
1 hour 30mins... Is this a record for boot time?
I suspect that there is actually a problem here, not just a small delay...

---

### Post by nikgare on 2008-07-02
Yeah, more than 10 minutes and something has gone wrong.
Can you skip the samba initilization by preesing "ctrl c"?
If not, you might need to boot off a live CD and remove the contents of smb.conf (or is that smbd.conf?) and see if that helps. -.make a backup of the conf file first!

---

### Post by alingham on 2008-07-02
Yeah - booted off the LiveCD and changed the /etc/nswitch.conf back to normal (without wins)...
I read that the reason why you'd use NETBIOS (hence the nswitch.conf with wins workaround) is so that your Samba shares you can use their Windows name to reference them. So I left it in, pinged the machine I wanted, got the IP address, and put that into /etc/fstab.
Tomorrow I will find out if the system has dynamic IP's though!!! In which case I'm back at square one.

If anyone else can come up with a solution to the nswitch.conf work around causing boot to hang, I'd be much appreciative. I prefer to use Netbios names for the Samba shares...

---

