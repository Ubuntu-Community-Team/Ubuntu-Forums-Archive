---
title: "Old Hardware &amp; Ubuntu - How to use it console only again?"
date: 2007-06-22
forum: General Help
---

### Post by isync on 2007-06-22
Hi,

after installing Ubuntu "not as server", I ended up with a working but not so fast graphical system. Now, what can I do / do I have to do, to make the box "console-only" again. Or how can I turn off as much non-used services as possible to free RAM?
(step-by-step commands welcome..)



**The story behind it:**

I have installed Ubuntu 7.04 on an old AMD 450Mhz System holding 192MB of RAM. Now I see that the overall performance is quite low. I intended to run the box as host for a cpu intensive Perl-script...

Now, letting it run in Gnome in a terminal window, I get a speed of 1/6 of the speed I get on a modern K6 machine. So far so good.

But when I looked at "free", I see quite some of the RAM is eaten up by the window manager. So I did
```
sudo /etc/init.d/gdm stop
``` and exited to console only operation of the box to see if it performs better. It did. When I get 1 cycle per second under GNOME, I get 1.5 cycles in console only. And free tells me that I got about 50MB more of free RAM. So I think the performance of my script is somewhat related to free RAM.

---

### Post by tgalati4 on 2007-06-22
You answered your own question.  Print a list of what is in /etc/init.d.

Make notes as you stop each individual service.  Continue until something breaks.  Turn the offending service back on.

What is it exactly that your script does?  We're curious.

---

### Post by isync on 2007-06-22
Being not (yet) a big linux geek, how do I exactly "stop individual services"?

> What is it exactly that your script does? We're curious.
Sorry to disappoint you: it is munging boring statistical data from the lab and generating reports of it... ;)

---

### Post by tgalati4 on 2007-06-22
If you print out a list of /etc/init.d you will have something like:

acpid                ifrename                         readahead
acpi-support         inetd                            readahead-desktop
alsa-utils           keymap.sh                        README
anacron              klogd                            reboot
apcupsd              laptop-mode                      rmnologin
apmd                 linux-restricted-modules-common  rsync
atd                  lm-sensors                       rwhod
binfmt-support       loopback                         samba
bittorrent           lvm                              screen
bluez-utils          makedev                          screen-cleanup
bootclean.sh         mdadm                            sendmail
bootlogd             mdadm-raid                       sendsigs
bootmisc.sh          module-init-tools                sensord
brltty               mountall.sh                      single
checkfs.sh           mountdevsubfs                    skeleton
checkroot.sh         mountnfs.sh                      smartmontools
console-screen.sh    mountvirtfs                      ssh
cron                 mpd                              stop-bootlogd
cupsys               mtab                             stop-readahead
dbus                 mysql                            sudo
dns-clean            mysql-ndb                        sysklogd
evms                 mysql-ndb-mgm                    udev
festival             networking                       umountfs
fetchmail            ntp-server                       umountnfs.sh
flashplugin-nonfree  nvidia-kernel                    umountroot
gdm                  pcmcia                           ups-monitor
glibc.sh             pcmciautils                      uptimed
gnump3d              powernowd                        uptimed.sh
halt                 powernowd.early                  urandom
hostname.sh          ppp                              usplash
hotkey-setup         pppd-dns                         vbesave
hplip                procps.sh                        waitnfs.sh
hwclockfirst.sh      rc                               x11-common
hwclock.sh           rc.local                         xinetd

It's a big list.

If you don't need printing then:

sudo /etc/init.d/cupsys stop

Don't need speech synthesis in programs:

sudo /etc/init.d/festival stop

Examine what processes you are running and that will give you a clue as to what to kill:

ps -ef > myhumungouslistofprocessesthatIwanttoexamine.txt

Look at all the processes that you may or may not need for your mungefest.

sudo kill -9 1234

(Where 1234 is the process number of the process that you don't need anymore for this session.)

---

### Post by isync on 2007-06-22
Thanks for the effort!! :KS

---

