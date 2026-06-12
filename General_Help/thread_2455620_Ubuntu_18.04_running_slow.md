---
title: "Ubuntu 18.04 running slow"
date: 2020-12-23
forum: General Help
---

### Post by FrenchyFungus on 2020-12-23
Hello,

Our desktop computer was starting to get pretty sluggish, so a couple of weeks ago I did a fresh install of the OS (Ubuntu 18.04). Things were better for a few days, but that hasn't lasted.
Performance seems to get gradually worse throughout the day. It is almost entirely used for internet browsing, streaming TV and general office use, so nothing I would consider too intensive.

The computer is about 5 years old, so it's certainly not new, but I was hoping to get a few more years out of it at least. Specs are:

Intel Core i3 6100 Processor
4GB DDR4 2133Mhz Memory 
500GB SATA Hard Drive
Intel H110M Chipset Motherboard

Any advice or suggestions greatly appreciated.

---

### Post by TheFu on 2020-12-23
Reinstall is how to fix Windows stuff when it gets slow.  For Unix systems, it doesn't often help.
Almost always, performance issues can be traced to one of 3 things:
[LIST]
[*]failing hardware
[*]misconfigured hardware/drivers
[*]software bug
[/LIST]

Most of those would be logged in the system logs, so check those.  If you need help with that, google "ubuntu log files".
The CPU and RAM should be fine for normal browsing and streaming of video up to 1080p resolution.

My initial concern would be for the 500G HDD.  A new 500G SSD can be found as a drop-in replacement for around $50, but definitely check the system logs first.  

For extra credit, check the SMART data using smartctl.  There might be a GUI that will show SMART data, but it depends on your specific distro.  The CLI smartctl program requires being run 3 times to get data out, not just 1, so be certain to find a how-to ... or look for my posts in these forums which spell out how.

---

### Post by mrdc76 on 2020-12-24
Reinstalling 18.04 was pointless as 20.04 is available. The browser or a browser extension might be leaking memory. Disable browser extensions or change the browser to test.

---

### Post by guiverc on 2020-12-24
I'd agree with @mrdc76.  

(I'd for sure check hardware as @TheFu suggested; on almost any issue I check SMART health of my drives, if I can't recall last time I did a memory test, I usually do that too (*overnight*) and if the problem is related to freezing would for sure do a hardware scan (*visual check of capacitors, look at PSU power etc*).

 My desktop is a 2009 dell that is is rebooted about once a week, but on occasion does become rather sluggish.  The fix for me is closing my always-open `firefox` & `chromium`... give the system a little time to clean up the memory, then re-open them. 

Myself I don't think it's the browsers themselves, but add-ons I use, that I'm unwilling to give up. The browsers are fine without the extensions, but I'd rather use the extensions I have running &  restart browsers now and again.  (note: *at times I look at which is the problem & only restart that one browser, but usually I just restart both as that's faster [than working out which is using all the RAM/swap] & restarting both has better results...*)

---

### Post by TheFu on 2020-12-24
Yep. Low RAM will slow a system down.  Troubleshooting that is pretty easy. Use 'top' and 'free -hm'.
'top' shows the process list by which process is using the most CPU. It also shows RAM use.  As guiverc says, browsers, especially the big, huge, popular ones, are hogs.  They can easily eat 4G of memory.

I use 4 extensions in Firefox and none in Chromium or dillo or lynx.  My minimal extensions in Firefox sometimes cause issues - but I can't live without TreeStyleTabs.  Sometimes the leaks are a real issue. Other times, it isn't a problem for many weeks.  I just wait until my system starts feeling slow, then check 'top' and if firefox is using 8G of memory, close or kill it. For systems with 4G of RAM or less, having swap of 4.1G is important. Systems with more RAM generally don't get into too much trouble with swap, but I still use 4.1G so there is sufficient time for me to "feel" the slowing happen and take proactive steps.  Unix systems don't handle out of RAM situations very well.  I'd really like to tell a browser to never use more than 1G of RAM, period.

---

### Post by FrenchyFungus on 2020-12-28
Hi, thanks all for the help!

18.04 is installed rather than 20.04 for aesthetic preference/I'm used to it.

Running the SMART self-test in Disks returns "Disk is OK" and an "OK" assessment for each attribute. Is that the same thing that smartctl would do?

I will run a memory test overnight later.

free -hm gives:
```

              total        used        free      shared  buff/cache   available
Mem:           3.7G        2.0G        172M        586M        1.6G        967M
Swap:          2.0G          0B        2.0G

```

There's only one addon installed in Firefox (AdBlock), so little scope for reducing that.

Can someone please point me towards a guide or something explaining what I should be looking for in the system logs?

Thanks again

---

### Post by FrenchyFungus on 2020-12-28
When playing a youtube video in Firefox, top shows:

```
PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND     
5464 <user>   20   0 3098776 367908 143084 S  52.5  9.4   3:23.07 Web Content 
1807 <user>   20   0 4222780 476500 184220 S  27.1 12.2   9:59.23 firefox     
```

That seems like a lot of CPU, no?

---

### Post by TheFu on 2020-12-28
> **FrenchyFungus said:**
> 18.04 is installed rather than 20.04 for aesthetic preference/I'm used to it.

As long as a release is supported for at least 1 more year, personal preference is a great reason to run a specific release.  I'm still running 16.04 on most of my systems, but wouldn't install it onto any new machines today ... or since around June 2020.

> **FrenchyFungus said:**
> Running the SMART self-test in Disks returns "Disk is OK" and an "OK" assessment for each attribute. Is that the same thing that smartctl would do?
SMART saying "OK" doesn't really say much.  Often, it means that the test ran, not that anything was OK. We need to look at the full data:
```
SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   016    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0005   138   138   054    Pre-fail  Offline      -       100
  3 Spin_Up_Time            0x0007   100   100   024    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0012   100   100   000    Old_age   Always       -       9
  5 Reallocated_Sector_Ct   0x0033   100   100   005    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000b   100   100   067    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   128   128   020    Pre-fail  Offline      -       18
  9 Power_On_Hours          0x0012   100   100   000    Old_age   Always       -       650
 10 Spin_Retry_Count        0x0013   100   100   060    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       9
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       34
193 Load_Cycle_Count        0x0012   100   100   000    Old_age   Always       -       34
194 Temperature_Celsius     0x0002   153   153   000    Old_age   Always       -       39 (Min/Max 25/47)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0022   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0008   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x000a   200   200   000    Old_age   Always       -       102
```
There are problems in the data above.  A little farther down in the report, there are clear errors listed ... 
```
  61 18 18 00 cf c7 40 08      00:02:43.691  WRITE FPDMA QUEUED
  61 20 10 d8 ce c7 40 08      00:02:43.691  WRITE FPDMA QUEUED
  61 28 08 70 ce c7 40 08      00:02:43.690  WRITE FPDMA QUEUED
  61 30 00 a0 ce c7 40 08      00:02:43.690  WRITE FPDMA QUEUED
```
and farther down:
```
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%       650         -
# 2  Short offline       Completed without error       00%       622         -
# 3  Short offline       Completed without error       00%       164         -
# 4  Short offline       Completed without error       00%        31         -
# 5  Short offline       Completed without error       00%        18         -
```
See - it says "_without error_", so everything is fine **BUT IT ISN'T FINE!!!!!**

I don't trust the GUI SMART tools because they dumb down the output to the point that it isn't useful.  The status of a disk changes over time. The only way to see those changes, is to run periodic reports and notice the changes **over time**.

> **FrenchyFungus said:**
> I will run a memory test overnight later.

free -hm gives:
```

              total        used        free      shared  buff/cache   available
Mem:           3.7G        2.0G        172M        586M        1.6G        967M
Swap:          2.0G          0B        2.0G

```
I think your swap is much too small.  Double it. Appears you have 4G of RAM which is shared with the iGPU.  If you run a modern browser, you need 4G of swap if more than 5 tabs are open. 

> **FrenchyFungus said:**
> There's only one addon installed in Firefox (AdBlock), so little scope for reducing that.
There are multiple AdBlockers and lots of fake ones that actually provide data back to people you'd probably not want to have that data. Please double-check - triple-check that the addon you have is actually reputable.

> **FrenchyFungus said:**
> Can someone please point me towards a guide or something explaining what I should be looking for in the system logs?
Google "ubuntu log files"
They aren't really ubuntu specific, but there is a guide written by either Canonical or the forum guys here at help.ubuntu.com or wiki.ubuntu.com that seems to be useful.

---

### Post by TheFu on 2020-12-28
Some youtube videos use a video codec that Google has been pushing, VP9, but isn't directly supported by browsers and GPU decoders. That means the CPU has to do all the video decoding.   And those to lines are using around 900MB of RAM, while reserving much more virtual memory (3G and 4.2G)

Bigger swap needed, IMHO.

---

### Post by HermanAB on 2020-12-28
It is no use poking around in the dark.  Run top or htop to see what is sapping the power and kill it.

---

