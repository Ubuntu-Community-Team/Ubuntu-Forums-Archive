---
title: "Getting Ubuntu to recognise 2nd core"
date: 2006-11-18
forum: General Help
---

### Post by lazerradial2003 on 2006-11-18
When i initially installed ubuntu on my dual core box, i disabled IOAPIC to get round one of the early problems with edgy and Core 2 processors, apparently there is a work around (disabling USB legacy keyboard support or something), is there anyway i can try this workaround, without completely re-installing the system. 

I can enable IOAPIC now but ubuntu doesnt seem to automatically detect the second core, any suggestions on what to do here.

I would also very much like the option to go back on any changes i make in the event of it not working.

Thanks, lazerradial

---

### Post by janbockaert on 2006-11-18
Did you install the smp-kernel? I only had a problem with dual core during install. After i upgraded a clean dapper install, i could install the smp kernel without any problem, and i'm working on both of my cores.

---

### Post by lazerradial2003 on 2006-11-18
I'm not sure, i just installed from one of the dailies, i can now get the live CD to boot using the workaround, and the sys config there shows two processors, is their a terminal command that i can use to double check that only one core is being detected in my current install?

If so si there a way of re-installing / compiling the kernel or something which will make it detect the second core without re-installing the whole system?

Thanks, lazerradial

---

### Post by lolocaust on 2006-11-18
Have you tried using synaptic to install a new kernel with -smp at the end of the name?

---

### Post by Grog140 on 2006-11-18
If your using Edgy then from my experience it should recognize both cores with the generic kernel. At the Grub boot menu if you see a 386 kernel, anything without smp at the end or something that says generic and you are running edgy then do this:

"sudo aptitude install linux-generic"

If you are running dapper and there isn't an smp kernel then do this:

"sudo aptitude install linux-686-smp"\

Should work

---

### Post by lazerradial2003 on 2006-11-18
Cheers, i'm running Edgy but using LILO not GRUB, is there another way i can find out whether im running the smp kernel or not?

---

### Post by NetworkGuy on 2006-11-18
By default, Edgy uses a SMP kernel.

From a terminal type ```
uname -a
``` to see exactly what kernel you are using.

---

### Post by lazerradial2003 on 2006-11-19
thanks for all the replies,i get the following when i enter uname -a:

Linux ubuntu 2.6.17-10-386 #2 Fri Oct 13 18:41:40 UTC 2006 i686 GNU/Linux

so should i do this:

"sudo aptitude install linux-generic"

as suggested earlier in order to try and get it to recognise the second core? 

cheers, lazerradial

---

### Post by lazerradial2003 on 2006-11-19
update, i've now tried installing linux-generic and theres no change as far as i can see.Does anyone know how can i check for sure whether the two cores have been detected or not? I'm using kde not gnome, it was easy in gnome lol.  

Thanks for the help so far, lazerradial

---

### Post by der_joachim on 2006-11-19
> **lazerradial2003 said:**
> update, i've now tried installing linux-generic and theres no change as far as i can see.Does anyone know how can i check for sure whether the two cores have been detected or not? I'm using kde not gnome, it was easy in gnome lol.  


Sure. Open a Konsole, and use the command *top* . With the *1* key 
you can toggle specification by CPU.

---

### Post by andyrobo60 on 2006-11-19
run "sudo apt-get install linux-686-smp" and it should be running on both cores. 

Do you have an app to tell you how much you are using your cpu (i use system monitor in gnome). that should list both cores.

---

### Post by lazerradial2003 on 2006-11-19
thanks, 1 seems to toggle between cpu0 and cpu(s), the latter showing different threads to the first, does this mean both cores are being used? i would have expected it to have cpu0 and cpu1...?

thanks, lazerradial

---

### Post by lazerradial2003 on 2006-11-19
what changes exactly are being made if i run:

sudo apt-get install linux-686-smp

mainly will this pgrade by 32 bit edition of egdy to 64bit, im trying to avoid 64 bit for now because of the associated compatibility problems....

the description for this package in synaptic says:

Obsoleted by: linux-image-generic
This package is for upgrades only.

which concerns me slightly lol. 

thanks, lazerradial

---

### Post by janbockaert on 2006-11-21
no it will not upgrade to 64 bit, it will install multi-core support. This is the kernel you need! go in synaptic, search for -smp, and install the kernel. make sure you boot in the -smp (or generic) kernel. In Grub, you need to make it the default, no idea how this works in lilo.

---

### Post by lazerradial2003 on 2006-11-21
Ok, in the end i re-installed my whole system, which sorted out the problems i was having with the 2 cores and power management. I now have two questions, firstly which linux-restricted-modules should i use, i tried the -generic one and had a lot of problems, uname -a returns the following, should i be using the 686 version? 

Linux ubuntu 2.6.17-10-generic #2 SMP Fri Oct 13 18:45:35 UTC 2006 i686 GNU/Linux

Secondly is there an easy way of creating some sort of restore CD which will restore my root partition to an exact specified state AND restore the correct LILO coniguration to the MBR and so-on... 

Thanks, lazerradial

---

### Post by janbockaert on 2006-11-22
as far as i know, the generic kernel is a dummy package, that let ubuntu choose the right kernel (somthing new in edgy). So if you have dual core, generic will be the same kernel as 686-smp. i don't have my laptop here, so i can't check what restricted modules i have installed (but i suppose it is genereric). i guess that installing 686 or generic will make no difference.

Maybe your problems are lilo related? however, i can't help you with lilo, never used it.

---

### Post by lazerradial2003 on 2006-11-22
Thanks for the reply, I guess I'll just have to continue experimenting with the NVIDIA stuff, need to find a way to make an easy to restore disk first since having to re-install every time it all goes wrong is getting tedious!

---

