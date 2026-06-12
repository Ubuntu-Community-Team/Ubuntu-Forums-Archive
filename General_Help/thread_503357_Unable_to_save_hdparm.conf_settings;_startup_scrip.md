---
title: "Unable to save hdparm.conf settings; startup scripts not executing?"
date: 2007-07-17
forum: General Help
---

### Post by steve457 on 2007-07-17
I'm having issues with the startup scripts in that they do not seem to be executing properly.  I'm sure they are working, however, as other things startup fine on a reboot.  There are only 2 commands which I am trying to add, and neither of them appears to be executing at startup.  

The first thing I'm trying to do is set my acoustic management level (works fine from the command line).  I modified the /etc/hdparm.conf file to include this setting:

```
/dev/sda {
     acoustic_management = 253
}
```

Upon rebooting, the level was never set.  Ok that's the first problem.  Second issue is I am trying to set a route for my network using the command:

```
route add -net 192.168.1.50 gw 192.168.1.1 -mask 255.255.255.255 eth1
```

The route command works fine from the command line, and sets the functionality that I desire.  I added that command into the /etc/network/interfaces file at the very end.  This command also appears to not work upon a reboot.  

i then tried adding both of those commands into my own sh script, and sym. linking them as S99MyScript from the /etc/rc3.d directory.  That also did not seem to work, as the script had no effect.

Is there something I am overlooking?  Are the commands I am trying to add in the correct locations?  Any log files I can check to see where the problem may be?

Thanks.

---

### Post by pointone on 2007-07-17
Ubuntu uses runlevel 2 by default, so you'll want them in /etc/rc2.d/.

Alternatively, you can add them in /etc/rc.local, which is probably a cleaner solution.

---

### Post by steve457 on 2007-07-17
I added the command for hdparm into the /etc/rc.local file and it works great!  Thanks so much for the tip.  I also moved some stuff in the /etc/network/interfaces file, so the command for route appears to be working as well.

---

