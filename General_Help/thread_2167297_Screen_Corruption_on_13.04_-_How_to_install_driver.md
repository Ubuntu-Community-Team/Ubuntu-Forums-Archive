---
title: "Screen Corruption on 13.04 - How to install drivers without being able to read?"
date: 2013-08-13
forum: General Help
---

### Post by Quinny898 on 2013-08-13
Right, so this is what I've done so far:
I have a PC that came with Windows 8, (I turned off the secure boot option)
The components are as follows:
Intel i7-3770
16GB ram
Nvidia GT630 - I believe this is what's causing the issue
And the monitor, a LG E2242C 22 Inch one

I wrote the ISO to a USB pen and this is what I see when I press try:
[IMG]http://i.imgur.com/UTJC5r7.jpeg[/IMG]

I think it's a problem with the Nvidia drivers, but the terminal is unreadable, so how can I go about installing them?
Or is it something else?

Thanks

---

### Post by The Cog on 2013-08-13
As the stick boots, you get a picture of a keyboard and a little man at the bottom of the page - while this shows you can press enter and get more options. There is a set of extra options behind F6 (if I remember right), and one of the options in there is nomodeset. Mark that and continue to boot - hopefully that will sort your problem. 

I have to do that with my desktop. I seem to remember that the problem doesn't exist in the instaled OS, but I wouldn't swear to that. I always install the nvidia drivers after installing a new OS.

---

### Post by Quinny898 on 2013-08-13
Worked absolutely perfectly, did that, got it partitioned and it works :D

This is what I did:
Partition using gparted live (this took some messing, had to remove some boot options, also live Ubuntu didn't load due to no nvidia drivers)
Boot Ubuntu Live USB with "Install" and "nomodeset" (As the stick boots I get a sort of grub like screen which is similar)
Installed Ubuntu as normal
On reboot I was stuck at Ubuntu's terminal, installed the nvidia stuff and rebooted and it booted


Thanks for all your help

---

