---
title: "Ubuntu 13.04 performance issues"
date: 2013-05-15
forum: General Help
---

### Post by grashdur on 2013-05-15
Dear All,

I've been having serious performance issues since I installed Ubuntu 13.04. Strangely, I haven't found any guidance about this when searching the Forum so far, nor from a Google search. All I see is discussion of performance problems of at least three years ago, and raves about how much faster 13.04 supposedly is.

When I scroll the launcher or use ALT-Tab to switch among windows (is that what's now called "the Lens"?), things move jumpily and with delay. This makes it harder to switch to the right program.

Unity's launcher icons don't usually show with those little notches which programs are already open, as they had consistently done in 12.04. I was seeing them occasionally a few days ago, now not at all.

Opening a 1.1 MB spreadsheet file in LibreOffice now takes 81 seconds. I didn't time it in 12.04, but I think it took maybe a quarter or a fifth as long. I tried changing LibreOffice's memory settings to increase memory use, but it still takes 81 seconds to open the file.

In Softmaker Office, there is a little delay between typing each key and the character appearing on screen. This distracts me and makes it hard for me to type. (Actually, this is even starting to happen a little in gedit.) Also, boldface letters do not show in boldface.

Opening an 83k WAV file with "Videos" (isn't this the same old Totem program?) gives me garbled, incomprehensible audio. (But with VLC Media player it works fine, and playing a DVD in "Videos" seems to basically work, with just a little jumping as I select things in the DVD menu.)

Using FontForge, now whenever I generate a font it has kerning errors -- as if the program is running out of memory or something.

Many Youtube videos play badly, stopping frequently even though my DSL download speed still tests at 11-12Mb/s. Some other videos online play a little choppy.

Sound from a radio stream running in Audacious cuts out and sometimes shuts off, especially when I'm switching among different windows.

I recently uninstalled five different things from Unity: photo previews, Amazon, Ubuntu One music, etc. I see some performance improvement after doing so, but it's still not great.

I am mystified about why performance is so bad with 13.04, and why this problem doesn't seem to be affecting anyone else. I basically have a default installation of Ubuntu, on a fairly high-powered, not-very-old, computer that was designed and built just for Linux (specs below in footer). Looking at the System Monitor, I never see memory usage going up to half capacity, though it often stays a little over one-third. When I open Rhythmbox or a large spreadsheet, both CPUs go up close to 50%, although on the System Monitor's graphic display on the Resources tab, they seem to go close to 100%, off and on, during that time. 

My root partition is 6.7 GB, or 60%, full. I originally sized it at 8GB but had to expand it to 12 when it was getting 97% full. My /tmp partition right now is at 3%. Looking at processes in the System Monitor, right now gnome-system-monitor is taking the most CPU, at 6%. Occasionally other process shoot up higher, around 20%

Could it be a video driver issue? (I use a Gateway 17" monitor from 2006). Or just a bunch of separate issues? These problems get worst most when I have plenty of programs open (at the moment I have eight program windows open, and I often go up to twelve). But according to the System Monitor, I'm hardly using the resources that are available on my computer.

At the same time, I do see one performance improvement compared to 12.04: 

Opening a small file in LibreOffice, like 25k, is much faster now -- almost instantaneous.

(I don't see any noticeable change in bootup time.) 

I want to make some little adjustment to make everything work better. If this is actually just a whole bunch of separate issues (in addition to the many bugs I'm seeing in programs such as Rhythmbox), then I'll probably install 12.04 in my other root partition. But I'm reluctant to do that, since reinstalling is incredibly time-consuming.

Thanks for any insights. 

Scott

---

### Post by grashdur on 2013-05-17
There was only one way to fix this problem -- I did have to install the 12.04 Pangolin version.

---

### Post by grashdur on 2013-05-18
Uh,... nope. I just now received a new monitor and set it up. It doesn't work with 12.04, so I'm stuck with the performance issues until I can figure something out. 

(And figure out how to change the default OS -- none of the instructions I'm finding online actually work.)

---

### Post by upulr on 2013-05-18
Perhaps you could submit a bug report. Following is an extract from the Ubuntu Manual.

8.4
Submitting bug reports
As described in section 3.4, bug reports are managed in Launchpad. It is one central place where the Ubuntu
developers manage the bug submitted by users and try to fix the issues. Submitting bug reports to Launchpad can
be easily done via the terminal using one simple command. This is illustrated in this section. In order to submit bug
reports, you need to know the name of the package you are reporting the bug against. Once you know the name of
the package, type ubuntu-bug package name as shown in figure 8.20
Figure 8.20: Submit bug report
When you execute this command in the terminal, Ubuntu will collect all necessary information about your system
automatically and create a bug report in Launchpad. You are however required to enter a bug title, description on
how to reproduce this and provide any screenshots if necessary. A well described bug report will help the developers
identify the problem quickly and solve the issue. It will then be issued as an update to all the Ubuntu users.
Some common package names are mentioned here. If it is graphical issue the most probable package is compiz. So
then you would type ubuntu-bug compiz. If the bug is related to the dash or launcher, the package name is unity.
If you are unable to find the package name, just use of the above mentioned package names. The bug triagers will
relate it to the correct package for you.

For me, I use my laptop mainly for internet and watching movies. Apart from certain functions keys not working, I can see a lot of movies going blotchy when they are played and this did not happen in 12.04 to 13.04. Only in 13.10. For my main issue, I submitted a bug report and hope to get some feedback next week.

---

### Post by grashdur on 2013-05-21
Yet another glitch came along in 13.04: After a few days of use, Unity freezes up and has to be rebooted on every other login.

The ultimate solution was in fact to go back to 12.04. I was able to get my monitors to work perfectly using amdcccle (something already installed by default -- you can sudo it in Terminal). 

The updates corrupted my user account in 12.04, so I had to make a new one and copy all my files over to it. 

Now I can finally get back to work.

---

