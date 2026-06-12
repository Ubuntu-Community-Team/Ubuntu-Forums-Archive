---
title: "Shut down/Suspend etc. Icon and both Toolbars dissapear"
date: 2008-05-21
forum: General Help
---

### Post by Jackfrost123 on 2008-05-21
From my screen when I click the, what's its name, the exit icon I suppose, the one offering you to suspend, shut down, log off etc. So both bars top, and bottom, dissappear and this has been happening consistently for the past few days.

Maybe it's something to do with me shuting down abruptly, just pressing te shut down button, when the system froze up a few times. But what could I do? It's not as if the system monitor worked when I clicked on it (as I would in windows) so I could kill the process that was hogging down the system. Here in ubuntu when something goes horribly wrong, that's it you are done for, and then more problems....

I would also like to kindly ask if there are any diagnostic tools, and how can I trigger/run them, defragment, system diagnostics etc.

All in all I am very dissapointed by ubuntu and linux, they have nowhere near the stability, (and you can't believe how much I hate saying this), of windows (or os x from what I hear). But having such crippling bugs (i suppose that is what it is) such as the one I described is adding insult to injury.

Anyway. Do you guys think there is some workaround my problem? I searched the forum and google it but to no avail. Doesn't help much of course if you don't know even the name of the exit/shut down/ etc. button....

p.s. gnome desktop is what I have. Opera also is gone downhill too together, not opening up pdfs, not remembering my last open tabs, and saying couldn't save some file...

---

### Post by Jackfrost123 on 2008-05-21
bump up.

---

### Post by xeth_delta on 2008-05-21
I don't use Gnome myself, but KDE, but will try to offer a hand. First, what version are you using? I is not a beta/alpha version, right? Please offer us more information regarding your system and configuration.

That said, I am sorry to hear about the problems you met. I guess there are a restricted number of systems on which for certain reasons there are stability issues. A large amount of people, me included find it on the systems they use to be at least if not more stable than Windows. I use it on a Mac, by the way, so I can compare on all three OSs.

Let us know how it goes and we'll try to help.

---

### Post by MythosLegend on 2008-05-21
I'm guessing you have Hardy Heron. I'm using 7.10 gusty.

> **Jackfrost123 said:**
> From my screen when I click the, what's its name, the exit icon I suppose, the one offering you to suspend, shut down, log off etc. So both bars top, and bottom, dissappear and this has been happening consistently for the past few days.


Are the bars/panels on autohide? 

> **Jackfrost123 said:**
> 
I would also like to kindly ask if there are any diagnostic tools, and how can I trigger/run them, defragment, system diagnostics etc.


Linux doesn't have fragmentation problems. You should be fine without a defrag tool (as long as you don't go over 80% disk usage)

I believe it's ctrl + alt + Backspace to restart your session. This will make you exit out.

---

### Post by Jackfrost123 on 2008-05-21
Hey, xeth and mythos, first off thanks you guys for replying. I am using hardy heron, on an intel m at 1.6 ghz with 512 ram, its a laptop. 

"Are the bars/panels on autohide?"

No, I don't think so, I am 99.9% sure they are not. This must be somekind of bug because when i click the exit (PLEASE somebody tell the name of this icon...) icon on the far right, instead of getting the options menu (suspend, hibernate etc...) the two bars just dissapear, and that's all that happens.

"Linux doesn't have fragmentation problems. You should be fine without a defrag tool (as long as you don't go over 80% disk usage)"

Why is that? I am over 80% however. Any suggesttions for defrag tools?\

any suggestions for diagnostic tools? That's important, are there none of these????

Thanks for all the help, and esp. the ctrl alt backspace shortcut, that's something along the lines of what I am looking for...but for the time being...

I am pretty desperate, I can't bear re-installing...

---

### Post by Jackfrost123 on 2008-05-22
bump bump

---

### Post by xeth_delta on 2008-05-22
> **Jackfrost123 said:**
> Hey, xeth and mythos, first off thanks you guys for replying. I am using hardy heron, on an intel m at 1.6 ghz with 512 ram, its a laptop. 

"Are the bars/panels on autohide?"

No, I don't think so, I am 99.9% sure they are not. This must be somekind of bug because when i click the exit (PLEASE somebody tell the name of this icon...) icon on the far right, instead of getting the options menu (suspend, hibernate etc...) the two bars just dissapear, and that's all that happens.

"Linux doesn't have fragmentation problems. You should be fine without a defrag tool (as long as you don't go over 80% disk usage)"

Why is that? I am over 80% however. Any suggesttions for defrag tools?\

any suggestions for diagnostic tools? That's important, are there none of these????

Thanks for all the help, and esp. the ctrl alt backspace shortcut, that's something along the lines of what I am looking for...but for the time being...

I am pretty desperate, I can't bear re-installing...

The file system Ubuntu uses as default (ext3) is quite efficient and it is good at avoiding fragmentation problems. I will look up for some of the tools you described, but truth be told, I haven't needed some sort of defragmenter, and I have been using different flavours of Linux for years.

About the problem with the screen. Is the interface locking when you try to exit? Are you using compiz/beryl? Are you sure your version of Heron is the final release and not a beta?

Open a terminal and type:
```
sudo lshw -C video
glxinfo | grep -i direct
glxinfo | grep -i opengl
```
Please post the output.

---

### Post by Jackfrost123 on 2008-05-23
"Is the interface locking when you try to exit?"

I am not sure what you mean, like I said, when I press the exit button both bars dissapear and no second options window comes up to choose suspend/shut down/etc. etc. But other than that everything seems to function ok, if there a sense of ok in that state. (And btw both opera and firefox are having issues with saving, bookmarking etc. etc. every since this)

"Are you using compiz/beryl?"
I don't know. Is compiz some window enhancement scheme? Probably not, I haven't changed the default state of hardy.
"Are you sure your version of Heron is the final release and not a beta?"
Yeap.

"Please post the output." It's about the opegl etc. video mode right?

Here it is:
//edit coming up on the next post from my laptop and not this windows vista pc I am using for writing this down. 

Thanks again for the help, I am currently and sadly looking to a clean install as my best option to tell you the truth buddy.

---

### Post by Jackfrost123 on 2008-05-23
PCI (sysfs)  

  *-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: 82852/855GM Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm vga_controller bus_master cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: 82852/855GM Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0

direct rendering: Yes

OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 852GM/855GM 20061017 x86/MMX/SSE2
OpenGL version string: 1.3 Mesa 7.0.3-rc2
OpenGL extensions:

---

### Post by MythosLegend on 2008-05-23
Here is a link of equivalent programs. Link maybe outdated and all programs might not be for ubuntu.

[http://www.linuxrsp.ru/win-lin-soft/table-eng.html](http://www.linuxrsp.ru/win-lin-soft/table-eng.html)

You probably can get more up-to-date info on programs in this thread.
[http://ubuntuforums.org/showthread.php?t=33183](http://ubuntuforums.org/showthread.php?t=33183)

---

### Post by MythosLegend on 2008-05-23
Accidental double posts.
[SIZE="1"]
(how do i delete this?)[/SIZE]

---

### Post by Jackfrost123 on 2008-05-23
thanks for the link, but what does this have to do with the issues I am facing?

---

### Post by MythosLegend on 2008-05-23
It doesn't deal with the issue you are facing, but you did ask for some diagnostic tools.

---

### Post by Jackfrost123 on 2008-05-23
thanks for that buddy. GREAT.

---

### Post by MythosLegend on 2008-05-23
Compiz is installed by default.
Several people have problems with compiz and their toolbars and stuff missing. 

You have an option since you don't use compiz. You might not like it. You can try to uninstall compiz (through synaptic) to see if it is causing problems for you . 

That's the only thing I can think of right now.

---

### Post by itaintover on 2008-05-23
Maybe you accidentally uninstalled gnome panel with another application? ;]

---

### Post by dreamnid on 2008-05-23
I was running Hardy fine on my laptop, until I ran an update (which  I don't remember what they were, but there wasn't many of them).  I had the same problem where clicking on the power button would not do anything, and both toolbars are unresponsive.

When I restart now, none of the toolbars would come up.  I can't even get alt-f2 (run program) to open.

Compiz shouldn't be running since my video card is a ATI Mobility 9000 which ATI doesn't have a driver for, so no compositing support.

---

### Post by Jackfrost123 on 2008-05-24
Well that's something, someone corraborating what I have said, same thing here. It was AFTER an update that I started having these isssues. I just hadn't associated one even with the other, and now that another user mentioned it it rung a bell.

Can someone identify the guilty update?

---

### Post by dreamnid on 2008-05-24
JackFrost,

I reported the bug here: [https://bugs.launchpad.net/ubuntu/+bug/234567](https://bugs.launchpad.net/ubuntu/+bug/234567)

Hopefully, we can get some developers input into the problem.

I think you should add a comment with your problem along with the stuff that you pasted here (diagnostic info).

Thanks!

---

### Post by xeth_delta on 2008-05-24
> **dreamnid said:**
> 
Compiz shouldn't be running since my video card is a ATI Mobility 9000 which ATI doesn't have a driver for, so no compositing support.

You can get 3D hardware acceleration via the Open Source driver provided in X. On an old laptop of mine which had an ATI Radeon Mobility 9000 IGP the X driver provided hardware acceleration and performance was reasonable, considering it was an old slow integradet card.

---

### Post by xeth_delta on 2008-05-24
> **Jackfrost123 said:**
> PCI (sysfs)  

  *-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: 82852/855GM Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm vga_controller bus_master cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: 82852/855GM Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0

direct rendering: Yes

OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 852GM/855GM 20061017 x86/MMX/SSE2
OpenGL version string: 1.3 Mesa 7.0.3-rc2
OpenGL extensions:

What seems a bit odd to me, is that both Screens are declared as unclaimed. In my computer only the second one appears like this. Maybe someone more knowledgeable can shed more light on this.

---

### Post by Jackfrost123 on 2008-05-26
It seems completely strange to me too, and as far as I can remember out of my 15+ years with computers, it's never happened, but everything is back to normal....

Or so it seems, don't ask me what happened i the interim. I might have installed another update, although I am not sure, and it's very doubtfull that this had any relevance at all. But as I was about to ditch everything the system is back to up to scratch, or so it seems, and it's  been convincing me ever since of not going for a clean-re-intalll.


Well...

---

