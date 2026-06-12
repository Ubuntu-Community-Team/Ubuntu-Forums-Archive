---
title: "Advantages Of Building Your Own Kernel?"
date: 2008-03-16
forum: General Help
---

### Post by solarwind on 2008-03-16
I've heard of distros like ArchLinux which optimize their kernel for i686, making it significantly faster than Ubuntu's relatively sluggish i386 kernel. Is it worth the effort to recompile your own kernel? Will it break my ATI drivers? Can I always revert to my old kernel?

---

### Post by Rocket2DMn on 2008-03-16
I think the newer kernels automatically tweak for i686, so in that respect you don't need to compile your own kernel.  Other advantages though would be trying to make your kernel leaner by disabling unnecessary modules and components.  In general, you don't need to - I don't feel that it's worth it.  And yes, you can always revert to your old kernel - it would be listed in GRUB.  It may break drivers if you compiled or are running restricted drivers, but those can be redone to match the newer kernel.

---

### Post by solarwind on 2008-03-16
> **Rocket2DMn said:**
> I think the newer kernels automatically tweak for i686, so in that respect you don't need to compile your own kernel.  Other advantages though would be trying to make your kernel leaner by disabling unnecessary modules and components.  In general, you don't need to - I don't feel that it's worth it.  And yes, you can always revert to your old kernel - it would be listed in GRUB.  It may break drivers if you compiled or are running restricted drivers, but those can be redone to match the newer kernel.

Thanks for the reply. Are you saying that the newer vanilla kernels auto optimize or the newer builds of Ubuntu?

---

### Post by Rocket2DMn on 2008-03-16
I believe that is correct - I think they automatically detect at runtime what type of processor you are using.  This is what I've been told when I inquired about compiling a 686 kernel.  
To get a true performance increase, the programs you are running would probably need to be compiled for i686 anyway.  Either way, I don't think you are likely to see much, if any, performance gain.

---

### Post by solarwind on 2008-03-17
> **Rocket2DMn said:**
> I believe that is correct - I think they automatically detect at runtime what type of processor you are using.  This is what I've been told when I inquired about compiling a 686 kernel.  
To get a true performance increase, the programs you are running would probably need to be compiled for i686 anyway.  Either way, I don't think you are likely to see much, if any, performance gain.

What is correct? The vanilla kernel or the Ubuntu kernel?

---

### Post by Rocket2DMn on 2008-03-17
The vanilla kernels do that and Ubuntu uses kernels that are new enough to take advantage of that.  I don't know in what version they started autodetecting your processor, but we use that functionality now in Ubuntu as well.

---

### Post by Arthur Archnix on 2008-03-17
I've installed Arch to see the performance gains, and was underwhelmed. Others report being amazed. I think it's a good idea to have a spare partition where you can experiment with different distros, but everything has a cost. Ease of use in ubuntu costs you in terms of performance. Speed in Arch costs you in terms of ease of use. 

As for the advantages to building your own kernel, you own Linux education is the strongest in my opinion. If you're only interest is in improving the performance of Ubuntu I'd suggest you begin by learning to remove uneeded packages and services without breaking your system.

---

### Post by Rocket2DMn on 2008-03-17
Agreed, you will see much more of a performance gain by disabling unneeded services and what not.  I suggest using "bum" - Bootup Manager.  I don't recall if it comes preinstalled in Gutsy, but you can run
```
sudo apt-get install bum
``` to make sure you have it and you can access it from System->Administration->Bootup-Manager.  It is much more powerful than the Services program under System->Administration.
Disabling such services as Bluetooth, APMD, and nvidia-kernel (if you dont have an nvidia card) help.  You can also check the box for Advanced and look under the Services tab for a few more.  The program allows you to start/stop services on the fly as well.

---

### Post by solarwind on 2008-03-17
> **Rocket2DMn said:**
> Agreed, you will see much more of a performance gain by disabling unneeded services and what not.  I suggest using "bum" - Bootup Manager.  I don't recall if it comes preinstalled in Gutsy, but you can run
```
sudo apt-get install bum
``` to make sure you have it and you can access it from System->Administration->Bootup-Manager.  It is much more powerful than the Services program under System->Administration.
Disabling such services as Bluetooth, APMD, and nvidia-kernel (if you dont have an nvidia card) help.  You can also check the box for Advanced and look under the Services tab for a few more.  The program allows you to start/stop services on the fly as well.

Very useful information. Thanks! I will also experiment with ArchLinux and a Gentoo based distro like Sabayon to see which one has the best performance.

---

### Post by Rocket2DMn on 2008-03-17
No problem.  I've heard good things about Arch and my roommate has used Gentoo - it was a lot of work to setup, but he likes it and is happily awaiting the next release.

---

