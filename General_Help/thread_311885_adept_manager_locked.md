---
title: "adept manager locked"
date: 2006-12-03
forum: General Help
---

### Post by p2cd3 on 2006-12-03
Did a new install last night, nvidia was picked correctly - good install.

I was installing java & the screen locked, did show details, the accept license could not be accepted, have since read how to get past this - but, the answers say to close the program.

That's the problem, I've been going in circles trying to close adapt manager, could not find the lock file in MC.

Any suggestions?

---

### Post by LLRNR on 2006-12-03
If I understand correctly, you want to stop Adept Manager but can't, right ? 

There are many solutions for this...

**1.** In a konsole, type **xkill** and then click on the Adept Manager window.

**2.** In a konsole, type **ps -e | grep adept** and look at the PID (the 4 digits number) corresponding to the "*adept_manager*" entry. Then type **kill -9 PID** where "PID" is the 4 digits number located before.

That should do it, I know it's not very elegant but it should help you at least to "kill" Adept.

LLRNR

---

### Post by p2cd3 on 2006-12-03
Yes, that removed the adept manager, but when I open adept manager I get this message:

You will not be able to change your system settings in any way (install, remove or upgrade software), because another process is using the packaging system database (probably some other Adept application or apt-get or aptitude). Please close the other application before using this one.

I also did grep on apt-get & aptitude - still not opening adept manager

---

### Post by LLRNR on 2006-12-03
Well this is odd... when I **ps -e | grep adept** I only get 2 processes, and these are "*adept_manager*" and "*adept_notifier*", I don't think it's got anything to do with your problem... but before rebooting maybe you could try killing *adept_notifier* too. :-k 

LLRNR

---

### Post by p2cd3 on 2006-12-03
Yes, I did remove the notifier also & no difference - hate to lower myself & reboot - will reply after reboot

---

### Post by p2cd3 on 2006-12-03
Rebooted & still same error message - I think it is still the lock file I need to remove - still cannot find it

---

### Post by LLRNR on 2006-12-03
I'm not quite sure on what exactly you need to remove/lock/unlock, but the "process" is as follows:

- when you begin an install or open Adept Manager, in /var/lib/dpkg the empty file called "lock" will be locked - it will cannot be opened, which means that it's used by a process;
- if, during this install (let's say you launched Adept Manager), you also try a *sudo aptitude install something* through the CLI, then you'll get - in the konsole - an error that appears as follows :
```
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```
- when you finish the install or close Adept Manager, the "lock" file in /var/lib/dpkg will become available (it will be unlocked, so that other processes demanding access to it will be able to use it).

Ok, apart from this I can't tell you anything else, I'm afraid I don't know why you can't access Adept... :(

LLRNR

---

### Post by p2cd3 on 2006-12-03
I am still getting this message:
You will not be able to change your system settings in any way (install, remove or upgrade software), because another process is using the packaging system database (probably some other Adept application or apt-get or aptitude). Please close the other application before using this one.

I gentoo linux when a program freezes or locks, I would go into MC & delete the lock file & all was corrected - this does not happen with /var/lib/dpkg. I'm thinking there must be another program running locked but, cannot find it

Thanks for the help LLRNR

---

### Post by p2cd3 on 2006-12-03
SOLVED

sudo apt-get dist-upgrade
dpkg --configure -a

This did the trick adept manager is back & running

---

### Post by catalina on 2006-12-15
Just wanted to pass along a thank you for the solution.  I was having the same problem when I was downloading java.  I am wondering if there is a problem with the version of Java I was trying? (sun)

Dean.

---

### Post by billstowell on 2006-12-15
[QUOTE=p2cd3;1840412]Did a new install last night, nvidia was picked correctly - good install.

I was installing java & the screen locked, did show details, the accept license could not be accepted, have since read how to get past this - but, the answers say to close the program.

That's the problem, I've been going in circles trying to close adapt manager, could not find the lock file in MC.

Any suggestions?[/QUOTE  How did you get around the "accept license"?  Also, Ihad the same problem trying to install java plugins for firefox.  After looking attips from elijahlofgren.com I did

sudo dpkg --configure -a

that unlocked adept--however, when I try to download/install a file now I get this error message:
"There was an error committing changes.  Possibly there was a problem downloading some packages or the commit would break packages."

I haven't figured out how to get adept to work normally.  Any ideas?--I' running Kubuntu edgy--

thanks for your help

---

### Post by descomputer on 2007-08-13
Had the exact same problem that adept manager would not be able to make changes.

Found this page and the solution:

sudo apt-get dist-upgrade
dpkg --configure -a

It worked for me also.  Thank You.

---

### Post by Teedyo on 2007-08-21
I have the exact same issue as bill.

dpkg --configure -a unlocked adept but I now get the unable to commit changes error.

---

### Post by Teedyo on 2007-08-21
> **Teedyo said:**
> I have the exact same issue as bill.

dpkg --configure -a unlocked adept but I now get the unable to commit changes error.

Got it.  I had deleted the 'Partial' directory thinking it would be re-created automatically.  Putting it back corrected my secondary problem.

---

### Post by th3rmos on 2007-09-03
Running 

```
sudo apt-get dist-upgrade
dpkg --configure -a
```

worked me too! Thanks for the post!

---

### Post by flyerfox on 2007-10-27
I'm having the same problem.... 

I was trying to upgrade to Ubuntu 7.10 last night, but the upgrade process got interupted... I killed adept manager.... but when I try I restart the upgrade process, I get the following error message:
```

$ sudo apt-get dist-upgrade
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

I tried the "dpkg --configure -a"  work-around suggested above, but get the following ereror message.... 

```
$ sudo dpkg --configure -a
dpkg: status database area is locked by another process

```

I'd very much appreciate any tips on how to get past this annoying error...

FYI... Here's the output from when I run top:

```

$ top
top - 11:50:59 up 10:58,  1 user,  load average: 0.04, 0.05, 0.07
Tasks: 160 total,   1 running, 157 sleeping,   1 stopped,   1 zombie
Cpu(s):  0.7%us,  0.2%sy,  0.0%ni, 98.5%id,  0.2%wa,  0.0%hi,  0.5%si,  0.0%st
Mem:   1026452k total,   946184k used,    80268k free,     9960k buffers
Swap:  3004112k total,   419108k used,  2585004k free,   248688k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 5858 romesh    15   0  4880 1616 1216 S    1  0.2   4:23.35 conky
 5678 root      15   0  314m  45m 3124 S    0  4.5   5:24.60 Xorg
    1 root      18   0  2912  532  460 S    0  0.1   0:01.42 init
    2 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0
    3 root      34  19     0    0    0 S    0  0.0   0:04.07 ksoftirqd/0
    4 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0
    5 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1
    6 root      39  19     0    0    0 S    0  0.0   0:02.14 ksoftirqd/1
    7 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/1
    8 root      10  -5     0    0    0 S    0  0.0   0:00.04 events/0
    9 root      10  -5     0    0    0 S    0  0.0   0:00.00 events/1
   10 root      19  -5     0    0    0 S    0  0.0   0:00.02 khelper
   11 root      10  -5     0    0    0 S    0  0.0   0:00.00 kthread
   35 root      10  -5     0    0    0 S    0  0.0   0:00.00 kblockd/0
   36 root      10  -5     0    0    0 S    0  0.0   0:00.00 kblockd/1
   37 root      10  -5     0    0    0 S    0  0.0   0:00.00 kacpid
   38 root      10  -5     0    0    0 S    0  0.0   0:00.00 kacpi_notify
  158 root      10  -5     0    0    0 S    0  0.0   0:00.04 kseriod
  188 root      15   0     0    0    0 S    0  0.0   0:00.73 pdflush
  189 root      11  -5     0    0    0 S    0  0.0   0:09.62 kswapd0
  190 root      11  -5     0    0    0 S    0  0.0   0:00.00 aio/0
  191 root      11  -5     0    0    0 S    0  0.0   0:00.00 aio/1
  825 root      15   0     0    0    0 S    0  0.0   0:00.00 kirqd
 2048 root      10  -5     0    0    0 S    0  0.0   0:00.00 ksuspend_usbd
 2049 root      10  -5     0    0    0 S    0  0.0   0:00.00 khubd
 2093 root      17  -5     0    0    0 S    0  0.0   0:00

```

Thanks, in advance...

---

### Post by jpirie on 2008-04-05
Hi People,
Have been scanning this forum for an answer to my problem.
I too am unable to update packages in Kubuntu.  I have tried everything that Linux users have so far suggested and still not luck.  I have even re installed Kubuntu from scratch (Partition reformatted) but still...no updates.
I read this threat and it looked like my problem but...

james@K-Asus:~$ sudo apt-get dist-upgrade
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
james@K-Asus:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege

Still no luck.  NOw, if anyone...anyone at all can see what I am doing wriong then I would really appreciate help before I am forced to admit defeat and revert to the unglorious Windoze environment for good :(

Simply put, I cannot connect and download any package updates or even install new packages, for example Mozilla Thunderbird, as it is all unavailable.

Help?

Thanks.

James

---

