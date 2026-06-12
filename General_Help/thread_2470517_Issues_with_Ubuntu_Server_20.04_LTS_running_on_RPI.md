---
title: "Issues with Ubuntu Server 20.04 LTS running on RPI4b"
date: 2022-01-02
forum: General Help
---

### Post by guillaumesoucy on 2022-01-02
Hello everybody,  
 
 
 I have Ubuntu 20.04 Server LTS installed on one of my Raspberry PI 4b and it seem to periodically crashing. It look at the Ubuntu’s logs but I couldn’t identified the issue.
 
 
 I notice when getting the issue happen, the network port activity led is still blinking. I’m not sure if it is only openssh-server of crashing or the entire machine.  
 
 
 There the logs: [ATTACH]289717[/ATTACH]

 
 
 Thank-you in advance for help!
 
 
 Guillaume

---

### Post by DuckHook on 2022-01-04
[list=1]
[*]What do you mean by periodically crashing? Every day? Once a week?
[*]The logs are unrevealing. Do they overlap a crash? If so, is it the period between Jan 1 & 2? If not, then you need to look at the logs of events just prior to the a crash. kern.log is also sometimes revealing. But these days, a: ```
sudo journalctl -p err
```…is often the most informative.
[*]Don't just post a raw log. The chances of someone bothering to dive into your massive logs is small unless you make it much easier on us. It starts with bookmarking when the crash occurs in the log timestamps. You can also try prefiltering out the irrelevant lines with grep.
[*]What is your physical setup? Provide list of all peripherals connected to RPi.
[/list]
I have three RPi 4b running Focal with no problems. How long have you been running them? How active are they? What do you run on them?

Do be aware that the standard RPi setup using SD cards can be a weak point: SD cards have limited write cycles and running a typical Ubuntu install will cause a lot of write wear. This can manifest in oddball behaviour that is difficult to pin down.

---

### Post by guillaumesoucy on 2022-01-08
Hello, 

It could happen only once a week like it can be three or four time a week. Like today, I power cycle the machine at around 9 AM and it crash around noon.

```
sudo journalctl -p err
``` give me this:

```
-- Logs begin at Wed 2021-07-21 15:00:22 EDT, end at Sat 2022-01-08 14:04:42 EST. --
Jul 21 15:00:22 ubuntu kernel: spi-bcm2835 fe204000.spi: could not get clk: -517
-- Reboot --
Jul 21 15:00:22 ubuntu kernel: bcm2708_fb soc:fb: Unable to determine number of FBs. Disabling driver.
Jul 21 15:00:22 ubuntu kernel: spi-bcm2835 fe204000.spi: could not get clk: -517
-- Reboot --
Jul 21 15:00:22 flood-001-01 kernel: bcm2708_fb soc:fb: Unable to determine number of FBs. Disabling driver.
Jul 21 15:00:22 flood-001-01 kernel: spi-bcm2835 fe204000.spi: could not get clk: -517
-- Reboot --
Jul 21 15:00:22 ubuntu kernel: bcm2708_fb soc:fb: Unable to determine number of FBs. Disabling driver.
Jul 21 15:00:22 ubuntu kernel: spi-bcm2835 fe204000.spi: could not get clk: -517
-- Reboot --
Jul 21 15:00:22 ubuntu kernel: bcm2708_fb soc:fb: Unable to determine number of FBs. Disabling driver.
Jul 21 15:00:22 ubuntu kernel: spi-bcm2835 fe204000.spi: could not get clk: -517
-- Reboot --
Jul 21 15:00:22 ubuntu kernel: spi-bcm2835 fe204000.spi: could not get clk: -517
-- Reboot --
Jul 21 15:00:22 flood-001-01 kernel: spi-bcm2835 fe204000.spi: could not get clk: -517
-- Reboot --
Jul 21 15:00:22 ubuntu kernel: spi-bcm2835 fe204000.spi: could not get clk: -517
-- Reboot --
Jul 21 15:00:22 ubuntu systemd[841]: /usr/lib/systemd/system-generators/netplan failed with exit status 1.
-- Reboot --
Jul 21 15:00:22 ubuntu systemd[842]: /usr/lib/systemd/system-generators/netplan failed with exit status 1.
-- Reboot --
Jul 21 15:00:22 ubuntu systemd[845]: /usr/lib/systemd/system-generators/netplan failed with exit status 1.
-- Reboot --
Jul 21 15:00:23 ubuntu kernel: bcm2835-isp bcm2835-isp: bcm2835_isp_get_supported_fmts: port has more encoding than we provided space for. Some are dropped.
-- Reboot --
Jul 21 15:00:23 ubuntu kernel: bcm2835-isp bcm2835-isp: bcm2835_isp_get_supported_fmts: port has more encoding than we provided space for. Some are dropped.
-- Reboot --
Jul 21 15:00:23 ubuntu kernel: : bcm2835_codec_get_supported_fmts: port has more encoding than we provided space for. Some are dropped.
-- Reboot --
Jul 21 15:00:23 ubuntu kernel: : bcm2835_codec_get_supported_fmts: port has more encoding than we provided space for. Some are dropped.
-- Reboot --
Jul 21 15:00:23 ubuntu kernel: bcm2835-isp bcm2835-isp: bcm2835_isp_get_supported_fmts: port has more encoding than we provided space for. Some are dropped.
-- Reboot --
Jul 21 15:00:23 ubuntu kernel: bcm2835-isp bcm2835-isp: bcm2835_isp_get_supported_fmts: port has more encoding than we provided space for. Some are dropped.
-- Reboot --
Jul 21 15:00:23 flood-001-01 kernel: bcm2835-isp bcm2835-isp: bcm2835_isp_get_supported_fmts: port has more encoding than we provided space for. Some are dropped.
-- Reboot --
Jul 21 15:00:23 flood-001-01 kernel: bcm2835-isp bcm2835-isp: bcm2835_isp_get_supported_fmts: port has more encoding than we provided space for. Some are dropped.
Jul 21 15:00:23 flood-001-01 kernel: : bcm2835_codec_get_supported_fmts: port has more encoding than we provided space for. Some are dropped.
-- Reboot --
Jul 21 15:00:23 ubuntu kernel: : bcm2835_codec_get_supported_fmts: port has more encoding than we provided space for. Some are dropped.
-- Reboot --
Jul 21 15:00:23 flood-001-01 kernel: : bcm2835_codec_get_supported_fmts: port has more encoding than we provided space for. Some are dropped.
-- Reboot --
Jul 21 15:00:23 ubuntu kernel: : bcm2835_codec_get_supported_fmts: port has more encoding than we provided space for. Some are dropped.
-- Reboot --
Jul 21 15:00:23 ubuntu kernel: brcmfmac: brcmf_fw_alloc_request: using brcm/brcmfmac43455-sdio for chip BCM4345/6
-- Reboot --
Jul 21 15:00:23 ubuntu kernel: brcmfmac: brcmf_fw_alloc_request: using brcm/brcmfmac43455-sdio for chip BCM4345/6
-- Reboot --
Jul 21 15:00:23 flood-001-01 kernel: brcmfmac: brcmf_fw_alloc_request: using brcm/brcmfmac43455-sdio for chip BCM4345/6
-- Reboot --
Jul 21 15:00:23 ubuntu kernel: brcmfmac: brcmf_fw_alloc_request: using brcm/brcmfmac43455-sdio for chip BCM4345/6
```

Is there a way to see the system load just before it crash? A kind of load history? BCM look the be the CPU.

Concerning the setup, there only two things plugged into the Pi, power adapter (the official one) and a network cable. The SD card is brand new. It is a good brand, Kingston and the usage is very low, the only thing that I ran is wget to download files from the internet. Each time that I connect to it , the load is very low, less than 0.3. There no screen/keyboard connected to the Pi as I manage it from the SSH. 

The setup is old from December 2021 (the Pi is from 2019 but the MicroSD is new from last December.)

THanks, 

Guillaume

---

### Post by guillaumesoucy on 2022-01-11
Hello, 

Any idea?

Thank-you

Guillaume

---

### Post by DuckHook on 2022-01-11
Reading your original post more carefully:
> **guillaumesoucy said:**
> &#8230;I notice when getting the issue happen, the network port activity led is still blinking. I&#8217;m not sure if it is only openssh-server of crashing or the entire machine.  

So I assume that you SSH into the RPi? If so, then the next time it "crashes", try plugging in a monitor and keyboard to see if the basic machine is still running.

I'm at a bit of a loss to suggest next steps to you. I believe that the logs are still your best bet.

What apps have you installed? You are using it as a server, but no file storage, so what kind of server?

The only other idea I have is to create another server on another SD card (so cheap these days) and try that one. It may be that your current install is corrupted for some reason.

Where did you get the server image? Was it direct from Canonical here: [https://ubuntu.com/raspberry-pi](https://ubuntu.com/raspberry-pi)
&#8230;or from RPI?: [https://www.raspberrypi.org/downloads./](https://www.raspberrypi.org/downloads./)

These are the only images you should be using. Do not use images from any other source. If one of them is giving you the trouble, try the other.

---

### Post by guillaumesoucy on 2022-01-18
Yes, I will have a to plug a monitor ans keyboard because it keep crashing. I will need to do it on next Saturday. 

I'm only downloading things with wget nothing very heavy. 

The SD card is brand new but will try another one. 

I took the image from Canonical. 

Thanks, 

Guillaume

---

### Post by DuckHook on 2022-01-18
Is the RPi in a remote location? It's challenging to diagnose issues or solve problems when you don't have physical access to the device and the only means of access (ssh) is the very service that keeps crashing.

Further things to try/look into:

[list=1]
[*]It may be that your downloading drops or hangs your whole network service (just a wild guess&#8212;without log data it is impossible to do anything but guess). Try invoking wget from a terminal multiplexer like *screen* or *tmux*, then detaching the session to free up the tty. If you are lucky, even if the screen/tmux session hangs, you will still be able to ssh into the server.
[*]Make sure you are fully updated.
[*]If problem persists with new SD card, you may wish to try the standard release (currently Impish), or even Ubuntu Core instead. Note that things will work a bit differently in Core. Everything is done through snaps, not the normal repos.
[*]Make sure you are running 64 bit, not 32.
[/list]

---

### Post by guillaumesoucy on 2022-01-18
The RPi is at my place but I'm in another town during weekday for work reasons. During weekends I do have a physical access to the RPi. I will try first to plugin a screen and a keyboard first to know if the entire machine is freezing or if its only the ssh service.

wget is running with the -b flag so it is in the background. 

The OS is fully updated, on a daily basis.

I'm currently running 20.04, it certainly worth trying 21.1. 

My RPi running the 64 bit version. 

Thank-you, 

Guillaume

---

### Post by DuckHook on 2022-01-18
Ah. I see.

Even if wget is pushed to the background it is still worth trying one of the multiplexers.

Also worth exploring: run wget within a VM or a container (Docker or LXD)

The idea is to isolate the wget process as much as possible so that it does not interfere with the host system.

These are just steps in the troubleshooting process. I'm not even sure that wget is the problem. It is a simple, elegant app that has been around since forever and is stable and rock solid. Netplan is newer and the problem may be there. As already said, without log data, it's just groping in the dark.

Do you connect via ethernet or WIFI? When doing stuff like intense DLing, best to use ethernet. If WIFI, problem could also be with that.

---

### Post by HermanAB on 2022-01-18
Put the RPi on a proper UPS, or at least a decent surge suppressor and it will be much happier.

---

### Post by DuckHook on 2022-01-18
> **HermanAB said:**
> Put the RPi on a proper UPS, or at least a decent surge suppressor and it will be much happier.

&#8593; &#128077; &#8593;

---

### Post by guillaumesoucy on 2022-01-18
For the logs, can I post them again, this is not a problem. I just don't want annoy peoples with my logs. ;-)

For the multiplexer, I do connecting to my workstation remotely using x2goclient/server, if the idea of the terminal multiplexer is to keep things on the foreground to monitor, I can leave the terminal with the ssh connection to the problematic RPi open on my workstation. Even If disconnect everything will stay as-is (this is why I do work using remote workstation). 

For the connection medium it use gigabit ethernet. 

@HermanAB The RPi and the entire network devices are on UPS(s) and backed by a diesel Caterpillar standby generator. But the question worth to be asked as dirty power can effectively disturb electronics included RPi. ;-)


Thanks, 

Guillaume

---

### Post by TheFu on 2022-01-18
> **guillaumesoucy said:**
> F But the question worth to be asked as dirty power can effectively disturb electronics included RPi. ;-)
 

Yes. Dirty power is bad. Was that a serious question?
You can also try a different tty.  <cntl><alt>F2 - F8

I would stop patching the daily too.  That isn't sufficiently stable to figure out what is wrong.  I patch weekly.

---

### Post by DuckHook on 2022-01-19
> **guillaumesoucy said:**
> For the logs, can I post them again, this is not a problem. I just don't want annoy peoples with my logs. ;-)
I don't think you will annoy anyone if you first go through them yourself and get rid of the unimportant stuff, which is the large majority.

There is admittedly a technique and a learning curve to reading logs, though hopefully one that you won't find too steep.

You/we are looking for events just before a crash. All of the stuff that is logged during boot is unimportant, so please do at least some filtering first before posting.
> …if the idea of the terminal multiplexer is to keep things on the foreground to monitor, I can leave the terminal with the ssh connection to the problematic RPi open on my workstation…
This is one reason but not the only one. The other reason(s) are to decouple your wget session from your shell so that if wget hangs, it won't affect your shell. Again, this is not likely, but every little thing helps.
> **TheFu said:**
> …Was that a serious question?
I believe OP was not asking a question but making a statement agreeing that dirty power is bad.

---

### Post by guillaumesoucy on 2022-02-06
Okay so, after one week it froze again, no SSH access, physical keyboard not responding. I took a picture of the connected screen this morning:

[https://ubuntuforums.org/attachment.php?attachmentid=289975&stc=1](https://ubuntuforums.org/attachment.php?attachmentid=289975&stc=1)

Um, yesterday morning it had only four lines that I can’t remember, next time gonna picture that screen as well.

Thank-you

Guillaume

---

### Post by TheFu on 2022-02-07
Please realize that you can boot using a "Try Ubuntu" flash drive/ISO and see all the logs on the storage device, copy the relevant lines somewhere as text and post just the text. Showing more than 3 lines with the same error might feel good, but a few lines BEFORE and after the error will be extremely helpful.

If I were going to try to help, I'd want to select the error and put it into google to search. I might add "ubuntu xx.xx" <---- where xx.xx is the release number for the OS to narrow down results.  Also, if this isn't an application error, then I'd want to check the kernel bug database for the error.  Ubuntu has a built-in error reporting facility. apport-bug. It collects all the logs that the bug team would like.

---

### Post by DuckHook on 2022-02-07
&#8593; &#128077; &#8593;

I hope the participants in this other thread won't mind: [https://ubuntuforums.org/showthread.php?t=2471707](https://ubuntuforums.org/showthread.php?t=2471707)

…but the process that this other member went through is the proper way to present log information so that others can help.

[LIST=1]
[*]Nail down the time of the crash,
[*]Include the log info from ten or twenty lines before the crash—more if it seems relevant,
[*]Post the log data as code and not as a screenshot (which is almost impossible to read). TheFu has discussed how to get that info off of a crashed box.
[/LIST]

---

### Post by MAFoElffen on 2022-02-08
This is what I usually ask people to do... Find the crash. Find a keyword or timestamp to ID it (something to ID that line of the log).

Use:
```

dmesg | grep -b100 'timestamp_or_other keyword' > ~/extracted_log.txt

```

Have the User upload it to a pastebin.

From there I can search my own keywords, or download to a text file to analyze.

Screen shots are hard to analyze.

I'm a 'helper"... But please help people to be able to help you.

---

### Post by TheFu on 2022-02-08
I like 
```
$ sudo egrep -i -A5 -B5 'error|warn' /var/log/*g
```

Lots of ways to get the data.  journalctl has some great filtering capabilities, but that quickly becomes dependent on the subsystem with the issue. Find a journalctl how-to guide and it can get us almost anything we need.

---

### Post by #&amp;thj^% on 2022-02-08
> **TheFu said:**
> I like 
```
$ sudo egrep -i -A5 -B5 'error|warn' /var/log/*g
```

Lots of ways to get the data.  journalctl has some great filtering capabilities, but that quickly becomes dependent on the subsystem with the issue. Find a journalctl how-to guide and it can get us almost anything we need.

Dude you are just full of little Gems Today. I do not why I haven't thought of this myself. (keeper)
Sorry Off Topic

---

### Post by MAFoElffen on 2022-02-08
As TheFu said  sometimes depending on SubSystems... 

Relating to sometimes things bleed over from an overload of other systems. for example, in the OP's post of output in Post #3, it shows he is running headless, but has his HDMI port left on. After the output of that port not being connected had enough errors, it started shutting ports and chips down to stop the overflow of errors... Just saying that some things can be remotely connected or affected.

I have Raspberry PI4 with Ubuntu Server 20.04.03. And yes, in a blue moon, I admit, it freezes. With a reboot, It continues for 'months' of uptime. In my own experience and for what I run on it, it is inconvenient. Maybe I 'should" look more into it. But since it corrects itself on reboot, I haven't.

---

### Post by guillaumesoucy on 2022-02-17
Ok thanks everyone but what should I do? I'm totally lost in that.

---

### Post by TheFu on 2022-02-17
> **guillaumesoucy said:**
> Ok thanks everyone but what should I do? I'm totally lost in that.

You should look at the logs, try to research all the errors, see if that research provides any clues for the issue.  It might be anything, including a bad raspberry pi.  Swap/disable 1 thing at a time until you figure out where the issue is, then replace that last thing.

I have 2 raspberry Pis (v2 and v3), but have never put Ubuntu on them. The only issues I've had were 
a) sdcard eventually going bad - that was 3+ yrs of use.
b) bad power. Replaced the PSU.

I don't use wifi with either. I did once, just to test that it works, but both use wired ethernet. My network treats all wifi as untrusted, so being wired gains the Pis access to network resources they can't access otherwise.

---

