---
title: "Ubuntu little crashes"
date: 2021-07-01
forum: General Help
---

### Post by azbios on 2021-07-01
Hello Guys,

Recently my Ubuntu started to give some strange crashes, like: Every second it crashes a little and then comes back. 
Videos and audio are played normally, but while I'm typing and moving the mouse cursor, I can see these little crashes. 
Justs Stops and then come back, every second. This started when i'm used the Ubuntu 18.04, but even after the update, this crashes continue.

My pc Specs:

CPU: Six-Core AMD Ryzen 5 1600 AF 3.2GHZ
GPU: GTX 1650 4gb 
RAM: 16gb 2666mhz Dual-Channel
MOBO: ASROCK A320M
Actual Ubuntu version 20.04 LTS

---

### Post by Autodave on 2021-07-01
What, if any, driver are you using for the nVidia card?  Where did you get the driver from?

---

### Post by azbios on 2021-07-02
I installed the lastes driver at the time, with that command : [COLOR=#111111][FONT=Menlo]sudo apt install nvidia-driver-"driverversion"[/FONT][/COLOR]

---

### Post by Autodave on 2021-07-02
Can you make a USB boot disk with 20.04 and boot to that and see what happens?  I am thinking that something was corrupted when you installed 18.04 and stayed corrupted during the update.

---

### Post by azbios on 2021-07-02
I'll make the USB Boot Disk and see what happens, then i'll comeback with the results.

---

### Post by TheFu on 2021-07-02
BTW, The best way to install nvidia drivers is **sudo ubuntu-drivers autoinstall**

I have a ryzen 2600 with an nvidia 1030 GT (v460 drivers) and haven't seen the same issue - though I have been having odd total system lockups the last week or so.  Thought it was the new kernel and Intel igb driver, so I dropped back to the prior kernel and it was stable all week - until today.  The entire system froze. I was looking at a manpage at the time, but the system probably had 15 terminals open and 3+ other GUI programs, while it was running 5-10 virtual machines.

When I say _froze_, I mean
[LIST]
[*]mouse doesn't move; keyboard doesn't work
[*]GUI doesn't update
[*]cannot change to any different TTY
[*]other systems cannot get a ping response
[/LIST]
Frozen.  So I press the reset button, fscks happen and the system comes up.  Then I look at the log files ... only to see that log entries were happening after the system freeze. I noted the time on the clock from the froze screen.
/boot/vmlinuz-5.4.0-74-generic is stable for about 5 days.
/boot/vmlinuz-5.4.0-77-generic was stable less than 2 days.

Can you be a little clearer on what you mean by "crash"?  A crash means a specific program dies and leaves a core dump.  Is that happening or is the system just unresponsive for a few seconds, then comes back?

No end-user program should be able to lock up any Linux system. Period.

---

### Post by azbios on 2021-07-05
When i say "Crash", is that what you said: "the system just unresponsive", but in my case, for one second. 
I ran the USB Boot Disk and everything is normal, the system ran smoothly.

---

### Post by TheFu on 2021-07-05
Look at the log files for the times when the system is unresponsive. That should show something. I'd use **journalctl** for that. It lets us specify time intervals.

---

### Post by azbios on 2021-07-06
I Looked on the **journalctl **and he show this every second:

/usr/lib/gdm3/gdm-x-session[2354]: (--) NVIDIA(GPU-0): GDH PHILCO (DFP-1): connected
/usr/lib/gdm3/gdm-x-session[2354]: (--) NVIDIA(GPU-0): GDH PHILCO (DFP-1): Internal TMDS
/usr/lib/gdm3/gdm-x-session[2354]: (--) NVIDIA(GPU-0): GDH PHILCO (DFP-1): 600.0 MHz maximum pixel clock

GDH PHILCO is my primary monitor.

---

### Post by Autodave on 2021-07-06
Someone may have a better answer, but if it were my machine I would be doing a fresh install and then updating the graphic's driver as TheFu suggested earlier.  Make sure that you back up everything that you need to keep FIRST!

---

### Post by azbios on 2021-07-06
I uninstalled the Nvidia driver and used the Nouveau driver to test and the system ran smoothly, but the resolution of my secondary screen got messed up.

Then i installed again with the TheFu suggestion and the problem is back again.

---

### Post by TheFu on 2021-07-06
> **azbios said:**
> I Looked on the **journalctl **and he show this every second:

/usr/lib/gdm3/gdm-x-session[2354]: (--) NVIDIA(GPU-0): GDH PHILCO (DFP-1): connected
/usr/lib/gdm3/gdm-x-session[2354]: (--) NVIDIA(GPU-0): GDH PHILCO (DFP-1): Internal TMDS
/usr/lib/gdm3/gdm-x-session[2354]: (--) NVIDIA(GPU-0): GDH PHILCO (DFP-1): 600.0 MHz maximum pixel clock

GDH PHILCO is my primary monitor.

I used to work for Philco, but definitely NOT the same company.
Have you tried using a different ubuntu live boot environment?

[https://forums.developer.nvidia.com/t/xorg-0-log-with-flood-message-dfp-1-connected-and-screen-locking-every-second/50154/2](https://forums.developer.nvidia.com/t/xorg-0-log-with-flood-message-dfp-1-connected-and-screen-locking-every-second/50154/2) is what returned from a google search for those messages.  nVidia says to try a different cable or monitor.  A different cable solved it for that person.

---

### Post by Autodave on 2021-07-06
Try another cable first and see what happens.

Did you do a complete install or just the graphics drivers?  I recommend a complete install of the OS.

---

### Post by azbios on 2021-07-06
Autodave, i just reinstalled the graphic drivers. I'll do the complete installation, if the solution of TheFu does not work.

---

### Post by azbios on 2021-07-07
Guys, thanks for the help and pacience, i changed the HDMI cable and the system ran smoothly.
I'll mark the thread as Solved.

---

