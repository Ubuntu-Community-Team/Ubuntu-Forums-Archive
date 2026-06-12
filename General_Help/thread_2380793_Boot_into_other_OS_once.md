---
title: "Boot into other OS once"
date: 2017-12-22
forum: General Help
---

### Post by mastablasta on 2017-12-22
I've searched quite a bit, but most of the instructions seem obsolete. i am planning to use Kubuntu to be able to still do safe internet browsing after the firefox support is dropped for WinXP.

I have this strange nVidia card, where the POST output signal s always sent to TV and only when the OS loads it would switch to the monitor as the only active output. This means that GRUB is then also only displayed on TV and i can't see it on my monitor.

I would like to install Linux ot this PC and keep the WindowsXP, so i saw there is an option for telling the OS to boot into Windows on restart and avoid messing with grub and TV input menu everytime the there is a game request. 

KDE4 had this neat feature built in but it was dropped for some reason with KDE5 (maybe i should enter a feature request).

I then found this script claiming to do the same as boot-once in SUSE.  GRUB selector: [https://github.com/Cypresslin/grub_selector](https://github.com/Cypresslin/grub_selector)
Has someone tried this? would this work?

but i am having a hard time figuring out if this really could work as well as it is still not as easy as double clikcing a deskotp icon and then having a reboot countdown. So i searched further and came up with this debian way: 
 [https://wiki.debian.org/GrubReboot](https://wiki.debian.org/GrubReboot)

Bu the problme is the wiki article is quite old and i am not sure if this could apply to Ubuntu. and even this kind of method seems that it is not working for everyone as some posts online would suggest. Also why is GRUB saved when switching OS? i want it to be the same just boot into different os on reboot.

So i am asking here what do others use for easy switch between OS? Does anyone have this kind of boto once setup?

I am thinking that i can move most old game to Linux, but occasionally a boot to widnows might sitll be necessary for some games as well as certain Government software. ](*,)

---

### Post by leunam12 on 2017-12-22
That article about grub-reboot is very interesting, I am going to try that.
Is you computer a laptop and changing the video card is not a possibility?
How about buying a second computer? If all you want is to surf the web you can
find something relatively inexpensive on eBay.

---

### Post by Cavsfan on 2017-12-22
There is a Grub wiki in my signature that is good for dual booting, multi-booting etc. It's pretty straight forward.
I have Arch Linux, Xubuntu 16.04, Xubuntu 17.10, Xubuntu 18.04 and Windows 10 on my system and it boots default to Windows 10 because that is the way I set it up to do.
You can choose the default OS, and a bunch of other eye candy like backgroud, font colors, etc.

You have all the same options that Grub2 provides, such as booting into the backup kernel or recovery.

Here is my current setup on Grub. This is on Arch Linux but I have my current grub installed on Xubuntu 18.04 since it has the additional font color option of the top and bottom of the screeen.
Arch only provides the ability to change the colors of the box and menu entries as well as the selected (highlighted) line. The top and bottom are white.

[[IMG]http://www.zimagez.com/miniature/20171119182421.jpg[/IMG]]("http://www.zimagez.com/zimage/20171119182421.php")

---

### Post by Cavsfan on 2017-12-23
I also set my timeout to 60 seconds because I'm sometimes slow to decide with OS to boot into.

Did you look at the wiki? Did you have any questions or thoughts about it?

---

### Post by mastablasta on 2018-01-03
> **leunam12 said:**
> That article about grub-reboot is very interesting, I am going to try that.
Is you computer a laptop and changing the video card is not a possibility?
How about buying a second computer? If all you want is to surf the web you can
find something relatively inexpensive on eBay.

the PC got occupied during holidays. :-/

this is almost brand new video card. it is a possibility but it will cost me. it is also a very old system so not many new cards fit on it or work with it.

saving up for new PC, but i would like to leave this one for the kids, so they can play on it as well as safely surf the web. current GPU card enables them to play games on it from years 2007, 2008 maybe some form 2009. so let's say PS3 era, which is not that bad, especially since they haven't played many of them and old games are cheap. 

> **Cavsfan said:**
> I also set my timeout to 60 seconds because I'm sometimes slow to decide with OS to boot into.

Did you look at the wiki? Did you have any questions or thoughts about it?

i did look at the wiki, but my whole issue is that i can not see grub on boot.  i mean i can see it if i turn on the TV as it is displayed there. the whole idea of booting once is that when you need windows you just double click the icon and PC reboots into windows. when you are done in windows the process can be the same or with a few click you run the reboot and you are back to linux. you don't need to select correct grub kernel etc. after that linux acts as the only OS on disk ("booting wise") until you decide you need windows again.

---

### Post by again? on 2018-01-04
Run this command to show your grub entries.
```
grep menuentry /boot/grub/grub.cfg | grep "^menuentry" | sed -e 's/.*Memory test.*//g' -e "s/menuentry '//g" -e 's/ --class.*//g' -e "s/'//g" -e '/^$/d' -e "s/ {//g"
```

Then use your complete windows grub line in this command to reboot into it. 
```
grub-reboot "[COLOR="#FF0000"]your windows grub line[/COLOR]"; **gnome-session-quit --reboot**
```
Change **gnome-session-quit --reboot** for the reboot command applicable to your desktop session.

To allow grub-reboot to be used without sudo, run (******Warning this allows /usr/bin/grub-editenv to be executed by any user)
```
sudo chmod +s /usr/bin/grub-editenv
```

I only use a 3sec timeout in grub because I have set up a quicklist menu to choose the next boot from various installs including live ISOs.

Example using my details:
```
**[COLOR="#006400"]glen@GU17:~$[/COLOR] grep menuentry /boot/grub/grub.cfg | grep "^menuentry" | sed -e 's/.*Memory test.*//g' -e "s/menuentry '//g" -e 's/ --class.*//g' -e "s/'//g" -e '/^$/d' -e "s/ {//g"**
Ubuntu
Ubuntu 16.04.3 LTS (16.04) (on /dev/sda1)
Fedora 25 (Workstation Edition) (on /dev/sdb5)
Ubuntu 17.10 (17.10) (on /dev/sdc1)
Ubuntu Xenial 16.04.2 ISO
Lubuntu 16.04.1 ISO
Ubuntu Zesty 17.04 ISO
Ubuntu-Gnome 17.04 ISO
Ubuntu Artful 17.10 ISO
Xubuntu 16.04.1 ISO
```

To boot into Fedora I would run...
```
grub-reboot "Fedora 25 (Workstation Edition) (on /dev/sdb5)"; gnome-session-quit --reboot
```
The exec command in my desktop launcher looks like this
```
Exec=sh -c 'grub-reboot "Fedora 25 (Workstation Edition) (on /dev/sdb5)"; gnome-session-quit --reboot'
```

In  /etc/default/grub, I do **not** need to set GRUB_DEFAULT to "saved".
```
**[COLOR="#006400"]glen@GU17:~$[/COLOR] cat /etc/default/grub**
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
##  info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=3
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet"
GRUB_CMDLINE_LINUX=""
```

---

