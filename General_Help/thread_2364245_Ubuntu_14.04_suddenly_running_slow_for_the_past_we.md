---
title: "Ubuntu 14.04 suddenly running slow for the past week"
date: 2017-06-20
forum: General Help
---

### Post by swarup on 2017-06-20
I've been using Ubuntu 14.04 since it came out over three years ago. I have a fast computer, and it has always run very, very fast. Out of the blue, for the past 7-10 days, there are delays in every action. For example I use Thunderbird email client. In my inbox, just scrolling from one email to the next there are delays. If I want to move a mail from one folder to another there are delays in grabbing the email, and then in moving it. If I type something even in gedit, there are delays in the letters appearing. Could it be a change that was brought about by the software updater? Or could it be a virus or malware? I've been using Ubuntu since 2007, and never had any virus or malware. (Nor have I used any anyvirus or antimalware softare).

---

### Post by TheFu on 2017-06-20
Can you post some specs so we know what you are working with?  The output from **inxi -Fz** would be helpful. Please use *code tags*.

Also, with your obvious skill, have you determined what is using all the RAM, swap, and CPU?  Can you post that too?

If the file system is full, that has drastic impacts on performance.

Do the system logs show any issues?  Always check the logs.  That is where most hardware problems will show. A failing disk drive or loose cable can really impact performance too.

Seeing the relevant output from those things will lead to more ideas.

---

### Post by swarup on 2017-06-20
```
swarup@swarup:~$ inxi -Fz
System:    Host: swarup Kernel: 3.13.0-119-generic x86_64 (64 bit) Desktop: Gnome Distro: Ubuntu 14.04 trusty
Machine:   System: Apple (portable) product: MacBookPro5 2 version: 1.0
           Mobo: Apple model: Mac-F2268EC8 Bios: Apple version: MBP52.88Z.008E.B05.0905042202 date: 05/04/09
CPU:       Dual core Intel Core2 Duo CPU T9600 (-MCP-) cache: 6144 KB flags: (lm nx sse sse2 sse3 sse4_1 ssse3 vmx) 
           Clock Speeds: 1: 1596.00 MHz 2: 1596.00 MHz
Graphics:  Card-1: NVIDIA G96M [GeForce 9600M GT] 
           Card-2: NVIDIA C79 [GeForce 9400M] 
           X.Org: 1.15.1 drivers: nvidia (unloaded: fbdev,vesa,nouveau) Resolution: 1920x1200@60.0hz 
           GLX Renderer: GeForce 9400M/integrated/SSE2 GLX Version: 3.3.0 NVIDIA 340.102
Audio:     Card: NVIDIA MCP79 High Definition Audio driver: snd_hda_intel Sound: ALSA ver: k3.13.0-119-generic
Network:   Card-1: Broadcom BCM4322 802.11a/b/g/n Wireless LAN Controller driver: wl 
           IF: wlan0 state: up mac: <filter>
           Card-2: NVIDIA MCP79 Ethernet driver: forcedeth 
           IF: eth0 state: up speed: 100 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 121.3GB (54.8% used) 1: id: /dev/sda model: APPLE_SSD_TS128A size: 121.3GB 
Partition: ID: / size: 71G used: 62G (94%) fs: ext4 ID: swap-1 size: 8.32GB used: 2.99GB (36%) fs: swap 
RAID:      No RAID devices detected - /proc/mdstat and md_mod kernel raid module present
Sensors:   System Temperatures: cpu: 72.0C mobo: N/A gpu: 69C 
           Fan Speeds (in rpm): cpu: N/A 
Info:      Processes: 253 Uptime: 3 days Memory: 6932.9/7729.8MB Client: Shell (bash) inxi: 1.9.17 

```

When I open System Monitor, under "processes" it looks like the CPU is hardly being utilized. But when I look under the "resources" tab, it shows the two cpus mostly at 55-60% utilization, but sometimes rising up to 100% utilization. I guess the question is what is using the CPU? All I am running is two browsers (Firefox and Chromium), then gedit, TB, and kexi (Database). In Kexi I merely maintain tables, no complex data manipulation. 

I've also tried htop, conky, and ps aux | sort -k 3. I didn't see anything that looked suspicious there, but if any of the data produced from those would be useful to see, let me know and I can paste it here.

If there are other tools for getting useful info in this regard, then if you'd remind me of the commands for those items (to determine what is using the RAM, swap, and CPU etc), I'll be happy to supply them.

I'll just add: This is an apple system, but the issue is a generic system utilization issue and has nothing to do with this being an apple system. So advance request to administrators: Kindly refrain from moving this to the Apple forum. This is a generic 14.04 issue. Thanks.

---

### Post by HermanAB on 2017-06-21
Don't guess, measure.

To see what is going one, run the 'top' utility, then kill/fix whatever is tying the CPU up.

For network problems, there is also 'ntop'.

---

### Post by TheFu on 2017-06-21
Do the log files have anything relevant?

---

### Post by swarup on 2017-06-21
When I have my Chromium and Firefox browsers open, whatever cpu is getting utilized most of the usage is from them, perhaps because I keep quite a large number of tabs open at a top with them (Firefox around 30 tabs, chromium around 15). After I close them and run htop, there is hardly any utilization of the cpu at all. The main user becomes htop itself, at around 4.5%. But even in that condition, when I go to my TB inbox and try to move from one mail to the other in the inbox, there are delays. It is bizarre!

@TheFu: You asked about log files. Could you give me some guidance as to how to generate those so I can look at them or present them here?

---

### Post by TheFu on 2017-06-21
I typed "*ubuntu log files*" in to a search engine: [https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles) was at the top.

Chromium and Firefox are hogs. Using both at the same time with more than a few tabs is likely to hog all system resources.  Thunderbird is 50% lighter than Firefox, IME.  Is the mail local or remote?  I use an imap server.

BTW, I use all 3 of these programs, probably in a way similar to you on systems with half (or less) the amount of RAM you have, but with faster CPUs.

Your CPU is running VERY hot.  That means it could be slowing the clock speed for thermal management.  Clean out the dust, make sure the fan is working correctly.

```
  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND    
  698 root     -51   0       0      0      0 S   1.0  0.0   1:07.87 irq/37-ELA+
 2126 jp        20   0 3832804 1.095g  94792 S   1.0 29.3 114:06.35 firefox    
 1287 root      20   0  299712  57768  45336 S   0.7  1.5  17:04.07 Xorg       
 3029 jp        20   0 2781968 551132  81036 S   0.7 14.1  45:55.64 thunderbird
```
This system only has 4G of RAM total, some of that is used by the iGPU.  Firefox is sucking 3.7G now with 14 tabs and thunderbird 2.7G.  It has a Core i3 CPU about 2.5x faster than your CPU.

```
$ free -hm
              total        used        free      shared  buff/cache   available
Mem:           3.7G        1.7G        323M        108M        1.7G        1.6G
Swap:          4.1G         96M        4.0G
```
As you can see, through the magic of shared libraries, the memory use isn't just for those programs. Resident RAM usage is 1G and 500MB.  I'll restart firefox sometime today before all the RAM use, including virtual memory, eats through all the system resources.

But your system has much more RAM, so you can have many more tabs opened before FF crashes.

Check the log files.

---

### Post by swarup on 2017-06-21
Actually I counted the tabs I keep open in Firefox-- over 60 tabs. But I've been doing this for the past ten years with this computer, and for the past two years with Chromium open as well at the same time with 15-25 tabs open. Never a problem at all until the past 7-10 days. And even if I close both browsers, the problem-- that is the delays-- persist. For example, even when both browsers are closed, there are delays in TB with simply opening mails or scrolling through the inbox. In reply to your question re TB, it is a pop3 I use, with Earthlink.

I used the following command, for the log output: 

```
while true; do (echo "%CPU %MEM ARGS $(date)" && ps -e -o pcpu,pmem,args --sort=pcpu | cut -d" " -f1-5 | tail) >> ps.log; sleep 5; done
```

Here is the result:

```
%CPU %MEM ARGS Wed Jun 21 10:40:52 EDT 2017
 0.2  0.3 /usr/lib/unity/unity-panel-service
 0.3  1.1 nemo
 0.4  0.3 C:\Program
 1.0  0.3 gedit
 1.7  0.0 bash
 1.8  1.9 compiz
 3.2  5.0 /usr/lib/thunderbird/thunderbird
 5.3  2.4 /usr/bin/X
 5.6  0.2 gnome-terminal
25.4  4.5 /usr/lib/firefox/firefox
%CPU %MEM ARGS Wed Jun 21 10:40:57 EDT 2017
 0.2  0.3 /usr/lib/unity/unity-panel-service
 0.3  1.1 nemo
 0.4  0.3 C:\Program
 0.8  0.0 bash
 1.0  0.3 gedit
 1.8  1.9 compiz
 3.1  0.2 gnome-terminal
 3.2  5.0 /usr/lib/thunderbird/thunderbird
 5.3  2.4 /usr/bin/X
25.0  4.5 /usr/lib/firefox/firefox
%CPU %MEM ARGS Wed Jun 21 10:41:02 EDT 2017
 0.2  0.3 /usr/lib/unity/unity-panel-service
 0.4  1.1 nemo
 0.4  0.3 C:\Program
 0.5  0.0 bash
 1.0  0.3 gedit
 1.8  1.9 compiz
 2.0  0.2 gnome-terminal
 3.2  5.0 /usr/lib/thunderbird/thunderbird
 5.4  2.4 /usr/bin/X
24.7  4.5 /usr/lib/firefox/firefox
%CPU %MEM ARGS Wed Jun 21 10:41:07 EDT 2017
 0.2  0.3 /usr/lib/unity/unity-panel-service
 0.4  1.1 nemo
 0.4  0.3 C:\Program
 0.4  0.0 bash
 1.0  0.3 gedit
 1.5  0.2 gnome-terminal
 1.8  1.9 compiz
 3.2  5.0 /usr/lib/thunderbird/thunderbird
 5.4  2.4 /usr/bin/X
24.3  4.5 /usr/lib/firefox/firefox
%CPU %MEM ARGS Wed Jun 21 10:41:12 EDT 2017
 0.2  0.3 /usr/lib/unity/unity-panel-service
 0.3  0.0 bash
 0.4  1.1 nemo
 0.4  0.3 C:\Program
 1.0  0.3 gedit
 1.2  0.2 gnome-terminal
 1.8  1.9 compiz
 3.2  5.0 /usr/lib/thunderbird/thunderbird
 5.4  2.4 /usr/bin/X
23.9  4.5 /usr/lib/firefox/firefox
%CPU %MEM ARGS Wed Jun 21 10:41:17 EDT 2017
 0.2  0.3 /usr/lib/unity/unity-panel-service
 0.2  0.0 bash
 0.4  1.1 nemo
 0.4  0.3 C:\Program
 1.0  0.3 gedit
 1.0  0.2 gnome-terminal
 1.8  1.9 compiz
 3.2  5.0 /usr/lib/thunderbird/thunderbird
 5.4  2.4 /usr/bin/X
23.5  4.5 /usr/lib/firefox/firefox
%CPU %MEM ARGS Wed Jun 21 10:41:22 EDT 2017
 0.2  0.3 /usr/lib/unity/unity-panel-service
 0.2  0.0 bash
 0.4  1.1 nemo
 0.4  0.3 C:\Program
 0.8  0.2 gnome-terminal
 1.0  0.3 gedit
 1.8  1.9 compiz
 3.2  5.0 /usr/lib/thunderbird/thunderbird
 5.4  2.4 /usr/bin/X
23.2  4.5 /usr/lib/firefox/firefox
%CPU %MEM ARGS Wed Jun 21 10:41:27 EDT 2017
 0.2  0.3 /usr/lib/unity/unity-panel-service
 0.2  0.0 bash
 0.4  1.1 nemo
 0.4  0.3 C:\Program
 0.7  0.2 gnome-terminal
 1.0  0.3 gedit
 1.8  1.9 compiz
 3.2  5.0 /usr/lib/thunderbird/thunderbird
 5.4  2.4 /usr/bin/X
22.9  4.5 /usr/lib/firefox/firefox
%CPU %MEM ARGS Wed Jun 21 10:41:32 EDT 2017
 0.2  0.6 /usr/lib/x86_64-linux-gnu/hud/hud-service
 0.2  0.3 /usr/lib/unity/unity-panel-service
 0.4  1.1 nemo
 0.4  0.3 C:\Program
 0.6  0.2 gnome-terminal
 1.0  0.3 gedit
 1.8  1.9 compiz
 3.2  5.0 /usr/lib/thunderbird/thunderbird
 5.4  2.4 /usr/bin/X
22.5  4.6 /usr/lib/firefox/firefox
%CPU %MEM ARGS Wed Jun 21 10:41:38 EDT 2017
 0.2  0.6 /usr/lib/x86_64-linux-gnu/hud/hud-service
 0.2  0.3 /usr/lib/unity/unity-panel-service
 0.4  1.1 nemo
 0.4  0.3 C:\Program
 0.6  0.2 gnome-terminal
 1.0  0.3 gedit
 1.8  1.9 compiz
 3.2  5.0 /usr/lib/thunderbird/thunderbird
 5.4  2.4 /usr/bin/X
22.2  4.6 /usr/lib/firefox/firefox
%CPU %MEM ARGS Wed Jun 21 10:41:43 EDT 2017
 0.2  0.6 /usr/lib/x86_64-linux-gnu/hud/hud-service
 0.2  0.3 /usr/lib/unity/unity-panel-service
 0.4  1.1 nemo
 0.4  0.3 C:\Program
 0.5  0.2 gnome-terminal
 0.9  0.3 gedit
 1.8  1.9 compiz
 3.3  5.0 /usr/lib/thunderbird/thunderbird
 5.4  2.4 /usr/bin/X
21.9  4.6 /usr/lib/firefox/firefox
%CPU %MEM ARGS Wed Jun 21 10:41:48 EDT 2017
 0.2  0.6 /usr/lib/x86_64-linux-gnu/hud/hud-service
 0.2  0.3 /usr/lib/unity/unity-panel-service
 0.4  1.1 nemo
 0.4  0.3 C:\Program
 0.5  0.2 gnome-terminal
 1.1  0.3 gedit
 1.8  1.9 compiz
 3.3  4.9 /usr/lib/thunderbird/thunderbird
 5.5  2.4 /usr/bin/X
21.6  4.6 /usr/lib/firefox/firefox
%CPU %MEM ARGS Wed Jun 21 10:41:53 EDT 2017
 0.2  0.6 /usr/lib/x86_64-linux-gnu/hud/hud-service
 0.2  0.3 /usr/lib/unity/unity-panel-service
 0.4  1.1 nemo
 0.4  0.3 C:\Program
 0.4  0.2 gnome-terminal
 1.1  0.3 gedit
 1.8  1.9 compiz
 3.3  4.9 /usr/lib/thunderbird/thunderbird
 5.5  2.4 /usr/bin/X
21.4  4.6 /usr/lib/firefox/firefox
%CPU %MEM ARGS Wed Jun 21 10:41:58 EDT 2017
 0.2  0.6 /usr/lib/x86_64-linux-gnu/hud/hud-service
 0.2  0.3 /usr/lib/unity/unity-panel-service
 0.4  1.1 nemo
 0.4  0.3 C:\Program
 0.4  0.2 gnome-terminal
 1.2  0.3 gedit
 1.8  1.9 compiz
 3.3  5.0 /usr/lib/thunderbird/thunderbird
 5.5  2.4 /usr/bin/X
21.1  4.6 /usr/lib/firefox/firefox
%CPU %MEM ARGS Wed Jun 21 10:42:03 EDT 2017
 0.2  0.6 /usr/lib/x86_64-linux-gnu/hud/hud-service
 0.2  0.3 /usr/lib/unity/unity-panel-service
 0.4  1.1 nemo
 0.4  0.3 C:\Program
 0.4  0.2 gnome-terminal
 1.1  0.3 gedit
 1.8  1.9 compiz
 3.3  4.9 /usr/lib/thunderbird/thunderbird
 5.6  2.4 /usr/bin/X
20.9  4.6 /usr/lib/firefox/firefox
%CPU %MEM ARGS Wed Jun 21 10:42:08 EDT 2017
 0.2  0.6 /usr/lib/x86_64-linux-gnu/hud/hud-service
 0.2  0.3 /usr/lib/unity/unity-panel-service
 0.4  1.1 nemo
 0.4  0.3 C:\Program
 0.4  0.2 gnome-terminal
 1.2  0.3 gedit
 1.8  1.9 compiz
 3.3  4.9 /usr/lib/thunderbird/thunderbird
 5.6  2.4 /usr/bin/X
20.6  4.7 /usr/lib/firefox/firefox 
```

Incidentally, although the problem is nearly constant, it is not always there. Right now, while I created the above log file, things are working normally. You mentioned the temperature of the CPU. Could that be the entire problem? Would the CPU dysfunction at the temperatures noted? I have been working with ambient temperature of 80-82 degrees F (28 C). Although that happens every summer, and it never slowed the computer down before.

---

### Post by TheFu on 2017-06-21
[https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)

What do they say?

---

### Post by swarup on 2017-06-21
What does *who* say?

That is quite a lengthy link containing many different types of log files. If you would give a bit more pointed guidance as to what sort of log file will be helpful, I'd be happy to execute it and see what it says.

---

### Post by TheFu on 2017-06-21
Looking through **all** the log files has been suggested because it could be anything.  That link was an answer to a prior question - which log files.  ALL OF THEM.  I would start with grep'ing for errors and warnings for the non-compressed files. That should provide some files, since there are always errors.  Then look in each file just above where the errors are.  
```
$ sudo egrep -in 'error|warn' /var/log/*log
```

I see about 40 errors. Most aren't important. Half of the remaining were due to suspend errors with file systems, encryption and network interfaces.  There's a gvfs issue - but I don't use that, so it isn't important.  And there is a chromium segfault in libxul.

Issues in dpkg.log file probably don't matter. Use your judgment.

I'd look mostly for disk failures and CPU step-down due to overheating.  I have a box that does that all the time.
```
[559787.259534] CPU0: Core temperature above threshold, cpu clock throttled (total events = 20316369)
[559787.259536] CPU4: Core temperature above threshold, cpu clock throttled (total events = 20316478)
[559787.260534] CPU4: Core temperature/speed normal
[559787.260535] CPU0: Core temperature/speed normal

```  It is transcoding some TV recordings, which is extremely CPU intensive.

Oh ... and look at **dmesg** too. That's a command.

---

### Post by swarup on 2017-06-21
I ran the command:
```
$ sudo egrep -in 'error|warn' /var/log/*log
```

I've pasted the output at this link:

[https://paste.ubuntu.com/24919581/](https://paste.ubuntu.com/24919581/) 

There was a bunch of output before this, but I think there were so many lines of output that the terminal window only kept these lines, which are the final section.

And the output of dmesg, I've placed at this link:

[https://paste.ubuntu.com/24919598/](https://paste.ubuntu.com/24919598/)

Same goes for the above-- there were so many lines of output that the terminal window only kept these lines, which are the final section.

I am really not able to interpret these lines, so if you would have a look at them and let me know what you think, I would be very grateful.

---

### Post by swarup on 2017-06-22
I think I may have discovered a major player in my CPU overusage as well as overheating. I have completely closed the chromium browser, some time ago. Now when I run htop, it shows me that the top user of the cpu is the Chromium browser. And the Chromium browser is closed! See below:

[ATTACH=CONFIG]275732[/ATTACH][ATTACH=CONFIG]275732[/ATTACH][ATTACH=CONFIG]275732[/ATTACH]

I highlighted that top-most process using >40% of the cpu and forcefully closed it using F9 in htop. The cpu usage immediately dropped from 48% to 3%, and the fan dropped to a whisper over the following 2 minutes. 

My question is why are there all these chromium process running, when the chromium browser itself has been closed?

---

### Post by dragonfly41 on 2017-06-23
Chromium processes can be launched from other applications, not just chromium browser.  Perhaps by teamviewer, for example? If you shut down teamviewer do you still see chromium processes running?

---

### Post by swarup on 2017-06-23
@dragonfly: Excellent point! I never use teamviewer, haven't used it for years. But it always runs in the background. So now I've uninstalled teamviewer completely. That should help.

But how can I get a list of applications that would launch Chromium processes, when the Chromium browser is not even open?

---

### Post by dragonfly41 on 2017-06-23
> But how can I get a list of applications that would launch Chromium processes, when the Chromium browser is not even open?

I would try listing the apps you are running and go through them using this command to look at their dependencies.

apt-cache depends package-name

e.g. apt-cache depends gedit

...


If you do not use wine I would consider uninstalling it if there are no other windows programs to run.

...

I use Chromium Browser as my default browser.

If you launch System Tools > System Monitor > Processes tab you will see running processes (just like htop but in a GUI).

Now click on Process Name tab to sort processes by name.

You will see a &#8220;chromium-browser --type=renderer&#8221; process for each browser tab you have open, plus other chromium-browser processes for the browser itself.

If you right click on any chromium-browser name select Properties.

e.g. in my display &#8220;chromium-browser --enable-pinch&#8221; shows Properties
Status Running
CPU 2%

This is the parent browser process.

Only the active browser tab has Status Running.  All the other tabs have Status Sleeping.


[Later edit]

I have just remembered.
If you click on top right icon in System Monitor you can click "dependencies" to see a process tree structure.

---

### Post by swarup on 2017-06-23
@dragonfly: Very helpful, thank you. 

Just one thing I couldn't try:
> If you right click on any chromium-browser name select Properties
Here on right clicking all the options were greyed out. 

Actually now that I've killed several processes and uninstalled a few applications, the computer cpu is hardly being utilized, the fan is quiet, and the cpu is running cool. So all this is a great success and a great relief!

Only one problem remains: There is still the mystery of delays when typing in gedit or in TB, or when scrolling through mail in TB. These seem like not very energy intensive processes, and it is quite mysterious to me why even after getting down to a very reasonable cpu utilization level of 3 or 4% when all internet browsers are closed, and 15-20% when the browsers (Firefox and Chromium both with 30-60 tabs open) are running, still I have these funky delays in small tasks.

---

### Post by dragonfly41 on 2017-06-24
> [COLOR=#000000]There is still the mystery of delays when typing in gedit or in TB, or when scrolling through mail in TB.[/COLOR][COLOR=#000000]

This is what I would try to pin this down   ....

1.  Try running gedit standalone from terminal .. to see if typing lag continues ..
```
gedit -s
```

2. Try backing up Thunderbird profile and create a new profile to see if lag continues (warning: I see that you are using POP, so you might get some emails which you cannot recreate in your original profile)

3. Do you see these symptoms if you logout and login to another user profile such as guest (or add a new user account)?

4. Close down browsers while trying these tests.





[/COLOR]

---

