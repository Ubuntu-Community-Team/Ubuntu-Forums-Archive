---
title: "Updates about to break my system, AGAIN?"
date: 2006-08-03
forum: General Help
---

### Post by viciouslime on 2006-08-03
This morning 48 updates have appeared, one of which is a kernel one. Everytime the ubuntu kernel has been updated, my system breaks. It looks like this is going to happene again, because there is no updated restricted modules. I use the nvidia driver from the repos, I could understand if I had installed it manually from the nvidia site, but I haven't, it is just from the repos, why does this keep happening?

---

### Post by Lunar_Lamp on 2006-08-03
I believe that each time you update your kernel you need to reinstall the nvidia drivers.  Not quite sure as I use an ATI card, so can't comment in detail on nvidia.

What do you mean by 'breaks'?

---

### Post by viciouslime on 2006-08-03
I mean X won't start. Usually you have to wait a few days until someone updates the restricted modules and then you can update those and use the new kernel. It's simple enough, but to a n00b it could be the difference between sticking with ubuntu or scrapping it.

Why can't they just release the kernel update at the same time as the restricted modules so noone ends up stuck at a command line.

---

### Post by cantormath on 2006-08-03
> **viciouslime said:**
> I mean X won't start. Usually you have to wait a few days until someone updates the restricted modules and then you can update those and use the new kernel. It's simple enough, but to a n00b it could be the difference between sticking with ubuntu or scrapping it.

Why can't they just release the kernel update at the same time as the restricted modules so noone ends up stuck at a command line.


I wonder, if you dont update the kernel, is it really that bad?

what repos are you using when you do your updates (etc/apt/sources.list)?

---

### Post by viciouslime on 2006-08-03
Just the standard repos +universe and multiverse. Nothing else. It's not that it's bad not updating the kernel, it's that most people will run an update not knowing what a kernel is. They'll update everything, thinking that's the right thing to do and all of a sudden their computer won't boot. Doesn't quite seem to fit ubuntu's goal.

---

### Post by mcduck on 2006-08-03
just install the linux-386, linux-686 or linux-k7 metapackage, or whatever kernel you are running. These packages depend on latest kernel image, restricted modules and kernel headers and having one installed makes sure that you automaticly get updates for all kernel-related files.

Install the one you want and you'll never again have to manually install your restricted modules or worry about kernel updates breaking your system :D

---

### Post by Martango on 2006-08-03
I was really surprised after I installed Ubuntu for the first time recently. I'm one of the newbe's but I knew in advance that updating the kernel should be done with caution. Because of that I carefully went through the list of about 130 security and software updates when Update Manager poped up for the first time. Maybe I overlooked some version numbers, but not one of the 130 updates had the word "kernel" in it's name. And since I'm a newbe, I don't know better, so I installed all 130 updates. After reboot I was of course very surprised that the kernel was updated from 2.6.15-23-386 to 2.6.15-26-386. I was lucky that it didn't affect my system, but I really don't know what happened. My guess now is that one or more of the updates depended of the new kernel version, and that's why the kernel was downloaded and installed with the other updates. If I was an experienced Linux user I might had discovered that but I didn't. I don't think that it is bad that the kernel is updated through Update Manager, but it would be nice to get some kind of warning when it happens. I don't know if that's impossible to implement, but it would certainly be big help! [-o<

---

### Post by viciouslime on 2006-08-03
I have got the linux-k7 package installed. The problem is for a few days between updates, the k7 restricted modules and the k7 kernel are incompatible.

---

### Post by pirast on 2006-08-03
The Ubuntu kernelpackages aren't called kernelxxxxxxx, they are called 

>  linux-image-2.6.15-26-386                2.6.15-26.46
  linux-image-2.6.15-26-686
  linux-image-2.6.15-26-amd64-generic      
  linux-image-2.6.15-26-amd64-k8        
  linux-image-2.6.15-26-amd64-server      
  linux-image-2.6.15-26-amd64-xeon        
  linux-image-2.6.15-26-hppa32           
  linux-image-2.6.15-26-hppa32-smp        
  linux-image-2.6.15-26-hppa64            
  linux-image-2.6.15-26-hppa64-smp       
  linux-image-2.6.15-26-itanium         
  linux-image-2.6.15-26-itanium-smp       
  linux-image-2.6.15-26-k7               
  linux-image-2.6.15-26-mckinley          
  linux-image-2.6.15-26-mckinley-smp      
  linux-image-2.6.15-26-powerpc           
  linux-image-2.6.15-26-powerpc-smp       
  linux-image-2.6.15-26-powerpc64-smp     
  linux-image-2.6.15-26-server             
  linux-image-2.6.15-26-server-bigiron     
  linux-image-2.6.15-26-sparc64           
  linux-image-2.6.15-26-sparc64-smp      

for example.

Updating the kernel should work great, thought as long as you didn't compile kernel modules yourself. When you use the official nvidia driver via nvidia-glx then the nvidia kernel modules will be updated at a kernel update, too.

---

### Post by mcduck on 2006-08-03
Updating your kernel is not dangerous at all, as long as you have the correct packages installed. Just see my previous post. They only break stuff if you have installed a different kernel by selecting a specific file version instead of installing the generic linux-<kernel version> metapackages.

So there is no need for any warning about kernel updating other than the one you get now after update that tells you to reboot to start using the updated kernel.

---

### Post by mcduck on 2006-08-03
> **pirast said:**
> The Ubuntu kernelpackages aren't called kernelxxxxxxx, they are called 



for example.

Updating the kernel should work great, thought as long as you didn't compile kernel modules yourself. When you use the official nvidia driver via nvidia-glx then the nvidia kernel modules will be updated at a kernel update, too.
yes, but you shouldn't install any of those packages yourself. If you do, you won't get proper updates.

---

### Post by Martango on 2006-08-03
Ok thanks - I better install the linux-386.

---

### Post by viciouslime on 2006-08-03
> **mcduck said:**
> Updating your kernel is not dangerous at all, as long as you have the correct packages installed. Just see my previous post. They only break stuff if you have installed a different kernel by selecting a specific file version instead of installing the generic linux-<kernel version> metapackages.

So there is no need for any warning about kernel updating other than the one you get now after update that tells you to reboot to start using the updated kernel.


Wrong. They SHOULD only break if you have installed a different kernel by selecting a specific file version instead of installing the generic linux. or indeed, if you have installed the nvidia driver from their website and compiled your own kernel module. However, because the restrcited modules aren't update at the same time as the kernel they are incompatible and you loose the ability to start X.

The updates should either be released simultaneously, or, the update manager shouldn't update the kernel until the restricted modules are available (assuming they'er installed of course).

---

### Post by gamma on 2006-08-03
I had a similar issue where restricted modules for kernel-xxx-ubuntu26 didn't exist yet, and they were stuck on restricted-xxx-ubuntu23. I'm guessing this is what broke your system. I usually double check before doing a kernel update now to see if there is a restricted module being updated. If I don't see one usually a resync will make it appear. Kernel upgrades in Ubuntu shouldn't be anything to worry about. I've found as long as you're using the default repos + multiverse and universe you'll have a pretty damn stable system. If you want to see update issues go switch to Gentoo. In the past there have been updates released that broke the system like an incompatible version of tar,  binutils or hotplug that caused a kernel panic on startup.

Kinda OT, but I recently switched back to the standard nv drivers. They're opensource, they work well with hibernate  and they're stable. There are a few bugs I have with them, but there are also some annoying bugs I've got with the nvidia drivers too... If you're not a gamer remove the restricted modules and switch to nv :P.

---

### Post by viciouslime on 2006-08-03
Unfortunately I like my games :( Also, the nv driver doesn't control the fan speed on my grpahics card so it always sounds like it is going to take off.

You're right though, that is what would break it and yes, after a day or so, the restricted modules do become available. That is why this time I have chosen not to update the kernel, I will wait for the restrcited modules to become available. What I am trying to say is, for people who are new to linux/ubuntu they won't be expecting this. It will say there are updates available, they will click "update" and voila, one broken system.

It caught me the last two kernel updates, but this time I was aware. your average user will not be though, no matter how many updates they do. I know that when I leave for uni next year, I couldn't leave my parents a computer with ubuntu on it if there was any chance that X would fail to start for them.

---

### Post by nocturn on 2006-08-03
I have an Nvidia card too (with restricted drivers) and I never had this problem after Hoary...

restricted modules have always been released at the same time the kernel was for me.

Strange...

Do you have an older Nvidia card?  They have a different driver package if I'm correct.

---

### Post by viciouslime on 2006-08-03
No, it's a 7800GT. Maybe you've just not got the kernel update until a day or so after it had come out, by which time the restricted modules would be out too.

---

### Post by Bigglez on 2006-08-03
Happened to me (again):mad: 

I am officially on Kubuntu 6.06 now - have spent 2 days updating it.

This morning nvidia driver worked fine.
Tested confirmed.

Later I did an update. something-kernel-something was in the list.
I said, "Nah. It'll be okay."
(Did stupid damn thing * see end)
Rebooted machine. 
No X.
](*,) 

Had to remove 'nvidia' to 'nv' before I could startx.

Uninstalled nvidia-glx and co.
Reinstalled them.

When I run startx from command line it says "Cannot find nvidia module"

H.A.N.D

This has happened on other machines I have installed. Now when one comes in I *DREAD* updating it because it's guaranteed to stuff the nvidia driver up.

(* Stupid thing I did)
Before I restarted I got all hyped on the GLX/compriz thing that I installed a bunch of stuff (followed a thread's instructions) and changed a few things in xorg and other places.

So, perhaps it was this that stuffed me, this time ... I don't think so, however.

Anyway. I am shocked that Kubuntu cannot degrade to an X of some kind when it can't find the nvidia module.

As viciouslime says, I can't leave this distro in non-geek hands - it will break and shock.

Any ideas?
Any suggestions?

PS - How do I boot from a previous kernel?

---

### Post by Robor on 2006-08-03
I've had kernel updates break my wireless (Intel Pro 2200BG) in Breezy and Dapper.  Dapper worked flawlessly 'out of the box' for me on my IBM T42.  I updated the kernel and it broke my wireless.  Usually I just go through the process of installing the latest driver, ieee80211, and firmware.  The previous kernel update broke my wireless and even going through the reinstall didn't work.  The wireless adapter is recognized but doesn't see my access point.  I've been to lazy to try again so I'm using the wired adapter.

That said, it's BS that updating the OS breaks things like this.  If Windows Updates broke things in this manner Microsoft would be taking it from all sides.  Linux does it and it's generally accepted.  Can you say double standard?

---

### Post by Bigglez on 2006-08-03
I don't like to moan at any Linux or OSS, so I won't go that far. I would say it's just a "to-do". For sure.

---

### Post by Bigglez on 2006-08-03
Anyone know how I can boot from a previous kernel version in Kubuntu?

---

### Post by Ramses de Norre on 2006-08-03
Install an older kernel (should be installed because kernel upgrades don't replace older kernels) and choose the entry for it in grub.. It should be there if you didn't delete the older kernel.

And for the kernel upgrades: I made a script of my own which takes care of all recompiling and reinstalling when a new kernel is installed (only my webcam driver for now), I only have to run "kernel_upgrade" when my kernel is upgraded and everything works again.

---

### Post by Bigglez on 2006-08-03
You know, on this subject:
Can anyone give us the lowdown on the situation?

The essential question is:
How do we delay the installation of a new kernel until the appropriate nvidia drivers are ready for that new kernel number?

Is there a way to control apt so that it will do this automatically?

If not:

Is there a way to cause X to fail gracefully on a restart when the nvidia version is out of synch with the kernel version?

---

### Post by viciouslime on 2006-08-03
Exactly, and if not, please can we get it in edgy?

---

### Post by mlind on 2006-08-03
Use APT to pin certaing packages (like kernel) or don't enable dapper-updates reposity at all, only dapper-security.

---

### Post by orb9220 on 2006-08-03
Other questions on these lines.

Why do they have a tab for changes in updater and nobody uses it. Would be nice especially for kernel and system critical files. And where would post out suggestions to do so?

And on kernels I have a P4 1.3ghz. with sse2 etc.. should I be using a differnt kernal than the 386? I am looking for stability and  compatability over speed.

Thanks

---

### Post by mlind on 2006-08-03
> **orb9220 said:**
> Other questions on these lines.

Why do they have a tab for changes in updater and nobody uses it. Would be nice especially for kernel and system critical files. And where would post out suggestions to do so?

And on kernels I have a P4 1.3ghz. with sse2 etc.. should I be using a differnt kernal than the 386? I am looking for stability and  compatability over speed.

Thanks

changelog information is actually always provided, but it's not available for fresh updates for some reason. Usually after few hours after the update has been release, update-manager finds the changelog from Ubuntu server.

You can also view these later:
```

aptitude changelog *package*

```

There's no major difference between 386, 686 or k7 kernels, at least speed-wise. What I've understood, 386 kernel users have had less worries than 686 or k7 users.

---

### Post by orb9220 on 2006-08-03
Thanks for the info

---

