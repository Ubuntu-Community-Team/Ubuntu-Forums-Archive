---
title: "System uses only CPU-No RAM"
date: 2016-11-23
forum: General Help
---

### Post by aviator1 on 2016-11-23
Hello:

Since switching to 16.04, I have had big problems saving a spreadsheet. I can open it, make no changes, and close, but it freezes and maxes out one of my processors (8 core AMD) for about 2 minutes. Then the movements are jerky.

Using system monitor, I see that no RAM is being used.......flat line at about 2 GB or less. I have 16GB RAM, but no swap. Was advised not to have one since I am using an SSD.

Is there some reason that no RAM is being used? I have looked at other operations, and the same thing is occuring.

I was OK with 14.04.

Thanks for any help.

EDIT. It is locked up now. 1 CPU is at 100% and RAM uses is about 2 GB. 

dave@dave-desktop:~$ free -m
              total        used        free      shared  buff/cache   available
Mem:          15949        1106       13852          35         990       14492
Swap:         16283           0       16283



Regards.

---

### Post by aviator1 on 2016-11-23
Here's what I get when I run top while the spreadsheet is locked up

```
top - 13:53:42 up 9 min,  1 user,  load average: 0.42, 0.48, 0.28
Tasks: 259 total,   2 running, 257 sleeping,   0 stopped,   0 zombie
%Cpu(s):  1.6 us,  0.4 sy,  0.0 ni, 97.9 id,  0.0 wa,  0.0 hi,  0.1 si,  0.0 st
KiB Mem : 16332208 total, 14099672 free,  1116284 used,  1116252 buff/cache
KiB Swap: 16674812 total, 16674812 free,        0 used. 14848708 avail Mem 

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+  COMMAND                                                                                                                                  
 1994 dave      20   0  622172  57188  32268 S   6.0  0.4   0:30.10  my-weather-indi                                                                                                                          
 1056 root      20   0  263100  78176  57208 S   3.3  0.5   0:37.16  Xorg                                                                                                                                     
 1619 dave      20   0 1608264 200208  80084 S   3.0  1.2   0:18.07  compiz                                                                                                                                   
 2049 dave      20   0 1491148 358408 116812 S   1.7  2.2   1:41.41  firefox                                                                                                                                  
 1533 dave      20   0  395940  12424  10992 S   1.0  0.1   0:02.67  indicator-appli                                                                                                                          
 1823 dave      20   0  506696  26560  19752 S   1.0  0.2   0:07.03  indicator-multi                                                                                                                          
 2484 dave      20   0  659392  37324  28784 S   1.0  0.2   0:00.44  gnome-terminal-                                                                                                                          
 1467 dave      20   0  575564  45488  26200 S   0.7  0.3   0:05.18  unity-panel-ser                                                                                                                          
 2502 dave      20   0   41916   3960   3232 R   0.7  0.0   0:00.15  top                                                                                                                                      
   60 root      20   0       0      0      0 S   0.3  0.0   0:00.01  kworker/u16:1                                                                                                                            
 1184 dave      20   0   44104   4664   2896 S   0.3  0.0   0:02.90  dbus-daemon                                                                                                                              
 1873 dave      20   0  244052  25204   9372 S   0.3  0.2   0:01.84  hp-systray                                                                                                                               
    1 root      20   0  185636   6276   3980 S   0.0  0.0   0:01.37  systemd                                                                                                                                  
    2 root      20   0       0      0      0 S   0.0  0.0   0:00.00  kthreadd                                                                                                                                 
    3 root      20   0       0      0      0 S   0.0  0.0   0:00.01  ksoftirqd/0                                                                                                                              
    5 root       0 -20       0      0      0 S   0.0  0.0   0:00.00  kworker/0:0H                                                                                                                             
    7 root      20   0       0      0      0 S   0.0  0.0   0:00.76  rcu_sched                                                                                                                                
    8 root      20   0       0      0      0 S   0.0  0.0   0:00.00  rcu_bh                                                                                                                                   
    9 root      rt   0       0      0      0 S   0.0  0.0   0:00.01  migration/0                                                                                                                              
   10 root      rt   0       0      0      0 S   0.0  0.0   0:00.00  watchdog/0                                                                                                                               
   11 root      rt   0       0      0      0 S   0.0  0.0   0:00.00  watchdog/1                                                                                                                               
   12 root      rt   0       0      0      0 S   0.0  0.0   0:00.01  migration/1                                                                                                                              
   13 root      20   0       0      0      0 S   0.0  0.0   0:00.00  ksoftirqd/1                                                                                                                              
   15 root       0 -20       0      0      0 S   0.0  0.0   0:00.00  kworker/1:0H                                                                                                                             
   16 root      rt   0       0      0      0 S   0.0  0.0   0:00.00  watchdog/2                                                                                                                               
   17 root      rt   0       0      0      0 S   0.0  0.0   0:00.01  migration/2                                                                                                                              
   18 root      20   0       0      0      0 S   0.0  0.0   0:00.02  ksoftirqd/2                                                                                                                              
   20 root       0 -20       0      0      0 S   0.0  0.0   0:00.00  kworker/2:0H                                                                                                                             
   21 root      rt   0       0      0      0 S   0.0  0.0   0:00.00  watchdog/3                                                                                                                               
   22 root      rt   0       0      0      0 S   0.0  0.0   0:00.00  migration/3                                                                                                                              
   23 root      20   0       0      0      0 S   0.0  0.0   0:00.02  ksoftirqd/3                                                                                                                              
   25 root       0 -20       0      0      0 S   0.0  0.0   0:00.00  kworker/3:0H                                                                                                                             
   26 root      rt   0       0      0      0 S   0.0  0.0   0:00.00  watchdog/4                                                                                                                               
   27 root      rt   0       0      0      0 S   0.0  0.0   0:00.00  migration/4                                                                                                                              
   28 root      20   0       0      0      0 S   0.0  0.0   0:00.01  ksoftirqd/4                                                                                                                              
   30 root       0 -20       0      0      0 S   0.0  0.0   0:00.00  kworker/4:0H                                                                                                                             
   31 root      rt   0       0      0      0 S   0.0  0.0   0:00.00  watchdog/5                                                                                                                               
   32 root      rt   0       0      0      0 S   0.0  0.0   0:00.00  migration/5                                                                                                                              
   33 root      20   0       0      0      0 S   0.0  0.0   0:00.00  ksoftirqd/5                                                                                                                              
   35 root       0 -20       0      0      0 S   0.0  0.0   0:00.00  kworker/5:0H                                                                                                                             
   36 root      rt   0       0      0      0 S   0.0  0.0   0:00.00  watchdog/6                                                                                                                               
   37 root      rt   0       0      0      0 S   0.0  0.0   0:00.00  migration/6                                                                                                                              
   38 root      20   0       0      0      0 S   0.0  0.0   0:00.00  ksoftirqd/6                                                                                                                              
   39 root      20   0       0      0      0 S   0.0  0.0   0:00.00  kworker/6:0                                                                                                                              
   40 root       0 -20       0      0      0 S   0.0  0.0   0:00.00  kworker/6:0H                                                                                                                             
   41 root      rt   0       0      0      0 S   0.0  0.0   0:00.00  watchdog/7                                                                                                                               
   42 root      rt   0       0      0      0 S   0.0  0.0   0:00.00  migration/7                                                                                                                              
top - 13:54:29 up 10 min,  1 user,  load average: 0.59, 0.51, 0.30
Tasks: 279 total,   3 running, 276 sleeping,   0 stopped,   0 zombie
%Cpu(s): 14.9 us,  0.5 sy,  0.0 ni, 84.5 id,  0.0 wa,  0.0 hi,  0.2 si,  0.0 st
KiB Mem : 16332208 total, 13943684 free,  1248060 used,  1140464 buff/cache
KiB Swap: 16674812 total, 16674812 free,        0 used. 14714740 avail Mem 

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND     
 2526 dave      20   0 1408008 203496 104664 R  99.3  1.2   0:32.90 soffice.bin 
 1056 root      20   0  269352  79792  58184 S   6.0  0.5   0:39.66 Xorg        
 1619 dave      20   0 1612240 200356  80084 S   6.0  1.2   0:20.42 compiz      
 1994 dave      20   0  622172  57188  32268 S   6.0  0.4   0:32.69 my-weather+ 
 2570 dave      20   0  672524  49228  34980 S   2.0  0.3   0:00.71 gnome-syst+ 
 2049 dave      20   0 1491148 357936 116812 S   1.7  2.2   1:42.34 firefox     
 1467 dave      20   0  575564  45544  26200 S   1.3  0.3   0:06.07 unity-pane+ 
 1823 dave      20   0  580428  26672  19748 S   1.3  0.2   0:07.69 indicator-+ 
 1184 dave      20   0   44104   4664   2896 S   0.7  0.0   0:03.23 dbus-daemon 
 1533 dave      20   0  395940  12424  10992 S   0.7  0.1   0:02.91 indicator-+ 
 1873 dave      20   0  244052  25204   9372 S   0.7  0.2   0:02.03 hp-systray  
    7 root      20   0       0      0      0 S   0.3  0.0   0:00.85 rcu_sched   
   61 root      20   0       0      0      0 S   0.3  0.0   0:00.29 kworker/0:1 
 1254 dave      20   0  345388   6856   5304 S   0.3  0.0   0:00.99 ibus-daemon 
 1273 dave      20   0  514592  39944  31736 S   0.3  0.2   0:00.46 ibus-ui-gt+ 
 2273 dave      20   0  653784  27108  16016 S   0.3  0.2   0:00.38 unity-scop+ 
    1 root      20   0  185636   6276   3980 S   0.0  0.0   0:01.37 systemd     
dave@dave-desktop:~$
```

---

### Post by #&amp;thj^% on 2016-11-23
**" CPU: 99.3  1.2   0:32.90 soffice.bin "**
aviator1 This has been around for a few years now: (known memory leak that hasn't been fixed for years) [https://ask.libreoffice.org/en/question/50932/freeze-with-100-cpu-after-opening-documents-via-api/](https://ask.libreoffice.org/en/question/50932/freeze-with-100-cpu-after-opening-documents-via-api/)
I am surprised you did not see it in 14.04.
But I have not found a fix for this yet either...But If you are interested I went with wps-office
and have not looked back. And not it matters here I also use it on Arch Rolling.
More Info Here: [https://www.wps.com/linux](https://www.wps.com/linux)

Downloads Here: [http://wps-community.org/downloads](http://wps-community.org/downloads)

WPS Office Fonts Here: [http://wps-community.org/downloads?vl=fonts](http://wps-community.org/downloads?vl=fonts)

Discription:
> WPS Office, is an office productivity suite.
WPS Office including Writer, Presentation and Spreadsheets, is a powerful office suite, which is able to process word file, produce wonderful slides, and analyze data as well. It is deeply compatible with all of the latest Microsoft Office file formats. It can easily open and read the documents created with Microsoft Office. This is the Linux version, and it's now a TESTING package. Welcome to our website: [http://wps-community.org](http://wps-community.org) 
And i used Gdebi to install it with.
If you do go this route set yourself for slight learning curve.
Note: I have not been able to install this yet on 16.10 due to a missing depends.
Kind Regards

---

### Post by aviator1 on 2016-11-23
Thanks very much.

Did not see it in 14.04.  Will look at the info you sent.

---

### Post by aviator1 on 2016-11-23
@ 1fallen:

Thanks for the info on the wps. I like the looks of it, but think I will wait and see if I get any responses from the forum before I attempt a change. 

I'm a long time user, but not well versed in the ins and outs of the real technical end of getting all of this working.

However, I did not have these freeze up issues with 12.04 or 14.04. Surely, I can't be the only person out there that is having these problems.

During another freeze up a few minutes ago, the RAM was locked at 1.7 GB of use (never waivered) and one of the CPU's was maxed at 100%. Sometimes the CPU's will switch 100% from one to another.

There must be a switch or setting to tell the software to use the RAM.

I do appreciate your reply and will consider the change if this keeps up.

In the meantime, I hope some of the old timers here can offer some advice.

Regards.

---

### Post by fenrice on 2016-11-23
One option might be to get the tar.gz file version from libreoffice that matches up with the version that comes with 14.04 . Not sure what that is, but it might be a work around for you. Here is a pointer over at libreoffice [https://ask.libreoffice.org/en/question/75536/where-can-i-download-old-versions-of-libreoffice/](https://ask.libreoffice.org/en/question/75536/where-can-i-download-old-versions-of-libreoffice/)

---

### Post by aviator1 on 2016-11-24
I've wondered about that.

Do you think this is a libreoffice issue and not a 16.04 issue?

Thanks for your reply. 

Have a happy Thanksgiving. That is if you are in the USA.. :-)

---

### Post by aviator1 on 2016-11-24
The plot thickens........

I downloaded and started using gnumeric for my spreadsheet.

It has a brief (<10 seconds) of freeze during an open or save process.

Will continue research.

---

### Post by #&amp;thj^% on 2016-11-24
> **aviator1 said:**
> @ 1fallen:

Thanks for the info on the wps. I like the looks of it, but think I will wait and see if I get any responses from the forum before I attempt a change.

I'm a long time user, but not well versed in the ins and outs of the real technical end of getting all of this working.

He He.. I totally get that...and why I fore-warned to set yourself for a learning curve.
But that said it is very minimal if you understand Office Software. (So it took me a bit longer to wrap my head around it.:D) 
Your Welcome for the information though.:)

> **aviator1 said:**
> 
In the meantime, I hope some of the old timers here can offer some advice.
Regards.

BTW I am an Old timer here been around here in UF since 2005..just a new user name.
By the sounds of things...I am curious about the spread sheet or Document in question.
If you had another machine..say with 14.04 running...I wonder if you would see the same memory leak. (Just Thinking out loud)
Anyway Good Luck and Best Regards

---

### Post by him610 on 2016-11-24
> no swap. Was advised not to have one since I am using an SSD.
> AMD 8530 4.0Ghz, 16GB RAM, 256GB SSD, 2 TB HDD, NVIDIA GT 640, Ubuntu 16.04 LTS

Why not put *swap* on the 2 TB HDD?

---

### Post by aviator1 on 2016-11-25
I have thought of that, but don't know how to add a swap anywhere.

---

### Post by aviator1 on 2016-11-25
I will try another machine. I think I still have 14.04 on another computer.

---

### Post by vasa1 on 2016-11-25
Is it with all spreadsheets or just one?

There have been quite a few reports of LibreOffice locking up things. No clear answer.

I have an oldish laptop which struggled a bit with the gtk3 version of LibreOffice. I switched to gtk2 mode and things went smoother for me.

When you run```
apt search libreoffice integration
```what is the output?

I get```
Sorting... Done
Full Text Search... Done
libreoffice-gnome/xenial 1:5.2.3~rc2-0ubuntu1~xenial1 amd64
  office productivity suite -- GNOME integration

libreoffice-gtk2/xenial,now 1:5.2.3~rc2-0ubuntu1~xenial1 amd64 [installed]
  office productivity suite -- GTK+ 2 integration

libreoffice-gtk3/xenial 1:5.2.3~rc2-0ubuntu1~xenial1 amd64
  office productivity suite -- GTK+ 3 integration

libreoffice-kde/xenial 1:5.2.3~rc2-0ubuntu1~xenial1 amd64
  office productivity suite -- KDE integration

```If anything else other than libreoffice-gtk2 is installed, try uninstalling those packages and see. You can always re-install them again but this step has helped some users.

---

### Post by aviator1 on 2016-11-25
Here is the info
```
dave@dave-desktop:~$ apt search libreoffice integration
Sorting... Done
Full Text Search... Done
libreoffice-gnome/xenial,now 1:5.2.3~rc2-0ubuntu1~xenial1 amd64 [installed]
  office productivity suite -- GNOME integration

libreoffice-gtk/xenial-updates,xenial-security 1:5.1.4-0ubuntu1 i386
  office productivity suite -- GTK+ integration

libreoffice-gtk2/xenial,now 1:5.2.3~rc2-0ubuntu1~xenial1 amd64 [installed]
  office productivity suite -- GTK+ 2 integration

libreoffice-gtk3/xenial 1:5.2.3~rc2-0ubuntu1~xenial1 amd64
  office productivity suite -- GTK+ 3 integration

libreoffice-kde/xenial 1:5.2.3~rc2-0ubuntu1~xenial1 amd64
  office productivity suite -- KDE integration

libreoffice-subsequentcheckbase/xenial,xenial 1:5.2.3~rc2-0ubuntu1~xenial1 all
  LibreOffice java test libraries

dave@dave-desktop:~$ 

```

---

### Post by aviator1 on 2016-11-25
Here is what I have tried so far:

Opened similar size spreadsheet using Libreoffice 5 on 16.04 (450KB/100K cells with about 50K with simple formulas).....................

Same issues as with current SS. I open, immediately close, and it freezes for 2.5 to 3.5 minutes. 1.6GB RAM being used and 1 core of CPU at 100%

I open the current SS with gnumeric. Slight delay, <5 seconds) and slight delay on save, <15 seconds. It does max out a core for those time periods. Uses no RAM either.

Opened current SS on 16.04 and saved to thumb drive as .xlsx and .ODS files. Both froze during save process for 2.5 to 3.5 minutes.

Opened and closed the .ODs SS on 12.04 with Libreoffice 3 with no problems. (Laptop with 2 GB RAM)

EDIT: Does not happen on smaller SS.

Opened and closed the .ODS SS on 14.04 with Libreoffice 4 with no problems. (very similar computer-8 core AMD with 16GB RAM)

Open and closed the .xlsx SS on Windows 7 ULT and Excel 2013 with no problems. (Laptop with 2 GB RAM) (Also, opened .ODS and converted to .xlsx with no problems)

Open and closed the .xlsx SS on Windows Vista and Excel 2003 (Had some formatting issues between .xls and .xlsx but no problems opening or closing-laptop with 2 GB RAM)

I have un-installed and re-installed Libreoffice 5. Notice that save paths stayed the same.

Any thoughts on the actual save process for Libreoffice 5?

---

### Post by aviator1 on 2016-11-25
What does this mean?
```

libreoffice-subsequentcheckbase/xenial,xenial 1:5.2.3~rc2-0ubuntu1~xenial1 all
  LibreOffice java test libraries
```

---

### Post by #&amp;thj^% on 2016-11-25
> **aviator1 said:**
> What does this mean?
```

libreoffice-subsequentcheckbase/xenial,xenial 1:5.2.3~rc2-0ubuntu1~xenial1 all
  LibreOffice java test libraries
```

Those should be just security updates.

---

