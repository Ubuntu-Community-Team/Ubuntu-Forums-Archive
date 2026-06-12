---
title: "new kernel, nvidia"
date: 2007-09-25
forum: General Help
---

### Post by posterboy on 2007-09-25
This AM, there's a new kernel, with associated packages. Strangely, (to me) there's no new nvidia driver. Huh? Look at this:

The following packages will be upgraded:
  linux-headers-2.6.20-16 linux-headers-2.6.20-16-generic
  linux-image-2.6.20-16-386 linux-image-2.6.20-16-generic linux-libc-dev
Next:
root@raymondjones:~# dpkg -l |grep nvidia
ii  nvidia-glx                                 1.0.9631+2.6.20.5-16.29                NVIDIA binary XFree86 4.x/X.Org driver
ii  nvidia-kernel-common                       20051028+1ubuntu7                      NVIDIA binary kernel module common files
And the question IS??????
Can I do this kernel without breaking my nvidia stuff?

---

### Post by useResa on 2007-09-25
Instead of nvidia-glx, I have nvidia-glx-new installed. See below:
```
0 rdrijsen@rdrijsen-laptop: ~
Tue Sep 25, 15:35 $ dpkg -l|grep nvidia
ii  nvidia-glx-new                             1.0.9755+2.6.20.5-16.29                NVIDIA binary XFree86 4.x/X.Org 'new' driver
ii  nvidia-kernel-common                       20051028+1ubuntu7                      NVIDIA binary kernel module common files
ii  nvidia-kernel-source                       1.0.9631+2.6.20.5-16.29                NVIDIA binary kernel module source
```

I have upgraded to the new kernel (see below) and experienced no problems.
```
0 rdrijsen@rdrijsen-laptop: ~
Tue Sep 25, 15:36 $ dpkg -l | grep 2.6.20-16
ii  linux-headers-2.6.20-16                    2.6.20-16.32                           Header files related to Linux kernel version 2.6.20
ii  linux-headers-2.6.20-16-generic            2.6.20-16.32                           Linux kernel headers for version 2.6.20 on x86/x86_64
ii  linux-image-2.6.20-16-generic              2.6.20-16.32                           Linux kernel image for version 2.6.20 on x86/x86_64
ii  linux-libc-dev                             2.6.20-16.32                           Linux Kernel Headers for development
ii  linux-restricted-modules-2.6.20-16-generic 2.6.20.5-16.29                         Non-free Linux 2.6.20 modules on x86/x86_64
ii  vmware-server-kernel-modules-2.6.20-16     2.6.20.5-16.29                         vmware-server modules for Linux (kernel 2.6.20)
```

DISCLAIMER: This worked on my box and I do hope you will have as little issues as I had :)
Should you run into problems, you can always restart.
Select the menu, immediately at the beginning of the start up and select the previous kernel.

---

### Post by posterboy on 2007-09-25
OK, I'm off to try this. THANKS!

---

### Post by bimmerd00d on 2007-09-25
Everything go alright?  The update just popped up in the corner of my screen :)  I've got the good ol' Nvidia driver too.

---

### Post by posterboy on 2007-09-25
I'll post back here with results as soon as i get 'er rebooted

---

### Post by bimmerd00d on 2007-09-25
> **posterboy said:**
> I'll post back here with results as soon as i get 'er rebooted

What's your method of upgrading the kernel with the nvidia-driver?  Do you use envy or the repo one?

EDIT:  Updated mine just fine, didn't have to do anything special, it just works.  I don't notice any differences, but at least i'm up to date :D

---

### Post by posterboy on 2007-09-25
Uh-oh, this turned out to be a disaster! Well, likely a temporary disaster, anyway. After the new kernel was installed, I restarted, and got a nasty error message about the nvidia driver couldn/'t be loaded. OK, let's fall back to the previous kernel. Not good, I edited xorg.conf to fall back to the "nv" driver, and I now have a screen, sort of, but no acceleration, of course. Here's what I show:

ray@raymondjones:~$ dpkg -l |grep nvidia
rc  nvidia-glx                                 1.0.9631+2.6.20.5-16.29                NVIDIA binary XFree86 4.x/X.Org driver
ii  nvidia-kernel-common                       20051028+1ubuntu7                      NVIDIA binary kernel module common files
ii  nvidia-new-kernel-source                   1.0.9755+2.6.20.5-16.29                NVIDIA binary 'new' kernel module source
ii  nvidia-settings                            1.0+20060516-3ubuntu1       

And here's the relevant part of the kernel stuff:

ii  linux-restricted-modules-generic           2.6.20.16.28.1                         Restricted Linux modules for generic kernels
ii  module-init-tools                          3.3-pre3-1ubuntu7                      tools for managing Linux kernel modules
ii  nvidia-kernel-common                       20051028+1ubuntu7                      NVIDIA binary kernel module common files
ii  nvidia-new-kernel-source                   1.0.9755+2.6.20.5-16.29                NVIDIA binary 'new' kernel module source

HELP!!!!!!!!!!!!!

---

### Post by bimmerd00d on 2007-09-25
> **posterboy said:**
> Uh-oh, this turned out to be a disaster! Well, likely a temporary disaster, anyway. After the new kernel was installed, I restarted, and got a nasty error message about the nvidia driver couldn/'t be loaded. OK, let's fall back to the previous kernel. Not good, I edited xorg.conf to fall back to the "nv" driver, and I now have a screen, sort of, but no acceleration, of course. Here's what I show:

ray@raymondjones:~$ dpkg -l |grep nvidia
rc  nvidia-glx                                 1.0.9631+2.6.20.5-16.29                NVIDIA binary XFree86 4.x/X.Org driver
ii  nvidia-kernel-common                       20051028+1ubuntu7                      NVIDIA binary kernel module common files
ii  nvidia-new-kernel-source                   1.0.9755+2.6.20.5-16.29                NVIDIA binary 'new' kernel module source
ii  nvidia-settings                            1.0+20060516-3ubuntu1       

And here's the relevant part of the kernel stuff:

ii  linux-restricted-modules-generic           2.6.20.16.28.1                         Restricted Linux modules for generic kernels
ii  module-init-tools                          3.3-pre3-1ubuntu7                      tools for managing Linux kernel modules
ii  nvidia-kernel-common                       20051028+1ubuntu7                      NVIDIA binary kernel module common files
ii  nvidia-new-kernel-source                   1.0.9755+2.6.20.5-16.29                NVIDIA binary 'new' kernel module source

HELP!!!!!!!!!!!!!

Where'd you get your nvidia driver from?  it's not the one from the repos is it?  Looks like you're using the old 9631 driver and i'm using the new 100.whatever one.  What nvidia card do you have that needs the 9631 driver, or have you just not updated to the newest one yet?

Here's my dpkg grep crap

bimmerd00d@bhlaptop:~$ dpkg -l |grep nvidia
ii  nvidia-glx-new                             100.14.19+2.6.20-16                    NVIDIA binary XFree86 4.x/X.Org 'new' driver
ii  nvidia-glx-new-dev                         100.14.19+2.6.20-16                    NVIDIA binary XFree86 4.x/X.Org 'legacy' dri
ii  nvidia-kernel-2.6.20-16-generic            100.14.19-0ubuntu3+2.6.20-16.31        NVIDIA binary kernel module for Linux 2.6.20
ii  nvidia-kernel-common                       20051028+1ubuntu7                      NVIDIA binary kernel module common files
ii  nvidia-new-kernel-source                   100.14.19+2.6.20-16                    NVIDIA binary 'new' kernel module source

---

### Post by posterboy on 2007-09-25
Yes, it is from the repos.. Maybe I messed up when I installed nvidia-glx-new. I have an old nvidia card, and it worked great before I got into this mess :)  If it ain't broke, don't FIX IT, right? 

HELP!

---

### Post by bimmerd00d on 2007-09-25
> **posterboy said:**
> Yes, it is from the repos.. Maybe I messed up when I installed nvidia-glx-new. I have an old nvidia card, and it worked great before I got into this mess :)  If it ain't broke, don't FIX IT, right? 

HELP!

First off, i'd try unloading the nvidia-glx driver and reinstalling it from scratch, then manually modifying the xorg.conf.  That should work in theory.  I use envy for my nvidia card and it just works great.  You might try using that, I didn't have to do anything to my nvidia stuff during this kernel update.

---

### Post by posterboy on 2007-09-25
There are several things associated with that. What, exactly, should I remove, please. Thank you!

---

### Post by bimmerd00d on 2007-09-25
> **posterboy said:**
> There are several things associated with that. What, exactly, should I remove, please. Thank you!

Fire up Synaptic, search nvidia and uninstall everything related.  Then download envy and give it a shot if you want to try that.  if not, then sudo apt-get install nvidia-glx

---

### Post by useResa on 2007-09-25
If you decide to install nvidia-glx-new make sure to remove nvidia-glx first (removing it afterwards resulted in an error in my situation).
So first:
```
sudo aptitude purge nvidia-glx
```Next
```
sudo aptitude install nvidia-glx-new
```[COLOR=Red]**NOTE:**[/COLOR] What does somewhat surprise me is that I also have nvidia-glx-new installed but I have the "old" 9755 driver.
```
0 rdrijsen@rdrijsen-laptop: ~
Tue Sep 25, 16:26 $ dpkg -l | grep nvidia
ii  nvidia-glx-new                             1.0.9755+2.6.20.5-16.29                NVIDIA binary XFree86 4.x/X.Org 'new' driver
ii  nvidia-kernel-common                       20051028+1ubuntu7                      NVIDIA binary kernel module common files
```

---

### Post by posterboy on 2007-09-25
Man, NONE of this is co-operating with me. :)
Looky:

root@raymondjones:~# dpkg -l |grep nvidia
pc  nvidia-glx                                 1.0.9631+2.6.20.5-16.29                NVIDIA binary XFree86 4.x/X.Org driver
pi  nvidia-kernel-common                       20051028+1ubuntu7                      NVIDIA binary kernel module common files
rc  nvidia-settings                            1.0+20060516-3ubuntu1  

Now, look at THIS:

when removing `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx'
  found `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx-new'
dpkg: error processing nvidia-glx (--purge):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 nvidia-glx


I haven't the foggiest idea what that means, or, worse, where to go from here to recover.

---

### Post by useResa on 2007-09-25
I encountered this too. That is why I indicated that BEFORE installing nvidia-glx-new you should remove nvidia-glx.
What I did when I encountered this:
1. Removed nvidia-glx-new (sudo aptitude purge nvidia-glx-new)
2. Removed nvidia-glx (sudo aptitude purge nvidia-glx)
3. Re-installed nvidia-glx-new (sudo aptitude install nvidia-glx-new)

This solved the situation for me.
Hope this will work for you too.

---

### Post by posterboy on 2007-09-25
Thanks, I'm trying. :) I can't remove it. here:
root@raymondjones:~# dpkg --purge nvidia-glx
(Reading database ... 143492 files and directories currently installed.)
Removing nvidia-glx ...
Purging configuration files for nvidia-glx ...
dpkg-divert: mismatch on package
  when removing `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx'
  found `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx-new'
dpkg: error processing nvidia-glx (--purge):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 nvidia-glx
AND



root@raymondjones:~# dpkg -r nvidia-glx
dpkg - warning: ignoring request to remove nvidia-glx, only the config
 files of which are on the system.  Use --purge to remove them too.

---

### Post by useResa on 2007-09-25
Don't know to what extend there is a difference, but could you try removing it by using aptitude (as I indicated) instead of dpkg?

---

### Post by posterboy on 2007-09-25
No difference, just more output. (which may be helpful, I hope)

root@raymondjones:~# aptitude purge nvidia-glx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages will be REMOVED:
  nvidia-glx{p} 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 143492 files and directories currently installed.)
Removing nvidia-glx ...
Purging configuration files for nvidia-glx ...
dpkg-divert: mismatch on package
  when removing `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx'
  found `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx-new'
dpkg: error processing nvidia-glx (--purge):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 nvidia-glx
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

---

### Post by useResa on 2007-09-25
Ooops ... my mistake.
First remove nvidia-glx-new 
Secondly remove nvidia-glx
Thirdly install nvidia-glx-new
This should get rid of the messages.

---

### Post by posterboy on 2007-09-25
Hmm, I don't have that:

root@raymondjones:~# dpkg -l |grep nvidia
pc  nvidia-glx                                 1.0.9631+2.6.20.5-16.29                NVIDIA binary XFree86 4.x/X.Org driver
pi  nvidia-kernel-common                       20051028+1ubuntu7                      NVIDIA binary kernel module common files
rc  nvidia-settings                            1.0+20060516-3ubuntu1                  Tool of configuring the NVIDIA graphics driv

Thanks for your patience with this, I do appreciate it.

---

### Post by useResa on 2007-09-25
From what I understand you did have it installed and there is a remainder left. Would you please try ```
sudo aptitude remove nvidia-glx-new
```?
If this works (maybe a warning about a directory not being empty) then try to remove nvidia-glx and then install nvidia-glx-new

---

### Post by posterboy on 2007-09-25
Nope, that didn't remove anything. 

 aptitude remove nvidia-glx-new
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Maybe lets's take another tack. I ran mondoarchive on Sept. 23. Not long ago, at all. 
Everything was working perfectly at that point. Now, IF I knew WHICH of the / dirs are involved here, MAYBE I could restore just those. Certainly, we need /usr, /lib, where is the dpkg database kept? and what others can we think of critical to this? What about the /boot dir? What about grub getting fixed after that. etc. etc.

---

### Post by useResa on 2007-09-25
Could you try the following
```
sudo dpkg-divert --list | grep nvidia-glx-new
```This will give you a listing of the diversion created by nvidia-glx-new

Next remove the diversions you have found by using the command
```
sudo dpkg-divert --remove <diversion name>
```For example
```
sudo dpkg-divert --remove  /usr/lib/libGL.so.1
```Do this for all the diversions you find for nvidia-glx-new

After that try to install nvidia-glx(-new) again.

---

### Post by posterboy on 2007-09-25
Yes, I really don't want to try the recover from DVD. Let's do this. I'm off to try it
back soon, and again, thanks for sticking with me on this.

---

### Post by posterboy on 2007-09-25
Wait a second, I thought I knew what to do, but, I don't.
Here's the confusion, from an example, please:
diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx-new
Now, what do I remove, /usr/lib/nvidia/libGL.so.1.xlibmesa?

---

### Post by useResa on 2007-09-25
> **posterboy said:**
> Wait a second, I thought I knew what to do, but, I don't.
Here's the confusion, from an example, please:
diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx-new
Now, what do I remove, /usr/lib/nvidia/libGL.so.1.xlibmesa?
```
sudo dpkg-divert --remove  /usr/lib/libGL.so.1
```
You take the string between the word **of** and the the word **to**.

---

### Post by posterboy on 2007-09-25
Thank you.

OK, here's what happens on that one:

pkg-divert --remove  /usr/lib/libGL.so.1
Removing `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx-new'
dpkg-divert: rename involves overwriting `/usr/lib/libGL.so.1' with
  different file `/usr/lib/nvidia/libGL.so.1.xlibmesa', not allowed
ANOTHER idea, please????   
:)

---

### Post by useResa on 2007-09-25
Searching the forums I came across[ this post]("http://ubuntuforums.org/showpost.php?p=2502530&postcount=6").
You are not the only one with dueling diversions.
Maybe the commands provided will also solve the issue for you.

---

### Post by posterboy on 2007-09-25
WAIT! It's FIXED, it's FIXED!!!!! WHEEE!!!!

I re-installed nvidia-glx-new. Then, I did a purge of that. MAYBE that undid the diversiions, I don't know. Then forced a re-install of just nvidia-glx. Somewhere during this, nvidia-settings got removed. Dunno why on that one, either.
After that, I manually fixed up xorg.conf to use the nvidia driver, and VOILA!!!!!!!!!!!!!!!
Looky:
7205 frames in 5.0 seconds = 1440.932 FPS
7196 frames in 5.0 seconds = 1439.075 FPS
7214 frames in 5.0 seconds = 1442.782 FPS
And, that's about as fast it normally is. It's an old card, for sure. But, I do love it. :)

Man, thank you so much for all your patience and help. Hanging IN there is the name of the game, right???

---

### Post by useResa on 2007-09-25
Woohoo! Congrats!

Indeed ... do not give up if at first you do not succeed.
In the end there is always a solution  :D

Glad you have things in working order again.

---

### Post by Kalibur on 2007-09-26
Below is what mine says am using the nVidia proprietary drivers then seem to be the only fail safe option for me cause I use a wide screen. I have had nvidia-glx(-new)it working before but its alway a hustle with xserver gui failing start in terminal and running sudo dpkg-reconfigure xserver-xorg troubleshooting nightmares.  Plus the nvidia driver has crystal clear smooth graphix.  Am using gutsy giibbon and fieasty by the way

[I]kalibur@kalibur-desktopr:~$ dpkg -l |grep nvidia 
ii  nvidia-cg-toolkit                          1.5.0.0019-1                            NVIDIA Cg Toolkit installer
ii  nvidia-glx                                 1:1.0.9639+2.6.22.3-12.5                NVIDIA binary XFree86 4.x/X.Org driver
rc  nvidia-glx-new                             100.14.11+2.6.22.3-12.5                 NVIDIA binary XFree86 4.x/X.Org 'new' driver
rc  nvidia-glx-new-dev                         100.14.11+2.6.22.3-11.4                 NVIDIA binary XFree86 4.x/X.Org 'legacy' dri
ii  nvidia-kernel-common                       20051028+1ubuntu7                       NVIDIA binary kernel module common files
rc  nvidia-settings                            1.0+20070502-1ubuntu1                   Tool of configuring the NVIDIA graphics driv
[/I]
So now every time I have an update I have to uncheck the nvidia-glx* because if I dont it will remove my nvida propreatary drivers.  
Why the nvida vs xorg battle anyway?

---

### Post by posterboy on 2007-09-26
I am a real newbie, here, I come from FC6, on this same box. There was always a wrestling match there to get this stuff to work. I suppose we have to accept that, nvidia won't let people read the source, and this is the result. How can we integrate with an unknown "black box" entity? On the plus side, nvidia HAS supported linux, and continues to do so, making me want to support them, as well. 
BTW, I am very pleased with Ubuntu, and feel that it's unlikely I would return to Fedora. 
In re: your issue, please tell me how to eliminate a package for upgrade consideration. In yum, there's a .conf file where packages can listed that you don't want upgraded. How is that done in apt?

---

### Post by useResa on 2007-09-26
> **posterboy said:**
> In re: your issue, please tell me how to eliminate a package for upgrade consideration. In yum, there's a .conf file where packages can listed that you don't want upgraded. How is that done in apt?Of course there will be more resources to find information on this, but I find this [APT HOWTO]("http://www.debian.org/doc/manuals/apt-howto/") very useful. With regard to your question, please read specifically [3.10]("http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-pin").

Another way is to do this by using Synaptics (if you prefer not to use the CLI).
Look up the package you do not want upgraded. Select this package and from the menu choose _P_ackage --> _L_ock version.

---

### Post by posterboy on 2007-09-26
AHA! Very similar to yum, just in a different place. No, I actually have become quite a CLI junkie over the last years, and I keep the X-server running, but also keep 3 terminals open constantly. I is my box, another to another box that's headless, and a root terminal. 
Again, thank you, another bookmark for me.

---

### Post by useResa on 2007-09-26
Your welcome, glad I could help.
Rock on and hope you will remain enjoying Ubuntu (and the forums ;))

---

