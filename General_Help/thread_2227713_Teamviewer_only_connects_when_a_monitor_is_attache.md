---
title: "Teamviewer only connects when a monitor is attached"
date: 2014-06-03
forum: General Help
---

### Post by Tony_Lillie on 2014-06-03
I'm running Ubuntu 14.04 (all updates current) on computer A and anytime I try to remote into computer A using Teamviewer from any other computer it ONLY works if I have a monitor attached to computer A. Said another way, I cannot go headless on computer A and remote in with Teamviewer, it hangs at the "initializing display parameters" screen. This was previously working fine, but I am not aware of any related updates. Though I did recently resync a raid 1 array where the root OS is mounted. The sync went fine and everything else is working perfectly.

To reiterate, remote sessions through Teamviewer work perfectly if a monitor is attached to computer A. I have attempted headless control from several of my computers and the same issue happens every time. The fact that it only happens when a monitor is not attached makes me think it is an Ubuntu issue and not Teamviewer.

One more thing: In an attempt to fix the problem I uninstalled Teamviewer and the configuration files, then reinstalled and the problem persists. I am using the 32 bit version of Teamviewer and all computers are running the most current version 9.

Thoughts anyone?

---

### Post by Tony_Lillie on 2014-06-03
So my research has led me to refine my question, because I now understand that the gui is designed NOT to launch if no monitor is detected. I've seen several posts that speak of workarounds, but none yet that answers the real issue. How can I start the gui desktop with no monitor attached? 

I don't want to use a different remote app like VNC, and I don't want to SSH in to the computer and start the gui manually. I want the simplicity that only Teamviewer seems to offer, but that requires a gui desktop environment to start even with no monitor.

There must be a way to bypass the monitor check or force the gui to start even if no monitor is detected.

---

### Post by Tony_Lillie on 2014-06-06
Well, I guess I shouldn't be surprised that there have been zero responses, because it's plain from all the evidence I could find that there is no other solution than to SSH into the machine and start a desktop session. So, here is my latest question that I REALLY NEED HELP with. What service do I start? Lightdm seems the obvious choice, but it's not working. Do I need to start an X session? I'm familiar with enabling X over SSH, but I want the native desktop on the remote machine to turn on so I can use teamviewer.

What commands could I issue to get the native desktop session to run?

---

### Post by citrocker on 2014-06-07
> **Tony_Lillie said:**
> Well, I guess I shouldn't be surprised that there have been zero responses, because it's plain from all the evidence I could find that there is no other solution than to SSH into the machine and start a desktop session. So, here is my latest question that I REALLY NEED HELP with. What service do I start? Lightdm seems the obvious choice, but it's not working. Do I need to start an X session? I'm familiar with enabling X over SSH, but I want the native desktop on the remote machine to turn on so I can use teamviewer.

What commands could I issue to get the native desktop session to run?

Hi Tony, I'm looking for a solution to this. I don't want to have a monitor attached if I don't need to. As long as the monitor are attached Teamviewer works. This is so stupid. I have my server on a very small space that I have to have the monitor on the floor in front of it. There must be away like you said to go around the problem. The question is how? I like Teamviewer much better then VNC (to slow in my opinion). Hoping someone can come up with a solution I can't because I'm a newbie on Linux.

---

### Post by Tony_Lillie on 2014-06-07
I have spent several hours on this now and been unable to find a software solution. Meaning, there is no consistent way to get Ubuntu to start a desktop environment without a monitor attached.

Fortunately I did find a really simple hardware solution at the following links: [http://www.geeks3d.com/20091230/vga-hack-how-to-make-a-vga-dummy-plug/](http://www.geeks3d.com/20091230/vga-hack-how-to-make-a-vga-dummy-plug/)  &  [http://soerennielsen.dk/mod/VGAdummy/index_en.php#3](http://soerennielsen.dk/mod/VGAdummy/index_en.php#3)
As you can see, it's very simple to "simulate" the resistance of a monitor and trick your OS into launching a desktop environment. I have not built mine yet, but am ordering the parts ASAP and will report back my results sometime next week.

I understand why Ubuntu is designed in this way, but it's really disappointing that there isn't a way to bypass the need for a monitor. In the year 2014 using SSH for remote access is practically Byzantine. Using a gui should not be considered a convenience or extravagance. It should be a non-negotiable. I can accept SSH for most servers, but servers are not the only computers that people run headless and need remote access to!

---

### Post by Tony_Lillie on 2014-06-08
I am thrilled to report that the "vga dummy" hardware workaround presented at the links in my previous post really works! I purchased a couple packages of 100 ohm resistors from the local Radio Shack, shut down my computer, unplugged it, stuck the resistors in the appropriate holes (see previous post for link), rebooted (obviously with no monitor), and the gui loaded exactly as if a monitor had been attached. I was then perfectly able to remote into the machine with teamviewer.

It's still disappointing that Ubuntu doesn't have a solution for this in the OS, but it is a very easy hardware "workaround" that definitely works!

---

### Post by hargrave-a on 2014-11-16
Thanks for your work here Tony, you've helped me solve the same problem.

Thanks for documenting your solution! :)

---

### Post by Tony_Lillie on 2014-11-16
I'm thrilled to discover I actually helped someone for a change. I'm usually the one getting the help.

Glad to be a contributing member of the Ubuntu community!

---

### Post by Jeff_Carey on 2015-05-25
Hi,

I ran into the same problem and the link here provides a software-only solution that worked for me:

[http://askubuntu.com/questions/453109/ubuntu-14-04-add-fake-display-when-no-monitor-is-plugged-in](http://askubuntu.com/questions/453109/ubuntu-14-04-add-fake-display-when-no-monitor-is-plugged-in)

---

### Post by David_Eschmeyer on 2015-09-16
I found the solution.  The ubuntu screensaver turns off the displays and gives this dreaded problem.  Instead, use i3lock and it will not turn off the displays and it turns out it is pretty cool, blurs out the screen to your specifications as a snapshot, and with a small tweak puts an image up as well in front of the blur on the center monitor.  No more problems connecting anymore.

[http://plankenau.com/blog/post/gaussian-blur-lock-screen-i3lock/](http://plankenau.com/blog/post/gaussian-blur-lock-screen-i3lock/)

[https://github.com/meskarune/i3lock-fancy](https://github.com/meskarune/i3lock-fancy)

also, you can manually turn out the displays with their power buttons, but since the video card is still providing signal as though they are on, you can still connect and initialize display.

---

### Post by zcambridge on 2016-05-02
What about mini DP? or DP (display port)? or HDMI? can these be solved by software/ hardware dummy as well?

> **Jeff_Carey said:**
> Hi,

I ran into the same problem and the link here provides a software-only solution that worked for me:

[http://askubuntu.com/questions/453109/ubuntu-14-04-add-fake-display-when-no-monitor-is-plugged-in](http://askubuntu.com/questions/453109/ubuntu-14-04-add-fake-display-when-no-monitor-is-plugged-in)

---

