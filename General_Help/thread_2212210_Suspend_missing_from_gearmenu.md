---
title: "Suspend missing from gear/menu"
date: 2014-03-20
forum: General Help
---

### Post by Joe_Johnston on 2014-03-20
Hi All,

I am missing the suspend option from the gear/menu and even the Power Options has Suspend grayed out. Does anyone know how to restore this option? Thank you.

---

### Post by gifford on 2014-03-20
What version of Ubuntu are you using?

---

### Post by Joe_Johnston on 2014-03-20
12.04

---

### Post by Joe_Johnston on 2014-03-20
Do you think there would be any merit in updating to 14.04 daily build today? It would probably take care of this issue and give me a chance to work with 14.04 in advance. I have not done this before with Linux, only with Window's beta but it appears they are pretty much done with the important parts and may be worth trying. Any advice?

---

### Post by grahammechanical on 2014-03-20
It may not fix the problem if ACPI is disabled in the BIOS/UEFI. I have been running Trusty Tahr since the beginning of its development cycle. I use it every day for my daily work but I store my data on another partition and I have alternative installs of Ubuntu that I can load into if something seriously breaks in Trusty Tahr. So, with those two considerations in mind I would say, give it a go but check the ACPI settings first.

This is about the only part of this wiki page that I understand.

> [COLOR=#333333][FONT=Ubuntu Beta]Modern power management is handled via ACPI, a spec designed by various companies (Microsoft, Intel, Phoenix, HP, etc). It contains information about the given system's hardware, including details on how to suspend/resume (and hibernate).[/FONT][/COLOR]

[https://wiki.ubuntu.com/UnderstandingSuspend](https://wiki.ubuntu.com/UnderstandingSuspend)

Regards.

---

### Post by gifford on 2014-03-20
I think you are referring to hibernation. Your answer may be found here: [http://askubuntu.com/questions/94754/how-to-enable-hibernation](http://askubuntu.com/questions/94754/how-to-enable-hibernation)
As for updating to 14.04, you could wait until the final beta is released in a few days or until it comes out next month. There are still a number of
issues being worked out. I have it on two machines with various issues on both, minor but still annoying.

---

### Post by Joe_Johnston on 2014-03-20
Thank you for the input and I will hold off on 14.04. 

I do mean Suspend as I have Hibernation available but no Suspend. I will check the BIOS settings but I think it was a fix I did a few days ago to "fix" the Suspend and do not remember the config file they stated to alter and cannot find it in my History. They stated to change something like "active=no" instead of yes.

---

### Post by Joe_Johnston on 2014-03-20
Hi All,

A quick update: I found the link to where I followed the directions to try and fix Suspend: [https://sites.google.com/site/easylinuxtipsproject/bugs](https://sites.google.com/site/easylinuxtipsproject/bugs)

It was under the section: Hibernate and suspend don't always work well: they make some computers malfunction or even enter a coma

8. This still happens with some hardware, and unfortunately .... there is no solution yet. Therefore it's better to turn off these two modes, if they don't work on your computer. 


In Ubuntu hibernation has therefore been disabled by default, but not suspend. If suspend works well on your machine, you don't have to change anything. 


a. First make sure that you have installed the applications gksu and leafpad:


Click on the grey Ubuntu logo (Dash home). Query: terminal. 
Click on Terminal.


Type (or copy/paste): 
sudo apt-get install gksu leafpad


Press Enter and submit your password. Please note that the password will remain invisible, not even asterisks will show, which is normal.


b. Then type in the terminal (use copy/paste):
gksudo leafpad /usr/share/polkit-1/actions/org.freedesktop.upower.policy 


Press Enter.


Now a text file opens. In this text file you'll find the following line twice (for suspend and for hibernate):
<allow_active>yes</allow_active>


Change yes into no, at first only for hibernate. If suspend malfunctions as well, then in both lines. The lines then become:
<allow_active>no</allow_active>


c. Save and close the text file. Then reboot your computer.

I reversed these instructions and all is back to normal. Thank you for the input and sorry for the confusion.

---

