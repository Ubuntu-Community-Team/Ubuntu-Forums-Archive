---
title: "how to monitor my downloads"
date: 2007-02-28
forum: General Help
---

### Post by STREETURCHINE on 2007-02-28
so i have been searching and trying to find ways to monitor what i download in total.

any programs out there to do this

i need it to monitor my total download

---

### Post by llamakc on 2007-02-28
Download through what mechanism? Using a browser only? Using the command `wget`? Emails also? 

Or do you want total traffic passed through your network connection?

You'll have to be specific, or approximate what you envision.

---

### Post by STREETURCHINE on 2007-02-28
i want to monitor everything that come in to my computer as a download,

 with my isp i have a download limit of 3 gig and lately they say i am using more than my limit,
i have queried it but they say they cant find any errors,
but since i am not doing anything differant than i normally do on here (i normally use around 1.7 -2.0 gig)
the last few months they say i have used 3.4 -3.7 gig and at 8.8c for every meg i go over it ,it is costing me.

so i need to track the total downloads and document them

---

### Post by llamakc on 2007-02-28
> **STREETURCHINE said:**
> i want to monitor everything that come in to my computer as a download,

 with my isp i have a download limit of 3 gig and lately they say i am using more than my limit,
i have queried it but they say they cant find any errors,
but since i am not doing anything differant than i normally do on here (i normally use around 1.7 -2.0 gig)
the last few months they say i have used 3.4 -3.7 gig and at 8.8c for every meg i go over it ,it is costing me.

so i need to track the total downloads and document them

```

ken@llamakc 07:24:24:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:09:DD:E2:41  
          inet addr:192.168.0.103  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:9ff:fedd:e241/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2109430 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1376080 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          **RX bytes:1777909011 (1.6 GiB)**  TX bytes:497485368 (474.4 MiB)
          Interrupt:50 Base address:0x6000 

```

Something like what I bolded above?

---

### Post by STREETURCHINE on 2007-02-28
yes as long as it can track the total for the month,or goes to a log every day i can read

---

### Post by llamakc on 2007-02-28
You could write a script to check the output of `ifconfig` every day at some time, and put the amounts in a text file. Maybe there's software that does this already? I'll look around.

---

### Post by STREETURCHINE on 2007-02-28
thank you,
i have been searching for a while not really found anything yet ,but i may not be looking in the right area,or asking the right questions.

as to a script well i certainly no good at doing that,:lolflag:

---

### Post by Maestro23 on 2007-02-28
> **STREETURCHINE said:**
> thank you,
i have been searching for a while not really found anything yet ,but i may not be looking in the right area,or asking the right questions.

as to a script well i certainly no good at doing that,:lolflag:

Try here also: [http://linuxappfinder.com/](http://linuxappfinder.com/)

---

### Post by z987k on 2007-02-28
wow, sounds like you need a new isp to be honest.
3Gb per month, I think i'd use that in general use forget about torrents.

---

### Post by STREETURCHINE on 2007-02-28
3 gig a month at $84.50 a month,
unfortunatly i am stuck with them.they are the only providers out here unless i go back to dialup

i have to use two way sat to get broadband out here

---

### Post by STREETURCHINE on 2007-02-28
maestro23

Try here also: [http://linuxappfinder.com/](http://linuxappfinder.com/)

i had a look ther but i cant find any thing that i think i could use.

thanks for the effort

---

