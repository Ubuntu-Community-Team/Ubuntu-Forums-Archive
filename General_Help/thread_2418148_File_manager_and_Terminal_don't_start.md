---
title: "File manager and Terminal don't start"
date: 2019-05-02
forum: General Help
---

### Post by ienien-77 on 2019-05-02
Hi,
I'm a little bit new on Ubuntu but i almost install it on all my computers.
Few days ago i decided that i will use Ubuntu instead of windows and so i boot on Ubuntu, it worked for few days without any problems and yesterday, when i restarted my computer, the terminal and file manager won't start.
I tried the terminal shotrcut (Ctrl+Alt+T) but it doesn't work. 
Whenever i try to launch it, it shows up on the top left corner and  after 10 - 20 second nothing happend and the loading stop, so i don't have any way to access either my terminal or my file manager wich is a problem.

I hope you have a fix for that that don't requier me to reinstall Ubuntu completly.

---

### Post by dragonfly41 on 2019-05-02
Access terminal by Ctrl+Alt+F1 toggle back to desktop by Ctrl+Alt+F7 as a temporary measure until it works again.

---

### Post by ienien-77 on 2019-05-02
> **dragonfly41 said:**
> Access terminal by Ctrl+Alt+F1 toggle back to desktop by Ctrl+Alt+F7 as a temporary measure until it works again.

I just tried it ... but it doesn't work. Ctrl+Alt+F1 make me logout and when i do Ctrl+Alt+F7 i have a black screen with a blinking _ on the top left corner of my screen  and i can't type anything

---

### Post by dragonfly41 on 2019-05-02
I'm afraid that I only have Ubuntu 16.04 experience with these keys .. but this might explain more ..

[https://askubuntu.com/questions/1045527/ctrlaltf7-doesnt-switch-back-to-x-session-in-kubuntu-18-04-bionic](https://askubuntu.com/questions/1045527/ctrlaltf7-doesnt-switch-back-to-x-session-in-kubuntu-18-04-bionic)

---

### Post by ienien-77 on 2019-05-02
I try Ctrl+Alt+F6 and it worked i was able to connect but i don't know what to do in order to repair my terminal. Also if i do Alt+F2 and i type nautilus ... it work (only nautilus) but when i try to launch the terminal it doesn't work. I'm totally lost here :)

---

### Post by Holger_Gehrke on 2019-05-02
Just entering 'terminal' in the Alt-F2 dialog won't work because (thanks to the long and involved history of terminals on X) it's not named simply 'terminal' but 'gnome-terminal' (assuming you're using mainline Ubuntu and not one of the other flavours). Each and every Desktop Environment has its own terminal program, just of the top of my head I know gnome-terminal, xfce4-terminal, konsole and lxterminal and there's several more which aren't associated with a specific DE. They all offer the same basic capability (text-based input and output for programs that need it, like for example the shell) but with different look and feel and different bells and whistles.

Holger

---

### Post by dragonfly41 on 2019-05-02
I'm assuming from your post that your desktop shows but you cannot launch terminal and file manager Nautilus.
Some configuration must be screwed up. You might try a guest account to see if gnome-terminal works.

I'm going to suggest an uncommon fix - installing an alternative terminal which you can use while troubleshooting
the cause of your normal terminal.

Launch Ctrl+Alt+F6 and run the command

sudo apt-get install yakuake

You could also try .

sudo apt-get install gnome-terminal

When you reboot you might be lucky to see gnome-terminal restored.

In addition you should see Yakuake under Applications > System Tools. 

After starting Yakuake in my case I press F12 to toggle display of shell terminal.
This works independently from gnome-terminal.

---

### Post by TheFu on 2019-05-02
Different GUIs tie different key-chords to different programs.  The ubuntu release and DE and WM each have a hand in the defaults.
Any default can be changed, usually.

So, if you want the most helpful responses, always lead with the version (number) of Ubuntu and the DE being used.  If no DE is being used, mentioning that with the WM would be helpful.

Or just post 
```
$ inxi -bnx
System:    Host: posc Kernel: 4.15.0-48-generic x86_64 (64 bit gcc: 5.4.0)
           Desktop: Openbox 3.6.1 Distro: Ubuntu 16.04 xenial
Graphics:  Card: Intel UHD Graphics 620 bus-ID: 00:02.0
           Display Server: X.Org 1.19.6 driver: intel
           Resolution: 1920x1080@60.01hz
           GLX Renderer: Mesa DRI Intel UHD Graphics 620 (Kabylake GT2)
           GLX Version: 3.0 Mesa 18.0.5 Direct Rendering: Yes
Info:      Processes: 261 Uptime: 3 days Memory: 3652.8/7859.5MB
           Client: Shell (tcsh) inxi: 2.2.35 

```
I've removed some of the output. It wasn't relevant.
From that output, you can see the Ubuntu version, lack of DE, WM and GPU information for my current system. Also that I'm not low on RAM and tcsh is my shell. I'm a little old-school.

---

### Post by timothylegg on 2019-05-02
One thing to try, before deciding to erase/reinstall:

Create a new user account using 'sudo adduser'.  After answering the questions, reboot the system and try logging in to that new account.  This would most likely work as expected.  If it does, we can go forwards from that point.

---

