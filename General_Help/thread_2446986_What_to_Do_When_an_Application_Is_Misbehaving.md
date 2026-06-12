---
title: "What to Do When an Application Is Misbehaving?"
date: 2020-07-10
forum: General Help
---

### Post by scribner on 2020-07-10
One of the reasons I use Ubuntu Linux is it's supposedly more stable than Windows or Mac. However, since I installed Ubuntu on my current computer several weeks ago, it has crashed twice because of Firefox. When Firefox froze, I tried most of the methods on this Web page to kill the application: [https://www.howtogeek.com/211153/how-to-kill-a-desktop-application-or-background-process-on-linux/](https://www.howtogeek.com/211153/how-to-kill-a-desktop-application-or-background-process-on-linux/)

None of them worked. My computer was even freezing as I tried to restart it, so I ended up pushing the power button (which I know isn't a safe way to shut down a computer).

Why is this happening, and what can I do when this happens? I've had Macs that were able to have an uptime of over a year, so what gives with Ubuntu? Why isn't it as stable as my Macs?

By the way, I keep a tab opened at all times for Amazon Music ([https://music.amazon.com](https://music.amazon.com)), so I think that may be the culprit. But this doesn't seem right. Linux is supposed to be stable!

---

### Post by TheFu on 2020-07-10
Have you looked at the system logs?  What do they show?
What are the system specs -  **inxi -Fz** will tell us much but the log files are the most important.

My linux systems stay up until i bring them down.  Comparing Linux which supports infinite hardware combinations to Apple with 10 HW combinations isn't exactly fair.

---

### Post by scribner on 2020-07-10
> **TheFu said:**
> Have you looked at the system logs?  What do they show?
What are the system specs -  **inxi -Fz** will tell us much but the log files are the most important.

My linux systems stay up until i bring them down.  Comparing Linux which supports infinite hardware combinations to Apple with 10 HW combinations isn't exactly fair.

Could you tell me how to look at the system logs? Sorry, I'm a noob!

I installed inxi and ran **inxi -Fz**. I think this is a safe program, but can you prove it to me? Anyway, here is the output:

```
**[edited]**@**[edited]**-ThinkPad-X270:~$ inxi -Fz
System:
  Kernel: 5.4.0-39-generic x86_64 bits: 64 Desktop: Gnome 3.36.1 
  Distro: Ubuntu 20.04 LTS (Focal Fossa) 
Machine:
  Type: Laptop System: LENOVO product: 20HN004VUS v: ThinkPad X270 
  serial: <filter> 
  Mobo: LENOVO model: 20HN004VUS v: SDK0J40697 WIN serial: <filter> 
  UEFI: LENOVO v: R0IET57W (1.35 ) date: 03/25/2019 
Battery:
  ID-1: BAT0 charge: 20.1 Wh condition: 20.9/23.5 Wh (89%) 
  ID-2: BAT1 charge: 20.8 Wh condition: 20.8/23.5 Wh (88%) 
CPU:
  Topology: Dual Core model: Intel Core i5-7200U bits: 64 type: MT MCP 
  L2 cache: 3072 KiB 
  Speed: 1361 MHz min/max: 400/3100 MHz Core speeds (MHz): 1: 1400 2: 1401 
  3: 1408 4: 1401 
Graphics:
  Device-1: Intel HD Graphics 620 driver: i915 v: kernel 
  Display: x11 server: X.Org 1.20.8 driver: i915 resolution: 1366x768~60Hz 
  OpenGL: renderer: Mesa Intel HD Graphics 620 (KBL GT2) v: 4.6 Mesa 20.0.4 
Audio:
  Device-1: Intel Sunrise Point-LP HD Audio driver: snd_hda_intel 
  Sound Server: ALSA v: k5.4.0-39-generic 
Network:
  Device-1: Intel Ethernet I219-V driver: e1000e 
  IF: enp0s31f6 state: down mac: <filter> 
  Device-2: Intel Wireless 8265 / 8275 driver: iwlwifi 
  IF: wlp3s0 state: up mac: <filter> 
Drives:
  Local Storage: total: 167.68 GiB used: 10.10 GiB (6.0%) 
  ID-1: /dev/sda vendor: Intel model: SSDSC2KF180H6L size: 167.68 GiB 
Partition:
  ID-1: / size: 163.55 GiB used: 10.09 GiB (6.2%) fs: ext4 dev: /dev/sda2 
Sensors:
  System Temperatures: cpu: 50.0 C mobo: N/A 
  Fan Speeds (RPM): cpu: 3054 
Info:
  Processes: 221 Uptime: 1h 39m Memory: 7.55 GiB used: 1.96 GiB (26.0%) 
  Shell: bash inxi: 3.0.38 
```

Also, can you prove to me that posting this output on the Web is safe?

Thanks for your help!

---

### Post by deadflowr on 2020-07-10
>  can you prove to me that posting this output on the Web is safe?

Anything that could help determine personal information about the system has been filtered out, like here
```
Network:
  Device-1: Intel Ethernet I219-V driver: e1000e 
  IF: enp0s31f6 state: down mac: **<filter> **
  Device-2: Intel Wireless 8265 / 8275 driver: iwlwifi 
  IF: wlp3s0 state: up mac: **<filter>** 
```

All other information is already publicly available.
And holds no personal relation to you specifically.
(Exception being the prompt at the start, which you can edit out if you want.
And isn't part of the command anyway)

---

### Post by TheFu on 2020-07-10
```
man inxi
```
Read about the options.  it is a little late to be asking. ;)  I’ve posted my output here a few times, but everyone has a different idea about privacy and what's important.  Here, I’m considered one of the more paranoid posters.

The main reason i asked for that report was to see the GUi, GPU, RAM, storage and hopefully the swap.  Rather than asking and getting - i don't know - answers, the command above provided factual answers.

The computer seems to be running hot to me.  My laptop is at 38 degC now. A desktop is 44 degC.

initially, thought the system might have a GPU driver or low RAM issue.  intel GPUs are well supported, automatically and 8GB of RAM should be sufficient for most needs.  i like to have 4G of swap on my desktops but that only seems really important for 4G and smaller RAM systems.  **free -hm** should show the swap and buffers used.  

As for log files, if you use any web search tool for "ubuntu log files", then the top results are: 
[LIST]
[*][https://ubuntu.com/tutorials/viewing-and-monitoring-log-files](https://ubuntu.com/tutorials/viewing-and-monitoring-log-files)
[*][https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)
[*][https://askubuntu.com/questions/186276/where-are-all-the-major-log-files-located](https://askubuntu.com/questions/186276/where-are-all-the-major-log-files-located)
[/LIST]
Some distros have a log viewer - I’ve never used one of those, sorry.

Note the domains all have "ubuntu" in the name?  While not 100% foolproof, that is a good sign ime for a reputable source of, not terrible, ubuntu, information.  Logs aren't ubuntu-specific.

Often when any OS seems flakey, it is a hardware issue.

Sometimes "ubuntu" matters.  Most of the time it doesn't.  Only experience will provide clues as to when and where the specific distro, release, and/or GUI used matters.  Regardless, when posting for help it would be good to always say: "Ubuntu 20.04 Gnome3, 8G RAM, intel GPU, patched in the last week" as an intro.

---

### Post by scribner on 2020-07-10
Thanks, both of you, for getting back to me. I see I can view logs with the GNOME System Log Viewer ("Logs"). But I don't know which type of or portion of the logs you want. I'm guessing these logs should still be available, as this malfunctioning happened today, even though I did have to manually shut down the computer.

Do you think my laptop is running too hot? How should I monitor that, and what steps should I take to rectify it?

---

### Post by VMC on 2020-07-11
Check out [*lm-sensors*]("https://help.ubuntu.com/community/SensorInstallHowto") for the temperature issues.

---

### Post by TheFu on 2020-07-11
> **scribner said:**
> Thanks, both of you, for getting back to me. I see I can view logs with the GNOME System Log Viewer ("Logs"). But I don't know which type of or portion of the logs you want. I'm guessing these logs should still be available, as this malfunctioning happened today, even though I did have to manually shut down the computer.

Do you think my laptop is running too hot? How should I monitor that, and what steps should I take to rectify it?

I have no interest in seeing log files. That's like "work" and I'm hear volunteering, not working.

I have interest in YOU looking through the logs to find problems.  Common terms used for problems are "error" or "warning", so perhaps searching for those terms in all log files is useful.  If it was me, I'd use a search tool called "egrep", but you do it however you like. Use that GUI program if it works for your needs.

Different systems retain logs for different periods of time. There are configuration files to control that.  Some systems delete all logs with every reboot.  Others will keep 10G of logs - which is probably 3+ yrs worth.  I like to keep about 500MB of logs so about 2-4 weeks are retained.  The settings are in /etc/systemd/journald.conf, I think.   
My custom settings are:
```
Storage=persistent
SystemMaxFileSize=500M
SystemMaxFiles=10

```
But you can pick whatever settings are useful for your needs. 

Different computers have different normal operating temperatures for the different parts of the computer.  The laptop I was on when I posted those temperatures was a Core i5-8250U, so pretty close to what you have. I thought that could be relevant. Perhaps not? We are guessing at issues and overheating is a common problem on laptops.  IME, and heat related issues show up in the system log files.  I had a 2009 Core i7-920 desktop that would shutdown cores due to overheating when working hard.  After I cleaned dust out of the case, off the fans, and re-applied a fresh CPU thermal grease layer between the CPU and cooling apparatus, it didn't have those issues anymore.  Still, the system kept working and didn't crash, so I'm at a loss for the crashing ... really need to check the log files.

---

