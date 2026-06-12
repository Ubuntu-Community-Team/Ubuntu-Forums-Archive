---
title: "inherit windows insecurity?"
date: 2008-05-21
forum: General Help
---

### Post by Phatz on 2008-05-21
Greetings,
 I've been searching for a few days trying to find out if installing Ubuntu (using Wubi) will result in Ubuntu  inheriting the vulnerabilities of windows. 
 My main concern is malware or rootkits accessing the windows (XP) file system (at any level) while running Ubuntu via the Wubi "dual boot".
 To put it simply, would a box running Ubuntu via Wubi be as safe from both internal and external threats as a box using a traditional dual-boot?
 Thanks.

---

### Post by ago on 2008-05-21
> **Phatz said:**
>  To put it simply, would a box running Ubuntu via Wubi be as safe from both internal and external threats as a box using a traditional dual-boot?
 Thanks.

Yes

Of course if your machine is compromised while you are in windows, the attacker may gain full control on ALL the files on ALL partitions/vm/virtual disks, and hence can compromise the Linux files. But the same holds for a traditional dual-boot installation.

---

### Post by abn91c on 2008-05-21
> **Phatz said:**
> Greetings,
 I've been searching for a few days trying to find out if installing Ubuntu (using Wubi) will result in Ubuntu  inheriting the vulnerabilities of windows. 
 My main concern is malware or rootkits accessing the windows (XP) file system (at any level) while running Ubuntu via the Wubi "dual boot".
 To put it simply, would a box running Ubuntu via Wubi be as safe from both internal and external threats as a box using a traditional dual-boot?
 Thanks.

if you are worried about rootkits etc install rkhunter from the repositories and check ubuntu for rootkits, also in a terminal window you can type top and it will show whats running on the computer

---

### Post by Phatz on 2008-05-22
Thanks for the info, and for taking the time.
p. azz

---

### Post by Crossroads on 2008-05-22
> **Phatz said:**
>  My main concern is malware or rootkits accessing the windows (XP) file system (at any level) while running Ubuntu via the Wubi "dual boot".
 To put it simply, would a box running Ubuntu via Wubi be as safe from both internal and external threats as a box using a traditional dual-boot?
 Thanks.

If i have understood correctly, "While running Ubuntu" is the key phrase in your enquiry. You would boot your PC, select Ubuntu and laod it up. At no stage does your PC go into Windows. So the running system is as safe as any Ubuntu system.

Of course, if you boot into Windows then you have all the traditional Windows security issues. I suppose some threat could get into your Windows environemnt, find your Wubi virtual disk files and attack them, but that seems to me to be a bit of a stretch.

---

### Post by drifter2502 on 2008-12-28
> **Crossroads said:**
> If i have understood correctly, "While running Ubuntu" is the key phrase in your enquiry. You would boot your PC, select Ubuntu and laod it up. At no stage does your PC go into Windows. So the running system is as safe as any Ubuntu system.

Of course, if you boot into Windows then you have all the traditional Windows security issues. I suppose some threat could get into your Windows environemnt, find your Wubi virtual disk files and attack them, but that seems to me to be a bit of a stretch.

I am confused with wubi running as an exe file in Windows. How does wubi work unless Windows is running in the background? Also if Windows is not running how come I can access all my files on it from wubi?

---

### Post by albinootje on 2008-12-28
> **drifter2502 said:**
> Also if Windows is not running how come I can access all my files on it from wubi?

Because you're using the same disk(s).

Windows can also see Linux partitions with certain software.
And from Windows you can browse through the Wubi installation files right away.

---

### Post by drifter2502 on 2008-12-28
> **albinootje said:**
> Because you're using the same disk(s).

Windows can also see Linux partitions with certain software.
And from Windows you can browse through the Wubi installation files right away.

Thanks. So when I am in wubi(not partitioned),Windows is not running at all. Is that correct?

---

### Post by albinootje on 2008-12-28
> **drifter2502 said:**
> Thanks. So when I am in wubi(not partitioned),Windows is not running at all. Is that correct?

I've never used Wubi (I would have to install Windows somewhere to test it), but I have started Linux inside DOS many years ago.

But I'm pretty sure the answer to your question is yes.
While running Wubi, Windows is not running.

---

### Post by Fzang on 2008-12-28
The way I see it: when you're using your WUBI'd linux, all files downloaded and transfered are going in/out of the virtual linux disk, with a linux file system

If a windows virus lands in /home I doubt it'd know where to go and what to do without a system32

But of course, stuff like that is probably more sophisticated than that...

---

### Post by Jammanuser on 2008-12-28
> **drifter2502 said:**
> Thanks. So when I am in wubi(not partitioned),Windows is not running at all. Is that correct?

That is correct. Wubi operates within a ext3 formatted partition-like file called a root.disk, which allows you to run Ubuntu separate from Windows, despite it being installed on the Windows partition. When you boot into Ubuntu at startup, it is like you are booting into a real (dedicated partition) install, even though it is in fact within Windows...;)

Hope this helps! :popcorn:

-Jam man

:guitar:

---

### Post by drifter2502 on 2008-12-30
Thanks for that. I feel more confident now. I don know if the originator of this thread Phatz is?

---

