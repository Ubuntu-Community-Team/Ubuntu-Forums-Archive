---
title: "Why did my UTC change?"
date: 2017-04-03
forum: General Help
---

### Post by ronnie.s on 2017-04-03
I use Ubuntu 16.04, which is in dual boot with Windows 10 (I think). I have not touched the Windows OS in the last 4 months or more. 

Today I noticed that the time which is displayed when I log into Ubuntu is not correct. I suspect it has something to do with daylight savings, although I'm not sure about this. The result of the command 
```
timedatectl
```
is
```
 Local time: Mon 2017-04-03 21:30:10 IST
  Universal time: Mon 2017-04-03 16:00:10 UTC
        RTC time: Mon 2017-04-03 16:00:10
       Time zone: Asia/Kolkata (IST, +0530)
 Network time on: yes
NTP synchronized: yes
 RTC in local TZ: no

```
which is obviously wrong, since a google search on UTC shows that my clock is about 1 hour ahead. 

Until a few days back, probably yesterday, everything was working fine, but now it's screwed up. I did update to the correct time using the command 

```
sudo ntpdate pool.ntp.org

```
however, after a restart, I went back to the wrong time. Now I live behind a firewall and the ntp port has been blocked, and therefore to use the ntp command, I have to switch over to the internet connection from my mobile phone, which is not something I want to do every time I start my computer. 

1. I am guessing that my laptop has a clock in it, and I'm also guessing that it is this clock which is being referred to as RTC. As is clear from the result of the command timedatectl, the hardware clock has been set to UTC. Are these assumptions correct?

2. Why did my UTC change all of a sudden, can someone please explain this?

Thanks in advance.

---

### Post by Bashing-om on 2017-04-03
ronnie.s; Hello:

Here is the deal:
Windows sets the hardware clock to local time by default. Linux/Unix sets it to UTC by default. One of them needs changing so they both use the clock the same way. -> [http://askubuntu.com/questions/169376/clock-time-is-off-on-dual-boot](http://askubuntu.com/questions/169376/clock-time-is-off-on-dual-boot)

Now, procedures in 16.04 (systemd) have changed from prior (upstart) releases.
[http://ubuntuhandbook.org/index.php/2016/05/time-differences-ubuntu-1604-windows-10/](http://ubuntuhandbook.org/index.php/2016/05/time-differences-ubuntu-1604-windows-10/)
Might try:
To change RTC in local TZ:
```

timedatectl set-local-rtc 1

```
More info here: [http://manpages.ubuntu.com/manpages/xenial/man1/timedatectl.1.html](http://manpages.ubuntu.com/manpages/xenial/man1/timedatectl.1.html)

[INDENT][INDENT]My bit to try and help
[/INDENT][/INDENT]

---

### Post by ronnie.s on 2017-04-05
Hi Bashing-om,

Thanks for your response. I did mange to fix the time on my computer. But for my own intellectual curiosity, I have a few questions. It will be very kind if you could answer them.

I almost never use Windows. But I haven't deleted it since if something goes wrong with the hardware, I'm worried that the people at repair store of my laptop company may create problems. As I had also mentioned in my question, I haven't booted into Windows for several months now. So here are my questions. It'll be helpful if you could answer them one by one in the order asked.

1. My laptop contains a battery operated clock, which is referred to as the Real Time Clock (RTC). When my laptop is switched off, this clock is powered by an internal battery. This clock is supposed to maintain (by my choice) the time given here [HTML]https://www.timeanddate.com/worldclock/timezone/utc [/HTML]
When I switch on my laptop, the OS reads the time from the RTC and puts the result into the system clock, also accounting for time zone. That is, the final result being that the system clock will display local time. Is this correct?

2. If the above is correct, and I have not logged into Windows for a long time, then why did my RTC change all of a sudden? Is it possible that when I powered on my computer, and before choosing Ubuntu from the Grub menu, Windows did something crazy which changed the time of the Real Time Clock?

Thanks.

---

### Post by Bashing-om on 2017-04-05
ronnie.s; Erahhh ...

1) I am  Not the smartest hardware tech, but ,,,
consider that bios has no networking abilities of it's own . What you set the hardware clock to is what is set ( me, I set the HWC to UTC).
However, newer systems could have abilities I am unaware of - case in point I have seen where newer systems have the ability to update bios to later versions . Now that do beg the question of how ?
2) Nope I fail to see how a operating system that is not loaded can have any effect . As to what may have changed the clock outside of Windows running and resetting the clock - I have no idea . Day-light savings time factor (one hour)?? 

[INDENT][INDENT]sometimes I just do not know
[/INDENT][/INDENT]

---

### Post by ronnie.s on 2017-04-06
Thanks for your help, Bashing-Om!

---

