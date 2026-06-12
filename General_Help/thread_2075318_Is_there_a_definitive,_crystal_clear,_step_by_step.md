---
title: "Is there a definitive, crystal clear, step by step How to NVidia proprietary driver?"
date: 2012-10-23
forum: General Help
---

### Post by Geezanansa on 2012-10-23
Have found it very difficult getting a working system due to driver problems.  Do appreciate drivers changing and kernels changing cause the need to reinstall drivers as and when required.  The reasons underlying to this is in fact imo what ubuntu is all about but am struggling to cherish a barely working pc.

The amount of unanswered posts, people posting saying they know the answer and not posting the answers, people posting solutions with no explanantion or reference to their sources, original posters not updating threads giving what worked for them are some of the things adding to the frustration of a pc running like a bag of spanners so i would like to know, "Is there a definitive, crystal clear, step by step How to install NVidia proprietary driver? 

The gist of the advice i have found in these forums suggest using nouveau "if it works for you" which is fine if you want to check your emails and as i intend using my pc for slightly more demanding applications as well as being able to change the icon launcher size the need for proprietary drivers beckons.

Keeping this post short as my time seems better spent studying Nvidia readme before trying the not so recommended way (especially for noobs like me) of installing driver direct from nvidia.  Overlooking something or type error could break ubuntu.

But if additional/proprietary  drivers used - ubuntu breaks drivers lol


Reading the nvidia readme is not ubuntu specific but am sure a more experienced ubuntuist could shed some constructive light on the subject as i am sure this is really a nooby thing in that it is not ubuntu or drivers at fault  but simply just how they are being used.

---

### Post by oldfred on 2012-10-23
What version nVidia card/chip and what version Ubuntu.

With older versions, you had to boot with nomodeset and then it offered to install the nVidia driver and just worked.

With 12.10 they forgot the headers so nVidia does not install. If you download headers and manually install nvidia, then it works.

Has most bug reports:
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-updates/+bug/1068341](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-updates/+bug/1068341)

[https://bugs.launchpad.net/fglrx/+bug/1068456](https://bugs.launchpad.net/fglrx/+bug/1068456)
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1068488](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1068488)
[https://bugs.launchpad.net/fglrx/+bug/1068661](https://bugs.launchpad.net/fglrx/+bug/1068661)

Has what worked for me, install headers & dpkg update.
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-updates/+bug/1068942](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-updates/+bug/1068942)

But you need the headers first:
When you see you are in the desktop but no icon or bar, right click to change desktop background
When the window appear, click all settings, now you see the system settings window.
Next, click on Software source, go in the additional drivers tab.
Select the 3 rd option, using video driver for the nvidia or AMD... fglrx-upgrade

cntrl-alt f1 or f2 to get to terminal also works
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install linux-headers-generic
# only reason to purge is there are several versions, if you know you have different nVidia use that: 
sudp apt-get purge nvidia*
sudo apt-get install nvidia-current
sudo dpkg-reconfigure nvidia-current

---

### Post by Geezanansa on 2012-10-23
Hi again oldfred

Yes sorry for not highlighting the many hours/days/weeks trying different drivers right from nouveau, trying the recommended and all the other proprietary drivers including vdpau and gallium!?  as well as adding ppa to try xswat drivers (which have worked for me in the passed)  As well as the NVIDIA  drivers directly from NVidia.

Can confirm have not had this trouble with graphics driver in older flavours either; though i have had to sometimes change kernel start up parameters.
It is only with the most recent 12.04 kernel and 12.10 kernel i have got this problem of not booting to log in screen when using proprietary drivers.  nouveau appears as driver being used in lspci but hardware details in system settings says gallium being used!?.

Running 12.04 and here is  what lspci -v gives regarding gpu.
[CODE][02:00.0 VGA compatible controller: NVIDIA Corporation GF119 [GeForce GT 520] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: ZOTAC International (MCO) Ltd. Device 3214
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at df000000 (32-bit, non-prefetchable) [size=16M]
    Memory at d0000000 (64-bit, prefetchable) [size=128M]
    Memory at dc000000 (64-bit, prefetchable) [size=32M]
    I/O ports at ec00 [size=128]
    Expansion ROM at def80000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: nouveau
    Kernel modules: nvidia, nouveau, nvidiafb
/CODE]
Trying 12.10 on an other system gives same results and appreciate that system would probably run on older flavours as that would allow access to more appropriate chipset drivers.

When i referred to nvidia proprietary drivers in op i intended to refer to the drivers directly from nvidia.  As many folks report that is what works for them in order to use their applications/games.

Reading up in nvidia readme [http://uk.download.nvidia.com/XFree86/Linux-x86/304.60/README/installdriver.html](http://uk.download.nvidia.com/XFree86/Linux-x86/304.60/README/installdriver.html) for the 304.60 driver Do realize as part of the preparation of installing these drivers nouveau will be blacklisted in a ,conf file and unloaded. This will stop unity working.
So the application that uses 3d acceleration might work but at a cost/ trade off  as unity will not!?

Installing graphics drivers is usually not a problem.  Trying to get gaming on linux is.  And have had some success but starting to appreciate all that  Ubuntu have achieved and what Valve are working on regarding Steam for Linux client. For their blog go here [http://http://blogs.valvesoftware.com/linux/faster-zombies/](http://http://blogs.valvesoftware.com/linux/faster-zombies/) .  Might not be of much interest to many current ubuntu users  but the number that are; is sure to grow in the very near future.  

Now how do i go about configuring ubuntu, graphics and applications in order for them to run?
Am sure playonlinux launching steam (for windows client) in order to start Call of Duty 2 from the Steam library list is doable....   
but only if there is a suitable driver being used appropriate to kernel.

---

### Post by sgage on 2012-10-23
sudo apt-get install nvidia-current

This has never failed for me.

---

### Post by Geezanansa on 2012-10-23
It has at least booted a desktop in the passed for me.

After trying nvidia-current again  realise need to remove ppa for xswat to get older drivers.....

With the exception of nouveau drivers what happens at boot is get post> grub >plymouth but lightdm crashes to black screen (dunno dm) so no log in screen just a black screen

removing nvidia-current after unsuccessfull boot( get post grub plymouth but lightdm crashes to black screen (dunno dm) so no log in screen- do have input so can tty to remove nvidia-current in order to fall back to nouveau.  After dpkg reconfigure and reboot still got black screen but lspci -v revealed nvidia-experimental-304 as being loaded so had to uninstall to fall back to nouveau

Think removing xswat ppa then updating, upgrading and then try nvidia-current will get things going.(like changing launcher icon size)

This will at least get 3d acceleration going for some eye candy but am sure for games/applications that the nvidia drivers direct from nvidia provide the answer for  fragging on linux.(hence op question and name of thread)

---

### Post by oldfred on 2012-10-23
Years ago I installed the nVidia drivers and they did not work and they had done so many thing to system that I have never reinstalled from nVidia. 

In the last few years the one's offered by Ubuntu have been good for me. I managed t avoid the .40 version that had issues and now often install not the current but the next one nvidia-current-updates.

---

### Post by sgage on 2012-10-23
> **Geezanansa said:**
> It has at least booted a desktop in the passed for me.

After trying nvidia-current again  realise need to remove ppa for xswat to get older drivers.....

removing nvidia-current after unsuccessfull boot( get post grub plymouth but lightdm crashes to black screen (dunno dm) so no log in screen- do have input so can tty to remove nvidia-current in order to fall back to nouveau.  After dpkg reconfigure and reboot still got black screen but lspci -v revealed nvidia-experimental-304 as being loaded so had to uninstall to fall back to nouveau

Think removing xswat ppa then updating, upgrading and then try nvidia-current will get things going.

Yes, ppa-purge the xswat ppa, apt-get purge nvidia-current to be safe, and apt-get install nvidia-current.

---

### Post by awr on 2012-10-23
Geezanansa,

I appreciate your frustration in not getting this to work. Without either a list of previous threads on what you have tried, or new details on your current configuration so we can try to work out what is going wrong from the beginning, I'm afraid you won't get the answer you need.

As sgage mentioned, in the majority of cases it is simply a matter of running "sudo apt-get install nvidia-current", or by using the additional drivers gui that comes with Ubuntu.  If this isn't working for you, then it would be great to work out why, but we need some basic information first.

Ubuntu version = 12.10 ??? (x64 or x32?)
Video card = NVIDIA GeForce GT 520
What ways have you already tried to install drivers?
Have you tried installing the drivers on a fresh/clean install of Ubuntu?
Do you have just the one video card?

---

### Post by sgage on 2012-10-23
> **awr said:**
> Geezanansa,

I appreciate your frustration in not getting this to work. Without either a list of previous threads on what you have tried, or new details on your current configuration so we can try to work out what is going wrong from the beginning, I'm afraid you won't get the answer you need.

As sgage mentioned, in the majority of cases it is simply a matter of running "sudo apt-get install nvidia-current", or by using the additional drivers gui that comes with Ubuntu.  If this isn't working for you, then it would be great to work out why, but we need some basic information first.

Ubuntu version = 12.10 ??? (x64 or x32?)
Video card = NVIDIA GeForce GT 520
What ways have you already tried to install drivers?
Have you tried installing the drivers on a fresh/clean install of Ubuntu?
Do you have just the one video card?

The 'additional drivers' thing has failed for me on more than one occasion. gtk-jockey works most of the time. apt-get install nvidia-current works virtually always.

---

### Post by Geezanansa on 2012-10-23
So now ppa for xswat drivers gone and nvidia-current = 295 driver  nvidia-current does not boot to log in screen.Again what happens is >  post> grub >plymouth but lightdm crashes to black screen (dunno dm) so no log in screen just a black screenThx for input folks and i am running 12.04 32 bit with a gt520 as gpu.


What i am trying to achieve is > Am sure playonlinux launching steam (for windows client) in order to  start Call of Duty 2 from the Steam library list is doable....   
but only if there is a suitable driver being used appropriate to kernel.     I know this is doable but need pointers on how to configure ubuntu, graphics and game launch/console commands but as driver problems persist have decided to post here BEFORE i tried install the latest linux driver from nvidia.


I have tried jockey-common, additional drivers, adding ppas and installing from cli to install many driver versions.  Have installed nvidia drivers direct from nvidia with good results.  until a kernel upgrade that is....  

Have made sure am using the latest linux kernel and kernel header.

I use these forums for guidance and searching for BLACK SCREEN shows this is not unique to nvidia 
This thread has been the most usefull to me so far [http://ubuntuforums.org/showthread.php?t=1743535&highlight=bogan](http://ubuntuforums.org/showthread.php?t=1743535&highlight=bogan)
Thinking that if nouveau works after trying proprietary drivers then all i need to do is install a working driver and since proprietary drivers does not work for me then maybe nvidia driver direct from nvidia is worth a shot again and posted here asking for ubuntu specific advice here after looking at nvidia readme before  trying to install the driveri.e. i asked                 **Is there a definitive, crystal clear, step by step How to NVidia proprietary driver?**

but obviously something is broken....

as stated several times when trying to illustrate ,prove and explain that i understand, know how to and can install nvidia-current  (but it does not boot to log in screen)
what happens at boot time when any driver other than nouveau is used  is > get post> grub >plymouth but lightdm crashes to black screen (dunno dm) so no log in screen just a black screenAre the drivers direct from nvidia's website proprietary?

---

### Post by Geezanansa on 2012-10-23
> Do you have just the one video card? Yes on an asrock alivenf6g vsta mobo.

> Have you tried installing the drivers on a fresh/clean install of Ubuntu?
Not yet.

What/which error logs or other info are the start to diagnosing?

---

### Post by awr on 2012-10-23
> **Geezanansa said:**
> 
**Is there a definitive, crystal clear, step by step How to NVidia proprietary driver?**


There is a ton of information on the net that will tell you how to install the drivers, including various means of resolving issues.  But for the sake of not knowing exactly what you have tried already, try this:

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

> **Geezanansa said:**
> 
as stated several times when trying to illustrate ,prove and explain that i understand, know how to and can install nvidia-current  (but it does not boot to log in screen)
what happens at boot time when any driver other than nouveau is used  is ....


Sorry if we have trouble understanding your level of knowledge, but unless you include ALL the information (including exactly what you have tried, what has failed, etc) we don't know where you are at.  Answers will come quicker if you include all the info to begin with.

As for your particular problem, if you can try it from a clean install of Ubuntu, then we have a base to work from and know what to expect as far as what files are changed etc.  Because you have tried many different methods, it is impossible to tell what is going on in your system.  If this is not possible, then either your answer may take longer or you may not get a working answer.

If you can't try on a fresh install, then I would suggest checking and perhaps posting some system logs and Xorg config files so we can work out where your system is failing.

---

### Post by Geezanansa on 2012-10-23
Thanks awr
Installing ubuntu 12.04 lts 32 bit onto its own hdd then updating and then installing nvidia-current (by cli from 3d desktop session) uses the recommended  driver as indicated in gkjockey(additional drivers).

Can confirm in 3d session as launcher icons can be resized.  

> 02:00.0 VGA compatible controller: NVIDIA Corporation GF119 [GeForce GT 520] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: ZOTAC International (MCO) Ltd. Device 3214
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at df000000 (32-bit, non-prefetchable) [size=16M]
    Memory at d0000000 (64-bit, prefetchable) [size=128M]
    Memory at dc000000 (64-bit, prefetchable) [size=32M]
    I/O ports at ec00 [size=128]
    [virtual] Expansion ROM at def80000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidia_current, nouveau, nvidiafb


Everything seems to be behaving as expected on a clean install.

Not connected other hdd yet so will get it hooked up...

---

### Post by Geezanansa on 2012-10-24
> Are the drivers direct from nvidia's website proprietary?
> There is a ton of information on the net that will tell you how to  install the drivers, including various means of resolving issues.  But  for the sake of not knowing exactly what you have tried already, try  this:
[http://https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](http://https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia) 

no. closed source.   soz

Thank you- that answers that then...

Have  had success with binary drivers in passed as with proprietary drivers.   But just starting to grasp concept of sym links, dependencies  runlevels... i.e. configuring hardware/os.  Proprietary drivers were not  behaving as expected so wanted to go for installing  closed drivers  just  to try other options.  some people sacrifice wobbly windows(ccsm)  to get their games going by using binary drivers as they perform better  for the purpose of running game...  apparently! 
 It seems to be a  compromise of fixing one thing to break something else.... in order to  achieve playing games(or anything else it seems....that is if it is not  installed from ubuntu software centre)

Are there any  steam users (windows client) out there that use ubuntu to play their games that could share how to get going ?  ooh that could be the title of my next thread..

---

### Post by vanquishedangel on 2012-10-24
I don't know if this helps or not but I used to have many issues with ATI cards that are similar to what you are experiencing here in this thread so i will explain the best I can the different scenario's that may help you find an answer.

When you install from the website you get a .run file, This file does not uninstall until you tell it to plus you need to uninstall the opensource drivers as well. Since it is not a .deb file or from the repos, the system will not uninstall it. This leads to conflicting drivers and a crash usually and both need to be uninstalled and the one you want reinstalled, this can be a hassle. You will need to look up how to uninstall the driver from the website.

A post I read before contained the experimental file that leads me to believe that most likely you guys with this issue have bits and pieces of other drivers trying to use the same resources, If the .run driver is installed it is trying to run the card along side what bits of the opensource one you have installed, or if you installed the proprietary ones with jockey some may be left.

also the tools bleachbit and deborphan were helpful in clearing up alot of left over crap as well but use at your own risk, I also run upgrade-system as well as it sanitizes the system, again your own risk but they help immensely with getting bits and pieces out. also run "sudo apt-get autoremove".

Jockey also offered the newer drivers and a set of older ones, for ati anyway but there was a glitch with installing the newer ones, that may also be the case for nvidia so use the older ones if offered.

Sorry I cannot give a definate way to do it as I havent had the issue in a long time also I have always had ATI.

---

### Post by Geezanansa on 2012-10-24
And finally...
here is a quote a member of the public made in the comments in the faster zombies article at steam on linux blog [http://blogs.valvesoftware.com/linux/faster-zombies/](http://blogs.valvesoftware.com/linux/faster-zombies/) that was referred to earlier in this thread

> n terms of the driver to be used for gaming, the AMD and Nvidia  drivers are closed source (there are open drivers but they’re not in a  usable state for gaming yet), and the Intel one is open-source, but  Intel has never made a “gaming” GPU until their recent generations of  CPUs. So basically, I’d love to see any discussion on whether Intel is a  viable option for gaming on Linux, so that you don’t need to mess around  with binary-only display drivers.
 Also, if you have any feedback to the AMD open-source team or the  community that do the Noveau driver I’m sure they’d love to hear from  you [IMG]http://blogs.valvesoftware.com/wp-includes/images/smilies/icon_smile.gif[/IMG] 



Actually found these comments on that blog one of the more constructive sources of getting things into some kind of perspective.  Certainly makes me appreciate ubuntu more...
Huge...  .huge undertaking  
There was a BBC documentary(Horizon-senses) that tried to explain how a computer renders graphics and showed how similarly our own brains worked in order for light from our eyes be rendered in our mind .  
so close

Is this the matrix?

maybe in couple years time we all have apu implants and running ubuntu

---

### Post by Geezanansa on 2012-10-24
Thx vanquishedangel for posting  .  Have been getting braver in cli,  chopping and changing hardware  config  as well as multibooting with windows 8 and trying out onboard  graphics  just for curiousity sake.....  and installing an older lexmark  printer. All  have not helped  in preventing the current situation.        
Think in 12.10  dkms can take care of nvidia updates (when you  driver is installed.)  or that is the plan (depend on kernel and  driver)!?

Jockey is used for additional drivers = current/new(add ppa = newer) drivers
Jockey-common is used (run by jockey-text from cli) to load older drivers into Jockey(additional drivers) list.
Which could prove handy for running some games like doom and the first call of duty

Steam for linux is coming to 12.04 soon as beta (for a  lucky few)  Have two installations now side by side : one  being nouveau  ONLY and the other a fresh install with nvidia-current(system  recommended)ANY

 Both are  ubuntu 12.04 32 bit.

Any body  have good results with launching steam games in ubuntu?  After clean  install what would be process to get everything working to launch steam  games?
Have tried wine with some success but better results with playonlinux and the game Call of Duty 2 which has many positive test results at  appdb

Still did not get those log files uploaded to try and shed some light on what could be stopping/breaking driver installation on that other drive but will do.


 would i be on the right line of thinking of  a proprietary driver as a  driver that has been modified by the owner/provider to allow use of by a  third party as agreed with provider and third party  or
nvidia  adjust their driver for use by ubuntu before passing it on to ubuntu  (users) so ubuntu cannot do their own tweeking before passing it on  because that is not the agreement.         any card player does not want  to show their hand all the time....
but if you aint playing cards; why not?

---

### Post by bogan on 2012-10-24
Hi!, Geezanansa,

I fully understand your difficulty in finding "**a definitive, crystal clear, step by step How to NVidia proprietary driver",** as the advice in the forum is so conflicted and personalised.

I also run an nvidia GT 520 on one Desktop, and an nvidia GT 7650 on another, on each I run two versions of the latest release of Ubuntu [ as well as 10.04,11.10, & 12.04.1]. 

Because of trouble in the past, similar to your experience, I deliberately run one as a new direct install using the default [nouveau/Gallium] drivers , and the other being updated, originally from 9.10, using the proprietary nvidia drivers: [ Until 12.10, I always used the nvidia.com downloaded .run files and had no problems with them, but all manner of problems with the various nvidia-current drivers, especially with Ubuntu 12.04.]

I suspect a lot of your problems arise from the 295.40 and 295.49 nvidia-current drivers that are still being offered with 12.04, despite being notoriously & seriously bugged.** Edit:** I see that, in 3.2.0-33 at least, nvidia-current is now 304.51,actually 304.48, although 295.40 is still there as nvidia-current-dev!!

The later nvidia.com drivers >=304.xx are DKMS compatible and the previous need to re-install after a kernal update, no longer obtains.

I would strongly recommend installing 12.10,  despite the problem of the missing Linux-headers file, and repeated 'Apport' error messages.

As to your Thread title question,  I am sending my attempt to provide one as a separate Post.

Caveat: I don't do gaming - apart from Flight SimulatorX - so although the GT 520 works perfectly in Unity 3D with nouveau, nvidia, nvidia-current[304] and nvidia-current-updates drivers on 12.10, that does not necessarily mean it will meet your Steam/Gaming requirements.

Chao!, **bogan**.

---

### Post by bogan on 2012-10-24
Hi!, **All**,

Right, so here is the full version of: 'How To Install Nvidia Drivers'. [ Slightly modified 29/10/2012]

Nvidia drivers for Linux come in various forms; directly downloaded from the Nvidia.com/Drivers website, or modified by Ubuntu as 'nvidia-current' and down loaded from a PPA . This guide is mainly concerned with the first, and installation via a Terminal.

_*Ubuntu nvidia-current drivers.*_
To install the Ubuntu modified drivers called nvidia-current and variants, the same preparatory steps should be taken, but omit stage 3.; and at stage 5, use:```
 sudo apt-get install nvidia-current # or nvidia-current-updates
``` Nvidia-current drivers can also be installed from System Settings>Additional Drivers. From Ubuntu 12.10, 'Additional Drivers ' is included in Software Sources. You can Right-Click on the Desktop, select 'Change Desktop Background', click the 'All  Settings' tab, select 'System>Software Sources' and the 'Additional Drivers ' tab, and Activate the driver you want.

[The following is based on Post #280 of MAFoElffen's Blank Screen magnum-opus Sticky in the Installations & Upgrades Forum.]
[http://ubuntuforums.org/showthread.php?t=1743535&page=109](http://ubuntuforums.org/showthread.php?t=1743535&page=109)

_* Summary.*_
 Under normal circumstances, this is all you need to do to install an nvidia.com downloaded driver:

 Reboot to a 'TTY' [Text Terminal or Text Console], or shut down the Xsession from a GUI screen, as the nvidia driver must be installed when the Xserver and GUI screen are inactive. Then CD to the folder where you have downloaded the NVIDIAxxx.run file, make it executable and run it with 'sh'.

_*Preparation*_.
However, the first time you do this there are some preparatory steps: first you should add some Blacklists to the /etc/modprobe.d folder; then ensure the necessary build procedures and header files are installed, and it is also advisable to purge any previous nvidia installations. 

_* Adding blacklists: *_
**Note: T**here may  already be nouveau blacklist files in /etc/modeprobe.d. Recent versions, v.304 onwards, of both the nvidia-installer and the Ubuntu-nvidia-current installations can create files blacklisting the default Nouveau driver so Stage 1. can be omitted. The Nvida installer will offer to create a blacklist file.

1.: Add blacklists, [ For drivers prior to v.304 ]:
In a Terminal ['Crtl+Alt+t'] enter:```
 gksudo gedit /etc/modprobe.d/nouveaublacklist.conf # If you do not have access to a GUI Screen 
# you will need to use a different text editor, eg. 'nano' or 'vim'.
```If the file does not exist, gedit will show a blank screen with that name, add:```
 # Added for nvidia driver.
blacklist nouveau
blacklist lbm-nouveau
options nouveau modeset=0
alias nouveau off
alias lbm-nouveau off
```Save and close gedit.[ The filename you use must end in: '.conf' ]

2.: Prep and make sure everything is there for any dependencies, and Cleanup:
Ensure you have fully updated your installation.
```
sudo apt-get update
sudo apt-get install build-essential gcc-4.5 g++-4.5 libxi-dev libxmu-dev freeglut3-dev
uname -r
```Insert the output of 'uname -r' in the following command: substituting it for 'uname -r'; for example:
"sudo apt-get install linux-headers-3.2.0-233-generic-pae"```
sudo apt-get install linux-headers-'uname -r'
sudo apt-get install linux-headers-generic
sudo nvidia-installer --uninstall # not needed if no prior nvidia-installation 
sudo apt-get remove --purge nvidia*
```You may get some 'file not found' messages on the last commands. That is okay. Continue. We just want to make sure that older modules are removed so that there is no conflict.

3.: _*Download.*_  [ Omit if choosing the nvidia-current driver]
Down load the appropriate driver from nvidia.com/Drivers:
[http://www.nvidia.co.uk/object/linux...driver-uk.html](http://www.nvidia.co.uk/object/linux...driver-uk.html) That is for the 32.bit version, make sure you have the correct one for your GPU.

If you do not know which GPU/Video card you have, run:```
lspci | grep -1A vga
```4. _*Stopping the Graphics session.*_
To install the downloaded driver, Xorg cannot be running. You need to shut down the X-Session. In a TTY , [ 'Ctrl+Alt+F1' ] or Terminal, enter:```
sudo service lightdm stop # If using 10.10 or earlier use 'gdm' in place of 'lightdm'
```You will get a black screen; if it does not have a login prompt, to get one, press 'Ctrl+Alt+F1' [or F2-F6], login, enter your password.[ It will not show, just type it & press 'Enter'] If you need to return to the GUI screen, press: 'Ctrl+Alt+F7' but first, run:```
sudo service lightdm start
```_*Alternatively,*_ reboot into the drop-down recovery menu, run 'Fsck' to set system to Read/Write, and drop to a Text Console and login:
In this case you should enter:```
 telinit 3 # to set system level.
```5.:_* Installing the driver.*_ If choosing an nvidia-current driver, see the second paragraph above, and skip to Stage 6.

In the following substitute the correct file name:

Change directory [cd] to the directory where you saved the nvidiaxxx.run file, for example:```
 cd /home/username/Downloads
ls 
```Running 'ls' will confirm you are in the right place and you can be sure the spelling is correct - entering 'NV' and pressing 'Tab' will Auto-complete the file name.

Mark the downloaded file as executable:```
sudo chmod a+x NVIDIA-Linux-x86-3.04.60.run
```Run the file to Install drivers:```
sudo sh NVIDIA-Linux-x86-304.60.run
```You may get an error message about a failed script, continue, accept the options, navigating by using 'Tab' and pressing 'Enter'.

6.: When complete, reboot,```
 sudo reboot
```If necessary edit the grub boot menu script, by pressing 'e' with the boot option highlighted and entering 'nomodset' after 'splash ' in the Linux line where it shows "ro quiet splash ", and pressing 'Ctrl+x' to boot.

7.: In case of difficulty you may need to run: sudo apt-get install --reinstall ubuntu-desktop # or:
sudo dpkg-reconfigure nvidia-current*

Chao!, **bogan**

---

### Post by Geezanansa on 2012-10-24
Thank you bogan .  Started following instructions to go for installation of the nvidia binary drivers from their website but...


Was unsure of what was meant by "text terminal" in order to start from step one of your guide so did a quick google and followed this guide [http://http://rolling-ubuntu.blogspot.co.uk/2012/06/ubuntu-1204-tip-booting-to-text-mode.html]("http://http//rolling-ubuntu.blogspot.co.uk/2012/06/ubuntu-1204-tip-booting-to-text-mode.html")  Running "gksudo gedit  /filename"  from text mode/terminal gives "Gtk warning cannot open display. "     Tried loading tty (ctrl+alt+F1) at log in screen but unsure how to mount ubuntu from tty.  Did not try tty from within desktop session.(x server could still be running even if lightdm stoppped)-- (edit no Text Terminal till step 4 of instructions. Steps 1-3 from desktop session)

Here is a quote from nvidia readme regarding /etc/modprobe.d/blacklist.conf
> **How do I prevent Nouveau from loading and performing a kernel modeset?**
    
 A simple way to prevent Nouveau from loading and performing a kernel modeset is to add configuration directives for the module loader to a file in /etc/modprobe.d/. These configuration directives can technically be added to any file in /etc/modprobe.d/, but many of the existing files in that directory are provided and maintained by your distributor, which may from time to time provide updated configuration files which could conflict with your changes. Therefore, it is recommended to create a new file, for example, /etc/modprobe.d/disable-nouveau.conf, rather than editing one of the existing files, such as the popular /etc/modprobe.d/blacklist.conf. Note that some module loaders will only look for configuration directives in files whose names end with .conf, so if you are creating a new file, make sure its name ends with .conf.
 Whether you choose to create a new file or edit an existing one, the following two lines will need to be added:
 blacklist nouveau options nouveau modeset=0No right or wrong way just food for thought....  maybe first option may better improve nvidia updates working

---

### Post by bogan on 2012-10-24
Hi!, **Geezanansa,** Thanks for the feedback, I have edited Post #19 to clarify the points you raised.

There is always the problem of trying to include all the points of one's own knowledge and experience, and foresee what others might encounter, whilst not creating  vast tracts, or risking being seen as condescending to those who class themselves as 'noobies'.

A 'Text Terminal' is a 'TTY' or a 'Text Console', or 'Shell' but one in which the Gui Screen is not used. Once again the curse of different terms being used for the same thing, and the same name being used for different things.

You are correct that I had missed the case of a reader who had no access to a GUI Screen, and would need to use another  text editor, not 'gedit'; such as 'nano' or 'vim'. As I have never used either of those, perhaps someone who has will correct me if they do not both work without a GUI.

I was aware of the passage you quote from Nvidia, and I have added the 'option nouveau modeset=0' line to the blacklist entry. Though in past experience it has never been needed, and was not included in the blacklist file that nvidia-installer itself created, nor is it included in the blacklist files created by nvidia-current.

Please do not hesitate to Post any further points of doubt or confusion, omission or error, that you find.

Chao!, **bogan**.

---

### Post by bogan on 2012-10-24
Hi!, again **Geezanansa,**

You Posted:>   Did not try tty from within desktop session.(x server could still be running even if lightdm stoppped).Whilst there have been Posts reporting 'sudo service lightdm stop' and other alternative lightdm commands, failing to stop the Xorg server - and I one time experienced this myself - that was not normal, and is an assumed bug occaisionally occurring in lightdm.

When it happened to me, I rebooted and then lightdm worked  as it should.

Chao!, **bogan.**

---

### Post by Geezanansa on 2012-10-24
Big Thank you bogan 

With regard your last post; would installed apps or anything else installed that  gets started up at boot have an effect on this?


What is difference between nouveau modeset 0 and options nouveau modeset 0?

---

### Post by bogan on 2012-10-24
Hi!, again,   Whoops!! My typo - corrected. 

Edit: Regarding your first question in Post #23 I would think not, but it might if it interacted with Compiz or unity greeter. I have had a lot of Apport errors with both lightdm and the greeter so anything is possible.

Chao!, bogan.

---

### Post by Geezanansa on 2012-10-24
With regard to etc/modprobe.d/blacklist.conf how about highlighting concern if anything else is in that file.  Renaming to anything you think would be suitable i.e. disable-nouveau.conf is suggested.  You do explain that that if white page comes up then gedit just made a fresh file for you which would confirm whatever the file name is it is good for purpose.

The point i raise is mentioned at Chapter 8.1. Interaction with the Nouveau Driver here [http://uk.download.nvidia.com/XFree86/Linux-x86/304.60/README/commonproblems.html#nouveau](http://uk.download.nvidia.com/XFree86/Linux-x86/304.60/README/commonproblems.html#nouveau)

Chao the now!

---

### Post by bogan on 2012-10-24
HI1,Geezanansa,

My current blacklist.conf file contains 19 items, including the nouveau and 4 legacy nvidia items, none of them [apart from the later, appear to me to have anything to do with video or xorg matters, and it has not produced any side effects Iam aware of; so I tended to discount nvidia's warning as a bit over-zealous.

On the other hand, having the nouveau blacklist in its own file would make it easier to revert to the nouveau driver, later on, if that were desired.

I am also wary of making things over-complex and intimidating. I'll think it over.

After-all, under most circumstances the only part you need to use, - after the first time - is: > To Install the nvidia driver it is necessary to reboot to a 'TTY' [Text  Terminal or Text Consol], or shut down the Xsession from a GUI screen,  as the nvidia driver must be installed when the Xserver and GUI screen  are inactive. Then CD to the folder where you have downloaded the .run  file, make it executable and run it with 'sh'.Chao!, **bogan**.

---

### Post by Geezanansa on 2012-10-24
> After-all, under most circumstances the only part you need to use, - after the first time - is:  	Quote:
 	 	 		 			 				To Install the nvidia driver it is necessary to reboot to a 'TTY'  [Text  Terminal or Text Consol], or shut down the Xsession from a GUI  screen,  as the nvidia driver must be installed when the Xserver and GUI  screen  are inactive. Then CD to the folder where you have downloaded  the .run  file, make it executable and run it with 'sh'. 			 		

Yep it is that simple.
It is simple .  Nice one bogan you just made something very intimidating appear very useful.

---

### Post by Geezanansa on 2012-10-24
bogans posts at  #18  and #19  in this thread and in [http://ubuntuforums.org/showthread.php?t=1743535&highlight=resolution+blank+screen ]("http://ubuntuforums.org/showthread.php?t=1743535&highlight=resolution+blank+screen")
are what has worked for me. The troubleshooter at the start of the other thread is brilliant.  Simple and effective. Thx op.
Now running the .run drivers and using the above resources to sort out another machine that is using vesa drivers and running 12.04  32bit  Desktop 3.2.0-32 -generic-pae.

---

### Post by bogan on 2012-10-25
Hi!,** Geezanansa**,

As a matter of interest, I checked out the /etc/modprobe.d folder in the installation  in which I run the nvidia-current-updates driver from the x-swat ppa.

There are two files of identical date & creation time, both created by nvidia-current, one is called:"nvidia-graphics-drivers.conf" and contains:>  # This file was installed by nvidia-current-updates
# Do not edit this file manually

blacklist nouveau
blacklist lbm-nouveau
blacklist nvidia-173
blacklist nvidia-96
blacklist nvidia-current
blacklist nvidia-173-updates
blacklist nvidia-96-updates
alias nvidia nvidia_current_updates
alias nouveau off
alias lbm-nouveau offThe other called: "nvidia-current-updates_hybrid.conf " is the same, but omits the legacy nvidia blacklists.

I have modified the list in Post #19 to include the extra nouveau entries, but not the nvidia alias entry, as I do not know what effect that would have with an nvidia.com downloaded driver.

Note that neither includes the "options nouveau modeset=0" entry, though, in another installation, the file created by a recent version of nvidia-installer, does include it.

Actually this info makes the creation of further blacklists redundant.

I have also made a few other changes to clarify things a bit - I hope.

Your comments - or those from anyone else reading this - welcomed.

Chao!, **bogan.**

---

### Post by Geezanansa on 2012-10-25
nice timing!

---

### Post by Geezanansa on 2012-10-25
Getting closer to following your instruction to a t bogan!  
Have not had proposed updates activated in software centre so that is why previously have been refering to 12.04  32bit  Desktop 3.2.0-32 -generic-pae where as the advice and instruction bogan gives at posts #18 and #19 refer to 3.2.0-33 -generic-pae.

 The way i read instruction  at step 2 and after updating  ```
ubuntu-user@ubuntuuser-desktop:~$ sudo apt-get install build-essential gcc-4.5 g++-4.5 libxi-dev libxmu-dev freeglut3-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
build-essential set to manually installed.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 freeglut3-dev : Depends: libgl1-mesa-dev but it is not going to be installed or
                          libgl-dev
                 Depends: libglu1-mesa-dev but it is not going to be installed or
                          libglu-dev
E: Unable to correct problems, you have held broken packages.
ubuntu-user@ubuntuuser-desktop:~$ uname -r
3.2.0-33-generic-pae

```

---

### Post by bogan on 2012-10-25
Hi!,** Geezanansa**,

I typed out a long repentant response to your sad Post only to have Firefox crash an loose it.

So this is a rather different reply, in view of what i found after typing most of it.

The command line was a direct copy/paste from MAQFoElffen's Post #280 and I checked it against your Post and it it is correct.

I then ran the line in my machine, without the last item: "freeglut3-dev", and it installed without trouble - some 96 MB of download - I then ran:```
 sudo apt-get install freeglut3-dev 
```on its own and that installed perfectly OK as well.

So the problem is not in the command line, but must be in your installation.

I can only suggest you run ```
sudo apt-get install -f
sudo dkpg-reconfigure -a
``` and assuming that does throw up any errors, run the command line again, first leaving off the last item, and then with just 'freeglut3-dev'.
**EDIT: **dkpg option was wrongly '-f', changed to '-a' [all]

'dpkg' comes with a warning that it may take a long time - I've had it take from 12 to 25 minutes, and can run with no signs anything is going on - just wait it out - equally, it can run in an interactive mode demanding you choose a whole series of alternatives - I choose the all the defaults or an empty script boxes and it went OK.

Good-luck!  Chao!, [B]bogan.
Edit:
Extract from my terminal:
[/B]> Unpacking libgl1-mesa-dev (from .../libgl1-mesa-dev_9.0-0ubuntu1_i386.deb) ...
Selecting previously unselected package libglu1-mesa-dev.
Unpacking libglu1-mesa-dev (from .../libglu1-mesa-dev_9.0.0-0ubuntu1_i386.deb) ...
Selecting previously unselected package freeglut3-dev:i386.
Unpacking freeglut3-dev:i386 (from .../freeglut3-dev_2.6.0-4ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Setting up freeglut3:i386 (2.6.0-4ubuntu1) ...
Setting up libdrm-dev (2.4.39-0ubuntu1) ...
Setting up mesa-common-dev (9.0-0ubuntu1) ...
Setting up libx11-xcb-dev (2:1.5.0-1) ...
Setting up libxcb-glx0-dev:i386 (1.8.1-1ubuntu1) ...
Setting up x11proto-fixes-dev (1:5.0-2ubuntu1) ...
Setting up libxfixes-dev (1:5.0-4ubuntu5) ...
Setting up x11proto-damage-dev (1:1.2.1-2) ...
Setting up libxdamage-dev (1:1.1.3-2build2) ...
Setting up x11proto-xf86vidmode-dev (2.3.1-2) ...
Setting up libxxf86vm-dev (1:1.1.2-1) ...
Setting up x11proto-dri2-dev (2.8-1) ...
Setting up x11proto-gl-dev (1.4.16-1) ...
Setting up libgl1-mesa-dev (9.0-0ubuntu1) ...
Setting up libglu1-mesa-dev (9.0.0-0ubuntu1) ...
Setting up freeglut3-dev:i386 (2.6.0-4ubuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
alan@alan-MS-7616:~$ 

---

### Post by Geezanansa on 2012-10-25
Thanks bogan

> I typed out a long repentant response to your sad Post only to have Firefox crash an loose it.  Thats funny that makes at least two conscientious posters in same thread.  

I think on this install of 12.04 3.2.0-33 what is happening when the blacklist file is written to stop nouveau is that Vesa drivers are being loaded (until nvidia is installed...)which gives the failing dependencies for freeglut3-dev.

Was just going to try sudo apt-get install   libgl1-mesa-dev & & libglu1-mesa-dev but did a google for libgl1-dev and checked additional drivers and system details which confirmed at this stage Vesa drivers were being used and nvidia 310 is available.(kernel update!?)

How tempting it was to try the threeten

But before trying that i just deleted the contents of /etc/modprobe.d/nouveaublacklist and rebooted which gives desktop using Gallium=mesa drivers.

So am ready to try from step one again.

What i have been learning today means that the other 12.04(3.2.0-32 fresh install)with the nvidia.run  drivers will be getting uninstalled.  Ubuntu Software Centre is for .....   software used by ubuntu!?

---

### Post by Geezanansa on 2012-10-25
How to confirm what gets blacklisted?
How to confirm what dependencies to install?

Looking at post 280 in our favourite thread made me decide to  just better let ubuntu decide.

Is blacklisting nouveau really a good idea if you want to use ubuntu as os?

After deleting the added blacklist file contents, rebooting and then just clicking on additional drivers  and selecting which ever driver (i chose 310)  then reboot.

On being presented with a beautifully sparkly login and desktop launched game from terminal and then well  it just worked.  And worked beyond expectations, amazingly so.. Keyboard controls worked fine but could not get xbox controller configured and working through game options so disabled gamepad in the game options then closed the game.  Loaded xboxdrv with mapping for game then launched game from terminal.

To achieve (more than)what i started this thread for ..
It is simple as installing ubuntu, update, reboot, add proposed updates, update, upgrade to up date to  kernel 3.2.0-33, reboot, update, select the driver of your choice from additional drivers, reboot and enjoy.

Now i will leave you all in peace and quiet as my reward for time and effort put into this is a fully working pc and have a slightly better understanding of the complexities of using  open source , closed source or proprietary drivers.   

It has to be said the results have far exceeded the results for any previous attempts as well as just installing i.e. just click n play baby oooh yeah!   Not unless there has been an onvisible  helping hand.
The times are a changin
Can not thank you enough for your time and patience bogan.  chao!

---

### Post by bogan on 2012-10-26
Hi!, **Geezanansa.**

Great!!  Glad you achieved what you wanted. I went through a very similar learning experience a couple of years ago, I am sure it will stand you in good stead.

Edit2: I have further modified the 'Guide' to make the blacklisting optional. as it seems clear the act of installation will do it anyway.

BTW: There was a typo in my last Post that I have corrected:> I can only suggest you run:    ```
 sudo apt-get install -f
 sudo dkpg-reconfigure -a 
``` and assuming that does throw up any errors, run the command line  again, first leaving off the last item, and then with just  'freeglut3-dev'.
**EDIT1: **dkpg option was wrongly '-f', changed to '-a' [all]. All the Best, Chao!. **bogan**.

---

### Post by bogan on 2012-10-30
**Re: How To Install Nvidia Drivers**

*Here is the latest version . [ Edited 30/10/2012]*

Nvidia drivers for Linux come in various forms; directly downloaded from  the Nvidia.com/Drivers website, or modified by Ubuntu as  'nvidia-current' and down loaded from a PPA . This guide is mainly  concerned with the first, and installation via a Terminal.

_*Ubuntu nvidia-current drivers.*_
To install the Ubuntu modified drivers called nvidia-current and  variants, the same preparatory steps should be taken, but omit stage 3.;  and at stage 5, use:```
sudo apt-get install nvidia-current # or nvidia-current-updates 
```Nvidia-current drivers can also be installed from System  Settings>Additional Drivers. From Ubuntu 12.10, 'Additional Drivers '  is included in Software Sources. You can Right-Click on the Desktop,  select 'Change Desktop Background', click the 'All  Settings' tab,  select 'System>Software Sources' and the 'Additional Drivers ' tab,  and Activate the driver you want.

[The following is based on Post #280 of MAFoElffen's Blank Screen magnum-opus Sticky in the Installations & Upgrades Forum.]
[http://ubuntuforums.org/showthread.p...43535&page=109]("http://ubuntuforums.org/showthread.php?t=1743535&page=109")

_* Summary.*_
 Under normal circumstances, this is all you need to do to install an nvidia.com downloaded driver:

 Reboot to a 'TTY' [Text Terminal or Text Console], or shut down the  Xsession from a GUI screen, as the nvidia driver must be installed when  the Xserver and GUI screen are inactive. Then CD to the folder where you  have downloaded the NVIDIAxxx.run file, make it executable and run it  with 'sh'.

_*Preparation*_.
However, the first time you do this there are some preparatory steps:  first you should add some Blacklists to the /etc/modprobe.d folder; then  ensure the necessary build procedures and header files are installed,  and it is also advisable to purge any previous nvidia installations. 

_* Adding blacklists: *_
**Note: T**here may  already be nouveau blacklist files in  /etc/modeprobe.d. Recent versions, v.304 onwards, of both the  nvidia-installer and the Ubuntu-nvidia-current installations can create  files blacklisting the default Nouveau driver so Stage 1. can be  omitted. The Nvidia installer will offer to create a blacklist file.

1.: Add blacklists, [ For drivers prior to v.304 ]:
In a Terminal ['Crtl+Alt+t'] enter:     ```
gksudo gedit /etc/modprobe.d/nouveaublacklist.conf # If you do not have a GUI
# Screen you will need to use a different text editor, eg. 'nano' or 'vim'. 
```If the file does not exist, gedit will show a blank screen with that name, add: 
      ```
# Added for nvidia driver. 
blacklist nouveau 
blacklist lbm-nouveau 
options nouveau modeset=0 
alias nouveau off 
alias lbm-nouveau off 
```Save and close gedit.[ The filename you use must end in: '.conf' ]

2.: Prep and make sure everything is there for any dependencies, and Cleanup:
Ensure you have fully updated your installation.```
sudo apt-get update
 sudo apt-get install build-essential gcc-4.5 g++-4.5 libxi-dev libxmu-dev freeglut3-dev 
uname -r 
```Insert the output of 'uname -r' in the following command: substituting it for 'uname -r'; for example:
"sudo apt-get install linux-headers-3.2.0-2-33-generic-pae"```
sudo apt-get install linux-headers-'uname -r'
sudo apt-get install linux-headers-generic
sudo nvidia-installer --uninstall # not needed if no prior nvidia-installation
sudo apt-get remove --purge nvidia* 
```You may get some 'file not found' messages on the last commands.  That is okay. Continue. We just want to make sure that older modules are  removed so that there is no conflict.

3.: _*Download.*_  [ Omit if choosing the nvidia-current driver]
Down load the appropriate driver from nvidia.com/Drivers:
[http://www.nvidia.co.uk/object/linux...driver-uk.html](http://www.nvidia.co.uk/object/linux...driver-uk.html) That is for the 32.bit version, make sure you have the correct one for your GPU.

If you do not know which GPU/Video card you have, run:```
lspci | grep -1A vga 
```4. _*Stopping the Graphics session.*_
To install the downloaded driver, Xorg cannot be running. You need to  shut down the X-Session. In a TTY [Text Terminal] , [ 'Ctrl+Alt+F1' ] or Terminal,  enter:```
sudo service lightdm stop # If using 10.10 or earlier use 'gdm' in place of 'lightdm' 
```You will get a black screen; if it does not have a login prompt,  to get one, press 'Ctrl+Alt+F1' [or F2-F6], login, enter your password.[  It will not show, just type it & press 'Enter'] If you need to  return to the GUI screen, press: 'Ctrl+Alt+F7' but first, run: ```
sudo service lightdm start 
```_*Alternatively,*_ reboot into the drop-down recovery menu, run 'Fsck' to set system to Read/Write, and drop to a Text Console and login:
In this case you should enter: ```
telinit 3 # to set system level. 
```5.:_* Installing the driver.*_ If choosing an nvidia-current driver, see the second paragraph above, and skip to Stage 6.

Change directory [cd] to the directory where you saved the nvidiaxxx.run file, for example:```
cd /home/username/Downloads 
ls 
```Running 'ls' will confirm you are in the right place and you can  be sure the spelling is correct - entering 'NV' and pressing 'Tab' will [/should] Auto-complete the file name.

[In the following substitute the correct file name:]

Mark the downloaded file as executable:     ```
sudo chmod a+x NVIDIA-Linux-x86-3.04.60.run 
```Run the file to Install drivers: ```
sudo sh NVIDIA-Linux-x86-304.60.run 
```You may get an error message about a failed script, continue,  accept the options, navigating by using 'Tab' and pressing 'Enter'.

6.: When complete, reboot, ```
sudo reboot 
```7.: In case of difficulty:
If necessary edit the grub boot menu script, by pressing 'e' with  the  boot option highlighted and entering 'nomodset' after 'splash ' in  the  Linux line where it shows "ro quiet splash ", and pressing 'Ctrl+x'  to  boot.

You may need to run one or more of: ```
sudo apt-get install --reinstall nvidia-common # for nvidia cards  5xxx FX or earlier
sudo apt-get install --reinstall ubuntu-desktop
sudo dpkg-reconfigure nvidia-current*
```[I][Revised: 30/10/2012]
[/I]
Chao!, **bogan**

---

### Post by bogan on 2012-11-15
Hi!, **All,**

 RE:** Warning**! Nvidia beta driver 310 does not support 6xxx series cards, and Nvidia warns it may ignore 7xxx series GPU's.

The same, presumably, applies to the **Additional Drivers 'nvidia-experimental-310' **driver, as well.

I have been running, successfully, the 310.14 driver, with 12.10  Quantal, on an 8GB USB SanDisk, in a computer with a GeForce GT 520  card. That is an nvidia.com downloaded '.run' file.

I transferred the USB to a computer with a GT 7650 card and its graphics  were a total shambles, with a GUI in a very low-res with huge  characters & Mouse cursor, but no launcher or tool bar panel.[  Nouveau was blacklisted.]

When I ran:```
NVIDIA-Linux-x86-310.14.run --latest
``` it listed  310.14 as installed, and 310.16 as the latest available. { Incidently,  310.16 is not listed as an available Beta driver on the nvidia website,  though the whole 7xxx series is listed as supported by 310.14 beta, but  not the 6xxx series}.

However, when I tried to reinstall 310.14, I got a message saying no  graphics card had been detected that was supported by 310.14, and if  installed it would ignore my GPU; ie. the GT 7650. It recommended I  install 304.60.

So if you have a 6000 or 7000 series video card watch out.

Chao!,** bogan**.

---

### Post by Geezanansa on 2012-12-08
>  
So if you have a 6000 or 7000 series video card watch out

Suggest making that read "If you have NVidia hardware watch out":p
 
```
lpci -nnk | grep -iA2 vga 
```gives card and ```
dpkg -l | grep -i NVidia 
```gives drivers 
 
Have been going for install of 304.63.run install and met the freeglut3-dev dependency problem again. Running the commands bogan suggests did not fix broken packages. This did not stop me trying for driver install - which gave no errors but on reboot was unacceptable as usable so uninstalled again. When uninstalling 304.63 there was a reference to opengl1.0 library being left as is. Is libgl1-mesa-dev opengl1.0 related? I wonder!
 
Doing a quick google and doing what machine telling me to I tried installing libgl1-mesa-dev which  doing a quick google for gave libgl1-mesa-dri  as one of the few dependencies so trying to uninstall that gave ```
The following packages will be REMOVED libgl1mesa-dri* steam* Ubuntu-desktop* xorg*
```
 
:)   Using ubuntu software centre to search for libgl1-mesa and removed the only entry- libgl1-mesa-glx then tried for install of freeglut3-dev again.  Using terminal  apt-get is asking for freeglut3 but it is not going to be installed.(as well as other dependencies mentioned at #31)
Something is broken and it probably opngl related. hmmm
 
Using Ubuntu software center to install freeglut3 works! but not freeglut3-dev
 
and I blacklisted nouveau so have nice psychadellic stripey wall paper!
 
ttfn

---

### Post by Geezanansa on 2012-12-09
Thx bogan for sharing some of the things "to be expected" after installing nvidia.run and highlighting how things do change over any given time period.  Keyboard shortcuts will allow navigation/use of ubuntu. Have had the problem of jockey not reporting accurately if drivers installed from terminal. i.e. if ```
sudo apt-get install nvidia-current
``` reboot and then open additional drivers there is no green indicator showing nvidia-current as active.  They both should report same right?

So after getting back to nouveau now have a reasonably good looking and acting ubuntu.
Replacing ubuntu-desktop from tty and a couple of reboots was all that was needed.

After having driver probs in 12.04 went for nvidiaxxx.run install and came here after skimming through though thought it might be worth trying nvidia304.run by simply downloading and installing.  Have documented some of the observations made and here is how the installer sees things [ATTACH]228416[/ATTACH] And straight off am asking Does the kernels and kernel commands look right?  Bear in mind there were no blacklists assigned or any of the dependencies installed prior to running nvidia.run installer.  Thought trying this would be a way to confirm if there was any remnant nvidia.run kicking about that the installer would pick up on.  I was thinking a long those lines as jockey (additional drivers) installs were failing.[ATTACH]228420[/ATTACH]

---

### Post by Geezanansa on 2012-12-09
[I]*

[/I]

---

### Post by bogan on 2012-12-09
Hi!, **Geezananza**,

I take a dim view of your taking my 'How To' and 'editing' it without acknowledgement or indicating what alterations you have made, whilst replacing my Signature with yours!.

Edit2: [COLOR=Red]You have also removed all the 'Code' blocks,  and their EOL markers so they are unreadable[/COLOR].

PLEASE EITHER DELETE THE WHOLE Post, or colour the changes and label them with " Edited by Ga", or some such, to make it clear which parts are your contribution.

Edit:2 If you have a suggestion for a change or an addition, please Post it here. i will gladly consider any betterment.

Regarding your previous Post, it is not clear to me what your problem is that you want assistance with. 
I have looked through the attachments and there is a very confused set of logs which do not offer much light on any particular problem.

it appears that for some reason the installer is installing all the kernal modules, nvidia, nouveau, & even fglrx, twice over and then removing them;  and, in one case, installing nouveau failed by being unable to detect the monitor screen.

I gather you have a GT7950 nvidia card running with 12.0.4 -35 using the 'nomodeset' boot option, and there should be no problems with that, but please Post: ```
lspci -nnk | grep -iA3 vga
/usr/lib/nux/unity_support_test -p
apt-cache policy nvidia-current
```Did you run:```
 sudo apt-get remove --purge nvidia*
``` before running the nvidia...run file ??

Edit: you should ensure there are the proper blacklist for nouveau in /etc/modprobe.d.

**bogan**.

---

### Post by Geezanansa on 2012-12-09
Post#40 Deleted as requested by bogan
Post#40 Deleted as requested by bogan
My intentions of copying and  pasting whole guide was to save your time.   I only marked as being edited and looking at earlier versions will  confirm changes.  These were mostly formatting and grammar with some  additions. I in no way intend taking credit for somebody elses efforts  but to only indicate that it has been changed. For readability the edits  were left unmarked.   Any reader of this thread can see it is your  guide and i fully acknowledge that.  Sorry did not mean to offend.   Could pm you a copy of deleted thread if you really want the information  regarding changes.  
I started this thread because i have driver problems not because i want to spend time on the forums.:razz:

> Regarding your previous Post, it is not clear to me what your problem is that you want assistance with. 
I have looked through the attachments and there is a very confused set  of logs which do not offer much light on any particular problem.The  problem i had was getting dependencies installed for installing the  latest 304.run driver.  The last post you refer to tried to explain that  the driver was installed and then uninstalled without the dependencies  and nouveau never got going again so tried drivers from jockey which  failed to install so then trying to install dependencies for .run  install attempt which gave the freeglut3-dev errors. 
The  p4 machine is now running a gt6800  with nouveau and running 3.2.0-34.   Have since installed an alongside 12.04.1 installation of 12.04.1.  So  now i have the opportunity to start from the beginning again.
> Edit: you should ensure there are the proper blacklist for nouveau in /etc/modprobe.d. Following your guide indicates 304.run installer makes blacklist.  Hopefully can confirm wether or not in half an hour or so.....

---

### Post by Geezanansa on 2012-12-09
304.64 installed following your guide. Nothing that I can see in the modeprobe.d directory blacklisting nouveau. Very low res.  Everything seems as should be with the exception of low res 640x480

---

### Post by bogan on 2012-12-09
Hi!, **Geezananza**,

Thanks. I will Post the latest version, shortly. If you consider the 'edits' important, please Post them. Edit: Are they what is in Post #38 ??

Re Low Res graphics, have you installed the latest version of nvidia-settings and tried to alter the resolution from that.
 It should show in Dash, or Admin Menu,  as Nvidia Xserver Settings, however, you may need to run it as Root in order to make the change permanent..

Otherwise set the resolution in System Settings>Displays.

Edit: If a nouveau blacklist was made by the nvidia-installer it will be in a file called: "/etc/modprobe.d/nvidia-grphics-drivers.conf", or similar.

Chao!,** bogan**.

---

### Post by Geezanansa on 2012-12-10
As mentioned to save time and effort i posted revised guide for your  approval.  Which you did not approve for as you took offence to somebody  adding to your work.  Why aren't the changes you have made highglighted  and marked?.  Since mentioning this you started marking edits.  Maybe  stand for more if this was the case previous to you mentioning this.   Whatever it is the point you are trying to make. Maybe taking this up in  meta would be appropriate to keep this thread on topic.

Ref making guide usable >"install linux-source" is pretty important !  
"Thanks. I will Post the latest version, shortly. If you consider the  'edits' important, please Post them. Edit: Are they what is in Post #38  ??"  No the changes were added to post #40. Which was deleted at your request.  Did you read it?  or just get enflamed with anger that somebody had the audacity to change your work .  Even if they were asking your approval.!  With your permission i could repost it.


I just want a working ubuntu and am not trying to prove a thing;  other than how to get a decent 3d driver installed in ubuntu as the default installed driver does not work for what i want to use my ubuntu system for.

You have not answered How to confirm which dependencies are required?


Low res would not be a problem if it was possible to change res to my liking in display options or nvidia xserver settings.  I know how to use ubuntu when it works. It is getting to work that is problem. It just aint happenin to anything that could be described as "usable".  It is irony that not blacklisting nouveau and using nvidia.run gives a fully working unity desktop.  Blacklisting nouveau does not give me a bootable desktop.  There is a point being made here, is it understandable?  There is nothing in modeprobe.d mentioning nouveau or nvidia=working unity desktop with 304.run

Then  i do agree the problem is with nvidia-settings.

---

### Post by Geezanansa on 2012-12-10
<iframe class="imgur-album" width="100%" height="550" frameborder="0" src="http://imgur.com/a/q5FM7/embed"></iframe>
Edit:
Edit2:[IMG]http://i.imgur.com/hyJKM.png[/IMG][IMG]http://i.imgur.com/1iv4k.png[/IMG]

---

### Post by bogan on 2012-12-10
Hi!, **Geezananza**,

I do not see much point in extending this exchange as we seem to be addressing different issues from opposing points of view.

To keep it on topic, the definitive version of my guide, which existed long before this thread, is not here but in my personal files. The first draft was approved by MAFoElffen, on whose original text it was based.

To update it I need detailed text I can confirm. If you asked me to approve the 'edits', I certainly did not see that request.

I did read through your #40 looking for 'edits', though not line by line, but only found a couple; when I saw the code blocks had been corrupted I gave up. Then I saw the signature had been removed and I was a bit annoyed, certainly, but not for the reason you infer. "Having the audacity to change" something is quite distinct from Plagiarism.

You Posted:```
You have not answered How to confirm which dependencies are required?
```I am no expert in that level of coding. I have long had doubts about the current application of the dependencies listed in my guide for installation with 'build-essential', which I copied direct from MAFoElffen's Post#280. I queried it with him, but he was, by then, no longer available to respond.
I have recently seen a different list and have been trying to confirm their correctness.

AFAIK: dpkg is the command to use to list dependences, but at the moment I can not put my finger on the correct option . I imagine it to be: " dpkg-query", or: " --get-selections [package-name-pattern...]" but 'man dpkg' is less than clear:>  It  should not be used by package maintainers wishing to understand how
       dpkg will install their packages. The descriptions of  what  dpkg  does
       when installing and removing packages are particularly inadequateRegarding Nouveau blacklists: 
In my personal experience, Nouveau is very unpredictable, sometimes it runs my graphics cards without problems and supports Unity 3d; at others it claims my hardware is inadequate and messes up a lot of things; there are various versions of the blacklists used, and Nouveau is equally unpredictable in its responses to them.

Nvidia-installer will only create Nouveau blacklists if it finds it to be installed and running, and with the agreement of the operator running the installation. An nvidia-current install does it automatically.

Chao!, **bogan**.

---

### Post by bogan on 2012-12-10
Hi!, **Geezananza**,

Re your last Post #: Does the drop-down menu of Resolution in 'Displays', or of Resolution in' Nvidia Xserver Settings' [ when run as root] not allow you to change from Low Res?

If not it is probably an example of the difficulty often reported with nvidia when a CRT Monitor is in use, for which it is unable to read the EID data.

Have you tried a 'Click' on the 'Basic' button to go to the 'Advanced' options?

I do not understand the 'Layout' bit about the screen height being less thsn 600 Pixels. Presumably a reflection of the " height =550" in the data you quote above the attachment.

Chao!, **bogan**.

---

### Post by Geezanansa on 2012-12-10
:popcorn::lolflag::lolflag::lolflag:
Ref NVidia dependencies: Why are you being so adamant about something that you can not validate or understand.?
 
 
Selecting 3rd party software and update options at installation is one option; using software centre to install restricted extras is another option to ensure right dependencies for kernel being used are installed to enable installation of NVidia drivers.
 
 
Why would I want to take credit for a not working guide?   Plagiarism?

---

### Post by bogan on 2012-12-10
Hi!,
Originally Posted by** Geezananz**a:> Why would I want to take credit for a not working guide?   Plagiarism?     Yeah, Good question; so Why did you??

Hasta Quando,** bogan.**

---

### Post by bogan on 2012-12-10
Re: **How To Install Nvidia Drivers ** [v8.1.1.12 by Bogan].

Here is the latest version . [Updated 17/12/2012 ] With thanks to **Geezananza **for his constructive criticism.

Nvidia drivers for Linux come in various forms; directly downloaded from the Nvidia.com/Drivers website, or modified by Ubuntu as 'nvidia-current', and down loaded from a PPA . This guide is mainly concerned with the first, and installation via a Terminal.

**_TIP_**: If you have a three-button or a scroll-wheel Mouse, to Copy/Paste, highlight the command, move the Mouse cursor to the destination point and press the middle button or scroll-wheel. - Presto!

_Ubuntu nvidia-current drivers._ [ Sometimes called 'Proprietary Drivers'.]
To install the Ubuntu modified drivers called nvidia-current and variants, the same preparatory steps should be taken, but omit stage 3.; and at stage 5, use:```
sudo apt-get install nvidia-current # or alter nvidia packagename 
```Nvidia-current drivers can also be installed from System Settings>Additional Drivers, or from Synaptic Package Manager, which will tell what is available.
[ From Ubuntu 12.10, 'Additional Drivers ' is included in Software Sources. You can Right-Click on the Desktop, select 'Change Desktop Background', click the 'All Settings' tab, select 'System>Software Sources' and the 'Additional Drivers ' tab, and Activate the driver you want.]

[The following is based on Post #280 of MAFoElffen's 'Blank Screen' magnum-opus Sticky in the Installations & Upgrades Forum.]There is an index in Post#2
[http://ubuntuforums.org/showthread.php?t=1743535&page=110](http://ubuntuforums.org/showthread.php?t=1743535&page=110)

_Summary._
Under normal circumstances, this is all you need to do to install, or re-install, an nvidia.com downloaded driver:

Reboot to a 'TTY' [Text Terminal or Text Console], or shut down the Xsession from a GUI screen, as the nvidia driver must be installed when the Xserver and GUI screen are inactive. Then CD to the folder where you have downloaded the NVIDIAxxx.run file, make it executable and run it with 'sh'.

_Kernel Updates:_
There are many Posts deprecating the use of the drivers Downloaded from the Nvidia.com>Drivers website; mainly because it used to be necessary to re-install them following a Kernel update. From v304.xx this is no longer the case, as nvidia drivers are now compatible with DKMS and hence the kernel modules are updated automatically, in the same way as with nvidia-current installations. With earlier versions it is still necessary.

_Preparation._
However, the first time you do this there are some preparatory steps: first you should add some Blacklists to the /etc/modprobe.d folder; then ensure the necessary build procedures and header files are installed, and it is also advisable to purge any previous nvidia installations.

_Adding blacklists:_
Note: There may already be nouveau blacklist files in /etc/modeprobe.d. Recent versions, v.304 onwards, of both the nvidia-installer and the Ubuntu-nvidia-current installations can create files blacklisting the default Nouveau driver so Stage 1. can be omitted. The Nvidia installer will offer to create a blacklist file.

1.: _Add blacklists,_ [ For drivers prior to v.304 ]:
In a Terminal ['Crtl+Alt+t'] enter: ```
gksudo gedit /etc/modprobe.d/nouveaublacklist.conf # If you do not have a GUI
# Screen you will need to use a different text editor, eg. 'nano' or 'vim'. 
```If the file does not exist, gedit will show a blank screen with that name, add:
```
# Added for nvidia driver.
blacklist nouveau
blacklist lbm-nouveau
options nouveau modeset=0
alias nouveau off
alias lbm-nouveau off 
```Save and close gedit. [ The filename you use must end in: ".conf" ]

2.: _Prep and make sure everything is there for any dependencies, and Cleanup:_
Ensure you have fully updated your installation.```
sudo apt-get update
sudo apt-get install build-essential gcc-4.5 g++-4.5 libxi-dev libxmu-dev freeglut3-dev libgl1-mesa-glx libglul-mesa libglul-dev
uname -r 
```Insert the output of 'uname -r' in the following command: substituting it for 'uname -r'; for example:
"sudo apt-get install linux-headers-3.2.0-2-33-generic-pae"```
sudo apt-get install linux-headers-'uname -r'
sudo apt-get install linux-headers-generic
sudo apt-get install linux-source
sudo nvidia-installer --uninstall # not needed if no prior nvidia-installation
sudo apt-get remove --purge nvidia* 
```You may get some 'file not found' messages on the last commands. That is okay. Continue. We just want to make sure that older modules are removed so that there is no conflict.

3.: _Download._ [ Omit if choosing an nvidia-current driver]
Download the appropriate driver from nvidia.com/Drivers:
[http://www.nvidia.co.uk/object/linux-display-ia32-310.19-driver-uk.html](http://www.nvidia.co.uk/object/linux-display-ia32-310.19-driver-uk.html) That is for the 32.bit version, make sure you have the correct one for your GPU.

If you do not know which GPU/Video card you have, run:```
lspci -nnk | grep -iA3 vga 
```4.: _Stopping the Graphics session._
To install the downloaded driver, Xorg cannot be running. You need to shut down the X-Session. In a TTY [Text Terminal], [ 'Ctrl+Alt+F1' ] or Terminal, enter:```
sudo service lightdm stop # If using 10.10 or earlier use 'gdm' in place of 'lightdm' 
```You will get a black screen; if it does not have a login prompt, to get one, press 'Ctrl+Alt+F1' [or F2-F6], login, enter your password. [ It will not show, just type it & press 'Enter'] If you need to return to the GUI screen, press: 'Ctrl+Alt+F7', but first, run: ```
sudo service lightdm start 
```_Alternativel_y, reboot into the Recovery drop-down menu, run 'Fsck' to set system to Read/Write, then 'Drop to a Root shell' and login if requested:
In this case you should enter: ```
telinit 3 # to set system level
```[Should 'fsck' hang, wait a minute or two, then enter 'Ctrl+c']

5.: _Installing the driver._ If choosing an nvidia-current driver, see  paragraph 3 above,"Ubuntu nvidia-current drivers." and skip to Stage 6.

Change directory [cd] to the directory where you saved the nvidiaxxx.run file, for example:```
cd /home/username/Downloads
ls 
```Running 'ls' will confirm you are in the right place and you can be sure the spelling is correct - entering 'NV' and pressing 'Tab' will [/should] Auto-complete the file name.

[In the following, substitute the correct file name:]

Mark the downloaded file as executable: ```
sudo chmod a+x NVIDIA-Linux-x86-304.60.run 
```Run the file to Install drivers: ```
sudo sh NVIDIA-Linux-x86-304.60.run 
```You may get an error message about a failed script, continue, accept the options, navigating by using 'Tab' and pressing 'Enter'. [If Nouveau is found to be running, the nvidia-installer may advise to abort and blacklist it, but if you choose to continue, it will create a blacklist for you.]

6.: _When complete,_ reboot, ```
sudo reboot 
```7.: _In case of difficulty:_
If necessary edit the grub boot menu script, by pressing 'e' with the boot option highlighted and entering 'nomodeset' after 'splash ' in the Linux boot line where it shows "ro quiet splash ", and pressing 'Ctrl+x' to boot.

_You may need to run one or more of: _
 NVIDIA XServer Settings [run as Root]```
gksudo nvidia-settings
sudo apt-get install --reinstall nvidia-common # for nvidia cards  5xxx FX or earlier
sudo apt-get install --reinstall ubuntu-desktop
sudo dpkg-reconfigure nvidia-current*
sudo update-initramfs -u

```[Revised: 17/12/2012]

Chao!,** bogan**.

---

### Post by Geezanansa on 2012-12-11
which would be good but maybe something like:  Here is the latest version . [ Edited 09/12/2012 by geezanansa]

Nvidia drivers for Linux come in various forms; directly downloaded from the Nvidia.com/Drivers website; modified by Ubuntu as 'nvidia-current'; or added to software sources from a PPA . This guide is mainly concerned with the first, and installation via a Terminal.

Ubuntu proprietary drivers.
To install the Ubuntu modified drivers called nvidia-current and variants, *N.B. the same preparatory steps should be taken, but omit stage 1.; and at stage 3, use: Code:
```
sudo apt-get install nvidia-current # or nvidia-current-updates # or nvidia-experimental-304 # or nvidia-experimental-310
# use #lspci -nnk | grep -iA2 vga # to confirm card
# use #dpkg -l | grep -i nvidia # to confirm your apt-get install options
```OR

Nvidia-current drivers can also be installed from System Settings>Additional Drivers. From Ubuntu 12.10, 'Additional Drivers ' is included in Software Sources. You can Right-Click on the Desktop, select 'Change Desktop Background', click the 'All Settings' tab, select 'System>Software Sources' and the 'Additional Drivers ' tab, and Activate the driver you want. Then do Stage 4.

[The following is based on Post #280 of MAFoElffen's Blank Screen magnum-opus Sticky in the Installations & Upgrades Forum.]
[http://ubuntuforums.org/showthread.p...43535&page=109](http://ubuntuforums.org/showthread.p...43535&page=109)

Summary.
Under normal circumstances, this is all you need to do to install an nvidia.com downloaded driver:

Reboot to a 'TTY' [Text Terminal or Text Console], or shut down the Xsession from a GUI screen, as the nvidia driver must be installed when the Xserver and GUI screen are inactive. Then CD to the folder where you have downloaded the NVIDIAxxx.run file, make it executable and run it with 'sh'.

Preparation.
However, the first time you do this there are some preparatory steps: first you should add some Blacklists to the /etc/modprobe.d folder; then ensure the necessary build procedures and header files are installed, and it is also advisable to purge any previous nvidia installations.

Adding blacklists:
Note: There may already be nouveau blacklist files in /etc/modeprobe.d. Recent versions, v.304.run onwards, of both the nvidia-installer and the Ubuntu-nvidia-current installations can create files blacklisting the default Nouveau driver so this is not mandatory and can be omitted. The Nvidia installer v.304.run onwards will offer to create a blacklist file.

Add blacklists, *N.B. For drivers prior to v.304.run
In a Terminal ['Crtl+Alt+t'] enter: Code:
```
gksudo gedit /etc/modprobe.d/nouveaublacklist.conf # If you do not have a GUI # Screen you will need to use a different text editor, eg. 'nano' or 'vim'.
```If the file does not exist, gedit will show a blank screen with that name, add:
Code:
# Added for nvidia driver. blacklist nouveau blacklist lbm-nouveau options nouveau modeset=0 alias nouveau off alias lbm-nouveau off
Save and close gedit.[ The filename you use must end in: '.conf' ]

Dependencies
Prep and make sure everything is there for any dependencies,
Ensure you have fully updated your installation. Code:
```
sudo apt-get update 
sudo apt-get install build-essential gcc-4.5 g++-4.5 libxi-dev libxmu-dev freeglut3-dev
``````
uname -r
```Insert the output of 'uname -r' in the following command: substituting it for 'uname -r'; for example:
"sudo apt-get install linux-headers-3.2.0-2-33-generic-pae" Code:
```
sudo apt-get install linux-headers-'uname -r'
sudo apt-get install linux-source
```Purge existing nvidia
```
sudo nvidia-installer --uninstall # not needed if no prior nvidia-installation 
sudo apt-get remove --purge nvidia*
```You may get some 'file not found' messages on the last commands. That is okay. Continue. We just want to make sure that older modules are removed so that there is no conflict.
```
dpkg -l | grep -i nvidia # to confirm
```Cleanup
```
sudo apt-get autoremove
sudo apt-get autoclean
```
1.: Download. [ Omit if choosing the nvidia-current driver]
Down load the appropriate driver from nvidia.com/Drivers:
[http://www.nvidia.co.uk/object/unix-uk.html](http://www.nvidia.co.uk/object/unix-uk.html) That is for the 32.bit version, make sure you have the correct one for your GPU.

If you do not know which GPU/Video card you have, run: Code:
lspci -nnk | grep -iA2 vga
2.: Stopping the Graphics session.
To install the downloaded driver, Xorg cannot be running. You need to shut down the X-Session. In a TTY [Text Terminal] , [ 'Ctrl+Alt+F1' ] or Terminal, enter: Code:
sudo service lightdm stop # If using 10.10 or earlier use 'gdm' in place of 'lightdm'
You will get a black screen; if it does not have a login prompt, to get one, press 'Ctrl+Alt+F1' [or F2-F6], login, enter your password.[ It will not show, just type it & press 'Enter'] If you need to return to the GUI screen, press: 'Ctrl+Alt+F7' but first, run: Code:
sudo service lightdm start
Alternatively, reboot into the drop-down recovery menu, run 'Fsck' to set system to Read/Write, and drop to a Text Console and login:
In this case you should enter: Code:
telinit 3 # to set system level.
3.: Installing the driver. If choosing an nvidia-current driver, see the advice at the beginning of this guide, and skip to Stage 4.

Change directory [cd] to the directory where you saved the nvidiaxxx.run file, for example: Code:
cd /home/username/Downloads ls
Running 'ls' will confirm you are in the right place and you can be sure the spelling is correct - entering 'NV' and pressing 'Tab' will [/should] Auto-complete the file name.

[In the following substitute the correct file name:]

Mark the downloaded file as executable: Code:
sudo chmod a+x NVIDIA-Linux-x86-3.04.60.run
Run the file to Install drivers: Code:
sudo sh NVIDIA-Linux-x86-304.60.run
You may get an error message about a failed script, continue, accept the options, navigating by using 'Tab' and pressing 'Enter'.

4.: When complete, reboot, Code:
sudo nvidia-xconfig
sudo reboot


Troubleshooting:
See the readme from where you downloaded the nvidiaxxx.run or ```
man nvidia-settings
```If necessary edit the grub boot menu script, by pressing 'e' with the boot option highlighted and entering 'nomodset' after 'splash ' in the Linux line where it shows "ro quiet splash ", and pressing 'Ctrl+x' to boot.
Ubuntu survival pack
You may need to run one or more of: Code:
sudo apt-get install --reinstall nvidia-common # for nvidia cards 5xxx FX or earlier sudo apt-get install --reinstall ubuntu-desktop sudo dpkg-reconfigure nvidia-current*[/QUOTE]
may be better for most folks?.  What do you think? Maybe you could make some changes to your guide/wiki?

---

### Post by Geezanansa on 2012-12-11
.
My old generic monitor is not helping things here but have managed to clear monitor xserver config and have much more as expected res. running nvidia-installer --uninstall gave the opengl 1.0 library  error again but removed the .run driver So back at software centre searching for mesa gave 57 results for technical items and looking at those many are labelled opengl.  This is when falling back to nouveau(vesa) after .run uninstall

So i still do not have 3d acceleration.  



[CODEshaun@P43-6ghz:~$ lspci -nnk | grep -iA2 vga
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation NV40 [GeForce 6800 GT] [10de:0045] (rev a1)
    Kernel modules: nouveau, nvidiafb
shaun@P43-6ghz:~$ dpkg -l | grep -i nvidia
rc  nvidia-current                         295.40-0ubuntu1.1                       NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-settings                        295.33-0ubuntu1                         Tool of configuring the NVIDIA graphics driver
shaun@P43-6ghz:~$ sudo apt-get remove nvidia-current
[sudo] password for shaun: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nvidia-current is not installed, so not removed
The following packages were automatically installed and are no longer required:
  nvidia-settings dkms screen-resolution-extra
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
shaun@P43-6ghz:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  dkms nvidia-settings screen-resolution-extra
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
After this operation, 2,627 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 151136 files and directories currently installed.)
Removing dkms ...
Removing nvidia-settings ...
Removing screen-resolution-extra ...
Processing triggers for man-db ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
shaun@P43-6ghz:~$ dkpg -l | grep -i nvidia
No command 'dkpg' found, did you mean:
 Command 'dpkg' from package 'dpkg' (main)
dkpg: command not found
shaun@P43-6ghz:~$ lsmod
Module                  Size  Used by
rfcomm                 38139  0 
bnep                   17830  2 
bluetooth             158438  10 rfcomm,bnep
parport_pc             32114  0 
ppdev                  12849  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
snd_ens1371            24819  2 
gameport               15060  1 snd_ens1371
snd_ac97_codec        110178  1 snd_ens1371
nouveau               712356  0 
ac97_bus               12642  1 snd_ac97_codec
ttm                    65344  1 nouveau
drm_kms_helper         45466  1 nouveau
snd_pcm                80845  2 snd_ens1371,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  2 snd_ens1371,snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
drm                   197599  3 nouveau,ttm,drm_kms_helper
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
i2c_algo_bit           13199  1 nouveau
mxm_wmi                12859  1 nouveau
wmi                    18744  1 mxm_wmi
snd                    62064  11 snd_ens1371,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac_hid                13077  0 
psmouse                86486  0 
video                  19068  1 nouveau
soundcore              14635  1 snd
snd_page_alloc         14108  1 snd_pcm
serio_raw              13027  0 
i2c_sis96x             12743  0 
sis_agp                13165  1 
shpchp                 32325  0 
8139too                23283  0 
8139cp                 26759  0 
][/CODE]

So with a 304 installer it should be a case of logging out.  alt+f1 to tty and log in.  Run nvidia.run


Please do not post another verion of your guide bogan.  Later i  will update and post what works for me on this older rig.   Thanks for all the tips and help though.

---

### Post by bogan on 2012-12-11
Hi!,** Geezananza**,

The following may reflect your problem: **Originally Posted by bogan:**[ See Post #37]QUOTE]**RE: Warning!** Nvidia beta driver 310 does not support 6xxx series cards, and Nvidia warns it may ignore 7xxx series GPU's.

The same, presumably, applies to the Additional Drivers 'nvidia-experimental-310' driver, as well.

I have been running, successfully, the 310.14 driver, with 12.10 Quantal, on an 8GB USB SanDisk, in a computer with a GeForce GT 520 card. That is an nvidia.com downloaded '.run' file.

I transferred the USB to a computer with a GT 7650 card and its graphics were a total shambles, with a GUI in a very low-res with huge characters & Mouse cursor, but no launcher or tool bar panel.[ Nouveau was blacklisted.]

When I ran:```
NVIDIA-Linux-x86-310.14.run --latest
``` it listed 310.14 as installed, and 310.16 as the latest available. { Incidently, 310.16 was not listed as an available Beta driver on the nvidia website, though the whole 7xxx series is listed as supported by 310.14 beta, but not the 6xxx series}.

However, when I tried to reinstall 310.14, I got a message saying no graphics card had been detected that was supported by 310.14, and if installed it would ignore my GPU; ie. the GT 7650. It recommended I install 304.60.

So if you have a 6000 or 7000 series video card watch out.[/QUOTE]Chao!, **bogan.**

---

### Post by bogan on 2012-12-11
Hi!,** Geezananza**,

In your Post, under 'Troubleshooting' you have put: "ubuntu survival pack".

I cannot find anything  of that name, in Software Center, or anywhere else,

Google offers 2 Urls for "Ubuntu 12.04 Survival Kit Part1" & Part2.

Is that what you were referring to??

I have just re-read all the Posts in this Thread, and compared your Post of 9/12/12 line by line with my version7, and I cannot see how we came to be so at cross purposes.

Nor can I understand what you intend by Posting that version with a suggestion I should make some changes to my Guide, followed by asking me not to Post another update.

You Posted:> Please do not post another verion of your guide bogan.  Later i  will update and post what works for me on this older rig. You are,of course, free to Post whatever you choose, but, please, if you base it on someone else's work, at least include an acknowledgement of your major source.

Chao!, **bogan.**

---

### Post by Geezanansa on 2012-12-12
ref ubuntu survival pack Q? - No
I had intended to show the following commands to be described as.!  Maybe if edited to bold font and underlining it would make it more apparent it is a paragraph heading.  I called the paragraph that as without these it is reinstall time for most folks.
:p
:lolflag:

Working through trying most driver versions has shown that different drivers give different problems.  The only one that works to what looks like a "normal" desktop is nouveau.  You have indicated because of the many many functions/capabilities of nouveau the version/type being used when installing nvidia drivers will have an outcome on how the nvidia driver can work. (Regardless of what is in modeprobe.d mentioning nouveau or are there reboots missing in guide?)Which has also been the root cause of freeglut3-dev not installing as it is mesa dependent.  
Using terminal output to point me in right direction has been more than enlightening.
[COLOR=RoyalBlue]
Also could mesa vesa thing be breaking jockey?[/COLOR]
[COLOR=RoyalBlue]Sorry to again be appearing to be overcomplicating things[/COLOR] [COLOR=RoyalBlue]but still do not have 3d acceleration with this hardware[/COLOR]. [COLOR=RoyalBlue] The application i wish to run requires 304.22 or newer.[/COLOR]


Additionally grub could be trying to legacy boot.

Re reading thread makes it more apparent you can see something i do not.  And possibly vice versa.

---

### Post by Geezanansa on 2012-12-12
> I have just re-read all the Posts in this Thread, and compared your Post  of 9/12/12 line by line with my version7, and I cannot see how we came  to be so at cross purposes.

Nor can I understand what you intend by Posting that version with a  suggestion I should make some changes to my Guide, followed by asking me  not to Post another update.

I do not want to waste your time.  The intended context was that after i post what works for me; maybe after your consideration, you might think it appropriate to update your guide.

---

### Post by bogan on 2012-12-12
Hi!, Geezananza,

You Posted: > you might think it appropriate to update your guide.I have, I am and I will.

But do not forget that the ability to edit and update a Post lapses after one week; so the only way to update after that is a new Post.

Chao!, **bogan.**

---

### Post by bogan on 2012-12-12
Hi!, Geezananza,

I have thoroughly checked out your suggestion to use "dpkg -l | grep -i nvidia" to check what driver versions are available to 'sudo apt-get install'.

I conclude it is not adequate as it only finds one of those  available in 'Additional Drivers': It is better to use Synaptic from which installation can also be carried out.

My present running 12.10 shows only```
:~$ dpkg -l | grep -i nvidia*
ii  nvidia-common      1:0.2.71.1       i386   transitional package for ubuntu-drivers-common
ii  nvidia-current-updates    304.51-0ubuntu1  i386   NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-current-updates-dev304.51-0ubuntu1  i386    NVIDIA binary Xorg driver development files
ii  nvidia-settings-updates   304.51-0ubuntu2  i386    Tool for configuring the NVIDIA graphics driver
:~$ 
```Whilst 'Additional Drivers' lists:
nvidia-current [304.51 really 304.48]
nvidia-experimental-310
Nouveau 1:1.0.2
nvidia-current updates [ 304.51]
nvidia-experimental-304

And Synaptic Package Manager additionally shows:
nvidia-173 
nvidia-173-updates

**EDIT:** I also checked it in 12.04, where 'dpkg' offered only the 304.51 nvidia-current driver, where 'Additional Drivers' and 'Synaptic' offered 5 variants.

You Posted:> [COLOR=RoyalBlue]still do not have 3d acceleration with this hardware[/COLOR].If that is the: "NVIDIA Corporation NV40 [GeForce 6800 GT] " then i do not think that you will, with present available drivers, and the 6xxx series has been dropped from support in the latest ones. But you should not have problems with a GT 520.

Chao!, **bogan.**

---

### Post by Geezanansa on 2012-12-14
Thx bogan. Big thx oldfred too with reference to post #2.

This is what basically worked for me to get better resolution and using  nvidia 310 on a 64bit system using nvidiaGT520 and running12.04 desktop  32bit
After making sure kernel, image and headers were all approopriately set  for the kernel being booted.  Remove pae kernel, headers and images.    Install linux-source.  Remove all nvidia to fallback to nouveau.   Removed evreything in /etc/X11/ that mentioned xorg.conf.  Rebooted.   Used additional drivers to install 310 driver. Rebooted.  Ran  nvidia-xconfig and rebooted.

[IMG]http://i.imgur.com/EStyh.jpg[/IMG]

---

### Post by Geezanansa on 2012-12-14
With reference to post # 59 bogan Did have code for showing what jockey sees in terminal or what jockey  would show via gtk. Will have a look in browsers history but they are  chocka with to many similar things which probably means searching for  the like.  I copied terminal text directly from other threads and after  using man options i.e. man dpkg or man lspci etc  maybe man grep might help for search options. **EDIT: **man apt-get was for me helpful in process as well especially when trying to fix held broken packages  This might be handy for using apt-get build- dep nvidia-experimental-310 or other options to build source kernel.  Dont quote me though.(on anything that has not been referencedlol)

Maybe installing nvidia.run  drivers breaks jockey.  I had noticed that when installing proprietary drivers from terminal did not show accurately in jockey as jockey did not indicate nvidia-current with green led to confirm this???  So after trying nvidia-installer --version to see if there was anything there and then jockey to see if anything there installed nope.  Again can not find part of thread i got the two codes from to help id card and confirm which nvidia packages were either installed or available.
   I am not experienced in using terminal or  writing how tos.   Maybe using forums is good for one thing and  ask/launchpad for other things.  To many similar questions at ask that  had qnswers that worked for op but did not provide a working solution  for me.  I did not understand what was causing this problem but in  hindsight it was/is several issues that caused boot time and graphics  issues all of which are all well documented nvidia/ubuntu issues with  working solutions.    

And just to encourage folks who are having  similar probs- just think of it as an introduction or initiation to  linux.  It is only easy when you know how!  The adventure may be  different on different hardware configs but the lessons learned are all  relative and will probably come in handy again....
Hopefully before they are forgotten!

---

### Post by bogan on 2012-12-14
Hi!, **Geezananza**,

You Posted:```
Maybe installing nvidia.run  drivers breaks jockey.
``` No, I think they just ignore each other.

Probably, the confusion arises because Update manager, 'dpkg', 'jockey' and 'Synaptic', [and some others] only have knowledge of Packages that are installed by themselves, or using 'dpkg, 'DKMS' or their terminal or GUI equivalents, such as 'APT' or 'Additional Drivers'.

Binary compilations and independent installations, such as AMD/ATI or NVIDIA installations, are not known to them, even though they may be DKMS compatible. They are not added to the databases on which 'jockey' etc depend. So any updates on either side are unknown to the other, unless specific proceedures are included to detect them, as is the case with Nvidia.run installations.

You also Posted:>  I am not experienced in using terminal or  writing how tos.
And:
Re reading thread makes it more apparent you can see something i do not.  And possibly vice versa.     That is probably true.
May I suggest, before your ability to edit your Post#52 lapses in a few days time, that you go through it and repair the [CODE] tags and replace the intra-command spaces & EOL Tags, that were corrupted by using Copy/Paste from another Post.

As it is, apart from being difficult to read, copy/pasting the commands to a Terminal will give multiple errors to anyone not very knowledgeable in terminal code.

Chao!, **bogan.**

---

### Post by Geezanansa on 2012-12-15
I would thank you bogan but it appears the record is stuck!

Please refer to post #34 as this is what is repeated in post #60.  So as your thread being posted a long time ago to which has been referred to in this thread DOES NOT WORK FOR ME.  That is why there has been suggestions to maybe clarify or edit what you recommend..


It is getting harder for me to bite my tongue!?  If you have been offended by anything that has been said or done - Please don't be.  If you aren't offended by anything that has been said and want to keep it that way then say no more on editing threads and guides
Or
=;


So if a novice user did install nvidia.run then had trouble booting to desktop again.  Once they did eventually get to tty or terminal they may mistakenly do apt-get driver.  Which would not show up in jockey(cos of nvidia.run still being installed.)
So i guess in a usable How to;  there may be advice on how to uninstall as well as install nvidia.run

```
lspci -v | grep -i vga
lspci -l | grep -i nvidia
dpkg -l | grep -i nvidia 
nvidia-installer --version
lsmod
``` were for me useful in identifying which card, drivers and modules are being used.

Things in forums are opinions.  Things in ```
man "whatever package"
``` are fact.  So agree an unreferenced fact is opinion.

---

### Post by bogan on 2012-12-15
Hi!, **Geezananza,**

Enough said!  No offence taken, nor ever was, beyond what I expressed specifically.

You have thanked me more than enough times in these Posts, and I appreciate that.

I only wish I knew what exactly in my Guide, it is that fails to work for you, and whether it is with both your 6xxx series card as well as the 5xx card.

I agree that much of what is in these Forum is opinion, but what is also fact is that solutions that work for many people, and their particular set-ups, often fail to work for others with, apparently, the same problem.

With any Guide, there are always more useful items that could be added; it is a matter of judgement where to draw the line.

Chao!,** bogan.**

---

### Post by Geezanansa on 2012-12-15
[IMG]http://i.imgur.com/TV2YJ.png[/IMG]

It would appear the only recommended method of installing nvidia is after checking your linux image and header match the kernel you are booting, install linux-source and choose a driver from additional drivers or nvidia .run.

Using man lspci to find lspci -v and lspci -nn | grep -i nvidia with dpkg -l | grep -i nvidia or nvidia-installer --version and lsmod will help to confirm which driver is installed as well as which kernel modules are being used.  Replacing nvidia with vga may show other drivers/modules

Thank you bogan.  You have answered the thread question in a much more constructive manner than simply saying no.  That is if simply installing a driver does not work!

Maybe working out the kernel bit can now mean i could (start thinking of how to ) build wine or other packages from source.....
or i could have a go at setting up a lanrom to boot all my machines from!

At least i can play my games if i get bored now!?:DIts all good!

---

### Post by bogan on 2013-02-01
Hi!, **All**,

There is a revised version of my "How To Install Nvidia Drivers"; Including an important change to the 'Removal of old drivers' instruction, [Section2a.] in the 'Installation & Updates' Sticky, Post#1126
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

Chao!, **bogan.**

---

### Post by blueicewater on 2013-02-12
> **oldfred said:**
> What version nVidia card/chip and what version Ubuntu.

With older versions, you had to boot with nomodeset and then it offered to install the nVidia driver and just worked.

With 12.10 they forgot the headers so nVidia does not install. If you download headers and manually install nvidia, then it works.

Has most bug reports:
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-updates/+bug/1068341](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-updates/+bug/1068341)

[https://bugs.launchpad.net/fglrx/+bug/1068456](https://bugs.launchpad.net/fglrx/+bug/1068456)
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1068488](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1068488)
[https://bugs.launchpad.net/fglrx/+bug/1068661](https://bugs.launchpad.net/fglrx/+bug/1068661)

Has what worked for me, install headers & dpkg update.
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-updates/+bug/1068942](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-updates/+bug/1068942)

But you need the headers first:
When you see you are in the desktop but no icon or bar, right click to change desktop background
When the window appear, click all settings, now you see the system settings window.
Next, click on Software source, go in the additional drivers tab.
Select the 3 rd option, using video driver for the nvidia or AMD... fglrx-upgrade

cntrl-alt f1 or f2 to get to terminal also works
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install linux-headers-generic
# only reason to purge is there are several versions, if you know you have different nVidia use that: 
sudp apt-get purge nvidia*
sudo apt-get install nvidia-current
sudo dpkg-reconfigure nvidia-current

Tried this method but getting this error:

> You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

Any suggestions?

---

