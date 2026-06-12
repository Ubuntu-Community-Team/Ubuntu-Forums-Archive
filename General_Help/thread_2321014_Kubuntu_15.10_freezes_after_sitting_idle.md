---
title: "Kubuntu 15.10 freezes after sitting idle"
date: 2016-04-19
forum: General Help
---

### Post by Infamshxr on 2016-04-19
Hey everyone. So I just installed Kubuntu 15.10 to replace Windows 7 because I kept getting a weird BSOD after doing file operations (copying/pasting/etc) over the network to and from my laptop. This computer is used as a file server mostly so I need stability. I'm working on figuring out some other issues right now, but two nights in a row I've noticed when I go to use the computer in the morning, it's frozen. Usually I have Firefox, terminal, and maybe system settings or Kate left open, since Ive been setting things up. But when it's frozen, the mouse cursor doesn't move, hitting NumLock doesn't turn it off or on, so the only thing I can do is painfully hold the power button down to shutdown and turn it back on again.

About the computer...
AsRock Q1900-ITX (embedded Intel Celeron J1900)
4GB G.Skill Ripjaws
Kingston V300 SV300S37A/120G 120GB SSD
Western Digital Blue WD10EZEX 1TB HDD (2 of these)
LG WH14NS40 Bluray Burner
Seasonic 360W Power Supply

I had issues installing Kubuntu and found I need to boot EFI and that fixed that problem. So now Kubuntu boots from the SSD in UEFI like apparently Win7 did. I think that's all the info I can think of atm.

I've seen older threads about a problem similar to mine, but they were much older versions of Ubuntu. Updating the kernal seems to fix the issue in other threads, but my system says it's up to date. Also, a lot of threads go unanswered or beyond my knowledge of Linux. Not sure what other info anyone might need to help figure this problem out, but just ask and I'll do my best to provide the info.

---

### Post by DuckHook on 2016-04-19
Don't rule out HW issues. If you got BSODs in Windows and now problems in different flavours of 'buntu, it seems too repetitive to be OS-related.

If you use as a file server, then consider getting rid of GUI and simplifying load and overhead. See if this helps.

Also, look through your logs filtering for anything obvious. If you need help reading them, feel free to post them back to this thread.

Install ssh-server so you can ssh into a frozen session.

As a last alternative try the REISUB method before forcing poweroff, especially with a server. Instructions [here]("https://en.wikipedia.org/wiki/Magic_SysRq_key").

---

### Post by Infamshxr on 2016-04-19
I thought of HW issues, but its a brand new PC. Everything seems to run fine when its running. I wouldn't know where to start. As for GUI, still need one as there are other things I do on it from time to time. 

Whats the commands to look at my logs?

I will install ssh-server, but once its frozen and I ssh in, then what?

I will give that REISUB a try next time it freezes. But what should I use CTRL+ALT+B? That's, to what I understand, the command to immediately reboot the system...

Or do I have to hit CTRL+ALT+R, then CTRL+ALT+E, then CTRL+ALT+I, then CTRL+ALT+S, then CTRL+ALT+U, then CTRL+ALT+B?

---

### Post by DuckHook on 2016-04-19
> **Infamshxr said:**
> I thought of HW issues, but its a brand new PC. Everything seems to run fine when its running. I wouldn't know where to start.Let's see how we can help with that...>  As for GUI, still need one as there are other things I do on it from time to time.Important to note that this requirement will conflict with the following...> This computer is used as a file server mostly ***so I need stability*** (emphasis mine).I do understand that the command line is intimidating and a lot of users want a GUI. However, it is important to note that GUIs increase complexity, resource usage, attack surface, malware points of entry (browsers are especially bad) and general things that can go wrong. This is why Linux servers always follow the KISS principle. People often note that Linux servers don't flatline as often as Windows servers; part of the reason is because Linux servers are usually sans GUI, so there's a lot less that can go wrong with them. If you really want a server where stability is the main goal, then you may wish to consider another machine (it doesn't have to be expensive if your main use is file server) for your server and free up your current one for client use.> Whats the commands to look at my logs?In Linux, logs are located in /var/log. You can view any of the important ones with a simple text editor. syslog and kern.log would be especially relevant in your case. You will need to wait for a freeze before looking at them because they are regularly compacted and rotated.> I will install ssh-server, but once its frozen and I ssh in, then what?ssh is a very powerful program that allows you to log in from another computer over the network. In case of a freeze, it may often be only the desktop environment that is frozen, but the underlying system is still fine. If you can ssh into the "frozen" computer, you can instruct it to safely shut down:```
sudo poweroff
```...or look at the logs before shutting down```
less /var/log/syslog
```You always want to shut down elegantly if you can. The danger in forcing a precipitous shutdown is especially significant with any sort of server. Files and databases can be corrupted if they happen to be open when you force a hard shutdown.> I will give that REISUB a try next time it freezes. But what should I use CTRL+ALT+B? That's, to what I understand, the command to immediately reboot the system...

Or do I have to hit CTRL+ALT+R, then CTRL+ALT+E, then CTRL+ALT+I, then CTRL+ALT+S, then CTRL+ALT+U, then CTRL+ALT+B?The key combo is not <Ctrl>+<Alt> but <Ctrl>+<Sysrq>. This is very important. <Ctrl>+<Alt> will do nothing. The <Sysrq> key on most modern keyboards is the <PrtScn> key which acts as one or the other depending on switches on some keyboards, or on whether things like <Shift> are held down (on most keyboards). The problem with going straight to <Ctrl>+<Sysrq>+<B> is that it doesn't clean up and unmount your drives before rebooting. In other words, it's little different from pulling the plug, which is what you are doing now. Always go through the REISUB sequence so that your computer has the chance to shut things down in an orderly and controlled fashion. Things won't get corrupted that way.

Since you have a GUI loaded, one possible situation comes to mind... disable your power manager. It may be that your machine is putting itself to sleep after a certain amount of time and not able to wake up properly upon revival (this is an example of why GUIs and servers just don't mix). Try this adjustment first to see if it works. But you should also still look through your logs and install ssh, because they all give you the chance to diagnose and shut down properly.

---

### Post by Infamshxr on 2016-04-20
Going to close the thread. I got fed up with Kubuntu cuz of some other issues I had and switched to Debian KDE, so far no problems like I had in Kubuntu. Thanks for the info, I appreciate learning new things and hopefully this will help me in the future. To answer some things about GUI and whatnot. Yes, this computer stays on 24/7. Does it need to be 100% foolproof stable? No, but I expect it to not randomly crash for no reason when it's not physically being used lol. If I make it crash, that's a different story. It was probably my fault lol! I'm definitely not experienced enough in Linux to be using it without a GUI. I can see disastrous results. Yes, I could go with a small footprint DE, but I really like KDE. Personal preference is all. So I'm gonna see how Debian KDE does sitting overnight. Hopefully all will be well. Thanks again!

---

### Post by QLee on 2016-04-20
> **Infamshxr said:**
> Going to close the thread. I got fed up with Kubuntu cuz of some other issues I had and switched to Debian KDE, so far no problems like I had in Kubuntu. Thanks for the info, I appreciate learning new things and hopefully this will help me in the future. To answer some things about GUI and whatnot. Yes, this computer stays on 24/7. Does it need to be 100% foolproof stable? No, but I expect it to not randomly crash for no reason when it's not physically being used lol. If I make it crash, that's a different story. It was probably my fault lol! I'm definitely not experienced enough in Linux to be using it without a GUI. I can see disastrous results. Yes, I could go with a small footprint DE, but I really like KDE. Personal preference is all. So I'm gonna see how Debian KDE does sitting overnight. Hopefully all will be well. Thanks again!

Well, no one is going to argue with you if you choose to change to Debian, however, if you encounter the same random freezes in Debian try adding intel_idle.max_cstate=1 to the GRUB line that boots your system.
i.e. in /etc/default/grub - GRUB_CMDLINE_LINUX_DEFAULT="quiet splash intel_idle.max_cstate=1" and then sudo update-grub

 The "Bay Trail" processors (like yours) and MBs that have them embedded at the present time often need to disable some of the powersaving features in order to not have random crashes. The kernel developers are working on the problem. [https://bugzilla.kernel.org/show_bug.cgi?id=109051](https://bugzilla.kernel.org/show_bug.cgi?id=109051) Remember what you have done so you can remove it once they deal with the problem. Some BIOS have a setting where you can disable the cstates and you could do it there if your MB will allow it. 

It will make your system use a bit more power and thus likely generate a bit more heat but not a huge difference.

---

### Post by DuckHook on 2016-04-20
> **Infamshxr said:**
> ...switched to Debian KDE...Hopefully all will be well. Thanks again!Best of luck. Debian is a good, solid and stable Distro. Hope all works out well for you.

---

### Post by Infamshxr on 2016-04-20
> **QLee said:**
> Well, no one is going to argue with you if you choose to change to Debian, however, if you encounter the same random freezes in Debian try adding intel_idle.max_cstate=1 to the GRUB line that boots your system.
i.e. in /etc/default/grub - GRUB_CMDLINE_LINUX_DEFAULT="quiet splash intel_idle.max_cstate=1" and then sudo update-grub

 The "Bay Trail" processors (like yours) and MBs that have them embedded at the present time often need to disable some of the powersaving features in order to not have random crashes. The kernel developers are working on the problem. [https://bugzilla.kernel.org/show_bug.cgi?id=109051](https://bugzilla.kernel.org/show_bug.cgi?id=109051) Remember what you have done so you can remove it once they deal with the problem. Some BIOS have a setting where you can disable the cstates and you could do it there if your MB will allow it. 

It will make your system use a bit more power and thus likely generate a bit more heat but not a huge difference.

Thanks for the tip! I'll keep that in mind if anything starts acting up. Although so far so good. It sat while I slept after work today and when I woke up to continue working on it, it was still OK. Not saying it won't happen, but so far so good. For the most part I'm liking Debian. Nice and solid, a lil different compared to Ubuntu, Kubuntu, and Mint, which is what I'm used to, but it's a learning experience. I just miss kde5. So pretty lol. All in good time, I suppose.
> **DuckHook said:**
> Best of luck. Debian is a good, solid and stable Distro. Hope all works out well for you.

Thanks, I'm hoping so too. Like I said above, so far so good and I'm liking it.

---

### Post by QLee on 2016-04-21
> **Infamshxr said:**
> Thanks for the tip! I'll keep that in mind if anything starts acting up. Although so far so good. It sat while I slept after work today and when I woke up to continue working on it, it was still OK. Not saying it won't happen, but so far so good. For the most part I'm liking Debian. Nice and solid, a lil different compared to Ubuntu, Kubuntu, and Mint, which is what I'm used to, but it's a learning experience. I just miss kde5. So pretty lol. All in good time, I suppose.

Yes, my "Bay Trail" froze less with Debian Jessie before I added the boot parameter, might be due to the older kernel. 

I assume you are using Debian stable so yes you will probably find some of the software "old" compared to the latest Ubuntu. There are backports for Debian stable but they aren't included in a default install. There are "branches" of Debian and the "testing" branch has the new software that is to be included in the next "stable", if you have a bit of skill and can tolerate occasional breakage, that might be of interest to you. There are several Debian forums too, sometimes not as polite as the forums here. You are correct, there will be a lot to learn.

I too wish you success.

---

### Post by Infamshxr on 2016-04-21
> **QLee said:**
> Yes, my "Bay Trail" froze less with Debian Jessie before I added the boot parameter, might be due to the older kernel. 

I assume you are using Debian stable so yes you will probably find some of the software "old" compared to the latest Ubuntu. There are backports for Debian stable but they aren't included in a default install. There are "branches" of Debian and the "testing" branch has the new software that is to be included in the next "stable", if you have a bit of skill and can tolerate occasional breakage, that might be of interest to you. There are several Debian forums too, sometimes not as polite as the forums here. You are correct, there will be a lot to learn.

I too wish you success.

Yes, running Stable 8.4 if I'm not mistaken. And yea, noticed a few KDE programs are old too, but I'll deal with it if it means it's going to be more stable. I don't physically use this computer enough anyways. It just sits on for my other devices to stream content off of and file sharing. Sometimes I need to use it to do stuff I don't like doing on my laptop or for research while I'm fixing another computer in my computer room. Just built this one a month or two ago. My last desktop (still running, but slowly dying) is almost 10 years old and still did what I needed it to do. I just wanted to build something low power so I can stop paying a crap ton to run the computer 24/7 lol. The old one I built for gaming on a budget at the time and energy savings weren't of any concern lol. As for the Debian forums, meh. I've been using the Ubuntu forums for so long, even when I had Mint a few years back. I'm used to it, most people are nice and treat not so advanced users like human beings. I can't stand rude people when I post a thread. Like if it was already asked and I didn't notice and they give me 'tude lol. Besides, most things on Debian kinda pertain to Ubuntu for the most part. IF not, I know how to Google ;-)

---

### Post by QLee on 2016-04-21
> **Infamshxr said:**
>  IF not, I know how to Google ;-)

I expect you will do, just fine. :-)

---

### Post by Infamshxr on 2016-04-21
Oh crap. I made an oopsie that I can't fix. When installing Debian alongside kubuntu I didn't realize kubuntu was EFI and Debian was not. So I had sdc1 which was the EFI boot partition, sdc2 which was kubuntu, sdc3 which was BIOS grub, and sdc4 which was Debian. So I wanted my space back from kubuntu, so I deleted the partitions for it, finding out I had to delete the grub partition in order to merge them, so I redid the partitions and got that the way I want, but now I can't figure out how to install grub one the new sdc1... I tried mounting it then using grub-install /dev/sdc1 and grub-install /dev/sdc1. Both give me errors saying...
Grub-probe: error: failed to get canonical path of 'auths'
Could not find device for /boot: not found or not a block device.

I've googled and googled. Nothing works.

---

### Post by Infamshxr on 2016-04-21
Oops

---

