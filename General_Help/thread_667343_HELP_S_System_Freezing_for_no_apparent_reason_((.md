---
title: "HELP :S System Freezing for no apparent reason :(("
date: 2008-01-14
forum: General Help
---

### Post by 1Slater1 on 2008-01-14
Hello people,
I'm relatively new to linux and my first distro was Ubuntu Feisty, i recently installed 7.10 Gutsy and i'm in serious trouble. My PC freezes for no apparent reason, and trust me when i say freezes that's what i mean, i cant use Ctrl+Alt+Backspace to restart the x server etc, the only solution is reset. This happens at least a dozen times a day and if i let my PC for the night to dl something then it's 100% certain that i'll find it in a 'frozen' state. A kind of chilly experience to the "most stable" system but it's probably due to my ignorance, what can i say... I really would appreciate any suggestions and/or solutions.
My PC characteristics are:
AMD Athlon 64 X2 Dual Core Processor 4200+
1GB Ram
NVidia GeForce 7300 GS

---

### Post by mccorkle on 2008-01-14
Has this just started with 7.10?  

Freezes like what you describe are almost always hardware conflicts with the kernel.  Hard disks, memory, cpu, even GPUs could be the culprit.  You might catch a glimpse of the failure if you leave it running at a console (hit ctrl-alt-f1 and login) and just tail -f your dmesg log:
`tail -f /var/log/dmesg`
If its a kernel panic, you'll get something in there.  

Assuming you get a hint of where the failure is, we could focus on figuring out why its happening at that point.  

::Mark McCorkle

---

### Post by 1Slater1 on 2008-01-14
Well first of all thnx for the fast responce :D
Hmm i did what you said, so supposedly if any crash n burn happens this process will record the reason?? And if that's the reason for the command where i'm supposed to view the log of this? tail -f /var/log/dmesg, seems obvious but just in case. And to answer your question yes this happened when i moved from 7.04 to 7.10. But this happened when i got my new PC so i dont think there is a relation there. I hope i dont have to go to Feisty, i really like Gutsy :)

---

### Post by redr on 2008-01-14
I had similar problem, though i am using fiesty. I am not sure whether I should start a new topic or reply here.

Events happened as follows

I logged on my machine and realized that its too slow.
It took more than a minute to open shell and give the output of 'top'.
and Xorg was using CPU in the range of 49% to 98%. and it was not momentary usage.
Ctrl+Alt+F1 was also damn slow. I had some other work so I locked the screen. I came after couple of hrs. Now output of top shown most of the CPU time being used by processes watchdog/0, kblocked/0, ksoftirq/0, events/0 (each process' usage in the range of 20% to 90 % or so.)
( I was using gnome. Are kblocked/0, ksoftirq/0 KDE processes?)
I couldnt do anything more. It was taking time to display keys being typed. So, finally I gave up and rebooted.
Now it appears to be working fine.
I checked /var/log/messages but couldnt make out anything. There was this line in the log file
[softlockup_tick+156/240] softlockup_tick+0x9c/0xf0
Is this the problem thing?

What can be the problem?
Thanks

---

### Post by mccorkle on 2008-01-14
What will happen is that when it crashes, it should leave the output on your screen so when you come back to the machine and its non-responsive, you can at least see why it crashed.  

As for Redr, I'd recommend you start a new thread, because even if both of you are looking at kernel driver lockups, the fixes will likely be vastly different, and I wouldn't want to confuse either of you by replying inline to both of you.

---

### Post by 1Slater1 on 2008-01-14
the output of the command was:

riddler@riddler-space:~$ tail -f /var/log/dmesg
[   13.348000] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 20
[   13.348000] ACPI: PCI Interrupt 0000:00:06.1[B] -> Link [LAZA] -> GSI 20 (level, low) -> IRQ 19
[   13.348000] PCI: Setting latency timer of device 0000:00:06.1 to 64
[   13.716000] input: ImExPS/2 Generic Explorer Mouse as /class/input/input3
[   14.292000] lp0: using parport0 (interrupt-driven).
[   14.332000] Adding 1951888k swap on /dev/sda3.  Priority:-1 extents:1 across:1951888k
[   14.672000] EXT3 FS on sda2, internal journal
[   15.320000] kjournald starting.  Commit interval 5 seconds
[   15.324000] EXT3 FS on sda4, internal journal
[   15.324000] EXT3-fs: mounted filesystem with ordered data mode.

which i don't think is what you meant by it cause it seems to me like an initializing process, i looked up the command and it's supposed to output the 10 last lines of a specified file. But the problem is that when the system freezes i cant see the output of the command :( Is there a way to see the last output after rebooting the machine?

---

### Post by mccorkle on 2008-01-14
Yeah, that's what I meant.  Just leave it there.  The '-f' option tells tail to "follow" the end of the file, so any time something new is added to dmesg, tail will push it to the screen.  My hope is that when you box randomly freezes again, right before it does, something will get pushed into dmesg and tail will show it to us before the machine completely stops.

---

### Post by 1Slater1 on 2008-01-14
No luck with this one cause i use it as you said on one of the consoles with ctrl-alt-F1, my point is i don't get the privilege to see the last output. The reason is simple, the system is non responsive at all so i cant ctrl-alt-f1 to see the last thing :( I have a suspicion that the problem is due to my graphic card cause when i look at video or something that uses graphics extensively i get these horizontal scrambled multicolor lines like a broken TV and i have to restart the X server to get this straight. But i have installed the restricted drivers for nvidia so i cant see anything more i could do on that.

P.S. I also noticed that my ram is getting over used for no reason at all, i used free -m and i got:
riddler@riddler-space:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1011        699        311          0        167        285
-/+ buffers/cache:        246        764
Swap:         1906          0       1906

and i have only firefox open at the moment :S

---

### Post by 1Slater1 on 2008-01-14
Ahhh at last :D I found what was the problem, it appears that having a dual core processor and an nvidia card causes instability issues of that kind. The solution was given by NVidia with the 169.07 drivers which can be downloaded here: [http://www.nvidia.com/object/linux_display_ia32_169.07.html](http://www.nvidia.com/object/linux_display_ia32_169.07.html)
and for 64bit systems:
[http://www.nvidia.com/object/linux_display_amd64_169.07.html](http://www.nvidia.com/object/linux_display_amd64_169.07.html)
Note that for those drivers to work i had to uninstall all previous drivers bundled with Ubuntu like nvidia-glx, nvidia-glx-new, nv etc all completely remomed. 

I hope my problem helps some one else also :)

---

