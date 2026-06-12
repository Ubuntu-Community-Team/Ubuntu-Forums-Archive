---
title: "System Beep during Boot"
date: 2008-05-03
forum: General Help
---

### Post by haelen on 2008-05-03
Since installing Hardy, my system beep annoyingly kicks in during the boot process. 

I can't see at what point it happens because of the splash screen.

TIA,
Tim

---

### Post by Aearenda on 2008-05-03
One way to suppress usplash is to press ESC when it says 'Press ESC to enter Menu', and then choose a recovery startup. When it stops to ask you what to do, just resume the startup. You may find that the text goes by too fast to be able to tell what is happening as the beep occurs - but you can review the startup after login using the system->administration->log viewer and looking through the kernel log, amongst others.

However, it may be that the beep is just GDM announcing its startup, in the absence of a working sound system - to turn that off, go to system->administration->login window, and then go to the 'Accessibility' tab, and disable the login screen ready sound.

---

### Post by haelen on 2008-05-03
> **Aearenda said:**
> One way to suppress usplash is to press ESC when it says 'Press ESC to enter Menu', and then choose a recovery startup. When it stops to ask you what to do, just resume the startup. You may find that the text goes by too fast to be able to tell what is happening as the beep occurs - but you can review the startup after login using the system->administration->log viewer and looking through the kernel log, amongst others.

However, it may be that the beep is just GDM announcing its startup, in the absence of a working sound system - to turn that off, go to system->administration->login window, and then go to the 'Accessibility' tab, and disable the login screen ready sound.

Hi,

I turned off the "login screen ready" sound, and I still get the beep.

The fact is, I'm not sure exactly what I need to be looking for if I look through the kernel log.

Best,
Tim

---

### Post by Aearenda on 2008-05-03
I don't know either! I guess you're looking for something that complains... :-) 
Any luck with watching the recovery startup?

---

### Post by el-mar01 on 2008-05-03
I got the beep on the Login Screen on Gusty ... but I fixed it somehow ... I think it was to do with the system having no sound drivers and it just beeped.

---

### Post by haelen on 2008-05-03
> **Aearenda said:**
> I don't know either! I guess you're looking for something that complains... :-) 
Any luck with watching the recovery startup?

Um, not really :( As you said, the screen scrolled too fast for me to even guess what the beep might relate to.

Tim

---

### Post by Zorael on 2008-05-03
There's a way that's not as verbose as picking the recovery mode, so it's easier to parse what might've gone wrong upon boot.

When the boot splash appears, shortly after having chosen your kernel and way before graphical environment loads, hit Ctrl+Alt+F1. If there isn't a wall of text greeting you, try switching to Alt+F8 and see if it's there instead, else pop back to Alt+F1. Once you find it, wait for the beep and see if there's an error message output at the same time.

---

### Post by haelen on 2008-05-03
> **el-mar01 said:**
> I got the beep on the Login Screen on Gusty ... but I fixed it somehow ... I think it was to do with the system having no sound drivers and it just beeped.

How did you fix it. Install required drivers?

Tim

---

### Post by Zorael on 2008-05-03
Installing drivers is usually not required in linux. To see if the drivers are loaded, enter this in a terminal and review its output.
```
$ lshw -C multimedia
```

Contradictory to popular misconception, linux *does* have the best drivers, though with lacking corporate support there are devices and peripherals that plain don't work. Try installing Vista on a system a few years old and see where that gets you, though. :>

---

### Post by haelen on 2008-05-03
```

  *-multimedia            
       description: Audio device
       product: 82801G (ICH7 Family) High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel

```

---

### Post by haelen on 2008-05-03
> **Zorael said:**
> There's a way that's not as verbose as picking the recovery mode, so it's easier to parse what might've gone wrong upon boot.


Thanks. It's useful to know this.

Yes, it was less verbose - but I could still only approximate what the beep was related to.

Something about "missing file .... kernel tree" perhaps? Maybe not.

Tim

---

### Post by Zorael on 2008-05-03
> **haelen said:**
> ```

...
       configuration: **driver=HDA Intel** latency=0 **module=snd_hda_intel**

```
So the driver is loaded properly.

Did you try the Ctrl+Alt+F1 / Alt+F1-F8 approach, to try to divine what's invoking the beep?

---

### Post by Aearenda on 2008-05-03
Sounds a bit like [https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/80535](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/80535)

Also see this: [http://www.linuxforums.org/forum/servers/111550-ubuntu-server-making-continous-beep-sound-urgent-pls-help.html](http://www.linuxforums.org/forum/servers/111550-ubuntu-server-making-continous-beep-sound-urgent-pls-help.html) - not sure it gets us any further though.

And [https://answers.launchpad.net/ubuntu/+question/28253](https://answers.launchpad.net/ubuntu/+question/28253).

---

### Post by Aearenda on 2008-05-03
The 'missing file' might be a key into the logs - try ```
grep issing /var/log/kern.log
```
Note the deliberate mistype - you should really do ```
grep [Mm]issing /var/log/kern.log
``` to pick up capital or lower M, but I'm just lazy...

---

### Post by haelen on 2008-05-03
> **Aearenda said:**
> Sounds a bit like [https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/80535](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/80535)

Also see this: [http://www.linuxforums.org/forum/servers/111550-ubuntu-server-making-continous-beep-sound-urgent-pls-help.html](http://www.linuxforums.org/forum/servers/111550-ubuntu-server-making-continous-beep-sound-urgent-pls-help.html) - not sure it gets us any further though.

And [https://answers.launchpad.net/ubuntu/+question/28253](https://answers.launchpad.net/ubuntu/+question/28253).

It's closest to the last bug - but mine only beeps once! Plus my PC is totally different from the one mentioned.

---

### Post by haelen on 2008-05-03
> **Aearenda said:**
> The 'missing file' might be a key into the logs - try ```
grep issing /var/log/kern.log
```
Note the deliberate mistype - you should really do ```
grep [Mm]issing /var/log/kern.log
``` to pick up capital or lower M, but I'm just lazy...

Nothing found unfortunately.

---

### Post by haelen on 2008-05-03
> **Zorael said:**
> So the driver is loaded properly.

Did you try the Ctrl+Alt+F1 / Alt+F1-F8 approach, to try to divine what's invoking the beep?

Yes, but still to fast (although less verbose) to identify.

---

### Post by Aearenda on 2008-05-03
Are you willing to upload /var/log/kern.log so we can have a look? You'll need to go to advanced mode, and then click on the paper-clip icon.

---

### Post by Zorael on 2008-05-03
Is it possible to hit Pause/Break when that scrolls by?

Enter to resume.

---

### Post by haelen on 2008-05-03
> **Aearenda said:**
> Are you willing to upload /var/log/kern.log so we can have a look? You'll need to go to advanced mode, and then click on the paper-clip icon.

[http://paste.ubuntu.com/9735/](http://paste.ubuntu.com/9735/)

Is that OK?

---

### Post by haelen on 2008-05-03
For some reason if I try to attach kern.log I get "invalid file" :(

---

### Post by Aearenda on 2008-05-03
It's there ok - but I can't see a reason for the beep :-(
Still working through it - but it's late here....

---

### Post by Aearenda on 2008-05-03
It seems that the system rebooted several times in a row - was that you trying to see the message as it scrolls by?

There is a gdm segfault that could be the culprit.

---

### Post by haelen on 2008-05-03
> **Aearenda said:**
> It seems that the system rebooted several times in a row - was that you trying to see the message as it scrolls by?

Yes.

> **Aearenda said:**
> There is a gdm segfault that could be the culprit.

Not sure what that means :)

I appreciate you looking through the log - and that it's late in Oz. At least this fault isn't impeding my work. It just annoys the hell out of anyone in the vicinity - particularly if they're still asleep ;)

---

### Post by Aearenda on 2008-05-03
You could always unplug the speaker - but that's cheating :-)

A segfault is a sort of program crash. Are you using a stock GDM theme (login screen), or a custom one?

Try this (it will stop GDM from starting up automatically - you will need to login to a command-line prompt to re-enable it, so don't do this if that sounds hard):
```
sudo mv /etc/rc2.d/S30gdm /etc/rc2.d/K30gdm
```
and reboot. 

The startup will finish with a command-line login prompt. Does the beep happen? If so, it's not GDM.

To re-enable, log in to the command line (same user and password as usual) and do 
```
sudo mv /etc/rc2.d/K30gdm /etc/rc2.d/S30gdm
```

You can then start GDM like this:
```
sudo /etc/init.d/gdm start
```
and you will soon be able to log in normally. It would be interesting to note if a beep occurs as GDM start up!

---

### Post by Aearenda on 2008-05-03
Actually, I've noticed the GDM segfaults occur later - probably as you restart. That's not it, but the test I just suggested is worth doing anyway. 

Approximately how many seconds into the boot does the beep happen?
Have you installed anything extra that runs as a service - apache, for example?

PS - no more from me until morning now.

---

### Post by haelen on 2008-05-03
I'm happy to try that, but when I try to move it I get this:

```
mv: cannot stat `/etc/rc2.d/S30gdm': No such file or directory

```

---

### Post by strabes on 2008-05-03
Why don't you just disable the system beep speaker? All you have to do is [blacklist the pcspkr module](http://strabes.wordpress.com/2006/10/16/remove-the-system-beep-in-ubuntu/).

---

### Post by haelen on 2008-05-03
> **strabes said:**
> Why don't you just disable the system beep speaker? All you have to do is [blacklist the pcspkr module](http://strabes.wordpress.com/2006/10/16/remove-the-system-beep-in-ubuntu/).

Perfect!

Thanks for that.

Tim

---

### Post by Aearenda on 2008-05-03
Disabling the speaker is cheating too! :-)
This means it will never beep, even at other times when it ought to.
Still, if that's acceptable, then we can stop mucking around with the startup process to try and find the real cause.

---

### Post by haelen on 2008-05-04
Hi,

I realise it's cheating. Let's say it's at least a temporary expedient ;) I've had to cheat twice with Hardy this week. I had to install the Windows version on Audacity under WINE, because the Linux one won't work. (Currently a bug reported by several others.

---

### Post by Aearenda on 2008-05-04
That's a useful tip - I use Audacity on a PC still running Gutsy, so now I know not to upgrade it yet!

By the way, do you use the realtime kernel (for audio stuff, I presume)?

---

### Post by vishzilla on 2008-05-04
I think I solved it by going to System>Prefs>Sound>System Beep. Unchecking Enable system beep and checking Visual Beep. I am not sure...I will enable it again and see if it happens.
Edit: I had this problem in Gutsy, Hardy no longer beeps the system. :)

---

### Post by haelen on 2008-05-04
> **Aearenda said:**
> That's a useful tip - I use Audacity on a PC still running Gutsy, so now I know not to upgrade it yet!

By the way, do you use the realtime kernel (for audio stuff, I presume)?

Yeah. Audacity under WINE is still limited somewhat (no way of controlling bitrate of MP3's, for example - defaults to 128).

Yes, using RT kernel.

Cheers,
Tim

---

### Post by Aearenda on 2008-05-04
Ok, that just confirms something I saw in the log you uploaded - I've never used the rt kernel. So now I'm wondering if you have some audio stuff installed that was doing the beeps - if you have time would you mind listing the files in /etc/rc2.d and /etc/rcS.d please? (I'm also still wondering why the gdm startup was missing).

```
ls /etc/rc2.d
ls /etc/rcS.d
```

---

### Post by haelen on 2008-05-04
> **Aearenda said:**
> Ok, that just confirms something I saw in the log you uploaded - I've never used the rt kernel. So now I'm wondering if you have some audio stuff installed that was doing the beeps - if you have time would you mind listing the files in /etc/rc2.d and /etc/rcS.d please? (I'm also still wondering why the gdm startup was missing).

```
ls /etc/rc2.d
ls /etc/rcS.d
```

```
K50ntp                              S18avahi-daemon        S20vboxdrv
README                              S18mysql-ndb           S20vboxnet
S01policykit                        S19cupsys              S24dhcdbd
S05vbesave                          S19mysql               S25bluetooth
S07linux-restricted-modules-common  S20apmd                S25pulseaudio
S09hsf                              S20apport              S89anacron
S10acpid                            S20dictd               S89atd
S10powernowd.early                  S20dkms_autoinstaller  S89cron
S10sysklogd                         S20hotkey-setup        S90binfmt-support
S10xserver-xorg-input-wacom         S20lastfmproxy         S95preload
S11klogd                            S20lastfmsubmitd       S98usplash
S12dbus                             S20makedev             S99acpi-support
S12hal                              S20nvidia-kernel       S99laptop-mode
S13gdm                              S20powernowd           S99rc.local
S16ssh                              S20rsync               S99rmnologin
S17mysql-ndb-mgm                    S20smartmontools       S99stop-readahead

```

and

```
haelen@dell:~$ ls /etc/rcS.d
README                S20checkroot.sh           S45waitnfs.sh
S01mountkernfs.sh     S22mtab.sh                S46libpam-foreground
S01readahead          S25brltty                 S46mountnfs-bootclean.sh
S02hostname.sh        S26cryptdisks-early       S49console-setup
S06keyboard-setup     S28cryptdisks             S55dns-clean
S08hwclockfirst.sh    S30checkfs.sh             S55pppd-dns
S08loopback           S35mountall.sh            S65firestarter
S10udev               S36mountall-bootclean.sh  S70screen-cleanup
S11hwclock.sh         S37apparmor               S70x11-common
S11mountdevsubfs.sh   S37mountoverflowtmp       S80bootmisc.sh
S13pcmciautils        S37udev-finish            S85urandom
S15module-init-tools  S39readahead-desktop      S90console-screen.sh
S17procps             S39ufw
S17procps.sh          S40networking

```

BTW, the system beep was a problem even *before* I installed Rt kernel.

Won't be able to respond any more today as I'm off out.

Cheers,
Tim

---

### Post by haelen on 2008-05-04
Thanks.

This was one of the first things I tried as a solution, and it didn't work.

Best,
Tim

---

### Post by Aearenda on 2008-05-04
You do have some stuff there that I don't have. To try to track it down, I would go to system->administration->services and disable all the extras/non-essentials you can there, then reboot and see if it beeps (with pcspkr enabled), and if not, then turn them on again gradually to see which it is. Here is my rc2.d list, so you can see what is extra: (my extras are bonager, ssh, samba, uml, vbox, smartmontools).

```
ls /etc/rc2.d
README                       S20bonager        S25bluetooth
S01policykit                 S20cupsys         S25pulseaudio
S05vbesave                   S20hotkey-setup   S30gdm
S10acpid                     S20nvidia-kernel  S89anacron
S10powernowd.early           S20powernowd      S89atd
S10sysklogd                  S20rsync          S89cron
S10xserver-xorg-input-wacom  S20samba          S98usplash
S11klogd                     S20smartmontools  S99acpi-support
S12dbus                      S20uml-utilities  S99laptop-mode
S16ssh                       S20vboxdrv        S99rc.local
S18avahi-daemon              S20vboxnet        S99rmnologin
S20apmd                      S24dhcdbd         S99stop-readahead
S20apport                    S24hal
``` and for completeness, my rcS.d list: ```
ls /etc/rcS.d/
README                              S35mountall.sh
S01mountkernfs.sh                   S36mountall-bootclean.sh
S01readahead                        S37apparmor
S02hostname.sh                      S37mountoverflowtmp
S06keyboard-setup                   S37udev-finish
S07linux-restricted-modules-common  S39readahead-desktop
S08hwclockfirst.sh                  S39ufw
S08loopback                         S40networking
S10udev                             S45waitnfs.sh
S11hwclock.sh                       S46mountnfs-bootclean.sh
S11mountdevsubfs.sh                 S49console-setup
S13pcmciautils                      S55dns-clean
S15module-init-tools                S55pppd-dns
S17procps                           S70screen-cleanup
S20checkroot.sh                     S70x11-common
S22mtab.sh                          S80bootmisc.sh
S25brltty                           S85urandom
S30checkfs.sh                       S90console-screen.sh
```

Mine was a fresh Hardy installation, not an upgrade.

Of course, you may not want to bother, now that disabling the pcspkr has solved the problem in practice, and I wouldn't blame you for that - this one has certainly had you doing more than your fair share of reboots!

---

### Post by haelen on 2008-05-04
Hi,

TBH, I wouldn't know where extras and which were not :)

I'm happy to leave it for now and make do with the temporarily disable spkr!

I appreciate your time. I don't know if the "thank" facility is working at the moment on the forums. I'll atke a look.

Cheers,
Tim

---

