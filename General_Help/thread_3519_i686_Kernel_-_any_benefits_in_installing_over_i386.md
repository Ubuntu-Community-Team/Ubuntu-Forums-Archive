---
title: "i686 Kernel - any benefits in installing over i386 with R50 Thinkpad?"
date: 2004-11-06
forum: General Help
---

### Post by rockyrobin on 2004-11-06
Hi,

I've been running my Ubuntu install great for a week now with no problems and was wondering if its worth the bother of changing my kernel from i386 to i686?

Chris

---

### Post by wallijonn on 2004-11-06
You can just add the i686 kernel and it will automatically add it to GRUB. Then you can choose whichever kernel you prefer. You can remove it through SPM to go back to your i386 kernel.

---

### Post by jdong on 2004-11-06
Theoretically the i686 kernel should be faster on a supported processor. However, I've never been able to feel the differences compiler optimizations make ...

---

### Post by rockyrobin on 2004-11-06
Sounds like it may be worth a looksee.
I've just been sniffing through Synaptic Package Manager and it lists -
linux-image-2.6.8.1-3-686
linux-image-686

Which of these should I be apt-get installing?

Using one of the above - will I have do to any post configuration?
I've only used lilo before and only used Slackware so am unfamiliar with working with Kernel's this way.

Will I have to reconfigure any config files or devices in any way?

I would hate to hose my install after having such a pleasent experience thus far.

---

### Post by jdong on 2004-11-06
They're the same package, actually. Linux-686 is a virtual package that links to the latest kernel version that's compiled for the 686, while the other refers to a specific version of the kernel. Flip a coin!

---

### Post by rockyrobin on 2004-11-06
thanks :)

Looks like linux-image-686 it will be then  \\:D/ 
I cannot believe it can be this easy as picking this one package in synaptic.
If this goes without a hitch i'll eat my pants.

Cheers,

Chris

---

### Post by rockyrobin on 2004-11-06
hehe,

Think i'll pass on the pants as it worked out fine.
Happy bunny :)
Thanks for your help.

Warm regards,

Chris

---

### Post by mduduzi on 2004-11-06
I installed the K7 kernel, after booting off it without any issues, I removed the 386 kernela and the thransition was just that, nothing to report -just worked.
Just to play it safe though, at the same time that I marked the 386 for removal, I mark the K7 for re-installation.

---

### Post by wallijonn on 2004-11-06
[QUOTE=rockyrobin]I cannot believe it can be this easy as picking this one package in synaptic.[/QUOTE]

It's what makes Ubuntu great. Notice how it didn't spend hours re-compiling? There were no scrolling realms of virtual pages. It does its thing in seconds and all you had to do was select, apply, exit, reboot.

I love Ubuntu.

---

### Post by jdong on 2004-11-07
Yeah, and the Ubuntu kernels are fine just the way they are!

---

### Post by mark on 2004-11-07
[QUOTE=jdong]Yeah, and the Ubuntu kernels are fine just the way they are![/QUOTE]
And the good news is that anybody that just *has to* diddle the kernel files still can!  Uh, I can't seem to find that option in the version of Microsoft Windows 2000 that I'm running...<g>

---

### Post by Julius on 2004-11-07
I have installed the i686 kernel package and it won't start X server (it will boot normally, and will try to start X server like three times before telling me it can't load). Does this have something to do with nvidia drivers? 

Any help would be appreciated ;)

(Shall I create a new post for this?)

---

### Post by rockyrobin on 2004-11-07
[QUOTE=Julius]I have installed the i686 kernel package and it won't start X server (it will boot normally, and will try to start X server like three times before telling me it can't load). Does this have something to do with nvidia drivers? 

Any help would be appreciated ;)

(Shall I create a new post for this?)[/QUOTE]

Julius - How many packages did Synaptic/APT download?

---

### Post by Julius on 2004-11-07
I don't remember, is there any log to check this?
I think it was 3-4 packages

---

### Post by kensai on 2004-11-07
[QUOTE=Julius]I don't remember, is there any log to check this?
I think it was 3-4 packages[/QUOTE]
 Yes it is the nvidia driver just do this. Install the linux-restricted-modules-686 they are in apt and reboot now Nvidia driver will work and you can start X just Fine.
PS. I figured this out just some hours ago, I was having the same prob. ;-)

---

### Post by Julius on 2004-11-07
Muchas gracias!
Now it has booted perfectly! ;) (And I think the hotplug subsytem thing takes even longer to start :P)

;)

---

### Post by jdong on 2004-11-07
LMAO, imagination....

---

### Post by kensai on 2004-11-08
[QUOTE=Julius]Muchas gracias!
Now it has booted perfectly! ;) (And I think the hotplug subsytem thing takes even longer to start :P)

;)[/QUOTE]
Denada!
Hotplug? I see no diference :wink: but I don't have 686 I have the AMD K7 kernel  \\:D/

---

