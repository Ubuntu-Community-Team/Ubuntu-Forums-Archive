---
title: "problems with vmware"
date: 2007-09-01
forum: General Help
---

### Post by mikeyandmary on 2007-09-01
I am running windows XP on my ubuntu laptop using vmware server. My laptop is 2.0Ghz Pentium M with 1Gig RAM. The virtual drive has 15 gig allocated. 

My first problem is that XP is running REALLY SLOW in vmware. 

My second problem is that XP doesn't remember my monitor settings so I have to fix it every time I restart. 

Any help would be great...

---

### Post by gtdaqua on 2007-09-01
Install "VMWare Tools" from "VM -> Install VMWare Tools.." from VMWare Server Console. This will accelerate some settings (video, network etc).

How much memory have alloted for XP? Atleast 512 is required for reasonable performance

---

### Post by mikeyandmary on 2007-09-01
Have installed VMWare tools and have 640MB memory allocated.

---

### Post by gtdaqua on 2007-09-01
Need some more details. 

when exactly is XP slowing down? When u run specific applications or simply loading?
have u allocated swap memory for the vm? 
what u mean by monitor settings?

---

### Post by Krijk on 2007-09-04
A bit off topic for your problem, but apparently I'm not the only one with issues

[http://ubuntuforums.org/showthread.php?t=542958&highlight=vmware](http://ubuntuforums.org/showthread.php?t=542958&highlight=vmware)

---

### Post by Cryptic1911 on 2007-09-04
are you sure you arent running out of memory in the host os? 1gb and you allocated 640mb to vmware's guest os?

---

### Post by OsuCowboy on 2007-09-04
This guy put together a good document on running XP inside a virtual machine.   

[http://www.hmobius.com/downloads/xp%20vpc.pdf](http://www.hmobius.com/downloads/xp%20vpc.pdf)

Also, giving XP its own disk, installing Windows Updates,  and defragging inside your XP virtual machine help.

Did you create your virtual machine with fixed disk size or allow it to grow as needed?  I think converter asked me that when I created my last one. (XP Pro)  If I remember right it said it
would improve performance.

Also, like Cryptic1911 suggests, I'd give XP 500meg at most with 1Gig total.

---

### Post by spupy on 2007-09-04
About the alocated RAM: VMware says ~220 is the recommended maximum for WinXP guest OS. I run vmware server on a 512MB laptop, and 220MB are ok for one program at a time (at least for what i am doing). Beyond the recommended maximum swaping occurs, but i don't know how much does that slow the computer.

---

### Post by dpj23 on 2007-09-04
I know everyone has sounded off about memory configurations...  I would suggest anything from 512 to 640...  This would provide a range that should produce desired results.  However, as indicated by many the higher you go, then you start to have problems with the host...  If XP is running slow I would start looking at the configuration of the XP quest machine...

---

### Post by Cornerville on 2007-09-11
The VMware server works fine on Ubuntu 7.04 until the system is rebooted, then it must be reconfigured with vmware-config.pl before it will work again.  Has anyone else had this problem. and if so, does anyone know of a fix?  Thanks.

---

### Post by spupy on 2007-09-11
> **Cornerville said:**
> The VMware server works fine on Ubuntu 7.04 until the system is rebooted, then it must be reconfigured with vmware-config.pl before it will work again.  Has anyone else had this problem. and if so, does anyone know of a fix?  Thanks.

Try not to reconfigure it but to remove this file:
/etc/vmware/not_configured
```
sudo rm /etc/vmware/not_configured
```

---

### Post by Cornerville on 2007-09-12
Thanks for the tip, I will try that next time I have to reboot.  Will I have to do that every time, or is it a one time fix.  Thanks Again

---

### Post by spupy on 2007-09-12
I have to do it after every reboot.

---

### Post by Cornerville on 2007-09-12
Thanks again, that may solve some problems and I will try it.  Will keep looking for a permanent fix, there must be one.  

:)

---

### Post by OsuCowboy on 2007-09-12
Had the same problem.

I had previously installed/uninstalled 1.0.2-2 player using default add-remove Ubuntu app.
It left behind a read only copy of /etc/init.d/vmware (old version) that screwed up my 2.0 install at boot time.

When vmware-config.pl runs it loads the modules/etc. and all works fine until you reboot.


sudo rm -f /etc/init.d/vmware
sudo vmware-config.pl
sudo rm /etc/vmware/not_configured
Also check that it's set to start in the various run levels:

e.g.  /etc/rc2.d/S90vmware -> /etc/init.d/vmware
I've got entries in rc2, rc3, and rc5.

---

### Post by Cornerville on 2007-09-12
First I ran sudo  rm-f /etc/init.d/vmware, then I ran vmware-config.pl and I got this output

Making sure services for VMware Server are stopped.

sh:  /etc/init.d/vmware  not found

unable to stop services for VM Server

Execution aborted,

Now what do I do?

:confused:

---

### Post by OsuCowboy on 2007-09-13
Sorry bout that.  :oops:
You should have the 2.0 version of that file in your vmware player sources.

vmware-player-distrib/installer/services.sh  
just rename services.sh to vmware and cp it to /etc/init.d/
Make sure it's executable (sudo chmod 755 /etc/init.d/vmware)

it takes parms as well, status is a good one.
Usage: vmware {start|stop|status|restart}


I attached mine here in case your's is missing.
It's from VMware-player-2.0.0-45731.i386.tar.gz

---

### Post by Cornerville on 2007-09-13
Thanks, that seems to have fixed it.

:)

---

### Post by Cornerville on 2007-09-13
Spupy, Your solution does work, think I will stick with that and I won't have to reconfigure it again.:cool:

---

