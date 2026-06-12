---
title: "Can't login after installing nvidia drivers."
date: 2015-06-26
forum: General Help
---

### Post by jakub19 on 2015-06-26
Hello, I know that there was many threads like this, but I just can't find working solution :(

I just started my adventure with linux (ubuntu) so I am total newbie at this, but I'm trying really hard :)

SO

after installing ubuntu
system started in 1024x768 resolution (1024x768 or 800x600 to choose)

window popped to update system, cliked ok, then reboot

system still in 1024x768
so i tried to
1) choose drivers from "additional drivers"
2) sudo apt-get install nvidia
3) sudo apt-get install nvidia-current
4) sudo apt-get install nvidia-[number]
 
After each of 1-2-3-4 the result was the same
system booted with "login screen" and when I input the password, screen goes black for seconds and puts me back in "login screen"
same with guest account

So what I'm doing at this step, going to text-mode - ctrl alt F1 - and remove nvidia

sudo apt-get remove --purge nvidia*

after that sytem boots in 1024x768 and I am still able to do anything

PLEASE help me with installation proper drivers and get proper resolution - 1600x900

my specs:
ubuntu 14.04
graphic card: geforce gt 525m

please please help me

---

### Post by dino99 on 2015-06-26
welcome to ubuntu  ):P

for your graphic card/chipset, install nvidia-346
> sudo apt-get purge nvidia*
also remove xorg.conf file if you have ran nvidia-settings, you dont need it and often push the mess inside the system
> sudo apt-get install nvidia-346

then the question is: do you also have 'optimus' enabled ? if 'yes' then turn it off for the first test; it can be re-enabled later if that works better without it. Do you have a cpu with an embedded gpu ?

---

### Post by jakub19 on 2015-06-26
Can you write everything again with more commands and enter each time to when it's time to reboot ? :D

how to check optimus?
how to remove xorg? where is it

---

### Post by grahammechanical on 2015-06-26
System Settings>Software & Updates will find and install appropriate proprietary video drivers for us.

Nvidia Optimus technology is where there is an Intel graphic adapter built into the motherboard and also an Nvidia graphic adapter in a slot on the motherboard and the system was purchased with this set up. It is called hybrid graphics.

The idea is that the Intel adapter is used for low graphic intensity tasks and the system switches to the Nvidia adapter for high graphic intensity tasks. Linux does not yet have proprietary video drivers that will do this switching automatically which is what happens with Windows machines. On Linux the switching has to be done manually using the Nvidia settings utility or Prime Indicator which puts an app indicator in the top panel. This is not necessary if we do not have Nvidia Optimus technology.

Oh, by the way, we do not remove X.Org. Everything runs on the X.Org X server. Are you thinking of some X server configuration file? One more thing. It is not clear that you are trying to get the monitor to run at a resolution higher that 1024 x 768.

I have found that a VGA connection between video adapter and monitor will limit screen resolution. DVI or HMDI give higher resolutions than VGA if the video adapter and the monitor have those connectors.

Regards.

---

### Post by Bashing-om on 2015-06-26
jakub19; Hello; Welcome to the forum.

Let's back up regroup and start again at square 1 ( the basics).

Graphics issue, we always want to know 1st is what hardware you have . So from the desktop open up a terminal - key combo ctl+alt+t - In this terminal type the command :
```

lspci -vnn | grep VGA -A 12

```
Which will identify the graphic's hardware.
Paste that output back to this thread:
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Next we want to know if the system is capable of loading a graphics driver:
What returns from terminal command:
```

sudo lshw -C display

```

With this info we have a good indication of where to go next to get a working display.

[INDENT][INDENT]get the kernel to talk to the monitor
[INDENT][INDENT][INDENT]got to have intermediate-tion
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by jakub19 on 2015-06-27
"lspci -vnn | grep VGA -A 12" right back at you ! :D

```

enfu@enFuego:~$ lspci -vnn | grep VGA -A 12
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09) (prog-if 00 [VGA controller])
    Subsystem: Dell Device [1028:04c4]
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at f1400000 (64-bit, non-prefetchable) [size=4M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 4000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>

00:16.0 Communication controller [0780]: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 [8086:1c3a] (rev 04)
    Subsystem: Dell Device [1028:04c4]
    Flags: bus master, fast devsel, latency 0, IRQ 50
    Memory at f1b05000 (64-bit, non-prefetchable) [size=16]
--
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF108M [GeForce GT 525M] [10de:0df5] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: Dell Device [1028:04c4]
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at f0000000 (32-bit, non-prefetchable) [size=16M]
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Memory at d0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at 3000 [disabled] [size=128]
    Expansion ROM at f1000000 [disabled] [size=512K]
    Capabilities: <access denied>

02:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1030 [Rainbow Peak] [8086:008a] (rev 34)
    Subsystem: Intel Corporation Centrino Wireless-N 1030 BGN [8086:5325]
    Flags: bus master, fast devsel, latency 0, IRQ 51

```

and "sudo lshw -C display" !

```

enfu@enFuego:~$ sudo lshw -C display
[sudo] password for enfu: 
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: GF108M [GeForce GT 525M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:f0000000-f0ffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:3000(size=128) memory:f1000000-f107ffff
  *-display UNCLAIMED
       description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:f1400000-f17fffff memory:e0000000-efffffff ioport:4000(size=64)

```

Now what my Master/Sensei? :D

---

### Post by dino99 on 2015-06-27
> **jakub19 said:**
> Can you write everything again with more commands and enter each time to when it's time to reboot ? :D

how to check optimus?
how to remove xorg? where is it

hey, be carefull, i've never said to remove xorg ;) but 'xorg.conf' you can easily find (if it exist) via the 'search' feature of your package manager (nautilus if gnome is used)
about 'optimus' glance to the bios/uefi settings first

---

### Post by Bashing-om on 2015-06-27
jakub19; Hey hey !


Now we do know a couple or few things.
1) Yep optimus technology at play here;
2) There is no graphics driver in-use for the Nvidia chip set.

So, to deal with optimus we install a Nvidia proprietary driver along with "nvidia-settings" to control/switch chip sets.

To that end, clean up and get ready to install:
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

```
Checking with Nvidia, they recommend the 352 version for your Nvidia card - the 346 might do better,- the latest and greatest may not be the best - we can see about that later. And in 14.04 release these drivers are not available . So we resort to our supported PPA to get the required driver:
Clean out old Nvidia stuff:
```

sudo apt-get remove --purge nvidia*

```
And install the source code to get AND install the Nvidia driver :
```

sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install nvidia-352

```

Reboot to see the effect . Nvidia-settings is automatically installed along with the driver. Activate 'nvidia-settings' from the GUI to make any tweaks . I do expect the system to be functional as is upon the reboot.

[INDENT][INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT][/INDENT]

---

### Post by jakub19 on 2015-06-29
Okay, so

```

enfu@enFuego:~$ sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
[sudo] password for enfu: 
cp: nie mo&#380;na wykona&#263; stat na &#8222;/etc/X11/xorg.conf&#8221;: Nie ma takiego pliku ani katalogu
enfu@enFuego:~$ 

```

Which basically means there's no such file (I didn't removed/deleted any file).
But ok I'm going through the next steps.

Purging... Done.

Installing driver... Done.

Now I will reboot and I'm hoping for the best.
I will post here the result :) from here or from windows :D

-----------

So... As I expected...
I'm stuck at "login screen".
When I enter my password screen goes black for couple of seconds then drops me back at the "login screen".
When I try to login as a Guest same thing happens.

And at this point I'm so bad at working at terminal (ctrl+alt+F1), so now... if anyone still wants to help me
you need to be very specific at what I am supposed to do :)

Please help :<

---

### Post by dino99 on 2015-06-29
There is a question i would like to know: is it a real ubuntu installation ? or inside windows (wubi is deprecated and broken)

---

### Post by jakub19 on 2015-06-29
Ubuntu downloaded from [www.ubuntu.com](www.ubuntu.com).
Partition ex4 100gb + swap 8gb :)

---

### Post by Bashing-om on 2015-06-29
jakub19; Well !

To say the least I am surprised that the Nvidia driver did not install.
Nvidia does use the xorg.conf file and it is unexpected that the file did not exist.

There are 2 major causes of your condition.
1) A loss of authorization to access your /home directory. Let's insure this is not the case:
Boot to terminal and execute terminal commands:
```

ls -al /home
ls -al .Xauthority
ls -al .ICEauthority

```
Do you have ownership and grouped to these files ? As in :
> 
sysop@1404mini:~$ ls -al /home
total 28
drwxr-xr-x  4 root  root   4096 May 19  2013 .
drwxr-xr-x 25 root  root   4096 Jun 16 17:30 ..
drwx------  2 root  root  16384 May 19  2013 lost+found
drwxr-xr-x 29 sysop sysop  4096 Jun 29 10:39 sysop

Where I am "sysop" .

2) Is the condition no graphics driver loaded ? :
```

dpkg -l | grep -i nvidia
cat /var/log/Xorg.0.log

```

Now let's see what we know and where we go from here.

[INDENT][INDENT][INDENT]it's all in the process
[/INDENT][/INDENT][/INDENT]

---

### Post by jakub19 on 2015-06-29
But how I am supposed to copy/paste anything from "text mode" [ctrl alt F1]? 
It's too many. I need to make pics and then rewrite it or there is some other way?
Maybe some log file of writed commands and their responses ?

---

### Post by Bashing-om on 2015-06-29
jakub19; Ooopppsds;

My oversight. We have a tool for that, pastebinit .
```

sudo apt-get install pastebinit
dpkg -l | grep -i nvidia | pastebinit
cat /var/log/Xorg.0.log | pastebinit

```
The results are URLs back to your terminal.
Pass these URLs back to the thread, and we can access these files on the paste site.

[INDENT][INDENT]more than one way, huh ?
[/INDENT][/INDENT]

---

### Post by jakub19 on 2015-06-30
So.

ls al /home
```

Total 12
[COLOR=#000000]drwxr-xr-x 3 root root 4096 cze 24 15:03 .
[/COLOR][COLOR=#000000]drwxr-xr-x 24 root root 4096 cze 24 16:21 ..
[/COLOR][COLOR=#000000]drwxr-xr-x 20 enfu enfu 4096 cze 30 13:39 enfu
[/COLOR]
```[COLOR=#000000]

ls -al .Xauthority
[/COLOR]```
[COLOR=#000000]-rw------- 1 enfu enfu 52 cze 30 13:39 .Xauthority[/COLOR][COLOR=#000000]
[/COLOR]
```[COLOR=#000000]

ls -al .ICEauthority
[/COLOR]```
[COLOR=#000000]-rw------- 1 enfu enfu 3542 cze 29 14:24 .ICEauthority[/COLOR][COLOR=#000000]
[/COLOR]
```[COLOR=#000000]

next...

dpkg -l | grep -i nvidia
[/COLOR]```
ii  bbswitch-dkms                                         0.7-2ubuntu1                                        amd64        Interface for toggling the power on nVidia Optimus video cards
rc  libcuda1-304                                          304.125-0ubuntu0.0.1                                amd64        NVIDIA CUDA runtime library
rc  libcuda1-304-updates                                  304.125-0ubuntu0.0.1                                amd64        NVIDIA CUDA runtime library
rc  libcuda1-331                                          331.113-0ubuntu1~xedgers14.04.1                     amd64        NVIDIA CUDA runtime library
ii  libcuda1-352                                          352.21-0ubuntu0~xedgers14.04.1                      amd64        NVIDIA CUDA runtime library
ii  nvidia-352                                            352.21-0ubuntu0~xedgers14.04.1                      amd64        NVIDIA binary driver - version 352.21
ii  nvidia-opencl-icd-352                                 352.21-0ubuntu0~xedgers14.04.1                      amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                          0.6.2                                               amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                                       352.21-0ubuntu0~xedgers14.04.1                      amd64        Tool for configuring the NVIDIA graphics driver

```

and the last one

```

cat /var/log/Xorg.0.log

```
worked ok, but when I wanted to send it to paste.ubuntu

```

cat /var/log/Xorg.0.log | pastebinit

```

This error occured (maybe some little mistakes, had to write it down :))
```

Traceback (most recent call last):
File "/usr/bin/pastebinit", line 345 in <module>
content sys.stdin.read()
File "/usr/lib/python3.4/codecs.py", line 313 in decode
(result, consumed) = self._buffer_decode ( data, self.errors, final)

UnicodeDecodeError: 'utf-8' codec can't decode byte 0x80 in position 12574: invalid start byte

```

Now what ? :(

---

### Post by Bashing-om on 2015-06-30
jakub19; OK;

Those results show that "you" do have the authorization to access your /home, so that is not an issue;
However, perhaps the issue is a conflict of drivers as there are remnants of the 304 and 331 versions remaining on the system.

Let's do try and purge all Nvida, and try and install the 352 version once more.
```

sudo apt-get remove --purge nvidia*

```
Check that there are no Nvidia components now on the system:
```

dpkg -l | grep -i nvidia

```

Do we have the PPA set up from which to obtain the driver ?
```

tail -v -n +1 /etc/apt/sources.list.d/*

```

IF and only IF the PPA source does exist; install the driver:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install nvidia-352

```

Reboot:
```

sudo shutdown -r now

```

Do you now come up on the GUI ? If required to do some tweaking, activate ' nvidia-settings ' from the GUI Nvidia menu.

All we want is for the kernel and monitor to communicate;

[INDENT][INDENT]surely we can make that happen
[/INDENT][/INDENT]

---

### Post by jakub19 on 2015-07-01
OK. I am trying again, btw. thx for respond.

I purged nvidia driver from "text mode" and rebooted so I have GUI now.

Applying to your guidance.

```

enfu@enFuego:~$ dpkg -l | grep -i nvidia
ii  bbswitch-dkms                                         0.7-2ubuntu1                                        amd64        Interface for toggling the power on nVidia Optimus video cards
rc  libcuda1-304                                          304.125-0ubuntu0.0.1                                amd64        NVIDIA CUDA runtime library
rc  libcuda1-304-updates                                  304.125-0ubuntu0.0.1                                amd64        NVIDIA CUDA runtime library
rc  libcuda1-331                                          331.113-0ubuntu1~xedgers14.04.1                     amd64        NVIDIA CUDA runtime library
ii  libcuda1-352                                          352.21-0ubuntu0~xedgers14.04.1                      amd64        NVIDIA CUDA runtime library
enfu@enFuego:~$ 


```

NEXT

```

enfu@enFuego:~$ tail -v -n +1 /etc/apt/sources.list.d/*
==> /etc/apt/sources.list.d/xorg-edgers-ppa-trusty.list <==
deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu trusty main

==> /etc/apt/sources.list.d/xorg-edgers-ppa-trusty.list.save <==
deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu trusty main
enfu@enFuego:~$ 


```

SO :D

```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install nvidia-352

```

and at the end reboot, let's hope for the best :)

I did also
```

sudo apt-get autoremove

```
before installing nvidia-352
...
rebooting now :)

---

### Post by jakub19 on 2015-07-01
--------------

guess what :( :( :(

---

### Post by Bashing-om on 2015-07-01
jakub19; Yikes !

As we are dealing with optimus technology ( hybrid Intel/Nvidia ) ->
OK, did 'nvidia-settings' get installed ?
(it should have !)
Let's check:
```

dpkg -l nvidia-settings

```

Do we have an active 'xorg.conf ' file ?
```

cat /etc/X11/xorg.conf 

```

[INDENT][INDENT]as we try and make sense of all this - not working 
[/INDENT][/INDENT]

---

### Post by jakub19 on 2015-07-02
dpkg -l nvidia-settings
```

Wybór:U=nieznany/I=instalacja/R=usuni&#281;cie/P=wyczyszczenie/H=zatrzymanie
| Stan:N=brak/I=zainstalowany/C=skonfigurowany/U=rozpakowany/
|/  F=cz&#281;&#347;c. skonfigurowany/H=cz&#281;&#347;c. zainstalowany/W=wyzw. czek./T=wyzw. zapl.
|| B&#322;&#281;dy?=(brak)/R-do pon. inst. (du&#380;e litery w "Stan" i "B&#322;&#281;dy"=problemy)
||/ Nazwa                                                 Wersja                                              Architektura Opis
+++-=====================================================-===================================================-============-===============================================================================
ii  nvidia-settings                                       352.21-0ubuntu0~xedgers14.04.1                      amd64        Tool for configuring the NVIDIA graphics driver

```

And here are all files from
/etc/X11/
```


app-defaults
cursors
default-display-manager
fonts
rgb.txt
X
xinit
xkb
Xreset
Xreset.d
Xresources
Xsession
Xsession.d
Xsession.options
xsm
Xwrapper.config

```

:(

---

### Post by Bashing-om on 2015-07-02
jakub19; Wellll ..

2 observations;
1st lets look closer at what is in the "/etc/X11/" directory:
```

ls -al /etc/X11/

```

Looking that the symbolic link:
> 
lrwxrwxrwx  1 root root    13 May 19  2013 X -> /usr/bin/Xorg

Does infact exist.

Then as there is no config file created --- humm, can not imagine, yet why not -- . Create one.

This time from within the 'nvidia-settings ' tool. I do not recall exactly where the option is, but I do recall it is available to create it.
In nvida-settings go ahead and set up the display(s) to your liking, and then save the settings.

That should then create anew the xorg.conf file.

Is the file created? Does it also continue to exist after a reboot ?

We must have that file;
[INDENT][INDENT]somethings there is no getting around
[/INDENT][/INDENT]

---

### Post by jakub19 on 2015-07-05
Well, i managed to achive sth during the weekend.

I was very busy so sorry for no posting.

I installed 'bumblebee' nvidia drivier.

And now after reboot i have GUI but still I cant change resolution to higher than 1024x768.

I can switch through drivers nvidia-352 and older versions and still have GUI.

I was installing bumblebee driver thx to this site

[http://ubuntuforums.org/showthread.php?t=1916538](http://ubuntuforums.org/showthread.php?t=1916538)

```

[COLOR=#000000]sudo add-apt-repository ppa:bumblebee/stable[/COLOR]
[COLOR=#000000]sudo add-apt-repository ppa:ubuntu-x-swat/x-updates[/COLOR]
[COLOR=#000000]sudo apt-get update[/COLOR]
[COLOR=#000000]sudo apt-get --purge remove xserver-xorg-video-nouveau[/COLOR]
[COLOR=#000000]sudo reboot[/COLOR]
[COLOR=#000000]sudo apt-get install bumblebee bumblebee-nvidia linux-headers-generic[/COLOR]
[COLOR=#000000]sudo reboot

```

some of this commands was not working, such purge remove xserver-xorg...

BUT still, we have achieved sth :D

NOW.

To chechk if the driver is in ? What to do.

And what with the resolution?

Please help, i need this for my RoR course.[/COLOR]

---

### Post by Bashing-om on 2015-07-05
jakub19; Hey hey !

Making good progress, But,
I have no experience with BumbleBee. I can offer no further advise.
Others here will take up my slack.

[INDENT][INDENT]now I do not know
[/INDENT][/INDENT]

---

### Post by jakub19 on 2015-07-05
Damn... You were the only one who was really trying to help :D

Waiting for next good person !

---

### Post by Bashing-om on 2015-07-05
jakub19; LOL ;

They are here, give it a bit for them to see and respond.

[INDENT][INDENT]all for 1 and one for all
[/INDENT][/INDENT]

---

### Post by jakub19 on 2015-07-11
Well... Still waiting...

---

### Post by Bashing-om on 2015-07-11
jakub19; Hey;

I do not know any who have BumbleBee installed, thus I can not direct any attention to this thread.

It is permissible to bump a thread after 24 hours rather than - as you have - awaiting 5 days.

Currently there is the greater support for nvidia-prime as the means to cope with hybrid graphics.

[INDENT][INDENT]to err is human
[INDENT][INDENT][INDENT]when I do not know I try to reduce that probability
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by jakub19 on 2015-07-12
Well... I've done it... But can anyone tell me... wtf...

I have installed ubuntu14 one more time but I didn't check the box for downloading updates during installation process...

After that... everything seems to be working fine... So I turned off updates...

BUT WHY IS IT LIKE THAT ?! -.-

---

### Post by Bashing-om on 2015-07-12
jakub19; Hey Hey ...

Yeah;
> 
but I didn't check the box for downloading updates during installation process...


So that now I expect that you are running the open source graphics driver.
check:
```

sudo lshw -C display

```
what is shown in the "configuration" line ?

You should allow updates for the system, the proprietary driver ( if any) will not be installed unless you take the actions to do so.

[INDENT]clean and pure
[INDENT][INDENT][INDENT]just the way we like it
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by monkeybrain20122 on 2015-07-12
BTW after you have installed the Nvidia driver, you should run 
```
sudo nvidia-xconfig
```

This creates the xorg.conf file. Then reboot. It seems that you haven't done that.

---

### Post by jakub19 on 2015-07-14
Well now... STOP :D

After 3rd or 4th reboot of ubuntu, it went back to the problem before...

I will reinstall it now again, check if everything is ok as it was just a "moment" ago.

Did ubuntu updated itself ? I didnt clicked anything to approve this :D what the hell... :<

I will post soon

---

### Post by Bashing-om on 2015-07-14
jakub19; Hey ..

Try'n to hang in here with you .

> 
Did ubuntu updated itself ? I didnt clicked anything to approve this &#65532; what the hell... :<

Depends; what is set in the update-manager for updates ? Maybe 'security updates" is set and automatically the system will update the effected packages ?

If you are running proprietary ( non-ubuntu) graphics drivers , then each time the kernel is upgraded, the driver is broke, and must then be rebuilt against the presently installed kernel. 

[INDENT][INDENT]maybe, one cause ?
[/INDENT][/INDENT]

---

### Post by monkeybrain20122 on 2015-07-14
> **Bashing-om said:**
> 
If you are running proprietary ( non-ubuntu) graphics drivers , then each time the kernel is upgraded, the driver is broke, and must then be rebuilt against the presently installed kernel. 
[INDENT][INDENT]
[/INDENT]
[/INDENT]


No. This is not true unless you install it manually from Nvidia, but if you install from the repo or a ppa you don't have to rebuild after kernel update.  There might be a time you had to do that, I don't know, but it hasn't been the case since I started Ubuntu around 10.04. fglrx may be different.

---

### Post by jakub19 on 2015-07-14
```

enfu@enFu:~$ sudo lshw -C display
[sudo] password for enfu: 
Sorry, try again.
[sudo] password for enfu: 
  *-display               
       description: VGA compatible controller
       product: GF108M [GeForce GT 525M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
        resources: irq:54 memory:f0000000-f0ffffff memory:c0000000-cfffffff  memory:d0000000-d1ffffff ioport:3000(size=128) memory:f1000000-f107ffff
  *-display
       description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:51 memory:f1400000-f17fffff memory:e0000000-efffffff ioport:4000(size=64)
enfu@enFu:~$ nvidia-detector 
none
none
enfu@enFu:~$ nvidia-settings
The program 'nvidia-settings' is currently not installed. You can install it by typing:
sudo apt-get install nvidia-settings
You will have to enable the component called 'main'

```

BUT FINALLY I HAVE 1600x900 resolution ! :D

In "Software and Updates" I have unchecked every box and in set Automatic Updates to never.

Now I can't install through "sudo apt-get". How to turn it and only this option "ON" ?

Maybe after that I could install nvidia drivers and everything would be ok - because some update is downloading and installing itself in "background" ? :)

Also... my "mouse" is kinda glitching... For a bit of second is disapearing and apearing again... disturbing...

---

### Post by Bashing-om on 2015-07-14
jakub19; Welp;

You do have to enable the respective repositories ( main, universe, multiverse, and possibly - probably -  partner).
Then apt-get will have access to the repositories as selected.
> 
 and in set Automatic Updates to never.

Now it is on you to periodically check for updates and install those that are recommended . That is the manner I use.

As to the proprietary graphics driver, Checking with Nvidia, I see they recommend the 352 version.
[http://www.nvidia.com/download/driverResults.aspx/86390/en-us](http://www.nvidia.com/download/driverResults.aspx/86390/en-us)

All we can do is try a driver, see how it performs, and if not satisfied, try a different one. I do not know how far back we can go and still have support for that card . 352 - 346 -340 - 331 or such. Purging the installed driver prior to installing another.

[INDENT][INDENT]one size does not fit all
[INDENT][INDENT][INDENT]sometimes it is trial and error
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by jakub19 on 2015-07-16
nothing helps  ;(

---

### Post by Bashing-om on 2015-07-16
jakub19; Hey;

I do not accept:
> 
nothing helps ;(

Because I do know better. It is but a matter of isolating the problem, and making the correction.

To that end, we always look to the package management system and insure it is in a happy state.
So what are we now working with ?
post back:
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*
sudo apt update
sudo apt upgrade

``` and let's see what it will take to get the package manager in a happy state.

[INDENT][INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT][/INDENT]

---

### Post by jakub19 on 2015-07-20
```

enfu@enFu:~$ cat -n /etc/apt/sources.list
     1    # deb cdrom:[Ubuntu 14.04.2 LTS _Trusty Tahr_ - Release i386 (20150218.1)]/ trusty main restricted
     2    
     3    # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     4    # newer versions of the distribution.
     5    deb http://pl.archive.ubuntu.com/ubuntu/ trusty main restricted
     6    deb-src http://pl.archive.ubuntu.com/ubuntu/ trusty main restricted
     7    
     8    ## Major bug fix updates produced after the final release of the
     9    ## distribution.
    10    deb http://pl.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
    11    deb-src http://pl.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
    12    
    13    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14    ## team. Also, please note that software in universe WILL NOT receive any
    15    ## review or updates from the Ubuntu security team.
    16    deb http://pl.archive.ubuntu.com/ubuntu/ trusty universe
    17    deb-src http://pl.archive.ubuntu.com/ubuntu/ trusty universe
    18    deb http://pl.archive.ubuntu.com/ubuntu/ trusty-updates universe
    19    deb-src http://pl.archive.ubuntu.com/ubuntu/ trusty-updates universe
    20    
    21    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22    ## team, and may not be under a free licence. Please satisfy yourself as to 
    23    ## your rights to use the software. Also, please note that software in 
    24    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    25    ## security team.
    26    deb http://pl.archive.ubuntu.com/ubuntu/ trusty multiverse
    27    deb-src http://pl.archive.ubuntu.com/ubuntu/ trusty multiverse
    28    deb http://pl.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
    29    deb-src http://pl.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
    30    
    31    ## N.B. software from this repository may not have been tested as
    32    ## extensively as that contained in the main release, although it includes
    33    ## newer versions of some applications which may provide useful features.
    34    ## Also, please note that software in backports WILL NOT receive any review
    35    ## or updates from the Ubuntu security team.
    36    deb http://pl.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
    37    deb-src http://pl.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
    38    
    39    deb http://security.ubuntu.com/ubuntu trusty-security main restricted
    40    deb-src http://security.ubuntu.com/ubuntu trusty-security main restricted
    41    deb http://security.ubuntu.com/ubuntu trusty-security universe
    42    deb-src http://security.ubuntu.com/ubuntu trusty-security universe
    43    deb http://security.ubuntu.com/ubuntu trusty-security multiverse
    44    deb-src http://security.ubuntu.com/ubuntu trusty-security multiverse
    45    
    46    ## Uncomment the following two lines to add software from Canonical's
    47    ## 'partner' repository.
    48    ## This software is not part of Ubuntu, but is offered by Canonical and the
    49    ## respective vendors as a service to Ubuntu users.
    50    # deb http://archive.canonical.com/ubuntu trusty partner
    51    # deb-src http://archive.canonical.com/ubuntu trusty partner
    52    
    53    ## This software is not part of Ubuntu, but is offered by third-party
    54    ## developers who want to ship their latest software.
    55    deb http://extras.ubuntu.com/ubuntu trusty main
    56    deb-src http://extras.ubuntu.com/ubuntu trusty main

```

```

enfu@enFu:~$ tail -v -n +1 /etc/apt/sources.list.d/*
==> /etc/apt/sources.list.d/heroku.list <==
deb http://toolbelt.heroku.com/ubuntu ./

==> /etc/apt/sources.list.d/webupd8team-java-trusty.list <==
deb http://ppa.launchpad.net/webupd8team/java/ubuntu trusty main
# deb-src http://ppa.launchpad.net/webupd8team/java/ubuntu trusty main

==> /etc/apt/sources.list.d/webupd8team-java-trusty.list.save <==
deb http://ppa.launchpad.net/webupd8team/java/ubuntu trusty main
# deb-src http://ppa.launchpad.net/webupd8team/java/ubuntu trusty main

==> /etc/apt/sources.list.d/webupd8team-sublime-text-2-trusty.list <==
deb http://ppa.launchpad.net/webupd8team/sublime-text-2/ubuntu trusty main
# deb-src http://ppa.launchpad.net/webupd8team/sublime-text-2/ubuntu trusty main

```

```

enfu@enFu:~$ sudo apt update
[sudo] password for enfu: 
Ign.  http://pl.archive.ubuntu.com trusty InRelease
Ign.  http://pl.archive.ubuntu.com trusty-updates InRelease                    
Ign.  http://pl.archive.ubuntu.com trusty-backports InRelease                  
Stary http://pl.archive.ubuntu.com trusty Release.gpg                          
Ign.  http://extras.ubuntu.com trusty InRelease                                
Ign.  http://ppa.launchpad.net trusty InRelease                                
Ign.  http://security.ubuntu.com trusty-security InRelease                     
Stary http://pl.archive.ubuntu.com trusty-updates Release.gpg                  
Stary http://pl.archive.ubuntu.com trusty-backports Release.gpg                
Stary http://extras.ubuntu.com trusty Release.gpg                              
Ign.  http://ppa.launchpad.net trusty InRelease                                
Stary http://pl.archive.ubuntu.com trusty Release                              
Stary http://security.ubuntu.com trusty-security Release.gpg                   
Stary http://pl.archive.ubuntu.com trusty-updates Release                      
Stary http://pl.archive.ubuntu.com trusty-backports Release                    
Stary http://extras.ubuntu.com trusty Release                                  
Stary http://ppa.launchpad.net trusty Release.gpg                              
Stary http://security.ubuntu.com trusty-security Release                       
Stary http://ppa.launchpad.net trusty Release.gpg                              
Stary http://pl.archive.ubuntu.com trusty/main Sources     
Stary http://ppa.launchpad.net trusty Release                                  
Stary http://pl.archive.ubuntu.com trusty/restricted Sources                   
Stary http://pl.archive.ubuntu.com trusty/universe Sources                     
Stary http://pl.archive.ubuntu.com trusty/multiverse Sources                   
Stary http://ppa.launchpad.net trusty Release                                  
Stary http://pl.archive.ubuntu.com trusty/main i386 Packages                   
Stary http://pl.archive.ubuntu.com trusty/restricted i386 Packages             
Stary http://extras.ubuntu.com trusty/main Sources                             
Stary http://pl.archive.ubuntu.com trusty/universe i386 Packages               
Stary http://pl.archive.ubuntu.com trusty/multiverse i386 Packages             
Stary http://extras.ubuntu.com trusty/main i386 Packages                       
Stary http://pl.archive.ubuntu.com trusty/main Translation-pl                  
Stary http://security.ubuntu.com trusty-security/main Sources                  
Stary http://pl.archive.ubuntu.com trusty/main Translation-en                  
Stary http://ppa.launchpad.net trusty/main i386 Packages                       
Stary http://security.ubuntu.com trusty-security/restricted Sources            
Stary http://pl.archive.ubuntu.com trusty/multiverse Translation-pl            
Stary http://ppa.launchpad.net trusty/main Translation-en                      
Stary http://pl.archive.ubuntu.com trusty/multiverse Translation-en            
Stary http://security.ubuntu.com trusty-security/universe Sources              
Stary http://pl.archive.ubuntu.com trusty/restricted Translation-pl            
Stary http://ppa.launchpad.net trusty/main i386 Packages                       
Ign.  http://toolbelt.heroku.com ./ InRelease                                  
Stary http://security.ubuntu.com trusty-security/multiverse Sources            
Stary http://pl.archive.ubuntu.com trusty/restricted Translation-en            
Stary http://pl.archive.ubuntu.com trusty/universe Translation-pl              
Stary http://security.ubuntu.com trusty-security/main i386 Packages            
Stary http://pl.archive.ubuntu.com trusty/universe Translation-en              
Stary http://pl.archive.ubuntu.com trusty-updates/main Sources                 
Stary http://pl.archive.ubuntu.com trusty-updates/restricted Sources           
Stary http://security.ubuntu.com trusty-security/restricted i386 Packages      
Stary http://pl.archive.ubuntu.com trusty-updates/universe Sources             
Stary http://pl.archive.ubuntu.com trusty-updates/multiverse Sources           
Stary http://security.ubuntu.com trusty-security/universe i386 Packages        
Stary http://pl.archive.ubuntu.com trusty-updates/main i386 Packages           
Stary http://pl.archive.ubuntu.com trusty-updates/restricted i386 Packages     
Stary http://pl.archive.ubuntu.com trusty-updates/universe i386 Packages       
Stary http://security.ubuntu.com trusty-security/multiverse i386 Packages      
Stary http://pl.archive.ubuntu.com trusty-updates/multiverse i386 Packages     
Stary http://pl.archive.ubuntu.com trusty-updates/main Translation-en          
Stary http://security.ubuntu.com trusty-security/main Translation-en           
Stary http://security.ubuntu.com trusty-security/multiverse Translation-en     
Stary http://pl.archive.ubuntu.com trusty-updates/multiverse Translation-en    
Stary http://toolbelt.heroku.com ./ Release.gpg                                
Stary http://pl.archive.ubuntu.com trusty-updates/restricted Translation-en    
Stary http://pl.archive.ubuntu.com trusty-updates/universe Translation-en      
Stary http://security.ubuntu.com trusty-security/restricted Translation-en     
Stary http://pl.archive.ubuntu.com trusty-backports/main Sources               
Stary http://pl.archive.ubuntu.com trusty-backports/restricted Sources         
Stary http://pl.archive.ubuntu.com trusty-backports/universe Sources           
Stary http://security.ubuntu.com trusty-security/universe Translation-en       
Stary http://pl.archive.ubuntu.com trusty-backports/multiverse Sources         
Stary http://pl.archive.ubuntu.com trusty-backports/main i386 Packages         
Ign.  http://extras.ubuntu.com trusty/main Translation-pl_PL                   
Stary http://pl.archive.ubuntu.com trusty-backports/restricted i386 Packages   
Stary http://pl.archive.ubuntu.com trusty-backports/universe i386 Packages     
Ign.  http://extras.ubuntu.com trusty/main Translation-pl                      
Stary http://pl.archive.ubuntu.com trusty-backports/multiverse i386 Packages   
Stary http://pl.archive.ubuntu.com trusty-backports/main Translation-en        
Stary http://pl.archive.ubuntu.com trusty-backports/multiverse Translation-en  
Ign.  http://extras.ubuntu.com trusty/main Translation-en                      
Stary http://pl.archive.ubuntu.com trusty-backports/restricted Translation-en  
Stary http://pl.archive.ubuntu.com trusty-backports/universe Translation-en    
Stary http://toolbelt.heroku.com ./ Release                                   
Ign.  http://ppa.launchpad.net trusty/main Translation-pl_PL                   
Ign.  http://ppa.launchpad.net trusty/main Translation-pl                     
Ign.  http://ppa.launchpad.net trusty/main Translation-en                     
Ign.  http://pl.archive.ubuntu.com trusty/main Translation-pl_PL              
Ign.  http://pl.archive.ubuntu.com trusty/multiverse Translation-pl_PL        
Ign.  http://pl.archive.ubuntu.com trusty/restricted Translation-pl_PL        
Ign.  http://pl.archive.ubuntu.com trusty/universe Translation-pl_PL          
Stary http://toolbelt.heroku.com ./ Packages                                  
Ign.  http://toolbelt.heroku.com ./ Translation-pl_PL                          
Ign.  http://toolbelt.heroku.com ./ Translation-pl 
Ign.  http://toolbelt.heroku.com ./ Translation-en 
Czytanie list pakietów... Gotowe 

```

```

enfu@enFu:~$ sudo apt upgrade
[sudo] password for enfu: 
Czytanie list pakietów... Gotowe
Budowanie drzewa zale&#380;no&#347;ci       
Odczyt informacji o stanie... Gotowe
Obliczanie aktualizacji...Gotowe
Nast&#281;puj&#261;ce pakiety zosta&#322;y zainstalowane automatycznie i nie s&#261; ju&#380; wi&#281;cej wymagane:
  account-plugin-windows-live libgtkspell0 libupstart1 pidgin-data
Aby je usun&#261;&#263; nale&#380;y u&#380;y&#263; "apt-get autoremove".
0 aktualizowanych, 0 nowo instalowanych, 0 usuwanych i 0 nieaktualizowanych.

```

After installing ubuntu without updating system during installation process I have 1600x900 - no internet connection.
When I connect to WiFi and reboot - ubuntu changes to 1024x768 and I have this resolution problem or sth...

Is there any way to add 1600x900 option and force ubuntu to use it ?

H e l p :]

---

### Post by jakub19 on 2015-07-20
Is this okay ?

[http://unix.stackexchange.com/questions/120955/ubuntu-14-04-nvidia-proprietary-drivers-installation](http://unix.stackexchange.com/questions/120955/ubuntu-14-04-nvidia-proprietary-drivers-installation)

---

### Post by jakub19 on 2015-07-20
And now the sound is gone to...
Fixed but... Sound doesnt work on "built-in speakers" of my dell laptop.
When I connect "outside" speakers sound works -.- what the hell...

---

### Post by CitadelUniversal on 2015-07-20
What's your hardware specification and desktop/laptop model? Is your graphics card actually Nvidia or AMD? What's your processor is it Intel or AMD? Those details you haven't clearly stated yet, plus some of us need the logs in English and not some other Language...

---

### Post by jakub19 on 2015-07-20
laptop: DELL 17R N7110 - but it cannot be found on internet with my specs ... strange I know ... O.o

NVIDIA Corporation GF108M [GeForce GT 525M] (rev a1)
Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz

So one more time, from the begining, what to do ?
And for this repair process i should switch to english language so the logs will be in english, right ?

btw. fixed sound ;)

---

### Post by Bashing-om on 2015-07-20
jakub19; Well ....

> **jakub19 said:**
> Is this okay ?

[http://unix.stackexchange.com/questions/120955/ubuntu-14-04-nvidia-proprietary-drivers-installation](http://unix.stackexchange.com/questions/120955/ubuntu-14-04-nvidia-proprietary-drivers-installation)

Yes, no, depends !
Is your box optimus technology ?
Be aware that BumbleBee is depreciated in favor of nvidia-prime in later releases. So, in the referenced link option #2 might be the preferred way to go - IF this is optimus .
Installing the proper driver for you card may indeed resolve the resolution issues.

To see what the condition is:
```

lspci -vnn | grep -i VGA
sudo lshw -C display
dpkg -l | grep -i nvidia
cat /var/log/Xorg.0.log

```

----------------------------------------
With no internet connection, will be hard pressed to effect  a solution. Restoring internet connectivity will be the 1st priority.

[INDENT][INDENT]just what I think
[/INDENT][/INDENT]

---

### Post by jakub19 on 2015-07-20
lspci -vnn | grep -i VGA
```

enfu@enFu:~$ lspci -vnn | grep -i VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09) (prog-if 00 [VGA controller])
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF108M [GeForce GT 525M] [10de:0df5] (rev a1) (prog-if 00 [VGA controller])

```

sudo lshw -C display
```

enfu@enFu:~$ sudo lshw -C display
[sudo] password for enfu: 
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: GF108M [GeForce GT 525M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:f0000000-f0ffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:3000(size=128) memory:f1000000-f107ffff
  *-display UNCLAIMED
       description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:f1400000-f17fffff memory:e0000000-efffffff ioport:4000(size=64)

```


dpkg -l | grep -i nvidia
```

enfu@enFu:~$ dpkg -l | grep -i nvidia
enfu@enFu:~$

```
shows nothing...


cat /var/log/Xorg.0.log
```

enfu@enFu:~$ cat /var/log/Xorg.0.log
[  6298.868] 
X.Org X Server 1.16.0
Release Date: 2014-07-16
[  6298.868] X Protocol Version 11, Revision 0
[  6298.868] Build Operating System: Linux 3.2.0-70-generic i686 Ubuntu
[  6298.868] Current Operating System: Linux enFu 3.16.0-43-generic #58~14.04.1-Ubuntu SMP Mon Jun 22 10:21:00 UTC 2015 i686
[  6298.868] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.16.0-43-generic root=UUID=a61fcf5c-e4bb-46b9-bc82-50fdfef63108 ro quiet splash nomodeset vt.handoff=7
[  6298.868] Build Date: 12 February 2015  11:11:29PM
[  6298.868] xorg-server 2:1.16.0-1ubuntu1.2~trusty2 (For technical support please see http://www.ubuntu.com/support) 
[  6298.868] Current version of pixman: 0.30.2
[  6298.868]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[  6298.868] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[  6298.868] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Jul 20 21:47:35 2015
[  6298.868] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[  6298.869] (==) No Layout section.  Using the first Screen section.
[  6298.869] (==) No screen section available. Using defaults.
[  6298.869] (**) |-->Screen "Default Screen Section" (0)
[  6298.869] (**) |   |-->Monitor "<default monitor>"
[  6298.870] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[  6298.870] (==) Automatically adding devices
[  6298.870] (==) Automatically enabling devices
[  6298.870] (==) Automatically adding GPU devices
[  6298.870] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[  6298.870]     Entry deleted from font path.
[  6298.870] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[  6298.870]     Entry deleted from font path.
[  6298.870] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[  6298.870]     Entry deleted from font path.
[  6298.870] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[  6298.870]     Entry deleted from font path.
[  6298.870] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[  6298.870]     Entry deleted from font path.
[  6298.870] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[  6298.870] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[  6298.870] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[  6298.870] (II) Loader magic: 0xb7717660
[  6298.870] (II) Module ABI versions:
[  6298.870]     X.Org ANSI C Emulation: 0.4
[  6298.870]     X.Org Video Driver: 18.0
[  6298.870]     X.Org XInput driver : 21.0
[  6298.870]     X.Org Server Extension : 8.0
[  6298.873] (--) PCI:*(0:0:2:0) 8086:0116:1028:04c4 rev 9, Mem @ 0xf1400000/4194304, 0xe0000000/268435456, I/O @ 0x00004000/64
[  6298.873] (--) PCI: (0:1:0:0) 10de:0df5:1028:04c4 rev 161, Mem @ 0xf0000000/16777216, 0xc0000000/268435456, 0xd0000000/33554432, I/O @ 0x00003000/128, BIOS @ 0x????????/524288
[  6298.873] (II) LoadModule: "glx"
[  6298.873] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[  6298.875] (II) Module glx: vendor="X.Org Foundation"
[  6298.875]     compiled for 1.16.0, module version = 1.0.0
[  6298.875]     ABI class: X.Org Server Extension, version 8.0
[  6298.875] (==) AIGLX enabled
[  6298.875] (==) Matched intel as autoconfigured driver 0
[  6298.875] (==) Matched modesetting as autoconfigured driver 1
[  6298.875] (==) Matched fbdev as autoconfigured driver 2
[  6298.875] (==) Matched vesa as autoconfigured driver 3
[  6298.875] (==) Assigned the driver to the xf86ConfigLayout
[  6298.875] (II) LoadModule: "intel"
[  6298.876] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[  6298.876] (II) Module intel: vendor="X.Org Foundation"
[  6298.876]     compiled for 1.16.0, module version = 2.99.914
[  6298.876]     Module class: X.Org Video Driver
[  6298.876]     ABI class: X.Org Video Driver, version 18.0
[  6298.876] (II) LoadModule: "modesetting"
[  6298.877] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[  6298.877] (II) Module modesetting: vendor="X.Org Foundation"
[  6298.877]     compiled for 1.16.0, module version = 0.9.0
[  6298.877]     Module class: X.Org Video Driver
[  6298.877]     ABI class: X.Org Video Driver, version 18.0
[  6298.877] (II) LoadModule: "fbdev"
[  6298.877] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[  6298.877] (II) Module fbdev: vendor="X.Org Foundation"
[  6298.877]     compiled for 1.16.0, module version = 0.4.4
[  6298.877]     Module class: X.Org Video Driver
[  6298.877]     ABI class: X.Org Video Driver, version 18.0
[  6298.877] (II) LoadModule: "vesa"
[  6298.878] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[  6298.878] (II) Module vesa: vendor="X.Org Foundation"
[  6298.878]     compiled for 1.16.0, module version = 2.3.3
[  6298.878]     Module class: X.Org Video Driver
[  6298.878]     ABI class: X.Org Video Driver, version 18.0
[  6298.878] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
    i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
    915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
    Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
    GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[  6298.879] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[  6298.879] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[  6298.879] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[  6298.879] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[  6298.879] (II) FBDEV: driver for framebuffer: fbdev
[  6298.879] (II) VESA: driver for VESA chipsets: vesa
[  6298.879] (++) using VT number 7

[  6298.887] (EE) open /dev/dri/card0: No such file or directory
[  6298.887] (WW) Falling back to old probe method for modesetting
[  6298.887] (EE) open /dev/dri/card0: No such file or directory
[  6298.887] (II) Loading sub module "fbdevhw"
[  6298.887] (II) LoadModule: "fbdevhw"
[  6298.888] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[  6298.888] (II) Module fbdevhw: vendor="X.Org Foundation"
[  6298.888]     compiled for 1.16.0, module version = 0.0.2
[  6298.888]     ABI class: X.Org Video Driver, version 18.0
[  6298.888] (**) FBDEV(1): claimed PCI slot 0@0:2:0
[  6298.888] (II) FBDEV(1): using default device
[  6298.888] (WW) Falling back to old probe method for vesa
[  6298.888] (EE) Screen 0 deleted because of no matching config section.
[  6298.888] (II) UnloadModule: "modesetting"
[  6298.888] (II) FBDEV(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[  6298.888] (==) FBDEV(0): Depth 24, (==) framebuffer bpp 32
[  6298.888] (==) FBDEV(0): RGB weight 888
[  6298.888] (==) FBDEV(0): Default visual is TrueColor
[  6298.888] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[  6298.888] (II) FBDEV(0): hardware: VESA VGA (video memory: 3072kB)
[  6298.888] (II) FBDEV(0): checking modes against framebuffer device...
[  6298.888] (II) FBDEV(0): checking modes against monitor...
[  6298.888] (--) FBDEV(0): Virtual size is 1024x768 (pitch 1024)
[  6298.888] (**) FBDEV(0):  Built-in mode "current": 78.7 MHz, 59.9 kHz, 75.7 Hz
[  6298.888] (II) FBDEV(0): Modeline "current"x0.0   78.65  1024 1056 1184 1312  768 772 776 792 -hsync -vsync -csync (59.9 kHz b)
[  6298.888] (==) FBDEV(0): DPI set to (96, 96)
[  6298.889] (II) Loading sub module "fb"
[  6298.889] (II) LoadModule: "fb"
[  6298.889] (II) Loading /usr/lib/xorg/modules/libfb.so
[  6298.889] (II) Module fb: vendor="X.Org Foundation"
[  6298.889]     compiled for 1.16.0, module version = 1.0.0
[  6298.889]     ABI class: X.Org ANSI C Emulation, version 0.4
[  6298.889] (**) FBDEV(0): using shadow framebuffer
[  6298.889] (II) Loading sub module "shadow"
[  6298.889] (II) LoadModule: "shadow"
[  6298.889] (II) Loading /usr/lib/xorg/modules/libshadow.so
[  6298.890] (II) Module shadow: vendor="X.Org Foundation"
[  6298.890]     compiled for 1.16.0, module version = 1.1.0
[  6298.890]     ABI class: X.Org ANSI C Emulation, version 0.4
[  6298.890] (II) UnloadModule: "vesa"
[  6298.890] (II) Unloading vesa
[  6298.890] (==) Depth 24 pixmap format is 32 bpp
[  6298.890] (EE) FBDEV(0): FBIOBLANK: Invalid argument
[  6298.890] (==) FBDEV(0): Backing store enabled
[  6298.890] (==) FBDEV(0): DPMS enabled
[  6298.891] (==) RandR enabled
[  6298.891] (II) Found 2 VGA devices: arbiter wrapping enabled
[  6298.905] (II) AIGLX: Screen 0 is not DRI2 capable
[  6298.906] (EE) AIGLX: reverting to software rendering
[  6298.924] (II) AIGLX: Loaded and initialized swrast
[  6298.924] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[  6298.942] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[  6298.947] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[  6298.947] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  6298.947] (II) LoadModule: "evdev"
[  6298.947] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  6298.948] (II) Module evdev: vendor="X.Org Foundation"
[  6298.948]     compiled for 1.16.0, module version = 2.9.0
[  6298.948]     Module class: X.Org XInput Driver
[  6298.948]     ABI class: X.Org XInput driver, version 21.0
[  6298.948] (II) Using input driver 'evdev' for 'Power Button'
[  6298.948] (**) Power Button: always reports core events
[  6298.948] (**) evdev: Power Button: Device: "/dev/input/event3"
[  6298.948] (--) evdev: Power Button: Vendor 0 Product 0x1
[  6298.948] (--) evdev: Power Button: Found keys
[  6298.948] (II) evdev: Power Button: Configuring as keyboard
[  6298.948] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[  6298.948] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[  6298.948] (**) Option "xkb_rules" "evdev"
[  6298.948] (**) Option "xkb_model" "pc105"
[  6298.948] (**) Option "xkb_layout" "pl"
[  6298.952] (II) XKB: reuse xkmfile /var/lib/xkb/server-61818C6B46DD4F01AE1F641F27B555591612208F.xkm
[  6298.953] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[  6298.953] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  6298.953] (II) Using input driver 'evdev' for 'Power Button'
[  6298.953] (**) Power Button: always reports core events
[  6298.953] (**) evdev: Power Button: Device: "/dev/input/event0"
[  6298.953] (--) evdev: Power Button: Vendor 0 Product 0x1
[  6298.954] (--) evdev: Power Button: Found keys
[  6298.954] (II) evdev: Power Button: Configuring as keyboard
[  6298.954] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[  6298.954] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[  6298.954] (**) Option "xkb_rules" "evdev"
[  6298.954] (**) Option "xkb_model" "pc105"
[  6298.954] (**) Option "xkb_layout" "pl"
[  6298.954] (II) config/udev: Adding input device Lid Switch (/dev/input/event2)
[  6298.954] (II) No input driver specified, ignoring this device.
[  6298.954] (II) This device may have been added with another device file.
[  6298.955] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[  6298.955] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[  6298.955] (II) Using input driver 'evdev' for 'Sleep Button'
[  6298.955] (**) Sleep Button: always reports core events
[  6298.955] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[  6298.955] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[  6298.955] (--) evdev: Sleep Button: Found keys
[  6298.955] (II) evdev: Sleep Button: Configuring as keyboard
[  6298.955] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1/event1"
[  6298.955] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 8)
[  6298.955] (**) Option "xkb_rules" "evdev"
[  6298.955] (**) Option "xkb_model" "pc105"
[  6298.955] (**) Option "xkb_layout" "pl"
[  6298.956] (II) config/udev: Adding input device Laptop_Integrated_Webcam_HD (/dev/input/event11)
[  6298.956] (**) Laptop_Integrated_Webcam_HD: Applying InputClass "evdev keyboard catchall"
[  6298.956] (II) Using input driver 'evdev' for 'Laptop_Integrated_Webcam_HD'
[  6298.956] (**) Laptop_Integrated_Webcam_HD: always reports core events
[  6298.956] (**) evdev: Laptop_Integrated_Webcam_HD: Device: "/dev/input/event11"
[  6298.956] (--) evdev: Laptop_Integrated_Webcam_HD: Vendor 0x1bcf Product 0x2881
[  6298.956] (--) evdev: Laptop_Integrated_Webcam_HD: Found keys
[  6298.956] (II) evdev: Laptop_Integrated_Webcam_HD: Configuring as keyboard
[  6298.956] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/input/input12/event11"
[  6298.956] (II) XINPUT: Adding extended input device "Laptop_Integrated_Webcam_HD" (type: KEYBOARD, id 9)
[  6298.956] (**) Option "xkb_rules" "evdev"
[  6298.956] (**) Option "xkb_model" "pc105"
[  6298.956] (**) Option "xkb_layout" "pl"
[  6298.957] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event9)
[  6298.957] (II) No input driver specified, ignoring this device.
[  6298.957] (II) This device may have been added with another device file.
[  6298.957] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event10)
[  6298.957] (II) No input driver specified, ignoring this device.
[  6298.957] (II) This device may have been added with another device file.
[  6298.958] (II) config/udev: Adding input device Logitech Unifying Device. Wireless PID:101a (/dev/input/event5)
[  6298.958] (**) Logitech Unifying Device. Wireless PID:101a: Applying InputClass "evdev pointer catchall"
[  6298.958] (II) Using input driver 'evdev' for 'Logitech Unifying Device. Wireless PID:101a'
[  6298.958] (**) Logitech Unifying Device. Wireless PID:101a: always reports core events
[  6298.958] (**) evdev: Logitech Unifying Device. Wireless PID:101a: Device: "/dev/input/event5"
[  6298.958] (--) evdev: Logitech Unifying Device. Wireless PID:101a: Vendor 0x46d Product 0xc52b
[  6298.958] (--) evdev: Logitech Unifying Device. Wireless PID:101a: Found 20 mouse buttons
[  6298.958] (--) evdev: Logitech Unifying Device. Wireless PID:101a: Found scroll wheel(s)
[  6298.958] (--) evdev: Logitech Unifying Device. Wireless PID:101a: Found relative axes
[  6298.958] (--) evdev: Logitech Unifying Device. Wireless PID:101a: Found x and y relative axes
[  6298.958] (II) evdev: Logitech Unifying Device. Wireless PID:101a: Configuring as mouse
[  6298.958] (II) evdev: Logitech Unifying Device. Wireless PID:101a: Adding scrollwheel support
[  6298.958] (**) evdev: Logitech Unifying Device. Wireless PID:101a: YAxisMapping: buttons 4 and 5
[  6298.958] (**) evdev: Logitech Unifying Device. Wireless PID:101a: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  6298.958] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0/usb3/3-2/3-2:1.2/0003:046D:C52B.0003/0003:046D:C52B.0004/input/input7/event5"
[  6298.958] (II) XINPUT: Adding extended input device "Logitech Unifying Device. Wireless PID:101a" (type: MOUSE, id 10)
[  6298.958] (II) evdev: Logitech Unifying Device. Wireless PID:101a: initialized for relative axes.
[  6298.958] (**) Logitech Unifying Device. Wireless PID:101a: (accel) keeping acceleration scheme 1
[  6298.958] (**) Logitech Unifying Device. Wireless PID:101a: (accel) acceleration profile 0
[  6298.958] (**) Logitech Unifying Device. Wireless PID:101a: (accel) acceleration factor: 2.000
[  6298.958] (**) Logitech Unifying Device. Wireless PID:101a: (accel) acceleration threshold: 4
[  6298.959] (II) config/udev: Adding input device Logitech Unifying Device. Wireless PID:101a (/dev/input/mouse0)
[  6298.959] (II) No input driver specified, ignoring this device.
[  6298.959] (II) This device may have been added with another device file.
[  6298.959] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[  6298.959] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[  6298.959] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[  6298.959] (**) AT Translated Set 2 keyboard: always reports core events
[  6298.959] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[  6298.959] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[  6298.959] (--) evdev: AT Translated Set 2 keyboard: Found keys
[  6298.959] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[  6298.959] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[  6298.959] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 11)
[  6298.959] (**) Option "xkb_rules" "evdev"
[  6298.959] (**) Option "xkb_model" "pc105"
[  6298.959] (**) Option "xkb_layout" "pl"
[  6298.960] (II) config/udev: Adding input device AlpsPS/2 ALPS DualPoint TouchPad (/dev/input/event7)
[  6298.960] (**) AlpsPS/2 ALPS DualPoint TouchPad: Applying InputClass "evdev touchpad catchall"
[  6298.960] (**) AlpsPS/2 ALPS DualPoint TouchPad: Applying InputClass "touchpad catchall"
[  6298.960] (**) AlpsPS/2 ALPS DualPoint TouchPad: Applying InputClass "Default clickpad buttons"
[  6298.960] (II) LoadModule: "synaptics"
[  6298.961] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[  6298.961] (II) Module synaptics: vendor="X.Org Foundation"
[  6298.961]     compiled for 1.16.0, module version = 1.8.99
[  6298.961]     Module class: X.Org XInput Driver
[  6298.961]     ABI class: X.Org XInput driver, version 21.0
[  6298.961] (II) Using input driver 'synaptics' for 'AlpsPS/2 ALPS DualPoint TouchPad'
[  6298.961] (**) AlpsPS/2 ALPS DualPoint TouchPad: always reports core events
[  6298.961] (**) Option "Device" "/dev/input/event7"
[  6299.020] (II) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: ignoring touch events for semi-multitouch device
[  6299.020] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: x-axis range 0 - 2000 (res 0)
[  6299.020] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: y-axis range 0 - 1400 (res 0)
[  6299.020] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: pressure range 0 - 127
[  6299.020] (II) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: device does not report finger width.
[  6299.020] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: buttons: left right middle double triple
[  6299.020] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: Vendor 0x2 Product 0x8
[  6299.020] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: invalid finger width range.  defaulting to 0 - 15
[  6299.020] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: touchpad found
[  6299.020] (**) AlpsPS/2 ALPS DualPoint TouchPad: always reports core events
[  6299.076] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input6/event7"
[  6299.076] (II) XINPUT: Adding extended input device "AlpsPS/2 ALPS DualPoint TouchPad" (type: TOUCHPAD, id 12)
[  6299.076] (**) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[  6299.076] (**) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: (accel) MaxSpeed is now 1.75
[  6299.076] (**) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: (accel) AccelFactor is now 0.082
[  6299.076] (**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) keeping acceleration scheme 1
[  6299.077] (**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) acceleration profile 1
[  6299.077] (**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) acceleration factor: 2.000
[  6299.077] (**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) acceleration threshold: 4
[  6299.077] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: touchpad found
[  6299.078] (II) config/udev: Adding input device AlpsPS/2 ALPS DualPoint TouchPad (/dev/input/mouse2)
[  6299.078] (**) AlpsPS/2 ALPS DualPoint TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[  6299.078] (II) config/udev: Adding input device DualPoint Stick (/dev/input/event6)
[  6299.078] (**) DualPoint Stick: Applying InputClass "evdev pointer catchall"
[  6299.078] (**) DualPoint Stick: Applying InputClass "trackpoint catchall"
[  6299.079] (II) Using input driver 'evdev' for 'DualPoint Stick'
[  6299.079] (**) DualPoint Stick: always reports core events
[  6299.079] (**) evdev: DualPoint Stick: Device: "/dev/input/event6"
[  6299.079] (--) evdev: DualPoint Stick: Vendor 0x2 Product 0x8
[  6299.079] (--) evdev: DualPoint Stick: Found 3 mouse buttons
[  6299.079] (--) evdev: DualPoint Stick: Found relative axes
[  6299.079] (--) evdev: DualPoint Stick: Found x and y relative axes
[  6299.079] (II) evdev: DualPoint Stick: Configuring as mouse
[  6299.079] (**) Option "Emulate3Buttons" "true"
[  6299.079] (**) Option "EmulateWheel" "true"
[  6299.079] (**) Option "EmulateWheelButton" "2"
[  6299.079] (**) Option "YAxisMapping" "4 5"
[  6299.079] (**) evdev: DualPoint Stick: YAxisMapping: buttons 4 and 5
[  6299.079] (**) Option "XAxisMapping" "6 7"
[  6299.079] (**) evdev: DualPoint Stick: XAxisMapping: buttons 6 and 7
[  6299.079] (**) evdev: DualPoint Stick: EmulateWheelButton: 2, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  6299.079] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input8/event6"
[  6299.079] (II) XINPUT: Adding extended input device "DualPoint Stick" (type: MOUSE, id 13)
[  6299.079] (II) evdev: DualPoint Stick: initialized for relative axes.
[  6299.080] (**) DualPoint Stick: (accel) keeping acceleration scheme 1
[  6299.080] (**) DualPoint Stick: (accel) acceleration profile 0
[  6299.080] (**) DualPoint Stick: (accel) acceleration factor: 2.000
[  6299.080] (**) DualPoint Stick: (accel) acceleration threshold: 4
[  6299.081] (II) config/udev: Adding input device DualPoint Stick (/dev/input/mouse1)
[  6299.081] (II) No input driver specified, ignoring this device.
[  6299.081] (II) This device may have been added with another device file.
[  6299.085] (II) config/udev: Adding input device Dell WMI hotkeys (/dev/input/event8)
[  6299.086] (**) Dell WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[  6299.086] (II) Using input driver 'evdev' for 'Dell WMI hotkeys'
[  6299.086] (**) Dell WMI hotkeys: always reports core events
[  6299.086] (**) evdev: Dell WMI hotkeys: Device: "/dev/input/event8"
[  6299.086] (--) evdev: Dell WMI hotkeys: Vendor 0 Product 0
[  6299.086] (--) evdev: Dell WMI hotkeys: Found keys
[  6299.086] (II) evdev: Dell WMI hotkeys: Configuring as keyboard
[  6299.086] (**) Option "config_info" "udev:/sys/devices/virtual/input/input9/event8"
[  6299.086] (II) XINPUT: Adding extended input device "Dell WMI hotkeys" (type: KEYBOARD, id 14)
[  6299.086] (**) Option "xkb_rules" "evdev"
[  6299.086] (**) Option "xkb_model" "pc105"
[  6299.086] (**) Option "xkb_layout" "pl"
[  6299.095] (EE) FBDEV(0): FBIOBLANK: Invalid argument
[  6304.472] (II) XKB: reuse xkmfile /var/lib/xkb/server-61818C6B46DD4F01AE1F641F27B555591612208F.xkm
[  6304.494] (II) XKB: reuse xkmfile /var/lib/xkb/server-0B9079E8447E201420CF6E60BCB5117BA454ED79.xkm
[  6304.508] (II) XKB: reuse xkmfile /var/lib/xkb/server-0B9079E8447E201420CF6E60BCB5117BA454ED79.xkm
[  6305.332] (II) XKB: reuse xkmfile /var/lib/xkb/server-925DE5C8A456DF6CC6764491CA73014235E322FE.xkm

```

Now what ? :)

---

### Post by Bashing-om on 2015-07-20
jakub19; OK;

Now we are getting somewhere.
We know:
this is a hybrid graphics system, Intel/Nividia
There is no driver installed for Nvidia, we need to install the proper driver, per Nvidia the 352.21 version ( that might be too cutting edge ?)

So now, how do we install the nvidia driver is the question. That is dependent on what release of ubuntu you have installed. That driver is availabale direct from our software repository IF you are running 15.04. Else - as you are running 14.04 -we get the driver from our trusted PPA.
```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
sudo apt-get purge nvidia*
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install nvidia-346

```

The driver is now installed ->

Reboot for the change to take effect. Now from the GUI 'nvidia-settings' Is "nvidia-prime". From here one controls the graphics sets. And yes, you have some homework to do to learn how to control your graphics sets .

And we have the driver installed.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by jakub19 on 2015-07-21
no xorg.conf file

ls /etc/X11/
```

enfu@enFu:~$ ls -l /etc/X11
total 76
drwxr-xr-x 2 root root  4096 lut 18 20:59 app-defaults
drwxr-xr-x 2 root root  4096 lut 18 20:58 cursors
-rw-r--r-- 1 root root    18 lut 18 20:59 default-display-manager
drwxr-xr-x 4 root root  4096 lut 18 20:53 fonts
-rw-r--r-- 1 root root 17394 gru  3  2009 rgb.txt
lrwxrwxrwx 1 root root    13 lip 18 11:32 X -> /usr/bin/Xorg
drwxr-xr-x 2 root root  4096 lut 18 20:59 xinit
drwxr-xr-x 2 root root  4096 sty 15  2014 xkb
-rwxr-xr-x 1 root root   709 kwi  1  2010 Xreset
drwxr-xr-x 2 root root  4096 lut 18 20:55 Xreset.d
drwxr-xr-x 2 root root  4096 lut 18 20:55 Xresources
-rwxr-xr-x 1 root root  3730 pa&#378;  8  2014 Xsession
drwxr-xr-x 2 root root  4096 lip 19 11:12 Xsession.d
-rw-r--r-- 1 root root   265 lip  1  2008 Xsession.options
drwxr-xr-x 2 root root  4096 lut 18 20:59 xsm
-rw-r--r-- 1 root root   601 lut 18 20:55 Xwrapper.config

```

Should I procced? :D

---

### Post by Bashing-om on 2015-07-21
jakub19; Hey ;

Not surprising there is no xorg.conf file; as looks like the Nvidia driver has never been installed.

Continue on, sir.

[INDENT][INDENT]small things however, can mean a lot
[/INDENT][/INDENT]

---

### Post by CitadelUniversal on 2015-07-21
Have you used the nvidia-xconfig command in the terminal? if you haven't then do so and reboot - the nvidia-xconfig will automatically generate a xorg.conf file....

Edit: Plus see [http://askubuntu.com/questions/132112/how-to-install-nvidia-geforce-gt525m-driver-on-ubuntu12-04](http://askubuntu.com/questions/132112/how-to-install-nvidia-geforce-gt525m-driver-on-ubuntu12-04)  - it may or may not help....

---

### Post by jakub19 on 2015-07-23
```

enfu@enFu:~$ sudo nvidia-xconfig
[sudo] password for enfu: 
sudo: nvidia-xconfig: command not found

```

Trying to install drivers, 1st, Bashin method... 16:33 23.07.2015

---

### Post by CitadelUniversal on 2015-07-23
Ok, do the following commands:

```
 sudo apt-get install nvidia-346 
```
```
 sudo nvidia-xconfig 
```

If using the Ubuntu v15.04 the nvidia drivers is at nvidia-346 if using lower versions like 14.04 it'll be nvidia-331 this should install a bunch of software's linked to the nvidia driver_**including**_ the nvidia-xconfig - this should work as nvidia-346 installs everything for me automatically....

Edit: If for some reason it doesn't work use this code ```
 lspci | grep VGA 
``` we need to know if your graphics card is Nvidia....

---

### Post by CitadelUniversal on 2015-07-23
I've just read the #44 and it looks like you've already posted the lspci | grep VGA command output, can you enter the UEFI/BIOS motherboard at the boot it should be the logo of the manufacturer and in mine it was under the Integrated Peripherals and see if you can turn off the intel graphics card and use the nvidia graphics card - if successful it should be using the nvidia and then it should be possible to use the nvidia drivers.... Also if not successful go back to the bios and re-change the intel graphics card and turn it back on - you should be able to enter it via F1 or one of the Function keys but if using an old system then it could be just the "delete" button which should enter the bios setting....

---

### Post by jakub19 on 2015-07-23
About
[http://askubuntu.com/questions/132112/how-to-install-nvidia-geforce-gt525m-driver-on-ubuntu12-04](http://askubuntu.com/questions/132112/how-to-install-nvidia-geforce-gt525m-driver-on-ubuntu12-04)

Stopped at
```

enfu@enFu:~$ sudo apt-get install xserver-xorg-video-intel
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 xserver-xorg-video-intel : Depends: xorg-video-abi-15
                            Depends: xserver-xorg-core (>= 2:1.14.99.902)
E: Unable to correct problems, you have held broken packages.

```

Now I will try to do this thing in UEFI/BIOS ;)

---

### Post by jakub19 on 2015-07-23
I didnt find anything where I could disable integrated graphics...

[ATTACH=CONFIG]263335[/ATTACH]


Now what... :/

---

### Post by Bashing-om on 2015-07-23
jakub19; UnGood;

This:
> 
The following packages have unmet dependencies:
 xserver-xorg-video-intel : Depends: xorg-video-abi-15
                            Depends: xserver-xorg-core (>= 2:1.14.99.902)
E: Unable to correct problems, you have held broken packages.

we need to address and get it fixed !

So what have we ? Post back the outputs of terminal commands :
```

dpkg -l xserver-xorg-core
dpkg -l xserver-xorg

```
And we proceed to see what it will take to

[INDENT][INDENT][INDENT]satisfy the package manager
[/INDENT][/INDENT][/INDENT]

---

### Post by CitadelUniversal on 2015-07-24
I've found this while searching and so far no-one had seemed to have suggested it so here you go [http://askubuntu.com/questions/140246/how-do-i-resolve-unmet-dependencies-after-adding-a-ppa](http://askubuntu.com/questions/140246/how-do-i-resolve-unmet-dependencies-after-adding-a-ppa)  - go down to the 2nd thread on that page the one which has over 291 thanks, and follow that persons instructions and report back on whether or not it worked.... It should at least allow you to go further, hopefully.

---

