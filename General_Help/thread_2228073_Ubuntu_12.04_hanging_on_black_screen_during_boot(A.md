---
title: "Ubuntu 12.04 hanging on black screen during boot(ATI/AMD/Radeon)"
date: 2014-06-05
forum: General Help
---

### Post by Austrie on 2014-06-05
I installed ubuntu 12.04 on to my whole hard drive recently, but a couple days ago I left my laptop alone and it died. When I tried to power it back, everything seemed normal at first; the manufacturer's logo came up, then the screen blinked, then the ubuntu loading logo, and a few seconds after it comes up the screen goes black. The keyboard and everything is working(Ex when I click the WiFi button, it changes colors like it's supposed to), but the screen just stays black. When I click the power button, the ubuntu loading screen shows up but then it shut down after two seconds. I'm able to get into grub and terminal mode(tty1??), but i'm not sure how to fix this issue. Could someone give me some advice please.

Edit: When I try, [COLOR=#333333][FONT=Arial]"sudo service lightdm restart" in terminal mode(tty1), every line says [OK] but it stops at checking battery state and doesn't restart.[/FONT][/COLOR]

---

### Post by Austrie on 2014-06-05
Bump

---

### Post by gtzanakis on 2014-06-05
Ok, first of all I'm not an expert, so try this while some more advanced people take a look. I think that the fact the wifi button works is irrelevant, as this is hard wired to work, and it will turn on and off, with the led indicating so, even if you don't have a OS installed.

Now, as for your problem, while you wait to hear from the pros, you could try to see if the power failure lead to any damage to your hard disk. Just in case. So, boot from a live cd and open a terminal. Do ```
sudo fdisk -l
``` to see what partitions you have there, and then do ```
sudo fsck /dev/sda1
``` but change sda1 to what the output of fdisk was in the previous command. Do that for all your partitions. If your disks got problems, you should see it..

---

### Post by Austrie on 2014-06-06
Sda1, system said this:
Device contains neither a valid dos partition table, nor Sun, sgi or osf disklabel. Building a new dos disklabel with disk identifier 0x3e395d1f. Changes will remain in memory only, until you decide to write them. After that of course the previous content won't be recoverable.
Warning: invalid flag 0x0000 of partition 4 will be corrected by w(rite)

Is anything wrong with system?

---

### Post by Austrie on 2014-06-07
I've discovered a fix, incase anybody else is having this issue. At first I tried do-release-upgrade but it said ubuntu had no new update; which is weird since 14.04 LTS is avaible. So I tried do-release-upgrade -d to install a developmental release; that's when it said 14.04 LTS is availble. After it instaleld, the loadining screen came up, the screen became black for little while then came back on. When I entered Ubuntu, I noticed my touchpad mouse wasn't workingl luckily my computer come with a second mouse. So I was able to do research on this issue, and I found this fix by lapromesa777 in a comments section:
Open the Terminal
cd /etc/modprobe.d/
gksudo gedit options.conf
In the text editor, type: options psmouse proto=imps
Save the file and close it.
sudo modprobe -r psmouse
sudo modprobe psmouse

Changing this thread to solved.

---

