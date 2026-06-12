---
title: "I can't login(Ubuntu 16.04)"
date: 2017-11-10
forum: General Help
---

### Post by abhigyann on 2017-11-10
I tried installing amd driver in one of the lines it said do this change on Grub file
Edit /etc/default/grub as root and modify GRUB_CMDLINE_LINUX_DEFAULT in order to add "amdgpu.vm_fragment_size=9" (without the quotes). The line may look something like this after the change: 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash amdgpu.vm_fragment_size=9" 
I figured that was the problem so I went to advanced options for Ubuntu and edited Grub file and removed that line still nothing happens

[https://m.imgur.com/G4tTzeD](https://m.imgur.com/G4tTzeD) 

This isn't my laptops picture 
but I get similar last message 
starting show Plymouth boot screen
Update:I updated the Grub by going to advanced options root and update-Grub now I can go to my login screen; I enter my password then it goes back to Plymouth boot screen and then back to login screen 
I can't even enter by using guest session

---

### Post by ajgreeny on 2017-11-11
We need to know a lot more about your OS version and your hardware before we can help you any more.

Since Ubuntu 16.04 there have been big problems with the AMD proprietary driver, and it is difficult to know what you have done from what you've said so far.

---

### Post by abhigyann on 2017-11-11
Ubuntu 16.04 lts xenial xerus
It's a HP Probook 450G3

[http://laptopmedia.com/review/hp-probook-450-g3-455-g3-review-what-a-budget-business-notebook-should-look-like/#gpu-8211-amd-radeon-r7-m340-2gb-ddr3](http://laptopmedia.com/review/hp-probook-450-g3-455-g3-review-what-a-budget-business-notebook-should-look-like/#gpu-8211-amd-radeon-r7-m340-2gb-ddr3)

---

### Post by Bashing-om on 2017-11-11
abhigyann; Humm ...

What results when you employ the grub boot parameter " radeon.modeset=0 " ?

Assuming here that you indeed do have an AMD card .

If we can get booted, then we see what else we can find out .

[INDENT][INDENT]got to be a reason
[/INDENT][/INDENT]

---

### Post by abhigyann on 2017-11-11
I am very new to Linux so some straight instructions would be the really helpful
I am guessing you were asking for this 
[IMG]https://imgur.com/gallery/itsHK[/IMG]https://imgur.com/gallery/itsHK

---

### Post by Bashing-om on 2017-11-11
abhigyann; Naw ,,,

Boot to the grub boot menu :
'e' key for edit mode -> boot parameters screen; and arrow down to the line starting with linux and over to quiet splash"
replace these terms with  radeon.modeset=0 .
key combo ctl+x to continue the boot process.

a one time boot thing - 
What results ?

[INDENT][INDENT]gotta be a way
[/INDENT][/INDENT]

---

### Post by abhigyann on 2017-11-11
Replace "quiet splash $vt_handoff" with "radeon.modeset=0"?

---

### Post by Bashing-om on 2017-11-11
abhigyann; Sure ,, 

try replacing all .. (16.04 == systemnd).
though replacing only quiet splash should be sufficient .

What a way to go

---

### Post by abhigyann on 2017-11-11
Still can't login after replacing quiet splash $vt_handoff with radeon.modeset=0 now the screen that comes after logging in went from aligned to randomly placed(it used to come in an aligned format before) on the screen but back to login page

---

### Post by Bashing-om on 2017-11-11
abhigyann; Whewwww ...

Let's boot up a liveUSB and from there take a look at what X is up to.
in the live mode ( try ubuntu ) ctl+x+t to gain a terminal.
execute and post back:
```

sudo parted -l

```
so I know where the root partition is located.

We then mount that partition and take a look at the log file.

[INDENT][INDENT]try and make sense of this mess
[/INDENT][/INDENT]

---

### Post by abhigyann on 2017-11-11
Umm do I just insert the live USB and restart cause I tried that and  I didn't get anything new on my Grub loader with the USB I did try to login with the USB inserted and now the it's the same thing login screen then that starting show plymouth boot screen(but it's back to ordered now) I need more directions on what you want me to do. While downloading I just made a bootable USB and restarted my laptop with it inserted it was pretty straight forward.
Ps:I can enter my ID through ctrl + alt+f1-6
And the order thing was probably because of radeon.modeset

---

### Post by Bashing-om on 2017-11-11
abhigyann; Well !

If you can log into the system ( crl+alt+F2) at the login screen of the install .. so much the better.

Log into the system here and execute:
```

cat /var/log/Xorg.0.log | nc termbin.com 9999

```
where the result is a URL back on terminal. Pass this link back here.
The action is to copy the log file to a pastebin site so we can view that file . There is no sensitive info in this file .

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by abhigyann on 2017-11-11
[http://termbin.com/7u1x](http://termbin.com/7u1x)

---

### Post by Bashing-om on 2017-11-11
abhigyann; Yuk !

> 
Kernel command line: -> recovery nomodeset


Skews the results . We need to boot the system without resorting to these expedients .
How have you set the boot parameter 'nomodeset' ? - as we need to remove it .

hybrid graphics and I have little experience with the AMD in this environment .

[INDENT][INDENT]a work in progress
[/INDENT][/INDENT]

---

### Post by abhigyann on 2017-11-11
I have no idea what nomodeset is so I am pretty sure I wouldn't have set it I don't care about those amd drivers at the moment  I thought downloading them would help my video games fps. Please give me directions to what I am supposed to do

---

### Post by Bashing-om on 2017-11-11
abhigyann; Try'n to

> 
 Please give me directions to what I am supposed to do

find out what you have done so we can undo it :)

If you reboot the machine, at the login screen key combo ctl+alt+F2 results in what ?

If you can login here to this interface .. show now anew:
```

lspci -k|grep -iEA5 'vga|3d' 
cat /etc/default/grub | nc termbin.com 9999
cat /var/log/Xorg.0.log | nc termbin.com 9999

```

what we are working with, what might be altered in the boot process, and what X thinks .

[INDENT]clean up and install ??[/INDENT]

---

### Post by abhigyann on 2017-11-11
[https://imgur.com/gallery/I6cfR](https://imgur.com/gallery/I6cfR)
For some reason | nc termbin.com isn't working I mean i did it 2posts ago anyways I have uploaded the Img for vga|3d one and  and did cat on my terminal for etc/default/grub as I said in my first post initially I had added a few lines in it given by amd but I have removed them and as for undoing things I might have done I have gone to advanced options for Ubuntu and I've updated Grub,  checked all file systems, used clean(to create free space), enable networking it said some. Config  file was missing I restarted to do the things in your previous post and then I thought I should look into enable networking then suddenly this came [https://imgur.com/gallery/ReYXo](https://imgur.com/gallery/ReYXo) (I am guessing I might have clicked update Grub)  but now on clicking enable networking it says  trying to start network manager... Then nothing happens
Edit:I have restarted my pc now the enable networking went back to grep: etc/resolved. Conf : no such file or directory I am guessing this is why termbin.com isn't working on ctrl+alt+f7 it's showing that I am connected to my wifi

---

### Post by abhigyann on 2017-11-13
[http://termbin.com/nuzq](http://termbin.com/nuzq) for etc/default/grub
[http://termbin.com/e1n9](http://termbin.com/e1n9) for xorg log
I used my live USB and booted in and this started working
I tried sudo apt update and got this at the end 
[https://imgur.com/gallery/v2q3T](https://imgur.com/gallery/v2q3T) it says skipping acquiring of a few packages never got that one before

---

### Post by Bashing-om on 2017-11-13
abhigyann; Ho Kay :)

I am a bit confused -

At the login screen of the installed system key combo ctl+alt+F2 yields a terminal where you can log into the system. yes or no ?

If yes - and you can log in - then we continue: 
fix the machine architecture ;
fix the graphic's driver

as we have from the log file:
> 
48.151] (EE) AIGLX: reverting to software rendering
[    48.158] (EE) AIGLX error: amdgpu does not export required DRI extension
[    48.159] (EE) GLX: could not load software renderer
[    48.159] (II) GLX: no usable GL providers found for screen 0
[    48.159] (II) modeset(0): Damage tracking initialized


so we know we have to determine the hardware and match a driver .

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by abhigyann on 2017-11-13
> **Bashing-om said:**
> 

If yes - and you can log in - then we continue: 
fix the machine architecture ;
fix the graphic's driver

 I can login but how do I fix the drivers as I said I am pretty new to Linux I'll need codes for those operations

---

### Post by Bashing-om on 2017-11-13
abhigyann; Great .

On to fixing.

Post back:
```

dpkg --print-architecture
lspci -k|grep -iEA5 'vga|3d'

```

Once we know the hardware we can then install the appropriate driver .

[INDENT][INDENT]we can do that [/INDENT][/INDENT]

---

### Post by abhigyann on 2017-11-14
Amd64 came from the first one and from the second one I got this :
VGA compatible controller :Inter corporation Sky Lake Integrated Graphics (Rev 07)
DeviceName:Onboard IGD
Subsytem:Hewlett-Packard Company skylake integrated graphics
Kernel driver in use:i915
Kerner model:i915
USB controller :Intel corporations sunrise point-of-sale USB 3.0 xHCI controller (Rev 21)

---

### Post by Bashing-om on 2017-11-14
abhigyann; Huh ?

That lspci output shows ONLY a Intel graphic's set . At this time I do not see AMD graphics as  any part in the picture.
" Sky Lake Integrated Graphics " is well supported in release 16.04; maybe all we have to do is clean up and re-install the sky lake driver ??

Let's take another look for any AMD hardware:
```

sudo apt update
sudo apt install inxi
inxi -GCS
sudo apt full-upgrade

```
inxi is a small tool with a lot of uses !

And I still want to remove that architecture doubt - that there is an invalid ID present.
show  the outputs of update/upgrade and verify what architectures are set on the system:
```

apt-config dump | grep Architecture

```

[INDENT][INDENT]garbage in is
[INDENT][INDENT][INDENT]garbage out
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by abhigyann on 2017-11-14
It isn't updating some applications and says temporary failure resolving 'app link'
I couldn't download inxi cause  it says temporary failure resolving 'in.archive.ubuntu.com' and at the end tells me to update or try - - fix-missing
I've uploaded the images of the above given errors and the result of architecture config
[https://imgur.com/gallery/W7FTF](https://imgur.com/gallery/W7FTF)

---

### Post by Bashing-om on 2017-11-14
abhigyann; Ouch .

Thar suggest that there is no internet connection.

How are you booting up ?

confirm:
what results:
```

ping -c3 8.8.8.8
ping -c3 ubuntu.com

```

should be as my results:
> 
sysop@x1604:~$ ping -c3 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=58 time=28.0 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=58 time=28.7 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=58 time=30.5 ms

--- 8.8.8.8 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 28.097/29.158/30.585/1.057 ms


sysop@x1604:~$ ping -c3 ubuntu.com
PING ubuntu.com (91.189.94.40) 56(84) bytes of data.
64 bytes from ovinnik.canonical.com (91.189.94.40): icmp_seq=1 ttl=53 time=120 ms
64 bytes from ovinnik.canonical.com (91.189.94.40): icmp_seq=2 ttl=53 time=121 ms
64 bytes from ovinnik.canonical.com (91.189.94.40): icmp_seq=3 ttl=53 time=127 ms

--- ubuntu.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2000ms
rtt min/avg/max/mdev = 120.805/123.322/127.965/3.311 ms
sysop@x1604:~$ 


[INDENT][INDENT]we got to be able to talk to Mother
[/INDENT][/INDENT]

---

### Post by abhigyann on 2017-11-14
I got the problem my isp is having some trouble at his end I'll run those codes as soon as I get my internet back up I am using my phone to write these replies :-P

---

### Post by Bashing-om on 2017-11-14
K

---

### Post by abhigyann on 2017-11-15
[http://paste.ubuntu.com/25965365/](http://paste.ubuntu.com/25965365/) inxi 
[http://paste.ubuntu.com/25965405/](http://paste.ubuntu.com/25965405/) architecture
And I did the full upgrade
[http://paste.ubuntu.com/25965423/](http://paste.ubuntu.com/25965423/) as you wanted to see the partitions before

---

### Post by Bashing-om on 2017-11-15
abhigyann;

clean up the Architectures:
```

sudo dpkg --remove-architecture i38

```

as this is invalid.

still .. do not see AMD; the output of inxi I had expected to be similar to my output :
```

sysop@x1604:~$ inxi -GCS
System:    Host: x1604 Kernel: 4.4.0-98-generic x86_64 (64 bit)
           Desktop: Xfce 4.12.3 Distro: Ubuntu 16.04 xenial
CPU:       Dual core AMD Athlon 64 X2 5000+ (-MCP-) cache: 1024 KB 
           clock speeds: max: 2600 MHz 1: 1000 MHz 2: 1000 MHz
Graphics:  Card: NVIDIA GK208 [GeForce GT 710B]
           Display Server: X.Org 1.18.4 drivers: nvidia (unloaded: fbdev,vesa,nouveau)
           Resolution: 1600x900@59.95hz
           GLX Renderer: GeForce GT 710/PCIe/SSE2
           GLX Version: 4.5.0 NVIDIA 384.98
sysop@x1604:~$

```
{
As a plus for installing inxi
A fast look at your current weather:
```
 
inxi -xxxw

```
}
Nothing can be done, until I know what we have - or do not have - for hardware .

[INDENT][INDENT]study 3 times
[INDENT][INDENT][INDENT]act once
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by abhigyann on 2017-11-15
[http://paste.ubuntu.com/25965714/](http://paste.ubuntu.com/25965714/)

---

### Post by Bashing-om on 2017-11-15
abhigyann; humm ..

should have been similar :
```

sysop@x1604:~$ inxi -xxxw
Weather:   Conditions: 52 F (11 C) - Overcast Wind: Calm Humidity: 94%
           Pressure: 30.06 in (1018 mb) Location: Heber Springs AR (USA) Altitude: 91 ft
           Time: November 15, 1:03 AM CST (America/Chicago) Observation Time: November 15, 12:55 AM CST
sysop@x1604:~$ 

```

to tired now to think straight . deal with this at a later time .. the graphic's driver the more important too .

[INDENT]a pause for the cause
[/INDENT]

---

### Post by Bashing-om on 2017-11-15
abhigyann; OK -

Pick this up once again .

I still do not know why the amdgpu driver is installed . We have yet to see any sign of an AMD graphic's card on this system. Does it even exist ? OR turned off in the firmware settings ?

One more way to look:
```

glxinfo|grep Op

```

[INDENT][INDENT]when I know better
[INDENT][INDENT][INDENT]I do different[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by abhigyann on 2017-11-15
In my second post I've given my laptops specifications I used the amd graphics card over there and inserted that info in amd site and downloaded the drivers.
That output of that code says Error:unable to open display

---

### Post by Bashing-om on 2017-11-15
abhigyann; Welll ...

> 
There’s one important thing to note here, though. Most regions don’t offer the configuration we are currently reviewing, but instead, the notebooks rely on the integrated GPUs – Intel HD Graphics 520 in the Intel-powered configuration and Radeon R5 in AMD’s case.


so all depends on what the configuration is in your case . To this time I have seen no evidence of a AMD graphic's card .

??
```

glxinfo|grep Op

```
As another look for this mysterious hardware .

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by abhigyann on 2017-11-15
Error:unable to open display

---

### Post by Bashing-om on 2017-11-15
abhigyann; Yup -

confirmed that " Error:unable to open display" is valid.
glxinfo|grep Op
No gui running, no display for info .

Lemme rack my brains some more to see what we can do to verify the existence of a AMD graphic's card.

[INDENT][INDENT]remove all doubt
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2017-11-16
abhigyann; Hey ...

Still here .
Until I am convinced of the status of the AMD hardware, there is not a thing I can do.

Maybe :
```

lspci -nnk | nc termbin.com 9999

```
into a pastebin -
where this will show all the devices on the system .

[INDENT][INDENT]only as good as the tools we work with[/INDENT][/INDENT]

---

### Post by abhigyann on 2017-11-16
[http://termbin.com/l1kp](http://termbin.com/l1kp)

---

### Post by Bashing-om on 2017-11-16
abhigyann; Yeah !


Now we are cooking with Crisco 
> 
00:02.0 VGA compatible controller [0300]: Intel Corporation Sky Lake Integrated Graphics [8086:1916] (rev 07)

Display controller [0380]: Advanced Micro Devices, Inc. [AMD/ATI] Topaz XT [Radeon R7 M260/M265] [1002:6900] (rev 83)
	Subsystem: Hewlett-Packard Company Topaz XT [Radeon R7 M260/M265] [103c:811c]
	Kernel modules: amdgpu


The card "Might" do well with the amdgpu driver :
see the note :
 TOPAZ/MESO Radeon R5 M315
Radeon R7 M260/M265/M340/M360/M445/M460  (./) *1 
 [https://help.ubuntu.com/community/AMDGPU-Driver](https://help.ubuntu.com/community/AMDGPU-Driver)

Alternately there is "prime" - But I do not have knowledge of it's use cases with the amdgpu driver.
[https://wiki.archlinux.org/index.php/PRIME](https://wiki.archlinux.org/index.php/PRIME)

And let's consider what we are going to do .

[INDENT][INDENT]where there is a will, there is a way[/INDENT][/INDENT]

---

### Post by abhigyann on 2017-11-17
I already have hwe and and Ubuntu 16.04 the third option it gave was to download Ubuntu 14.04 with fglrx driver

---

### Post by Bashing-om on 2017-11-17
abhigyann;

I agree, going back is not conducive to forward progress. 18.04 will soon be a reality.

Now, I am not aware with amdgpu that any method has proven effective.
But there is 
switcheroo:
IRT: [https://packages.ubuntu.com/search?keywords=switcheroo-control](https://packages.ubuntu.com/search?keywords=switcheroo-control)
 
> 
on machines with two graphics cards, you can now select the GPU to use when launching an application (via right clicking the app / game in the Activities). Under the hood, this uses vga_switcheroo with the switcheroo-control package and it only works with open source drivers. Note that switcheroo-control is not available in Ubuntu 17.04, at least for now, but is available in the GNOME 3 Staging PPA;

where progress is being made for forthcoming releases.

prime:
see what I can come up with.

Tomorrow eve I will go back to work on this and see what I can learn .

[INDENT][INDENT]got to be a way
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2017-11-17
abhigyann; Uh Huh .

While there is indeed a way:
[http://article.gmane.org/gmane.comp.video.dri.devel/149144](http://article.gmane.org/gmane.comp.video.dri.devel/149144) <- Re: [Intel-gfx] [PATCH v5 00/12] Enable GPU switching on pre-retina?MacBook Pro
[https://bugs.launchpad.net/ubuntu/+source/switcheroo-control/+bug/1671828https://blogs.gnome.org/uraeus/2016/11/01/discrete-graphics-and-fedora-workstation-25/](https://bugs.launchpad.net/ubuntu/+source/switcheroo-control/+bug/1671828https://blogs.gnome.org/uraeus/2016/11/01/discrete-graphics-and-fedora-workstation-25/)
[https://launchpad.net/ubuntu/+source/switcheroo-control/1.1-1](https://launchpad.net/ubuntu/+source/switcheroo-control/1.1-1)
[https://www.dell.com/support/article/us/en/19/sln298475/a-guide-to-hybrid-video-on-dell-pcs-with-an-ubuntu-operating-system?lang=en](https://www.dell.com/support/article/us/en/19/sln298475/a-guide-to-hybrid-video-on-dell-pcs-with-an-ubuntu-operating-system?lang=en)

[http://io.zwets.it/2016/08/18/opencl-on-a-dual-graphics-dell-m4800/](http://io.zwets.it/2016/08/18/opencl-on-a-dual-graphics-dell-m4800/) <-OpenCL on a dual graphics Dell M4800 . Looks doable, but how bad do you want to break your system in making it work ?
You always need at least XServer version 1.18 or later, and Mesa 11.2 or later, and
Linux 4.6 or later, but sometimes you need more modern versions, as described below.

[http://docs.psychtoolbox.org/HybridGraphics](http://docs.psychtoolbox.org/HybridGraphics) <- Support for hybrid graphics laptops. 

Why not take the easy way and fresh clean install 17.10 and be done with it ?
Should work out-of-the-box .

[INDENT][INDENT]what I think
[/INDENT][/INDENT]

---

### Post by abhigyann on 2017-11-21
If I boot from a bootable pd with Ubuntu 17.10 will it overwrite the old Ubuntu? Or I need to remove it somehow

---

### Post by Bashing-om on 2017-11-21
abhigyann; Still here :)

I do not understand the term :
> 
bootable pd 


If it is a medium containing the live desktop environment, and you boot " try ubuntu" then no - will not touch the installed operating system(s) .

[INDENT][INDENT]best I can
[INDENT][INDENT][INDENT]help where I can
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by abhigyann on 2017-11-21
Yes live pen drive. I'd prefer if it removes the old version cause it (Ubuntu 16.04) would just be hogging up space if I am using the newer version. So if I do install Ubuntu when using a 17.10 live USB would it remove the old one?if no, then how can I remove it?

---

### Post by Bashing-om on 2017-11-21
abhigyann;

In the pen drive choose " try ubuntu" see that all functions as you desire ( will be much slower in the live environment ) .
this mode will not touch the present install.

Now if you like what you have in 17.10 and want to replace 16.04 with 17.10 then choose "install ubuntu".
Now there are several options on how to install; by far the easiest for the less informed is to choose "erase disk and install ubuntu"
This option will do just that .. All required of you is to respond to a few rudimentary user set up questions .

Mind you .. installing 17.10 is but one option - maybe for sure the best ... but it is only an option .

your call 
[INDENT][INDENT]as to what you want to do [/INDENT][/INDENT]

---

