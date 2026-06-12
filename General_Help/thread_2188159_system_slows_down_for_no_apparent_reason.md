---
title: "system slows down for no apparent reason"
date: 2013-11-15
forum: General Help
---

### Post by dwjeanes2 on 2013-11-15
I was wondering if there is a tool to capture data to help determine what system component or application causes sudden bursts of disk activity and user interface sluggishness.

Normally, I run: 
FireFox v25.0
KVirc v4.1.3
and the current update of the media player, Totem 3.0.1

I also have an Oracle DB instance running, but it rarely is called or used.

Ubuntu version 12.04 LTS.

I have tried to look at the process table when this ocurs, but usually the problem is so bad that starting a shell is impossible.  What I am looking for is a tool that will capture process data and keep about 10 minutes worth in a file. I tried to script this using tail -f and ps, but trimming the file is where my script skills failed.  The file grew unwieldy very quickly, running the script 10 seconds apart for hours at a time.

I'll be happy to provide any info requested if anyone wants to take a stab at diagnosing this.

Thanks in advance.

Dave

---

### Post by TheFu on 2013-11-15
You want a system monitor. 
I like [SysUsage]("http://sysusage.darold.net/") since it works on desktops and servers. It isn't hard to install and having the data available for the last yr really does help.

Without data, it is hard to guess anything.

---

### Post by dwjeanes2 on 2013-11-15
> **TheFu said:**
> You want a system monitor. 
I like [SysUsage]("http://sysusage.darold.net/") since it works on desktops and servers. It isn't hard to install and having the data available for the last yr really does help.

Without data, it is hard to guess anything.


Thanks, I'll try it out.

---

### Post by TheFu on 2013-11-16
I really hoped that someone else would comment too and recommend some GUI tool for you. I'm sure they exist - I just don't use them.  

In the old days, we'd create little scripts to run sar and netstat every minute, storing the output into text files for later analysis and graphing.  Things like nagios, cacti, and the 20 other "also run here" tools have popped up. None of these are for end users.

I'd love to hear when/if you get any solution working.  It has been a while since [I installed SysUsage]("http://blog.jdpfu.com/2009/12/16/sysusage-3-0-installation-steps") so I'm on an older installation. For that version, I documented the dependencies and steps.  Hopefully the newer version isn't too different.

---

