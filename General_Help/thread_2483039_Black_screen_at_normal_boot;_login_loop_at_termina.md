---
title: "Black screen at normal boot; login loop at terminal boot - after upgrading to 22.04"
date: 2023-01-18
forum: General Help
---

### Post by louisash on 2023-01-18
Hello all,

I was hoping your expertise could help me get closer to a solution to a particularly nasty problem I am having after upgrading Ubuntu 20.04 LTS to 22.04 LTS in my workstation (which has a Nvidia RTX 3080 12gb GPU installed).

Basically, after that upgrade, the computer ceased being able to boot. Regular boot attempts result in the well known [black screen with blinking and non-responsive cursor]("https://askubuntu.com/questions/297080/ubuntu-boots-to-a-black-screen-with-blinking-a-underscore-character-after-releas").

However, in my case, if I drop to terminal mode, e.g. with Ctrl+Alt+F1, login attempts with any user name/password registered in the system lead to a terminal login loop (not [desktop login loop]("https://askubuntu.com/questions/223501/ubuntu-gets-stuck-in-a-login-loop")) - that is, after correct user name and password are inserted, it just goes back to the same login terminal prompt.
The only exception is if I log with user "root" and the root password at the terminal login prompt - that works and leads to a regular terminal session (same works at recovery mode).


**What have I tried:**

[LIST]
[*]the usual nomodeset and no splash parameters for logging in ([see]("https://askubuntu.com/a/162076"));
[*]the usual sudo apt-get update + sudo apt-get upgrade + sudo apt-get dist-upgrade ([see]("https://ubuntuforums.org/showthread.php?t=1620479"));
[*]reinstalling Nvidia most recent drivers via root terminal ([see]("https://askubuntu.com/a/650253"));
[*]turning off Wayland ([see]("https://askubuntu.com/a/1286728"));
[*]turning on and reconfiguring lightdm (sudo dpkg-reconfigure lightdm) ([see]("https://askubuntu.com/a/883399/1665637"));
[*]tried gdm3 instead of lightdm ([see]("https://askubuntu.com/a/350858"));
[*]checking .Xauthority ([see]("https://askubuntu.com/a/223634"));
[*]checking if my disk is full ([see]("https://askubuntu.com/a/710192"));
[*]reinstalling the desktop environment ([see]("https://www.makeuseof.com/fix-ubuntu-login-loop-issue/"));
[*]reinstalling the kernel ([see]("https://askubuntu.com/questions/298853/how-to-reinstall-newest-linux-kernel"));
[/LIST]

My question: what else can be done to try to solve this problem? My impression is that the key is to, first, understand what it causing the login-loop at terminal mode - but I have found very scarce mentions online to login-loop issues at terminal mode (desktop login-loop issues are somewhat common).

Thanks for any suggestions!

**EDIT:** Note that I never get to a desktop login screen - standard boot leads to black screen with flashing cursor. Then when I drop to tty for terminal mode login, logging in with any user other than "root" (including a new user created for test purposes) leads to terminal login loop.

**EDIT 2:** GRUB works - the blank screen with flashing cursor appears after the [Ubuntu loading screen]("https://ubuntuhandbook.org/wp-content/uploads/2022/10/splash-after-600x337.webp"). Then, when the blank screen with flashing cursor appears, I go to tty with Ctr-Alt-Fx. Logging in at the terminal login screen with any user other than "root" just loops back to the terminal login screen.
[IMG]https://ubuntuhandbook.org/wp-content/uploads/2022/10/splash-after-600x337.webp[/IMG]

---

### Post by tea for one on 2023-01-18
Are you aware of the two display servers available in Ubuntu 22.04 - Xorg and Wayland?
Nvidia and Wayland are not happy bedfellows yet.
Have you tried to boot into a Xorg session?
Select session as indicated in the attachment.
Any help?

---

### Post by louisash on 2023-01-18
Thanks for your reply! Unfortunately, however:

1- I never get to a desktop login screen; like I said the computer boots to a black screen with flashing cursor (so it never gets to the desktop login screen). Then, when I drop to terminal login, logging in with any user other than "root" leads to a login-loop.
2- note that I did try turning Wayland off via terminal and rebooting.

---

### Post by tea for one on 2023-01-18
In your first post, you mention gdm3 and lightdm.
Do you have more than one Desktop Environment?

Also, was this an in-situ upgrade?

---

### Post by louisash on 2023-01-18
> **tea for one said:**
> In your first post, you mention gdm3 and lightdm.
Do you have more than one Desktop Environment?

Also, was this an in-situ upgrade?

I installed gdm3 to test if using it would be of any help. I have tried both, with no luck (in fact, if using gdm3 I cannot even alternate to tty with Ctr+Alt+Fx" at the black screen with flashing cursor; so I reverted back to using lightdm).

And if by in-situ upgrade you mean upgrading from 20.4 LTS to 22.04 LTS without erasing/formatting the prior 20.04 LTS installation, yes. I upgraded from the Software Updates.

---

### Post by tea for one on 2023-01-18
When in-situ upgrades go pear-shaped, it is often difficult to pinpoint where the problem(s) exist.
There is a vast amount of info here about black screens [https://ubuntuforums.org/showthread.php?t=1743535](https://ubuntuforums.org/showthread.php?t=1743535) posted by MAFoElffen, an experienced user.
Have a look and see if there are any clues.

---

### Post by oldfred on 2023-01-18
Do you or can you get grub menu & boot recovery mode?
turn on Internet & reinstall nVidia driver?

Did you purge nVidia drivers before installing a new one?
sudo apt-get remove --purge nvidia-*
sudo ubuntu-drivers devices
sudo ubuntu-drivers autoinstall

---

### Post by louisash on 2023-01-19
> **tea for one said:**
> [COLOR=#000000]When in-situ upgrades go pear-shaped, it is often difficult to pinpoint where the problem(s) exist.[/COLOR]
[COLOR=#000000]There is a vast amount of info here about black screens [/COLOR][https://ubuntuforums.org/showthread.php?t=1743535](https://ubuntuforums.org/showthread.php?t=1743535)[COLOR=#000000] posted by MAFoElffen, an experienced user.[/COLOR]
[COLOR=#000000]Have a look and see if there are any clues.[/COLOR]
I spent a long time exploring that link, thanks. However, those solutions are either for when GRUB is not available yet, or for when loging from tty is possible. The center of my problem is that login is not possible with any user other than root in the tty terminal login screen.

> **oldfred said:**
> Do you or can you get grub menu & boot recovery mode?
turn on Internet & reinstall nVidia driver?

Did you purge nVidia drivers before installing a new one?
sudo apt-get remove --purge nvidia-*
sudo ubuntu-drivers devices
sudo ubuntu-drivers autoinstall

I do get to GRUB, then to the Ubuntu loading screen, then to the back screen with flashing cursor. Then, during the blank screen with flashing cursor, if I drop to terminal with Ctr+Alt+Fx, I see the terminal login screen. However, if I enter *correct* login and password info of any user other than root, hitting Enter just shows again the terminal login screen.

Yes, I can get to recovery mode, but no, I cannot enable network there. Digging more to find out why, I noted that [my syslog]("https://filebin.net/gr8yn7rvxpp5pojt") has a bunch of "Permission Denied" errors. But I can normally purge and reinstall NVidia drivers from booting with a USB Ubuntu ISO. Nothing changes.

---

### Post by louisash on 2023-01-19
[SIZE=3][COLOR=#232629][FONT=-apple-system]After an insanely time consuming journey, I found out that the login loop at terminal was being caused by some permission issues - which I never altered myself. Anyway, the solution was to reestablish the following:[/FONT][/COLOR]
[/SIZE]
chmod 755 /
chmod 755 /bin
chmod 755 /lib
chmod 755 /lib64

[SIZE=3][COLOR=#232629][FONT=-apple-system]With that, I was able to login via terminal with any user, at tty.[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]Then, the black screen with flashing cursor was treated with an install of the very recent Kernel 5.15.58:
[/FONT][/COLOR][/SIZE]
sudo apt-get install linux-image-5.15.0-58-generic

[SIZE=3][COLOR=#232629][FONT=-apple-system]And a purge + reinstall of the most recent Nvidia drivers:[/FONT][/COLOR][/SIZE]

sudo apt-get remove --purge nvidia-*
sudo ubuntu-drivers devices
sudo ubuntu-drivers autoinstall

---

### Post by MAFoElffen on 2023-01-19
Just as a reference to what is normal:
```

mafoelffen@Mikes-ThinkPad-T520:~$ ls -l /.
total 2097244
lrwxrwxrwx   1 root root          7 Sep 23  2021 bin -> usr/bin
drwxr-xr-x   4 root root       4096 Jan 18 22:59 boot
drwxr-xr-x   2 root root       4096 Sep 23  2021 cdrom
drwxr-xr-x  20 root root       4860 Jan 18 22:26 dev
drwxr-xr-x 169 root root      12288 Jan 18 23:07 etc
drwxr-xr-x   4 root root       4096 Dec 16  2021 home
lrwxrwxrwx   1 root root          7 Sep 23  2021 lib -> usr/lib
lrwxrwxrwx   1 root root          9 Sep 23  2021 lib32 -> usr/lib32
lrwxrwxrwx   1 root root          9 Sep 23  2021 lib64 -> usr/lib64
lrwxrwxrwx   1 root root         10 Sep 23  2021 libx32 -> usr/libx32
drwx------   2 root root      16384 Sep 23  2021 lost+found
drwxr-xr-x   3 root root       4096 Jan 18 22:26 media
drwxr-xr-x   6 root root       4096 Aug 31 09:38 mnt
drwxr-xr-x   3 root root       4096 Nov 25 06:54 nfs
drwxr-xr-x   6 root root       4096 Jan 18 22:58 opt
dr-xr-xr-x 534 root root          0 Jan 18 22:26 proc
drwx------  12 root root       4096 Jan 18 22:14 root
drwxr-xr-x  48 root root       1440 Jan 19 06:03 run
lrwxrwxrwx   1 root root          8 Sep 23  2021 sbin -> usr/sbin
drwxr-xr-x  16 root root       4096 Oct  9 15:28 snap
drwxr-xr-x   2 root root       4096 Aug 19  2021 srv
-rw-------   1 root root 2147483648 Sep 23  2021 swapfile
dr-xr-xr-x  13 root root          0 Jan 18 22:26 sys
drwxrwxrwt  26 root root      12288 Jan 19 06:28 tmp
drwxr-xr-x  14 root root       4096 Aug 19  2021 usr
drwxr-xr-x  16 root root       4096 Jan 18 22:13 var

```

---

### Post by scpatl4now on 2023-01-19
I have this problem, and this allows me to log in, but if I reboot again, I have to purge 
nvidia and reinstall again.  The thread I started is here.  I think there is a bigger problem happening

[https://ubuntuforums.org/showthread.php?t=2483064](https://ubuntuforums.org/showthread.php?t=2483064)

---

### Post by bigmell3 on 2023-08-11
Ahoy I was going crazy for a minute.  I upgraded to 22.04 from 20.04 as it was EOL for Ubuntu Mate.  A couple show stopping bugs followed by the blank screen.  The first problem was some python packages were not compatible with upgrading from the command line using 

**[COLOR=#000000]sudo do-release-upgrade[/COLOR]**

So first I had to remove the offending packages which was not entirely obvious.  I found a working solution here
[https://answers.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+question/702823](https://answers.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+question/702823)

Basically I had to run

[B][COLOR=#000000][FONT=&amp]sudo apt update
apt policy libpython3.10-stdlib
apt --simulate purge libpython3.10-stdlib
[/FONT][/COLOR][/B]
[COLOR=#000000][FONT=&amp][FONT=Verdana]To first check that the purge would work.  That looked ok so I ran[/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]**sudo apt purge libpython3.10-stdlib libpython3.10-minimal python3.10-minimal**
[/FONT][/COLOR]
So that fixed the first problem and the upgrade began working properly.  I then got the blank screen with flashing cursor after reboot so I hit ctrl+alt+f1 and ran 

[B]sudo apt update 
sudo apt upgrade[/B]

It told me I had some broken packages specifically libdvd-pkg. The specific error was

**libdvd-pkg: `apt-get check` failed, you may have broken packages. Aborting**


I found a fix here
[https://askubuntu.com/questions/1094062/libdvd-pkg-apt-get-check-failed-you-may-have-broken-packages-aborting](https://askubuntu.com/questions/1094062/libdvd-pkg-apt-get-check-failed-you-may-have-broken-packages-aborting)

Basically I had to run
**dpkg-reconfigure libdvd-pkg**


One more problem down.  Ok now for the blank screen.  Turns out it was the nvidia drivers.  I tried the solution here
[https://ubuntuforums.org/showthread.php?t=2468381](https://ubuntuforums.org/showthread.php?t=2468381)

But that didnt work that line was already commented out.  So I found this page 
[https://www.aptgetlife.co.uk/fixing-ubuntu-black-screen-with-blinking-cursor/](https://www.aptgetlife.co.uk/fixing-ubuntu-black-screen-with-blinking-cursor/)


and the solution was 
[B]sudo apt purge ~nvidia
sudo apt autoremove
sudo apt clean[/B]
[COLOR=#DDDDDD][FONT=monospace]

[/FONT][/COLOR]After a reboot that worked.  Mate was now running with the noveau driver installed.  No more blinking cursor screen. 

 However the driver crashed after a little while.  It did this 2 more times I think.  But I had this problem before so I knew the solution is to install the nvidia drivers.  I remember having to try a few different drivers before one worked right but that is basically what happened and how I got it working again with the noveau driver.  Next is manually install an nvidia driver which I can talk about a little.  It wasnt as straight forward as it would seem.  Strangely nothing was autodetected and dmesg was showing an error with the nouveau driver.

[B][Fri Aug 11 06:32:01 2023] nouveau 0000:03:00.0: msvld: unable to load firmware data
[Fri Aug 11 06:32:01 2023] nouveau 0000:03:00.0: msvld: init failed, -19
[Fri Aug 11 06:38:39 2023] nouveau 0000:03:00.0: fifo: fault 01 [WRITE] at 00000000068e0000 engine 00 [GR] client 0f [GPC1/PROP_0] reason 02 [PTE] on channel 4 [023f7aa000 Xorg[2968]]
[Fri Aug 11 06:38:39 2023] nouveau 0000:03:00.0: fifo: channel 4: killed
[Fri Aug 11 06:38:39 2023] nouveau 0000:03:00.0: fifo: runlist 0: scheduled for recovery
[Fri Aug 11 06:38:39 2023] nouveau 0000:03:00.0: fifo: engine 0: scheduled for recovery
[Fri Aug 11 06:38:39 2023] nouveau 0000:03:00.0: Xorg[2968]: channel 4 killed!
[Fri Aug 11 06:40:58 2023] nouveau 0000:03:00.0: Direct firmware load for nouveau/nve6_fuc084 failed with error -2
[Fri Aug 11 06:40:58 2023] nouveau 0000:03:00.0: Direct firmware load for nouveau/nve6_fuc084d failed with error -2
[Fri Aug 11 06:40:58 2023] nouveau 0000:03:00.0: msvld: unable to load firmware data
[Fri Aug 11 06:40:58 2023] nouveau 0000:03:00.0: msvld: init failed, -19[/B]


So none of the nvidia drivers were autodetected and I had to manually reinstall everything.  I found a solution here.
[https://linuxconfig.org/how-to-install-the-nvidia-drivers-on-ubuntu-22-04](https://linuxconfig.org/how-to-install-the-nvidia-drivers-on-ubuntu-22-04)

I had a few screen freezes and had to reboot, but basically I ran

[B]sudo add-apt-repository ppa:graphics-drivers/ppa
sudo ubuntu-drivers autoinstall
sudo apt install nvidia-driver-470
sudo reboot[/B]

And after a reboot it seems like everything is installed and working.  The Noveau driver error in dmesg is gone, no crashes so far after a few earlier, and the driver seems to be working fine.  Here is a niggling new change.  After the updates you now need root to run dmesg.  You can change it back to where users can run dmesg without root.  I found it a bit more convenient this way.  Found a solution here.
[https://unix.stackexchange.com/questions/390184/dmesg-read-kernel-buffer-failed-permission-denied](https://unix.stackexchange.com/questions/390184/dmesg-read-kernel-buffer-failed-permission-denied)

Basically after this error

**dmesg: read kernel buffer failed: Operation not permitted**

I ran 

**emacs /etc/sysctl.d/10-kernel-hardening.conf**


Uncomment the following line

[B]#kernel.dmesg_restrict = 0

[/B]Then run
[B]sudo service procps restart
dmesg -T
[/B]
This will make it so it works after a reboot.  The -T option on dmesg gives you a readable time instead of a long decimal number.  After that everything seems ok.  My raid array came back online ok.  Dmesg reported a brief error with one of my drives, but mdadm didnt remove it from the array.  I suspect it was related to those couple of crashes and the drive is more or less the same.  Old, full, gonna fail one day, but currently working fine.  I got one spare in the closet just in case  :)

I hope this helps.  Other than this the upgrade was unattended except for a few click ok and yes/no/default screens.  If anything isnt working like before I havent noticed it yet. 

 Oh, the default desktop theme in ubuntu mate changed from Ambiant and radiant themes to yaru mate.  I dont particularly like the new theme and was able to go back to the old one after installing it via ppa.  Found a solution here.
[https://ubuntu-mate.community/t/ubuntu-mate-22-04-theme-solved/25215/9](https://ubuntu-mate.community/t/ubuntu-mate-22-04-theme-solved/25215/9)
[URL="https://ubuntu-mate.community/t/ubuntu-mate-22-04-theme-solved/25215Basically"]
[/URL]Basically I ran
[B]sudo add-apt-repository ppa:lah7/ambiant-mate
sudo apt update[/B]
**sudo apt install ambiant-mate-gtk-themes ambiant-mate-icon-themes**

Then I went to system/preferences/look and feel/Appearance and changed my theme to Ambiant-MATE.  Good luck guys if anything else comes up I will post a reply to the thread but seems ok for the last half hour or so.

**UPDATE: I had to remove the fog on the flying toasters screensaver on xscreensaver.  I'll keep an eye on what else they have changed.

---

### Post by wavesound on 2024-03-02
Hi All
I now have this problem on all boots.
Black screen with mouse that can move ok.
IF I use the terminal and get to a prompt using: startx I get oops something went wrong.
On reboot all is fine.
So I reboot twice to get my desktop.
Cheers all
Ubuntu studio 22.04 fully updated.

---

