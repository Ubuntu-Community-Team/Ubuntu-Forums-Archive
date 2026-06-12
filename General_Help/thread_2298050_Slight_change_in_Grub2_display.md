---
title: "Slight change in Grub2 display??"
date: 2015-10-08
forum: General Help
---

### Post by DVD-R on 2015-10-08
Hi All,
I know this is an OOOOOLD topic, but Its been a long time since I've tinkered with Grub2 settings and my question has to do with 2 very simple changes.
I just installed Ubuntu Mate 14.04 on a laptop which now has Windows and 2 Ubuntu versions.

I just want to make 2 changes in what Grub displays during the time it is waiting for the user to select the OS of choice.
1) Remove the graphical image so Grub displays text on black screen.
2) The Ubuntu Mate text string is displayed as simply "UBUNTU" in the choice list, and I want to append that text string so that it reads "Ubuntu Mate 14.04"

I was hoping someone could give a quick tip for each one.
Sincere thanks for your help, in advance.
Thanks

---

### Post by DVD-R on 2015-10-08
I think I've got the steps:

To disable Plymouth graphical.

sudo gedit /etc/default/grub
Change the line &#8211; GRUB_CMDLINE_LINUX_DEFAULT=&#8221;quiet splash&#8221; to  GRUB_CMDLINE_LINUX_DEFAULT=""

And then initiate the grub update process
sudo update-grub

Navigate to /etc/grub.d
1) Stop 30_os-prober from executing at bootup
sudo chmod &#8211;x 30_os-prober

2) Stop the Theme from executing at bootup
sudo chmod &#8211;x 05_theme

3) Edit 10_linux
sudo gedit /etc/grub.d/10_linux

At the text "MenuEntry" make "UBUNTU" read "Ubuntu Mate 14.04"

When you have done all of the above 
sudo update-grub

---

