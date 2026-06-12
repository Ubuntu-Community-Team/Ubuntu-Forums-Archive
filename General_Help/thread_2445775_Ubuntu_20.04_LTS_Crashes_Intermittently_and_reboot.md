---
title: "Ubuntu 20.04 LTS Crashes Intermittently and reboots"
date: 2020-06-19
forum: General Help
---

### Post by robert71 on 2020-06-19
Hi Guys,

As the title says I have been experiencing an issue where my Ubuntu installations freezes up and crashes intermittently. 

Sometimes it reboots and sometimes it just becomes unresponsive until i just hit the reset button. 

It happens with different applications and at different loads, E.G. using chrome and GNS3 etc. 

I have done 

sudo apt-get upgrade && sudo apt-get upgrade 

However, the issue persist.  Im not sure where to start troubleshooting this issue from and would like some assistance. 

Thanks very much,

---

### Post by Autodave on 2020-06-19
Can you give us some info on your system please?

Have you run a memory test yet?  When I see that sort of behavior, I take a look at the RAM first.

---

### Post by robert71 on 2020-06-19
Please see the attached screenshot for the system information, 

If you require a specific piece of infor thats not listed here please let me know and ill include it

thanks

---

### Post by dino99 on 2020-06-19
Also can be a temp issue: check it via system-monitor  gnome's applet
Glance at 'journalctl -b' output from the terminal to know about error (red line) and warning (yellow line)

---

### Post by robert71 on 2020-06-19
I ran the command journalctl command but there are no red or yellow lines, any other suggestions

---

### Post by Autodave on 2020-06-19
Run a RAM test.

---

### Post by robert71 on 2020-06-20
@Autodave 

I ran three passes of 

[COLOR=#333333][FONT=inherit]memtest86+

no issues detected. 

Can you advise where to go from here  ?
Is there log files like in windows event viewer ? Sorry if im asking a stupid question but trying to learn linux OS are very different

thanks 

[/FONT][/COLOR]

---

