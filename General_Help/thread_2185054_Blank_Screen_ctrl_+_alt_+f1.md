---
title: "Blank Screen ctrl + alt +f1"
date: 2013-10-31
forum: General Help
---

### Post by MZBKA on 2013-10-31
Hello there,

I recently purchased a new desktop and am trying to get Ubuntu working correctly.  I have a NVIDIA GTX 780 graphics card, so I'd like to install the NVIDIA driver so that everything look pretty.  Unfortunately the procedure for installing this driver is insanely difficult.

I have downloaded the driver and attempted to install the run file.  Unfortunately, this brings up the error "You appear to be running an X server."  Whatever that means.

I've done some searching, and apparently, in order to fix this problem, I need to hit ctrl + alt +f1 and run commands from a terminal that's supposed to open.  Unfortunately, all I get is a blank screen.  ctrl + alt - f7 brings me back to Ubuntu.

I have read that I have this problem because I do not have the correct graphics driver installed.

I can't install the graphics driver because the virtual console won't work.
The console won't work because I can't install the graphics card.

Please help me exit this Möbius strip of stupid.

---

### Post by Mopar1973Man on 2013-10-31
I would start here... [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)  I've also got a Nvidia card as well but older. But really the only time you really need a video driver is for the flashy graphics or games. But you can run the Linux without a video just the same. So I would go back and check the drivers page and start there.

---

### Post by MZBKA on 2013-10-31
Thanks for your reply.  The installation instructions on the page you linked are from an older version of Ubuntu.

One cannot g[COLOR=#333333][FONT=inherit]o to [/FONT][/COLOR][B]System -> Administration -> Additional Drivers
[/B]

I am running Ubuntu now, but without the driver, Ubuntu thinks I'm on a laptop and the screen resolution is all messed up.

---

### Post by deadflowr on 2013-10-31
Did you try tty2?
ctrl+alt+f2

I'm guessing you're installing the driver from nvidia's download page instead of through the repos.
As there is no need to kill X if installing from the repos.

---

### Post by MZBKA on 2013-10-31
> **deadflowr said:**
> Did you try tty2?
ctrl+alt+f2

I'm guessing you're installing the driver from nvidia's download page instead of through the repos.
As there is no need to kill X if installing from the repos.

Hi there.  Thank you for your reply.  Yes, I tried ctrl+alt +f2-f6.  All of them give me a blank screen.

When you say "install through the repos", do you mean install through the Ubuntu Software Center?  In that case, I'm not sure what exactly I should install.

---

### Post by deadflowr on 2013-10-31
What version of Ubuntu are you running?

The repos to install the nvidia drivers are the same you would use if installing from additional drivers.

On newer systems (12.10 and newer) to get to the additional drivers, you need to open of the program "software and updates".
Software and Updates is actually software sources. It can also be accessed through the command line
```
software-properties-gtk
```
Additional Drivers is now a section of this.

I think though, that most of the time the recommended packages would be nvidia-current and nvidia-settings.
nvidia-current is the driver, while nvidia-settings is the graphical control panel.
The good thing about Ubuntu is that the dependencies should be brought in if needed. 


Though, still, it is rather odd you can't get to any of the tty1-6.

---

### Post by MZBKA on 2013-11-03
Thanks again for your reply.  I entered what you said and got to Additional Drivers, but there is nothing there.  "No proprietary drivers are in use"

I' running 13.04

---

### Post by deadflowr on 2013-11-03
Still interesting.

A thought here,
Are the restricted repositories enabled.

An easy way to find out is to reopen the software sources(aka software-properties-gtk) and in the section Ubuntu Software see if the entry is checked, if it isn't check it.

Odd still that drivers for nvidia didn't show up.

---

### Post by MZBKA on 2013-11-03
> **deadflowr said:**
> Still interesting.

A thought here,
Are the restricted repositories enabled.

An easy way to find out is to reopen the software sources(aka software-properties-gtk) and in the section Ubuntu Software see if the entry is checked, if it isn't check it.

Odd still that drivers for nvidia didn't show up.

Thanks for your reply.

Yes, the restricted repositories are enabled.

---

