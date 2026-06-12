---
title: "Need helpo with my sound right away!! leaving in 20 mins!!!"
date: 2007-12-27
forum: General Help
---

### Post by Psyco_Chipmunk on 2007-12-27
Angry  I broke my sound. No sound on my computer anymore. Need help pronto.
I was trying to fix a problem on my laptop, when ever i pluged in headphones to my laptop, the laptop speakers wouldent go of. So i tryed to fix it by following this little guide.

Quote:
Hi,

Ubuntu Rocks!! Fiesty is good. I got my sound working. So what I did was go to the wiki and read howto troubleshoot Sound.
Well summarizing it all this is what I did.
First of all I will like to tell you that there is a excellent guide here: [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting). Please read it before doing what is given below. (thanks to ikonia at irc)

Step 1)
sudo apt-get install build-essential linux-headers-$(uname -r) module-assistant

Step 2)
wget [ftp://ftp.alsa-project.org/pub/drive....14rc1.tar.bz2](ftp://ftp.alsa-project.org/pub/drive....14rc1.tar.bz2)
tar jxvf alsa-driver-1.0.14rc1.tar.bz2
cd alsa-driver-1.0.14rc1/
sudo ./configure --with-kernel=/usr/src/linux-headers-$(uname -r) --with-cards=hda-intel
sudo make
sudo make install

Step 3)
vi /etc/modprobe.d/options
Here I wrote:
options snd-hda-intel model=laptop-eapd
save and quit.

Step 4) Reboot

Step 5) Enable Internal Modem from within the BIOS

Step 6) Booted Ubuntu Fiesty Linux.

Step 7). LOL !!

Sound's working !! Cheers.

Regards
Deepsa
__________________
I did all of the steps, but when it came to step 3, i think i messed up. Here's what I did. I ran vi /etc/modprobe.d/options in the terminal, no gedit bofor it or anything, just plane vi /etc/modprobe.d/options. So this thing came up in the terminal,
__________________________________________________ _______________

options snd-hda-intel model=laptop-eapd#Enable double-buffering so gstreamer et. al. work
options quickcam compatible=2

options snd-hda-intel model=laptop-eapd # Default hostap to managed mode
options hostap_pci iw_mode=2
options hostap_cs iw_mode=2
model=default
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
"/etc/modprobe.d/options" [readonly] 7 lines, 187 characters

Being stupid like i am, i do the next part of step 3 right away, i past options snd-hda-intel model=laptop-eapd right into the terminal where its highlighted and pressed enter.

Something came up

W10: Warning: Changing a readonly file
E325: ATTENTION
Found a swap file by the name "/var/tmp/options.swp"
owned by: luke dated: Thu Dec 27 01:14:45 2007
file name: /etc/modprobe.d/options
modified: YES
user name: luke host name: luke-laptop
process ID: 23642
While opening file "/etc/modprobe.d/options"
dated: Thu Dec 27 02:02:05 2007
NEWER than swap file!

(1) Another program may be editing the same file.
If this is the case, be careful not to end up with two
different instances of the same file when making changes.
Quit, or continue with caution.

(2) An edit session for this file crashed.
If this is the case, use ":recover" or "vim -r /etc/modprobe.d/options"
to recover the changes (see ":help recovery").
If you did this already, delete the swap file "/var/tmp/options.swp"
to avoid this message.

Interrupt: Press ENTER or type command to continue



so i think i just exit out, i might have pressed enter, then i did the rest of the steps, rebooted, and Bam! No sound! . What do I do? How do I fix this? I really need some good help fast. Thanks!!!
__________________
Lenovo 3000N100 (07684KA Model) Intel Centrino Duo 1.66 Ghz. 1024 DDR2 RAM, 80 GB HDD, Intel High Defination Audio, 1280x800 Widescreen, Ubuntu 7.10 Gusty Gibbon. All is good =D.

---

