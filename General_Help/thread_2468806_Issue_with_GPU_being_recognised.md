---
title: "Issue with GPU being recognised?"
date: 2021-11-10
forum: General Help
---

### Post by the-bonny-light-horseman on 2021-11-10
Hello friendly folks,

I'm brand new to Ubuntu and Linux, been enjoying it so far however have been having issues with my gpu (I think). The issue first became apparent when I was unable to launch Steam.
Having done some digging I've only managed to uncover more gremlins.
I am unable to load any information on my GPU. I've tried inxi and lshw to fetch the data but neither works. When i type in inxi -G in the terminal it just hangs there forever, same with inxi --full and any lshw command just displays PCI (sysfs) and hangs. The inxi -c command for cpu information runs just fine. I installed a device manager and it lists my display renderer as Mesa DRI Intel HD Graphics 4400 (HSW GT2) The X.Org Foundation, but I know I have Radeon chip in this laptop (intel cpu).

To make things further complicated steam launched fine when I first installed. Unable to solve the problem I decided to reinstall ubuntu having a pretty much fresh install anyway, I tested inxi --G, it worked and correctly identified my Radeon chip. I installed steam and a couple of others things and everything was hunky dory, games ran no problem. Launched steam again today, it asked to install some packages, without really thinking (I thought ubuntu knew better than me so accepted). Now I can't run steam again and inxi data fetch is broken again. (Can't remember what packages they were, sorry!)
I've tried purging gpu drivers to reinstall but what I've found online hasn't worked. And I don't really know what I'm doing, don't want to make this mess even stickier!

My machine is an old HP Pavilion Notebook with a i5-4200 1.6GHz CPU and a 0896100000304100000620100/2164 HP motherboard. Can't remember the name of the GPU chip and away from home now so can't reinstall ubuntu for a while.

Sorry for the very wordy post, top marks for anyone who can help me solve this issue!
Many, many thanks in advance!

---

### Post by TheFu on 2021-11-10
First, start by patching the system fully.
Do that with 
```
sudo apt update
sudo apt full-upgrade
```

Now reboot.  

AMD GPU drivers are tied to the kernel. So are intel iGPU drivers.
On hybrid laptops, there are some common issues you can research, but you'll need to know the exact CPU, exact iGPU and exact Radeon GPU involved.  I think most people just disable the intel iGPU in the BIOS, since dynamically switching doesn't work well on Linux.

Really, need to patch using the commands above weekly.  Would also be helpful if you actually posted the output - a description is less useful.
Say the issue.
Say the expectations and post relevant HW and software stuff.
**inxi -Fxxxz** is a system overview. It says the MB, kernel version, OS release and a few other things that help people brainstorm solutions.
**inxi -Gxxz** is a GPU/graphics overview.

So far, this is what I think you've said.
Laptop - with Radeon and intel iGPU. Something about running games doesn't work, but I don't know if no GUI works at all or not. Don't know which GPU on the laptop is being used.
Steam .... yada yada yada (I'm not a gamer).
Something worked before. At some point, not sure when, it stopped working.

And I have some other laptop --- but it is completely unrelated to this, so ignore it.

See how easily things become misinterpreted?

---

### Post by the-bonny-light-horseman on 2021-11-10
Well this is an unexpected turn of events. I can't log into Ubuntu anymore. Brings me to a lot in screen and after I enter my password it brings me back to log in screen, also normally I automatically log in. 
Either I've scuffed everything up trying to fix things on my own or may have something to do with the fact that I cant do a soft shutdown on my laptop. Just hangs on black screen, had the same problem when I was running windows. Possibly due to my cmos battery being flat. 
I always hard shut down though and I've upgraded Ubuntu before and relaunched without problem. Don't know why it's not logging in now.

---

### Post by TheFu on 2021-11-10
Hardware issues are bad. Fix those first.

---

### Post by the-bonny-light-horseman on 2021-11-10
By selecting to log into 'Ubuntu Wayland' I'm not only able to log into Ubuntu but all my problems are fixed! I'm able to get system info on my gpu through inxi and steam launches. Don't know what Wayland is but it seem to do the trick!
Thank you for your help and patience, sir
I get a 'internal error' report - Title Xorg crashed with SIGABRT if there's a way to copy the message I would. Everything seems to run fine though

---

### Post by TheFu on 2021-11-10
Happy you solved it.  Please help the community by using the "thread tools" button near the top-right can marking it "SOLVED". This saves other members of the community time when they seek to help or find a solution.

Wayland is a very new "display manager" about 5 yrs, but probably being worked on for a decade.
For the last 30+ yrs, X11 was the display manager for Unix-like systems.  It is still available and for my workflows, Wayland breaks.

Xorg and Wayland are not interchangeable, at least not yet. For my needs, only xorg/X11 works - probably because I routinely run programs on multiple systems over the network and need to capture screens.  For example, this browser window is running on a different system than where my keyboard, monitor and mouse are connected.  Of 20 different programs currently running, about 80% of them are running on other computers, not the one I happen to be typing on.  To someone who doesn't know better, they appear just as normal windows - there isn't any difference when they run locally or remotely.

On Unix, the GUI is just another program, not anything special. Swapping different layers isn't hard.  Here's a diagram which attempts to explain the layers, but don't worry. It is only important if you want to get the most from the system: [https://upload.wikimedia.org/wikipedia/commons/0/03/X_client_server_example.svg](https://upload.wikimedia.org/wikipedia/commons/0/03/X_client_server_example.svg)  X11 also has some long-standing security problems with attempts to mitigate them over the last 30 years. Sometimes the results are better and sometimes not so great.  

Wayland doesn't have a client/server architecture for programs running locally.  [https://upload.wikimedia.org/wikipedia/commons/e/ea/Wayland_protocol_architecture.svg](https://upload.wikimedia.org/wikipedia/commons/e/ea/Wayland_protocol_architecture.svg) This would be more efficient, without the added overhead of network protocols. There is a compatibility layer, called Xwayland for network client/server stuff.

Efficient networking is a challenge for all time-sensitive interconnections.

---

