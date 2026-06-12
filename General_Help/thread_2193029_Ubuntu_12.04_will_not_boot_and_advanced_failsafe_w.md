---
title: "Ubuntu 12.04 will not boot and advanced failsafe will not load either."
date: 2013-12-10
forum: General Help
---

### Post by MiD-AwE on 2013-12-10
Please help. :(

I do not know what to try now. in the past I was able to rely on the failsafe graphics mode to rescue my install, but it fails too. I already prepared a 13.10 disk. can anyone help me use it to recover my system. I need to access 12.04 long enough to back up some things.

---

### Post by Bashing-om on 2013-12-10
MiD-AwE; Hi !

What is the nature of the failure of your 12.04 install, maybe fixable (??).

To access 12.04 from the liveDVD:
Boot the liveDVD -> "try ubuntu" mode -> Terminal:
terminal commands:
```

sudo mkdir /mnt/work
sudo mount /dev/sda1 /mnt/work

```
Copy files from home directory:
With a USB thumb drive inserted:
```

ls /media ## to get the UUID of the USB Drive
cp -p /mnt/work/home/MiD-AwE</>your files> /media/MiD-AwE/<some_UUID/<path&File_name>

```
(where "MiD-AwE" is your username)
This "assumes" that the 12.04 install is on that first hard drive (sda) and that the files you want to access on that disk are residing on the 1st partition (sda1) .

Else: if you prefer to use the GUI file manager:
```

gksudo nautilus

```
and open windows for the target and the destination; drag and drop files.

ReMeMber: (UN)mount the device (sda1) when done !
```

sudo umount /mnt/work

```
Gui: Right click and choose unmount - for both "sda1" as well as the USB thumb drive.

Hey doable,
[INDENT][INDENT]no step for a stepper
[/INDENT][/INDENT]

---

### Post by MiD-AwE on 2013-12-10
Ok. Now I'm on my phone. When I tried the failsafex I get

Fatal server error: no screens found

ddxSigGiveUp: Closing log
Server terminated with error (1).
Closing log file

I tried to log in normally and I got to a command line but nothing worked. Now I have 13.10 disk in and running but I need to try to recover my 12.04 install back. I have important x amp install in /opt and I can't ditch the 12.04.

Please help.

---

### Post by sammiev on 2013-12-10
Post #2 should get you the info you want. Did you even try what Bashing-om suggested?

---

### Post by MiD-AwE on 2013-12-11
I did, and quickly realized that would help me back up files. And, I was asked for the specific error that it may be possible to rescue the 12.04 install. That's the reason for post#3.

Thank you.

---

### Post by steeldriver on 2013-12-11
If you can boot as far as a terminal login, then it should just be a matter of identifying and fixing your graphics / X server subsystem - start by logging in and then running

```
sudo lshw -C display
```

No need to copy it all - just the product and driver should give us enough to get started.

---

### Post by MiD-AwE on 2013-12-11
I'll be at my computer in an hour. Thank you for your help.

---

### Post by MiD-AwE on 2013-12-11
I get this:
*-display
Description: VGA compatible controller
Product: GF110 [GeForce GTX 580]
Vendor: NVIDIA Corporation
physical id: 0
bus info: pci@0000:01:00.0
Version:  a1
Width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
configuration: driver=nvidia latency=0
Resources: irq:24 memory :fd000000-fdffffff memory:f0000000-f7ffffff memory:f8000000-f9ffffff ioport:e000(size=128) memory:fe000000-fe07ffff

Thanks again for any help.

---

### Post by steeldriver on 2013-12-11
Don't thank me yet - I don't really know whether I will be able to help ;) What I would do next if it was my system is check to see what proprietary driver (if any) is in use

```
jockey-text --list
```

It may take a while to produce any output, but you should see something like

```

xorg:nvidia_173 - NVIDIA accelerated graphics driver (Proprietary, Disabled, Not in use)
xorg:nvidia_173_updates - NVIDIA accelerated graphics driver (post-release updates) (Proprietary, Disabled, Not in use)
xorg:nvidia_304 - NVIDIA accelerated graphics driver (Proprietary, Disabled, Not in use)
xorg:nvidia_304_updates - NVIDIA accelerated graphics driver (post-release updates) (Proprietary, Enabled, In use)
xorg:nvidia_319 - NVIDIA accelerated graphics driver (Proprietary, Disabled, Not in use)
xorg:nvidia_319_updates - NVIDIA accelerated graphics driver (post-release updates) (Proprietary, Disabled, Not in use)

```

Don't bother copying all the text - all you really need to know is what driver version(s) are available / enabled / in use

This is all from the 12.04 system not the 13.10 live disk btw

---

### Post by Bashing-om on 2013-12-11
MiD-AwE; Hey,

Your last says that a driver is loaded for the Nvidia GTX 580 graphics card, humm, and you can not get a desk top ?

What errors do you get when you boot once more to the command line terminal with terminal code:
```

sudo service lightdm start

```
also what drivers are available ?
```

sudo apt-cache policy nvidia

```
gotta be a reason.
[INDENT][INDENT]we be a look'n
[/INDENT][/INDENT]

---

### Post by MiD-AwE on 2013-12-11
I'm waiting for something to happen now. After trying to start lightdm the last line is: stopping send an event to indicate Plymouth is up

Been this way for a while now. Just a few more minutes and I'll reboot again.

---

### Post by MiD-AwE on 2013-12-11
The Jockey-text --list  says: xorg:nvidia_319_updates - NVIDIA accelerated graphics driver (post-release updates) (Proprietary, Enabled, In use)

---

### Post by Bashing-om on 2013-12-11
MiD-AwE; Well ..
That response, good that there is not a ton of errors reported, 
bad that it should have only been a matters of seconds to generate and report conditions.
> 
stopping send an event to indicate Plymouth is up

beats me presently what upstart is up to.

OK, let's see if we can get more info;
What returns from:
```

startx

```
and still want to know what drivers are available/in-use (steeldriver).

[INDENT][INDENT]cause and effect
[/INDENT][/INDENT]

---

### Post by MiD-AwE on 2013-12-11
And, sudo apt-cache policy nvidia says: N: Unable to locate package nvidia.

---

### Post by MiD-AwE on 2013-12-11
Startx 
Gives the ddxSigGiveUp: Closing log
Just like before. It then ends with:
xinit: Unable to connect to X server: No such file or directory

---

### Post by MiD-AwE on 2013-12-11
Also, startx (higher up on the screen) it says: Nvidia: API mismatch: the NVIDIA kernel module has version 304.88, but this NVIDIA driver component has version 319.32. Please make sure that the kernel module and all NVIDIA driver components have the same version. 

How do I do that?

---

### Post by Bashing-om on 2013-12-11
MiD-AwE; Well,

I too am of a mind that the graphics driver and x server are not talking !
Before removing the driver and (re)installing let's try this:
```

sudo service lightdm stop
sudo dpkg-reconfigure nvidia-current

```
Reboot and let's see what happened.

[INDENT][INDENT]we be look'n
[/INDENT][/INDENT]

---

### Post by MiD-AwE on 2013-12-11
Ok, after the reboot I still only get command prompt. What now?

---

### Post by steeldriver on 2013-12-11
I think it should be safe to just remove nvidia-319 / nvidia-319 updates packages

```
sudo apt-get purge nvidia-319*
```

This should drop you back to 304 or 304-updates - then either restart lightdm (might be sufficient) or reboot again

---

### Post by MiD-AwE on 2013-12-11
Again, after the purge I'm at command prompt. 
I tried to start lightdm again and this time it says: Lightdm fail
And then *Starting Recovery options if display manager fails to start
And there it hangs.

---

### Post by steeldriver on 2013-12-11
Did you reboot after the purge? or just try restarting lightdm?

---

### Post by MiD-AwE on 2013-12-12
I did reboot and then tried restarting lightdm.

---

### Post by steeldriver on 2013-12-12
Hmm... what do

```

apt-cache depends nvidia-current

apt-cache depends nvidia-current-updates

```

say? Does

```

dpkg -l | egrep nvidia-[0-9]+

```

show the nvidia-304 package(s) there and the -319 package(s) gone?

---

### Post by MiD-AwE on 2013-12-12
It shows 3 references to 304.88-0ubuntu0.0.3 and 1 reference to 319.32-0ubuntu0.0.1

---

### Post by steeldriver on 2013-12-12
so were there error messages when you ran the apt-get purge command? that should have removed the 319 package

---

### Post by MiD-AwE on 2013-12-12
The only error was the notice that lightdm failed to start. And it froze at that point.

---

### Post by Bashing-om on 2013-12-12
I have been in attendance; but, calling it a night for this session.
Will check back in my AM.
I will consider purging the Nvidia drivers, and installing   nouveau.
Then consider if the Nvidia drivers should be (re-)installed ??

@steeldriver -> what do you think ?

[INDENT][INDENT]best regards
[/INDENT][/INDENT]

---

### Post by steeldriver on 2013-12-12
OK well I'm obviously not helping here, so I'm going to bow out - maybe Bashing-om will come back with some more ideas

---

### Post by MiD-AwE on 2013-12-12
Ok, Thank you. G'night all.

---

### Post by Bashing-om on 2013-12-12
MiD-AwE; Morning,

Still think the thing to do is take the graphics driver back to nouveau (open source).
To that end, do you recall how you installed the proprietary driver ?
Depending on how you installed is the method to (un)install.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by steeldriver on 2013-12-12
It's still odd that failsafe won't work either though, because failsafe  *should* be a plain (unaccelerated) VESA driver that works independently  of what nvidia drivers are present - at least that's what I thought  should happen

BTW have you looked at the X server log right after lightdm fails to start? e.g.

```
tail /var/log/Xorg.0.log
```

One thing that occurred to me later last night was that in most cases of driver mismatch the system doesn't drop to a console login (just the famous flashing cursor), so I wonder if the driver situation is basically OK but there is a residual xorg.conf file that is preventing X specifically from working?

It might be worth backing up those up and letting the system regenerate them i.e.

```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.11Dec13

sudo mv /etc/X11/xorg.conf.failsafe /etc/X11/xorg.conf.failsafe.11Dec13

```

[FWIW I managed to get my Quadro FX 570M based laptop into the 'flashing cursor' state yesterday by enabling the nvidia_319 driver from jockey-text while trying to reproduce your symptoms; purging nvidia-319* worked right away for me however]

---

### Post by Bashing-om on 2013-12-12
steeldriver's last welll worth consideration !

Also. thinking. With the proprietary driver, maybe an update to the kernel broke it, maybe DKMS not enabled in the Nvidia driver install ? Thus the driver failed to update (??)

Things work best overall when kept within ubuntu's package management system.

[INDENT][INDENT]we do fault isolation and restoration
[/INDENT][/INDENT]

---

### Post by MiD-AwE on 2013-12-12
Hi all, just got home.

I think I used jockey to install the driver, previously I had installed the cuda driver from nvidia's website. SDK and all.

---

### Post by MiD-AwE on 2013-12-12
Since nothing is working, couldn't I just remove it all and start over?

---

### Post by MiD-AwE on 2013-12-12
Trying to start lightdm freezes the computer.  I have to reboot. Will the log file still reflect the correct version?

---

### Post by steeldriver on 2013-12-12
it should reflect the last attempt to start the X server - whether your manual attempt or the regular boot / init process - should be relevant either way

---

### Post by MiD-AwE on 2013-12-12
I can't type the whole thing one my phone. The highlights are more of the same;

Fatal Server error:
No screens found

DdxSigGiveUp: Closing log
Server terminated with error ( 1 ). Closing log file. 

It is predicating every line with [        447.491]
And [         447.505] the server terminated line has [        447.506]

---

### Post by Bashing-om on 2013-12-12
MiD-AwE;

Yeah, that is about what I have in mind, revert all back to the open source driver, see what is, and then perhaps load a proprietary driver if needed:
Let's try this:
1st let's make sure we do not have a 3rd party ppa to deal with:
```

cat /etc/apt/sources.list
ls -la /etc/apt/sources.list.d

```
Now if there is no PPAs, then:

Does an (un)installer exist on the system ?
```

sudo find / -name "NVIDIA-Linux-*"

``` YES (??) stop. we will use it !
Else ->

Good to go for (uninstall/(re)install ??
OK -> Then:
```

sudo apt-get update
sudo service lightdm stop
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup ##just in case !
sudo nvidia-installer --uninstall #maybe yes or no .
sudo apt-get remove --purge nvidia-*
sudo apt-get remove --purge xserver-xorg-video-nouveau xserver-xorg-video-nv
sudo apt-get install xserver-xorg-video-nouveau
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg

```

Cross our fingers and toes and ->
Reboot

If all has gone according to plan .. booting to the GUI login ! .. login -> Desktop ??

[INDENT][INDENT]hey
[INDENT][INDENT][INDENT]It could happen
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by steeldriver on 2013-12-12
If you want to share logs, a simple way is to install pastebinit

```
sudo apt-get install pastebinit
```
and then for example
```
pastebinit /var/log/Xorg.0.log
```

and then just post the URL link here

---

### Post by MiD-AwE on 2013-12-12
The sudo find is working but taking a long time. Hope that is normal.

---

### Post by MiD-AwE on 2013-12-12
Ok.

It brought up:
/root/NVIDIA-Linux-x86_64-295.49.run
and
/home/chuck/NVIDIA-Linux-x86_64-295.53.run

---

### Post by Bashing-om on 2013-12-12
MiD-AwE;

Yeah, the find command will take some time .. should be done by now, though ! .. looking at every file on the system seeking a match.

What is the status presently ?

[INDENT][INDENT]pins a needles
[/INDENT][/INDENT]

---

### Post by MiD-AwE on 2013-12-12
The last post is all that it brought up.

---

### Post by Bashing-om on 2013-12-12
MiD-AwE; OK ,

I think those are both install scripts. As we can not (un)install with them, not going to be concerned with them.

Proceed forth to the manual (un)install and (RE-)install and lets see what the cat drags in.

[INDENT][INDENT]fingers still crossed
[/INDENT][/INDENT]

---

### Post by steeldriver on 2013-12-12
... it looks like the cuda .run files do actually have an uninstall action

```

$ ./cuda_5.5.22_linux_32.run --help
Options:
   -help                      : Print help message
   -driver                    : Install NVIDIA Display Driver
[COLOR=#0000cd][B]   -uninstall                 : Uninstall NVIDIA Display Driver
[/B][/COLOR]   -toolkit                   : Install CUDA 5.5 Toolkit (default: /usr/local/cuda-5.5)
   -toolkitpath=<PATH>        : Specify a custom path for CUDA location
   -samples                   : Install CUDA 5.5 Samples (default: /usr/local/cuda-5.5/samples)
   -samplespath=<PATH>        : Specify a custom path for Samples location
   -silent                    : Run in silent mode. Implies acceptance of the EULA
   -verbose                   : Run in verbose mode
   -extract=<PATH>            : Extract individual installers from the .run file to PATH
   -optimus                   : Install driver support for Optimus
   -override                  : Overrides the installation checks (compiler, lib, etc)
   -kernel-source-path=<PATH> : Points to a non-default kernel source location
   -tmpdir <PATH>             : Use <PATH> as temporary directory - useful when /tmp is noexec

```

---

### Post by Bashing-om on 2013-12-12
; Yikes !

There I go showing my ignorance again !
Should have throwed on the brakes at the mention of cuda, and done some more home work !

Are we too late ??

[INDENT][INDENT]I try for perfection
[INDENT][INDENT]sometimes I fall far from grace
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by MiD-AwE on 2013-12-12
I was waiting for you :\
I got myself into this mess thinking I knew a little something :)

---

### Post by MiD-AwE on 2013-12-12
Should I continue with your manual uninstall (darn auto correct) instructions?

---

### Post by Bashing-om on 2013-12-12
MiD-AwE; Wheewhhh !

Dodged that one !

OK .. I know nothing about cuda, let's await steeldriver's advise, seems he has some abilities here !
See if he knows how to invoke the uninstall script for cuda.

[INDENT][INDENT]step aside son
[/INDENT][/INDENT]

---

### Post by MiD-AwE on 2013-12-12
:) Ok

---

### Post by steeldriver on 2013-12-12
Sorry guys I don't have any experience with the nvidia CUDA SDK, just an observation that if you installed drivers via a .run file (i.e. outside of the package management system) it may explain why the purge attempts didn't help

If you aren't actually using the CUDA GPU programming functionality then I would be tempted to uninstall it (using the --uninstall option of the .run file) and then install any proprietary driver via the usual means (jockey or 'Additional Drivers') assuming the system can be made to boot normally - but I'm just guessing

---

### Post by Bashing-om on 2013-12-12
This may take a bit of research:
> 
Uninstallation
If you want to totally remove Cuda, juste delete the /opt/cuda and ~/NVIDIA_GPU_Computing_SDK folders:

rm -r ~/NVIDIA_GPU_Computing_SDK
sudo rm -r /opt/cuda
and remove the export PATH=$PATH:/opt/cuda/bin and export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/opt/cuda/lib:/opt/cuda/lib64 lines of the ~/.bash_profile file. 



gimme a bit of time to looksee and thinkee

But hey, sure am glad the brakes were applied prior to a real wreck of things.

---

### Post by Bashing-om on 2013-12-12
Guys, should not be too hairy.

What does the file look like ?
```

cat ~/.bash_profile

```

back to 1 step at a time
[INDENT][INDENT]progress made s l o w l  y[/INDENT][/INDENT]

---

### Post by MiD-AwE on 2013-12-12
> **Bashing-om said:**
> 
What does the file look like ?
```

cat ~/.bash_profile

```


It says: cat: /home/chuck/.bash_profile: No such file or directory

---

### Post by Bashing-om on 2013-12-12
MiD-AwE; Yuk !

Makes me wonder about what/where the paths were exported to:

CUDA (Compute Unified Device Architecture) is a parallel computing architecture developed by Nvidia for graphics processing.

This document provides instructions to install/remove Cuda 4.2 on Ubuntu 12.04.
> 
Preparation
Update variables, and this on every boot:

export PATH=$PATH:/opt/cuda/bin
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/opt/cuda/lib:/opt/cuda/lib64
echo 'export PATH=$PATH:/opt/cuda/bin' >> ~/.bash_profile
echo 'export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/opt/cuda/lib:/opt/cuda/lib64' >> ~/.bash_profile

Do you think we can get by with ignoring what paths may have been set and where ?
Maybe we should invest a bit more time and see where those paths may have been set (???) before proceeding.

[INDENT][INDENT]it is all in the process
[/INDENT][/INDENT]

---

### Post by MiD-AwE on 2013-12-12
Ok. Safety First. =D

---

### Post by Bashing-om on 2013-12-13
MiD-AwE; OK,

My think-ability has become impaired for this session.
I will pick this back up in my AM -once more.

[INDENT][INDENT]worth doing
[INDENT][INDENT][INDENT]worth doing right
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by MiD-AwE on 2013-12-13
Ok, g'night.

---

### Post by Bashing-om on 2013-12-13
MiD-AwE; OK, Back and much refreshed !

My reference - presently -:
[https://help.ubuntu.com/community/Cuda](https://help.ubuntu.com/community/Cuda)
is for cuda's version 4.2 on Ubuntu 12.04..
Do you know what version you have installed ?

And this may be the reason for the difficulties you have experienced:
> 
It is necessary to have a Nvidia proprietary driver up to 295.xx (which can be installed automatically or manually). For Ubuntu versions under 12.04, you will have to install Nvidia driver [color=red]manually[/color].

Nvidia's driver versions 304 or 319 should have worked if properly installed as, per Nvidia's site, the Quadro FX 580 does support cuda; and we are installing onto ubuntu 12.04 ! Can not see where you are at fault, MiD-AwE, for installing Cuda if you require more graphics power.
-----------

 I Remain in the mind set to remove all graphics drivers and install the open source drivers, see what results .. and then try again to install proprietary driver and then we can do the Cuda thing (?)
Presently I want to know what version of Cuda we are attempting to (un-)install, steeldriver's input(5.2) is cause to wonder - just to keep up this time with the p's and q's. Keep the mess behind us to a minimum to clean up.

[INDENT][INDENT]that is what I think
[/INDENT][/INDENT]

---

### Post by MiD-AwE on 2013-12-13
4.2 sounds right. I wanted 5 but could get it at the time.

---

### Post by Bashing-om on 2013-12-13
MiD-AwE; Hey !

I have been doing some homework:

> 
it brought up:
/root/NVIDIA-Linux-x86_64-295.49.run
and
/home/chuck/NVIDIA-Linux-x86_64-295.53.run

Not sure what is going on with the above /root/, or how to access that protected directory.
but: let's test with what we can access; What returns from:
```

sudo ./devdriver_4.2_linux_64_295.53.run --uninstall

```
As I have seen conflicting information on the proper method to remove Cuda. 
I can see no harm in trying to see if there are "(un-)installers, and then check and see what was not removed.

This makes some sense to me.

[INDENT][INDENT]and away we go again
[/INDENT][/INDENT]

---

### Post by MiD-AwE on 2013-12-13
ok. back home at last. I'll give it a try.

---

### Post by MiD-AwE on 2013-12-13
I get:
Error: File '/usr/lib/xorg/modules/extensions/libglx.so' is not a symbolic link.

---

### Post by MiD-AwE on 2013-12-13
Then several warnings about being unable to restore files because I used other drivers after the cuda driver that the cuda installer did not install. But, after all the warnings it says the uninstall is complete.

---

### Post by Bashing-om on 2013-12-13
MiD-AwE; Well, 

I think that is all to the good.
I must do some more home work and study to make a recommendation on how to cope with:
"/root/NVIDIA-Linux-x86_64-295.49.run"

Which may be the source of "because I used other drivers after the cuda driver that the cuda installer did not install"
We will continue this - if you are not terribly indisposed - on your tomorrow night.
Give me some time to research and consider.

[INDENT][INDENT]2 steps forward and 1 back
[/INDENT][/INDENT]

---

### Post by MiD-AwE on 2013-12-13
Thank you so much for all of your help. I'm afraid I will not be home after 4 pm tomorrow. But my morning is open and anytime Sunday after noon.

---

### Post by Bashing-om on 2013-12-13
MiD-AwE;
Well, I will take this up once more .. I am at GMT -6. I generally get back to the keyboard long about 11'ish.

Will holler at ya then.

[INDENT][INDENT]night night
[/INDENT][/INDENT]

---

### Post by MiD-AwE on 2013-12-14
Right on. I'm GMT -7.
G'night

---

### Post by steeldriver on 2013-12-14
> **Bashing-om said:**
> 
Not sure what is going on with the above /root/, or how to access that protected directory.


Not sure I understand, but /root is just root's home directory - you can get there directly by doing

```
sudo -i
```

Hope this helps

---

### Post by Bashing-om on 2013-12-14
@steeldriver, Sure it helps. I was reticent about posting the procedure on a open forum. Still am.

Let's take the less risky path and boot into "recovery mode" and do our work from there.
Boot to the grub menu and choose "recovery" -> "drop to root shell prompt".
Now be careful, no messing about ! We are going to enable the file system for read and write access - no mistakes permitted !
Terminal command:
```

mount -o remount rw /

```
You are in "/root" at this time, let's make sure the file in question is here:
```

ls -la  NVIDIA*

```
Now to execute the removal routine once more: - you are "root" and there is no need now to elevate privileges - run:
```

./devdriver_4.2_linux_64_295.49.run --uninstall

```
When completed, get out !
```

exit

```

Choose "resume normal boot" -- I do not know what will result at this time .. maybe you can and will boot to the GUI. Be interesting to see.

If you are "hung" let's back out gracefully:
key combo alt+SysRq (your key may also be Prt scrn) + r s e i r b . Typed slowly while holding alt and SysRq keys down ... That sequence should reboot the system.
-------------
At this point we want to get a status:
terminal command:
```

dkms status 

```
Chances are "dkms" is not installed, follow on screen directions and install the application.

Then we will resume removing drivers and proceed to install the open source driver and then; See what we are going to do about other driver installation.

sounds like [INDENT]a plan to me
[/INDENT]

---

### Post by MiD-AwE on 2013-12-14
Ok. Trying this now.

---

### Post by Bashing-om on 2013-12-14
k

---

### Post by MiD-AwE on 2013-12-14
It never goes as planned :(

ls -la NVIDIA* 
returns: -rwxrwxr-x 1 root root 58521195 Jun 9 2012 NVIDIA-Linux-x86_64-295.49.run

Then 
./devdriver_4.2_linux_64_295.49.run --uninstall
Returns:
bash: ./devdriver_4.2_linux_64_295.49.run: No such file or directory

Is this bad?

---

### Post by MiD-AwE on 2013-12-14
I have not rebooted yet. Should I?

---

### Post by Bashing-om on 2013-12-14
MiD-AwE; Sheesshhh.

Like you I do not know what to make of that !.. The file exist, but, but, but 

OK, Let's try steeldriver's move: From the root shell:
terminal command:
```

./cuda_4.2_linux_64_295.49.run --help
##or maybe something like this ?
/cuda_4.2._linux_64.run --help
##OR maybe
./devdriver_4.2_linux_64_295.49.run --help

```
Think'n maybe the .49 version does not support the "--uninstall" option ?

When I step into deep waters, I need to keep a 
[INDENT][INDENT][INDENT]life preserver handy[/INDENT][/INDENT][/INDENT]

---

### Post by MiD-AwE on 2013-12-14
I'm still @root shell. Should I do the "move from root shell now?

---

### Post by MiD-AwE on 2013-12-14
I suspect I asked a dumb question, so I'm continuing with the move.

---

### Post by Bashing-om on 2013-12-14
k

---

### Post by MiD-AwE on 2013-12-14
All three failed the same way:
no such file or directory

Does this mean it's clean with a bad reference?

---

### Post by steeldriver on 2013-12-14
You want to run the actual run file that you see i.e. after you 'sudo -i' to get into /root (as root)

```
./NVIDIA-Linux-x86_64-295.49.run --help
```

You should get a list of options like

```


./NVIDIA-Linux-x86_64-295.49.run [options]

This program will install the NVIDIA Accelerated Graphics Driver for
Linux-x86_64 295.49 by unpacking the embedded tarball and executing
the ./nvidia-installer  installation utility.

Below are the most common options; for a complete list use
'--advanced-options'.

--info
  Print embedded info (title, default target directory) and exit.

--check
  Check integrity of the archive and exit.

-x, --extract-only
  Extract the contents of ./NVIDIA-Linux-x86_64-295.49.run, but do not
  run 'nvidia-installer'.


The following arguments will be passed on to the ./nvidia-installer
utility:

  -a, --accept-license
      Bypass the display and prompting for acceptance of the
      NVIDIA Software License Agreement.  By passing this option
      to nvidia-installer, you indicate that you have read and
      accept the License Agreement contained in the file
      'LICENSE' (in the top level directory of the driver
      package).

  --update
      Connect to the NVIDIA FTP server '
      ftp://download.nvidia.com ' and determine the latest
      available driver version.  If there is a more recent driver
      available, automatically download and install it.  Any
      other options given on the commandline will be passed on to
      the downloaded driver package when installing it.

  -v, --version
      Print the nvidia-installer version and exit.

  -h, --help
      Print usage information for the common commandline options
      and exit.

  -A, --advanced-options
      Print usage information for the common commandline options
      as well as the advanced options, and then exit.


```

---

### Post by MiD-AwE on 2013-12-14
Ha, I just did

ls

It returned:
Desktop    NVIDIA-Linux-x86_64-295.49.run

Remember I'm still @root shell prompt.

---

### Post by oldos2er on 2013-12-14
What does ```
file NVIDIA-Linux-x86_64-295.49.run
``` say?

---

### Post by MiD-AwE on 2013-12-14
I just ttried to run
NVIDIA-Linux-x86_64-295.49.run
And it returns: command not found

---

### Post by MiD-AwE on 2013-12-14
With that I get:
 data

That's all.

---

### Post by steeldriver on 2013-12-14
you need a relative path

```
[COLOR=#0000ff]**./**[/COLOR]NVIDIA-Linux-x86_64-295.49.run --help
```

and depending how you copied it there you may need to make it executable first

```
chmod +x NVIDIA-Linux-x86_64-295.49.run
```

---

### Post by oldos2er on 2013-12-14
Could we see the 'file' command run against as I posted?

---

### Post by MiD-AwE on 2013-12-14
Following steeldriver's last info started the installer in root shell. So, I refused the license agreement to abort.

---

### Post by steeldriver on 2013-12-14
It looks like this older (295) installer does not have an explicit uninstall option - however since you already found and ran a newer uninstaller my instinct says we can ignore this one - all traces of the v.295 driver should be long gone, no? What does the team think?

---

### Post by MiD-AwE on 2013-12-14
Can I safely delete this installer from root?

---

### Post by Bashing-om on 2013-12-14
et al;

As it seems the file "NVIDIA-Linux-x86_64-295.49.run" was not made executable to begin with, I can see no harm in just deleting that file .. and carry on and see if "dkms" reveals anything else we should be aware of.
2nd thoght, might run:
```

dkms status

``` prior to removing the file !


[INDENT][INDENT]my thoughts
[/INDENT][/INDENT]

---

### Post by steeldriver on 2013-12-14
I would leave it there for now, it will not do any harm - I suggest you exit the root shell though, just to avoid accidents

How about we come at it from another angle - by seeing what actual nvidia kernel modules you have on the system right now e.g.

```
ls -ld /lib/nvidia*
```

```
find /lib/modules/`uname -r`/ -name 'nvidia*'
```

BTW have we tried booting with 'nomodeset' to see if we can get a fallback VESA driver that way?

---

### Post by Bashing-om on 2013-12-14
Agree !

---

### Post by MiD-AwE on 2013-12-14
Ok, I did not delete it. Resumed normally.  At the prompt checked dkms status.
It says
Nvidia-304, 304.88, 3.2.0-45-generic, x86_64: installed
3.2.0-52-generic is also installed

Nvidia-304-updates
&
Nvidia- 319-updates 
Are also install

---

### Post by Bashing-om on 2013-12-14
MiD-AwE; Making progress !

And what returns from steeldriver's last for "ls" and "find"?

Getting close !

---

### Post by MiD-AwE on 2013-12-14
I get 
drwxr-xr-x 2 root root 4096 Aug29 0021 /lib/nvidia-304
304-updates
319-updates

The last command says no such file or directory

---

### Post by Bashing-om on 2013-12-14
MiD-AwE; Yikes !

This is getting stranger all the time.
check once more please that:
```

find /lib/modules/`uname -r`/ -name 'nvidia*'

``` has no return, as that makes no sense as we know there are Nvidia drivers installed !

Still dotting out i's ... preparing to 

[INDENT][INDENT]jump
[/INDENT][/INDENT]

---

### Post by MiD-AwE on 2013-12-14
Ok. Find returns:
find: '/lib/modules/uname -r/': No such file or directory

That is the exact text.

---

### Post by Bashing-om on 2013-12-14
MiD-AwE; Well !

I am just going to "assume" that the install routine has removed them. Let's bite the bullet and do:

```

sudo apt-get update
sudo service lightdm stop
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup ##just in case !
sudo nvidia-installer --uninstall #maybe yes or no .
sudo apt-get remove --purge nvidia-*
## EDIT: above command will also remove the nvidia-common package and the nvidia-common package has as a dependency ##the ubuntu-desktop package.
##So after above command you should also give the installation command for ubuntu-desktop package:
sudo apt-get install ubuntu-desktop
sudo apt-get remove --purge xserver-xorg-video-nouveau xserver-xorg-video-nv
sudo apt-get install xserver-xorg-video-nouveau
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg
sudo update-initramfs -u

```
Cross our fingers and toes and ->
Reboot !

If all has gone well, you should now boot to the GUI login !

[INDENT][INDENT]maybe yes ?
[/INDENT][/INDENT]

---

### Post by steeldriver on 2013-12-14
The uname -r part needs to be EXACTLY how we posted it i.e. surrounded by backticks - it is meant to expand in the shell to the current running kernel.

If you can't find the backtick key then you can use the $(...) form instead

```
find /lib/modules/[COLOR=#0000ff]**$(**[/COLOR]uname -r[COLOR=#0000ff]**)**[/COLOR]/ -name 'nvidia*'
```

---

### Post by MiD-AwE on 2013-12-14
> **steeldriver said:**
> The uname -r part needs to be EXACTLY how we posted it i.e. surrounded by backticks - it is meant to expand in the shell to the current running kernel.

If you can't find the backtick key then you can use the $(...) form instead

```
find /lib/modules/[COLOR=#0000ff]**$(**[/COLOR]uname -r[COLOR=#0000ff]**)**[/COLOR]/ -name 'nvidia*'
```

Ok, that worked.
/lib/modules/3.2.0-52-generic/
     kernel/drivers/video/nvidia
     kernel/drivers/video/nvidia/nvidiafb.ko
     kernel/drivers/net/ethernet/nvidia
     updates/dkms/nvidia_304.ko
     updates/dkms/nvidia_304_updates.ko
     &
     nvidia_319_updates.ko

---

### Post by steeldriver on 2013-12-14
OK can we also see the contents of your /etc/modprobe.d/nvidia-graphics-drivers.conf if you have one

```
cat /etc/modprobe.d/nvidia-graphics-drivers.conf
```

I think *this* is where the actual version that gets loaded is aliased - and others get blacklisted

---

### Post by MiD-AwE on 2013-12-14
> **steeldriver said:**
> OK can we also see the contents of your /etc/modprobe.d/nvidia-graphics-drivers.conf if you have one

```
cat /etc/modprobe.d/nvidia-graphics-drivers.conf
```

I think *this* is where the actual version that gets loaded is aliased - and others get blacklisted

blacklist nouveau
blacklist lbm-nouveau
blacklist nvidia-173
blacklist nvidia-96
blacklist nvidia-current-updates
blacklist nvidia-173-updates
blacklist nvidia-96-updates
alias nvidia nvidia_319_updates
alias nouveau off
alias lbm-nouveau off

That looks problematic to me and I'm obviously a total newb. :)

---

### Post by steeldriver on 2013-12-14
Yes that's what I'm thinking also - despite attempts to remove it, nvidia_319_updates is still getting loaded for 'nvidia' - I'm going to crack a beer and have a think about how we go from here

---

### Post by Bashing-om on 2013-12-14
I had not thought about the blacklist file ! Yikes !

Me, dinner and a shower... 

[INDENT][INDENT]I shall return
[/INDENT][/INDENT]

---

### Post by MiD-AwE on 2013-12-14
I have an engagement this evening.  I won't be home till after midnight.  So if you have any ideas I'll give'm a try in the morning.

Thank you all.

---

### Post by Bashing-om on 2013-12-15
et al;

With due consideration, lets remove the " /etc/modprobe.d/nvidia-graphics-drivers.conf " file;
And
Check the directory for any thing we need to look at:
```

ls -la /etc/modprobe.d

```
Then
Take a gander at the "blacklist" file;
```

cat /etc/modprobe.d/blacklist.conf

``` To make sure nothing relevant is listed there.

OK, now if all are in agreement, can we now purge "Nvidia" and install the open source drivers and see where then we stand ?

[INDENT][INDENT]one big step for Nvidia
[/INDENT][/INDENT]

---

### Post by steeldriver on 2013-12-15
Can we take a moment to review before doing that? In particular MiD-AwE could you confirm whether you tried using jockey-text to disable xorg:nvidia_319_updates? Or have we just tried (1) apt-get purge and (2) the cuda removal process that Bashing-Om suggested? If we haven't tried jockey-text it might be worth giving that one chance.

Last night I updated my nvidia-based laptop to nvidia_319_updates (using the 'Additional Drivers' aka jockey-gtk) and I would be happy to attempt to downgrade via jockey-text as a dry run to see if that works - lmk

FWIW I tried manually editing my /etc/modprobe.d/nvidia-graphics-drivers.conf to alias nvidia to nvidia_304_updates and rebooted - it seemed to ignore it completely, as far as I could tell (at least using the nvidia-settings app) it was still running 319_updates (319.32). Unfortunately it doesn't seem to be possible to confirm that by using lsmod since 'nvidia' is just an alias... so it's possible that the modprobe file *is* loading the correct driver and that nvidia-settings is reading the version info from somewhere else.

---

### Post by Bashing-om on 2013-12-15
Yeah, I think that is perfectly in order ! .. The ultimate goal is to install Cuda 5.0. We just want a firm foundation from which to jump from.

[INDENT][INDENT]two heads are better than 1
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-12-18
MiD-AwE;

Car MiD-AwE, where are you ?

We have put a lot of time and effort into this, would like to know how it is going,

What is the current situation ?

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by egeezer on 2013-12-18
Hi, Bashing-om and steeldriver: I'm not MiD-AwE, but I just got into the same original mess today: no boot, flashing cursor, login showing the same Nvidia problem.* Not in front of me right now, but as I recall the error was that 304.88 is installed, should be 304.108.* MyGraphics card is a fairly simple one, GeForce 210.*  I'm probably in a better position to do something about it, too, because I have a dual boot with another Ubuntu 12.04 (both are actually Xubuntu) and I can mount the failing one from the surviving one, which does boot properly.  I can access all the modprobe.d files, and I imagine I could do something about the problem if I knew what I was doing (which at this point, I really don't).  Any advice?

Edited to add: time zone GMT -7

---

### Post by egeezer on 2013-12-19
Okay, MAJOR thanks to Bashing-om and steeldriver: I just kept plugging at the jockey-text command, and found that it can directly override the Enabled/disabled state of any particular driver in the list.  I enabled one that had been disabled, ran startx, and I was back in business.  Couldn't have done it without your generous contribution of time rescuing the other poster!

---

### Post by Bashing-om on 2013-12-19
@ egeezer; Great !

I had seen your posting, and had been considering "how to proceed" - proprietary driver, broke in a upgrade -.
Glad ya got it resolved and shared the means to do so.

[INDENT][INDENT]just keep on keep'n on
[/INDENT][/INDENT]

---

### Post by MiD-AwE on 2013-12-22
Hi all,

Too much life in the way of working out this issue. I'm finally back with some time and I'll try to catch up to you all. Let me look over the comments since I was last here and then I begin posting responses. If you gave up on me, then I just want to say thank you for all of your efforts.

Ok, I believe I'm all caught up but no new instructions did I find since my last action. Am I missing something? I still have nothing has changed on my end. ([COLOR=#000000]egeezer's[/COLOR] comment lead me to consider my available free space and I have enough to install a new distro if that would make this better. Please advise if you are still around.)

---

### Post by Bashing-om on 2013-12-22
MiD-AwE; Hey !

Yeah still here, 
We are at awaiting the response from steeldriver's post #107, before plowing on !

(The thought had occurred to me that you had gotten disgusted with the situation and did the nuclear solution of (re-)install !)

we will get back
[INDENT][INDENT]on track
[/INDENT][/INDENT]

---

### Post by egeezer on 2013-12-22
Hi, MiD!

Thought I might show you what fixed my problem: I ran the following:

```
jockey-text --list
```

Had to wait a while, then it showed me what drivers were available.  The enabled one was an NVIDIA-UPDATES, which I figured meant the updates, not the dfriver itself.  Immediately before that in the list was the 304 driver.

So I did ```
sudo jockey-text -e (the whole driver line)
```

waited while it worked, then```
startx
```

and I was back in business.

---

### Post by egeezer on 2013-12-22
P.S.  On another thread, steeldriver mentioned that insteadof enabling (the -e) the old driver, I could have used -d on the updates line to disable it.

---

### Post by MiD-AwE on 2013-12-22
[COLOR=#000000] (1) apt-get purge and (2) the cuda removal process that Bashing-Om suggested

That's it so far. How do I proceed with jockey?[/COLOR]

---

### Post by MiD-AwE on 2013-12-22
If everyone agrees this is a safe direction, I'll try anything :)

---

### Post by MiD-AwE on 2013-12-22
Ok, I think that we already removed too much to reuse and not enough to be rid of it. 

BRB

---

### Post by Bashing-om on 2013-12-22
et al;

I have my iron in several fires presently, let me get caught up to where I can focus on this.

[INDENT][INDENT]I'll Be Back
[/INDENT][/INDENT]

---

### Post by egeezer on 2013-12-22
I don't know about safe directions, because I'm not that familiar with what you've done already, but if you still can boot to a login cursor, you should run the jockey-text --list (TWO HYPHENS).  That will tell you what Nvidia drivers are present, which are disabled, and which is enabled (if any).  Using jockey-text --help will give you choices of enabling, disabling, checking for free and non-free, and a lot more.  It is a powerful utility that overrides others, so do be careful.

As for advice, I have only used the --enable to get back my old driver.

---

### Post by MiD-AwE on 2013-12-22
Ok, I'm on it :)

---

### Post by MiD-AwE on 2013-12-22
Ok, 

xorg:nvidia_304_updates - disabled, not in use
xorg:nvidia_319_updates - enabled, in use

Is returned from Jockey-text --list

---

### Post by egeezer on 2013-12-22
From all you've posted up to now, I would guess that you have indeed removed the actual nvidias, leaving only the instructions to update.  However, I do know what I would do: I would run sudo jockey-text -e xorg:nvidia_304-updates and see if anything useful happens.  If it did, I would run startx and cheer wildly when the desktop comes back.

If it didn't, I would reinstall and mutter vague curses.

---

### Post by steeldriver on 2013-12-22
AFAIK xorg:nvidia_304_updates is a complete driver package (not just a set of updates for xorg:nvidia_304) so yes you should be able to enable it by doing

```
sudo jockey-text -e xorg:nvidia_304_updates
```

If it complains about not being able to connect to a session bus then try

```
sudo jockey-text --no-dbus -e xorg:nvidia_304_updates
```

---

### Post by MiD-AwE on 2013-12-22
Do I need to be concerned about the "[COLOR=#000000]xorg:nvidia_319_updates - enabled, in use" anything to do there first?[/COLOR]

---

### Post by steeldriver on 2013-12-22
No I don't think so - enabling one driver from the list will automatically disable the other - in fact, I've usually used it that way i.e. by disabling a "troublesome" driver, which forces it to fall back to the previous one

```
sudo jockey-text **-d** xorg:nvidia_319_updates
```

(or **--disable**) should automatically switch to the next 'highest' available driver i.e. xorg:nvidia_**304**_updates

---

### Post by MiD-AwE on 2013-12-22
Here goes, I'll let ya know how it goes.

It's back =D

Thank you all so much. You're Awe-some ALL!

Celebrate good times come-on! :popcorn:

---

### Post by Bashing-om on 2013-12-23
et al ; Outstanding work !

Just goes to prove once more; always stay within the resources of the operating system, The checks and balances are in place for a reason, huh .

[INDENT][INDENT]all's well that ends well
[/INDENT][/INDENT]

---

