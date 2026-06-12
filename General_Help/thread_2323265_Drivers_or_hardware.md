---
title: "Drivers or hardware?"
date: 2016-05-04
forum: General Help
---

### Post by Laura_Nbl on 2016-05-04
Hi 

So my Acer Aspire E 15 recently started having immense problems (as in completely freezing and causing me to have to hard reboot it) and it won't respond to ANY keyboard shortcuts or anything. It started crashing about two weeks ago and it keeps getting worse (as in, a minimum of 3 times a day). I have installed a temperature and CPU monitor and the average temperature is around 74°C with CPU percentage about 40%. I am currently using Xenial Xerus, but this had started when I was still using Trusty. The very first time it crashed there was a black screen with an error log but I didn't catch what it said (just lots or ERROR and Oops messages) but now it just freezes and the fan is *really* loud. I am not really good at IT but I can paste logs here if somebody gives me instructions on how to find them. Oh, and my mom's laptop (same model and age) has just had the same problem for the first time today. I am doing an online school so I would *really *appreciate if somebody could help me :)

Thank you!

---

### Post by Linuxisfast on 2016-05-04
Boot off live CD/USB and do a RAM test, also check HDD SMART status under Gnome Disks.

---

### Post by Laura_Nbl on 2016-05-04
Ok, I'll find out how to do that. What should I report once I did?

---

### Post by mastablasta on 2016-05-04
well if RAM test fails - you need to replace the RAM. If SMART test failes you need to replace HDD.

also check for drivers if good ones are installed. if problem suddenly appeared (not after some kernel update or similar) then it is some other hardware error. backup your data and get it fixed at PC service or get a new PC. 

if problem appeared after a certain system update then try booting with older kernel (hold shift on boot to get old kernel menu). if the issue is kernel and drivers you need to report it on launchpad so osmeon can fix it.


dmesg command will print out any error messages on boot.

/var/log/ folder contains various system logs including error logs and GPU error logs. look into those as well. if there are some noticable errors then paste those here using the code tags (the # icon in advanced reply screen) or just attach the whole log ot the post. there are various GUI viewers available if one is not already preinstalled.

read more on error logs here: [https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)

---

### Post by Bucky Ball on 2016-05-04
... and as an afterthought: how old are the machines and when is the last time they had a good clean out with a can of compressed air?

As your first priority, before going much further (unless that's trying the compressed air, take the back off and blow out everything) I would boot from the install media (the USB or disk with the Ubuntu installer on it) and 'Try Ubuntu'. When at a desktop, back up anything you don't want to lose from the laptop hard drive to an external one or USB stick . Then move on.

Avoid using that hard drive unless you are backing stuff up or trying to fix while booted from a live session as you don't know whether it is that or not at this point.

---

### Post by Laura_Nbl on 2016-05-04
Well the RAM test passed, but when I tried to exit my computer crashed. The SMART test also passed but 'Airflow Temperature' has 'failed in the past'.

---

### Post by Bucky Ball on 2016-05-04
> **Bucky Ball said:**
> ... and as an afterthought: how old are the machines and when is the last time they had a good clean out with a can of compressed air?

Did you say airflow temerperature??? :|

You didn't answer the questions in my original post, but my guess is this is an older machine that's never seen compressed air, had the back panels off and a good blow out or had the air vents cleaned. Have a look at the air vents. See anything? Wads of dust for instance? Something's blocking the airflow in there and if you don't find out what, you might not have damaged hardware now but you will have sooner or later. Probably sooner.

---

### Post by Laura_Nbl on 2016-05-05
Right, I'll do that. But they're only 1.5 years old, otherwise I would've done it already.

---

### Post by Bucky Ball on 2016-05-05
Is it in a dusty spot? Can you actually see anything there in the vents in the side of the computer? It is up off the desk and on its rubber stoppers and not on a cushion, pillow, bedclothes, bean-bag or other soft surface!? (Or a lap with bulky clothing.) 

In other words, the side vents are clear of obstructions and the machine has some distance between it and the surface you're using it on? Blow out seems the next option if the RAM and hard drive check out, which they have.

---

### Post by mastablasta on 2016-05-05
i get dust buildup in about 6 months maybe even less (PC is always on + a main road is near my appartment).

it also depends on how often you vacuum the room. 

laptops are smaller and are even more problematic in this regard as the air has less pace to move in the first place.

---

### Post by Laura_Nbl on 2016-05-05
Yes, my room is quite dusty. It is usually on a desk, standing directly on the desk, and while some crashes happen while it is there, most of them do happen when I'm watching a movie in bed (with the laptop on my lap/blanket). I have cleaned/blown out the laptop now and, thank goodness, it still works. Noob+motherboard = bad idea. I will report tomorrow whether that was the problem or not.

---

### Post by mörgæs on 2016-05-05
> **Laura_Nbl said:**
> With the laptop on my lap/blanket.

Since most laptops have their air intake on the underside this will effectively make your laptop a vacuum cleaner for the dust and lint in bed. 

Youtube have many good videos showing how to tale hardware apart for cleaning. Take a look and see if it is difficult for your model.

---

### Post by pqwoerituytrueiwoq on 2016-05-05
> **Laura_Nbl said:**
> Well the RAM test passed, but when I tried to exit my computer crashed. The SMART test also passed but 'Airflow Temperature' has 'failed in the past'.

'Airflow Temperature' has 'failed in the past' not a fatal issue, given it is not good for that to happen, it just means it has gotten too hot in the past due to a poor (or clogged) cooling system, both are common for laptops
i'd start with a can or air and smite some dust bunnies

---

### Post by Laura_Nbl on 2016-05-05
Alright, so the dust was *not* the problem. It just crashed again. I checked the core temp just a few moments before it crashed and it was at about 50°C, just like it has been all morning since I cleaned it. Now, after I have re-booted it, the core temps are at about 73°C. What could possibly be causing such a heat surge? It wasn't even working hard (just firefox, updates and the system monitor).

---

### Post by Bucky Ball on 2016-05-05
Were you using it in bed? Flat surface only. If you're using it in bed, use a tray, not bedclothes or a pillow. If not, its puzzling what is causing the heat issue now we seem to have ruled out the obvious.

@pqwoerituytrueiwoq: Best read previous posts prior to posting. What you're saying is what's been discussed and has been done. ;)

---

### Post by Laura_Nbl on 2016-05-05
No, it was on my desk. And my room is quite cool as well, so I have no idea what could be causing this.

---

### Post by Laura_Nbl on 2016-05-06
Oh, and something else I noticed is that when I suspend my laptop there is a 80% chance that it will crash and 'shutdown' actually restarts the computer. As in, I click on shutdown and have to wait until it shut down, then quickly close the laptop or else it will boot again.

---

### Post by Bucky Ball on 2016-05-06
I can't see that anyone's asked, but perhaps they have and you've told us, apologies if that's the case, and it may not be directly related to your actual problem, but what release and flavour of Ubuntu are you using?

---

### Post by Laura_Nbl on 2016-05-06
Ubuntu 16,04. Xenial Xerus. But the crashing started when I was still using Trusty Tahr.

---

### Post by nukedathlonman on 2016-05-06
Does your notebook by chance an AMD "Carrizo" based APU (AMD A8-8600P, A10-8700P, FX-8800P)?

---

### Post by Laura_Nbl on 2016-05-06
After a long and intensive consultation with Mr. Google (even  scanning italian sites) - I still have no idea how to find that out.  Honestly, from what I've read, an APU is a CPU and a GPU in one? And AMD  is a company that produces those? All I can tell you is that my laptop  has an Intel Pentium quad core processor (N3530) and Intel HD graphics.

---

### Post by leunam12 on 2016-05-06
For proper cleaning of the fan and exhaust fins you have to remove the keyboard and then blow compressed air from the exhaust vents into the laptop. Don't do it inside the house since it will probably blow a lot of dust out. Check the video below for disassembly instructions, you only have to watch the first minute and 15". You don't have to remove any of the ribbon cables, all you have to do is keep the palmrest/keyboard panel raised an inch or so to allow the dust to escape.

[https://www.youtube.com/watch?v=DpawPQrqIq4&feature=iv&annotation_id=annotation_1091133151&src_vid=ysEMjTPp4hA](https://www.youtube.com/watch?v=DpawPQrqIq4&feature=iv&annotation_id=annotation_1091133151&src_vid=ysEMjTPp4hA)

---

### Post by Laura_Nbl on 2016-05-06
I did that. I wanted to take out the fan though, because according to the Internet one should. So I unplugged all the ribbon cables and wanted to take out the fan, but my laptop has a really sucky design where the entire motherboard needs to be taken out to remove the fan, so I just left it inside and blew out the whole thing.

---

### Post by Laura_Nbl on 2016-05-06
Woah, I just re-read your post and it now has a different meaning. I should raise the keyboard and then blow air in from the exhaust vents? Wouldn't that rev (not the right word, but I can't think of the right one) the fan up to unhealthy speeds though?!

---

### Post by QLee on 2016-05-06
> **Laura_Nbl said:**
> After a long and intensive consultation with Mr. Google (even  scanning italian sites) - I still have no idea how to find that out.  Honestly, from what I've read, an APU is a CPU and a GPU in one? And AMD  is a company that produces those? All I can tell you is that my laptop  has an Intel Pentium quad core processor (N3530) and Intel HD graphics.

Hello Laura, when you were searching with Mr. Google did you happen to find anything about the "Bay Trail" processors like yours and intermittent freezes?

This is what I have about the "Bay Trail":

The "Bay Trail" processors and MBs that have them embedded at the present time often need to disable some of the powersaving features in order to not have those random freezes. The kernel developers are working on the problem. [https://bugzilla.kernel.org/show_bug.cgi?id=109051](https://bugzilla.kernel.org/show_bug.cgi?id=109051) Some BIOS have a setting where you can disable the cstates and you could do it there if your MB will allow it. Remember what you have done so you can remove it once they deal with the problem.

If you encounter random freezes on a board that has one of those processors try adding intel_idle.max_cstate=1 to the GRUB line that boots your system. I wouldn't use it on any other family of processor. You can find a list at: [http://ark.intel.com/products/codename/55844/Bay-Trail](http://ark.intel.com/products/codename/55844/Bay-Trail)

For example: in the file /etc/default/grub  
change the line 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" 
to 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash intel_idle.max_cstate=1" 

and then ```
sudo update-grub
```, reboot to use it. Test by opening a terminal and entering: ```
cat /sys/module/intel_idle/parameters/max_cstate
```, it will return a number, 1 if you have done it correctly.


It will make your system use a bit more power and thus likely generate a bit more heat but not a huge difference.

Remember what you have done so you can remove it once they deal with the problem. <--------- *

[Edit] To answer your original question, I would consider this problem currently a hardware limitation, but classifying it doesn't really help.

---

### Post by Laura_Nbl on 2016-05-06
It doesn't say "quiet splash", is says ```
"$GRUB_CMDLINE_LINUX_DEFAULT crashkernel=384M-:128M"
``` 
Should I still change it?

Also, I googled and followed your links and that does seem to be my problem, but I didn't find anything about temperature in those posts. Mine is usually at about 70°C, would generating more heat not be a problem then?

---

### Post by QLee on 2016-05-06
> **Laura_Nbl said:**
> It doesn't say "quiet splash", is says ```
"$GRUB_CMDLINE_LINUX_DEFAULT crashkernel=384M-:128M"
``` 
Should I still change it?

Also, I googled and followed your links and that does seem to be my problem, but I didn't find anything about temperature in those posts. Mine is usually at about 70°C, would generating more heat not be a problem then?

That is not a standard line, you must have had a reason for it to get like that., maybe something related to this old bug. [https://bugs.launchpad.net/bugs/1318111](https://bugs.launchpad.net/bugs/1318111) Only you can know what you did and why.

It is your choice whether you want to try the boot parameter or not.

[Edit] I looked up the Intel N3530 for you and the package specification states: TJUNCTION 	100°C

---

### Post by Laura_Nbl on 2016-05-06
But will it do the same thing?

According to: 

[http://askubuntu.com/questions/542469/crashkernel-is-still-being-added-by-update-grub-after-removing-linux-crashdump](http://askubuntu.com/questions/542469/crashkernel-is-still-being-added-by-update-grub-after-removing-linux-crashdump) 

that line is there because I installed crashkernel. I de-installed it now, but the line is still there. 

Nevermind, that is what you said...

---

### Post by Bucky Ball on 2016-05-06
After you change anything in /etc/default/grub you must run save and close the file, then run

```
sudo update-grub
```

... for the changes to stick. 

Make that line look like this:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
```

... replacing 'nomodeset' with whatever option you're using if you're using another.

---

### Post by QLee on 2016-05-06
> **Laura_Nbl said:**
> But will it do the same thing?

According to: 

[http://askubuntu.com/questions/542469/crashkernel-is-still-being-added-by-update-grub-after-removing-linux-crashdump](http://askubuntu.com/questions/542469/crashkernel-is-still-being-added-by-update-grub-after-removing-linux-crashdump) 

that line is there because I installed crashkernel. I de-installed it now, but the line is still there. 

Nevermind, that is what you said...

That link also tells how to make the line stop occurring, it seems that when you installed and then uninstalled, it left a file in /etc/default/grub.d, as per the answer with the checkmark in the green circle.

---

### Post by Laura_Nbl on 2016-05-06
The file is read-only and I don't know how to change it.

---

### Post by QLee on 2016-05-06
> **Bucky Ball said:**
> After you change anything in /etc/default/grub you must run save and close the file, then run

```
sudo update-grub
```

... for the changes to stick. 

Make that line look like this:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
```

... replacing 'nomodeset' with whatever option you're using if you're using another.

I don't think Laura has tried to change the file yet, still trying to decide if she wants to try the boot parameter I suggested.

---

### Post by QLee on 2016-05-06
> **Laura_Nbl said:**
> The file is read-only and I don't know how to change it.

With 
```
gksudo gedit /etc/default/grub
``` Assuming you edit with gedit, use the text editor you have and are familiar with if you have a flavour with a different default text editor. 

Be careful you will be working as root.

---

### Post by Bucky Ball on 2016-05-06
Or:

```
sudo nano /etc/default/grub
```

... is another option if the above doesn't work or you're using nano.

Don't forget the:

```
sudo update-grub
```

... once you save and exit the file. ;)

---

### Post by Laura_Nbl on 2016-05-06
Ok, I worked out how to change it and did. I will keep you updated on whether or not it works. Thank you for your help so far :)!

---

### Post by QLee on 2016-05-06
You are welcome!

Yes, please let us know when it stops the freezes for you and mark the thread solved when you are satisfied.

---

### Post by nukedathlonman on 2016-05-06
> **Laura_Nbl said:**
> After a long and intensive consultation with Mr. Google (even  scanning italian sites) - I still have no idea how to find that out.  Honestly, from what I've read, an APU is a CPU and a GPU in one? And AMD  is a company that produces those? All I can tell you is that my laptop  has an Intel Pentium quad core processor (N3530) and Intel HD graphics.

Yes, AMD is a competitor to Intel - so no, your not running an APU.  Just your problem sounded similar (not quite the same) to one I've been trying to track down and resolve.

---

### Post by Laura_Nbl on 2016-05-07
So far, there have been no more random crashes but there has been a suspend-induced crash. However, it's still to early to tell whether the random crashes have stopped completely.

---

### Post by leunam12 on 2016-05-07
> **Laura_Nbl said:**
> Woah, I just re-read your post and it now has a different meaning. I should raise the keyboard and then blow air in from the exhaust vents? Wouldn't that rev (not the right word, but I can't think of the right one) the fan up to unhealthy speeds though?!
I have never had any problems doing it that way, but if you are concerned about that you can stop the fan from spinning with your finger. but the dust that is stuck in the fins is usually compressed there and won't come out if you blow in the other direction.

---

### Post by Laura_Nbl on 2016-05-08
Ok, so apparently there are no more random crashes *yay*, but it still aways crashes when I try to suspend/close it. Also, 'shut down' still restarts the computer.

---

### Post by Laura_Nbl on 2016-05-09
Should I start a new thread with this problem?

---

### Post by mörgæs on 2016-05-09
Better to search the existing threads dealing with the same problem. Quite a lot has been written.

---

### Post by Laura_Nbl on 2016-05-09
Oh, will do.

---

### Post by Bucky Ball on 2016-05-09
> **Laura_Nbl said:**
> Ok, so apparently there are no more random crashes *yay*, but it still aways crashes when I try to suspend/close it. Also, 'shut down' still restarts the computer.

> **Laura_Nbl said:**
> Should I start a new thread with this problem?

Yes please. Mark this one as solved, research your issue and post a new one if you can't solve and include anything you've tried or links you have questions about. Anything relevant to the problem and a descriptive thread title.

Thanks and good luck with it. ;)

(I actually thought I'd posted something similar to this last night but it was in the AM so ...)

---

