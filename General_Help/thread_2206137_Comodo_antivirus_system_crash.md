---
title: "Comodo antivirus system crash"
date: 2014-02-17
forum: General Help
---

### Post by philromford-q on 2014-02-17
I had the thing working, so I thought, after installing the correct driver. However, since then it will not run a full scan to completion, it gets so far then the whole system crashes; I have to switch off and re-boot. 

Can anyone offer an explanation/solution for this please?

---

### Post by SuperFreak on 2014-02-17
I had problems with Comodo AV including it crashing, slowing boot times and not scanning emails. Frankly came to the conclusion it was not ready for prime time and really not needed on a Linux computer so I uninstalled it. The only value I could see with it is if it scanned outgoing emails and thereby prevented my PC from infecting Windows computers(assuming my PC had picked up a Windows virus by email or download). I believe that Comodo is not designed to work with desktop email programs like Thunderbird though so I never got it to work. Windows viruses will not affect a Linux PC and as far as I know there are no known Linux viruses in the wild

---

### Post by QDR06VV9 on 2014-02-18
> **philromford-q said:**
> I had the thing working, so I thought, after installing the correct driver. However, since then it will not run a full scan to completion, it gets so far then the whole system crashes; I have to switch off and re-boot. 

Can anyone offer an explanation/solution for this please?
Sorry to hear your troubles are on going. Both of you.
I have without  A GLITCH Been running COMODO for the better part of a year now with nothing like your experiencing,
Infact no issues at all. Plus about 6 installs for friends.
Maybe you should start asking over in there [forums.]("https://forums.comodo.com/comodo-antivirus-for-linux-cavl-b275.0/-t85030.0.html")

---

### Post by 3rdalbum on 2014-02-18
> **philromford-q said:**
> I had the thing working, so I thought, after installing the correct driver. However, since then it will not run a full scan to completion, it gets so far then the whole system crashes; I have to switch off and re-boot. 

Can anyone offer an explanation/solution for this please?

Two possible explanations:

1. Bad RAM. One of the RAM sticks in your computer might be failing. Using RAM intensively, such as when you're doing a virus scan, can trigger a bad RAM stick to misbehave, crashing the system.

2. Bad hard disk. Go into Disk Utility and check out the SMART statistics for the hard disk you are scanning. If it shows more than 12 sectors waiting to be reallocated (or unrecoverable) then you've got yourself a bad disk there. The disk will only get worse, so back up all the files on the hard disk. Since the disk you are scanning is most likely a Windows disk (no viruses on Linux) you should also check that you have a Windows restore CD or a Windows retail CD so you can reinstall Windows onto a new disk.

---

### Post by philromford-q on 2014-03-02
I did i fact try their forum, no go there. So I have dumped it and installed AVG; that requires commands in terminal, so no GUI but it works.

---

### Post by philromford-q on 2014-03-02
1. RAM? I don't know.

2. BAD HD, it tests fine.

Now using AVG from the command line.

---

