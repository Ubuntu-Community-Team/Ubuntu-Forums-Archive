---
title: "Remote Desktop no monitor problem"
date: 2013-03-07
forum: General Help
---

### Post by offroadguy56 on 2013-03-07
Hello. I posted a question on the askubuntu section and got a useless answer. [http://askubuntu.com/questions/260059/run-without-monitor-in-12-10](http://askubuntu.com/questions/260059/run-without-monitor-in-12-10)

I've got a fresh install of Ubuntu Desktop 12.10 32-bit with Team Viewer 8.

My motherboard is an ASUS M2N-MX SE PLUS that has an integrated Nvidia GeForce 6100 video card.

I'm trying to set it up so I can leave my machine next to my router so I don't have to run the cord past everyone's rooms where they can trip on it. However there is just enough room to fit the tower and it will look very weird with a monitor randomly jutting out.

I've been to several websites explaining how to change the xorg-config file all of them have failed me and I've ended up having to reinstall Ubuntu to fix the "fixes".

What I'm trying to do is setup my machine to automatically startup Team Viewer 8, which I've already done, and then I'll use Team Viewer to restart the server I'm running off the machine or run any updates that are needed.

Of course Ubuntu won't boot up if it does not detect a monitor and the xorg-config edit's I've found don't do squat.

Am I missing something important? 
If there is any other kind of information you need let me know.
I'm also slightly new to Ubuntu. If you tell me what to type into the terminal I can get it done.

---

### Post by offroadguy56 on 2013-03-11
Hello?

anyone?

---

### Post by sudodus on 2013-03-11
Hi and welcome to the Ubuntu Forums :-)

I will try to help. And I will start with some questions, because I think that a good description of the problem is almost a solution.

- What do you want to do with the computer? I mean you wrote 'server', so what services do you want it to perform? What tasks, what programs do you want to run on it?

The standard recommendation is to run a server without any graphic desktop environment, only text. And this text interface can be viewed on a 'console', a simple monitor connected to it, or on a desktop or laptop or netbook computer connected via ssh and the local area network (or even the internet, but that is more complicated and risky). If you have no console monitor attached, it is often called a headless server. You can search for 'headless server' on the internet or here at the Ubuntu Forums, and find a lot of tips from people with a lot of experience of server management. [COLOR=#808080](I don't run any dedicated server, I only have some services running in my desktop Ubuntu 12.04: ssh, samba)[/COLOR]

- Please explain why you want to use Teamviewer for this task! That program is good, when you want to help someone far away to solve a problem, that is hard to describe without seeing and running the desktop. But why use it here, as a standard tool? You might have a very good reason, that I do not understand unless you explain it.

---

### Post by offroadguy56 on 2013-03-11
Hello and thanks.

What I want to do is run a minecraft server off the machine.

I'll be running bukkit which uses java and has a terminal window for entering in commands for the server.
I'll also need access to server files for updates and plugin installations and troubleshooting. FTP works good as I do manage another server on Gamservers.com

Yes I have heard of ssh but I really like to have a windows style GUI, which is why I had teamviewer. 
I could learn how to use ssh, I just wanted to know why the solutions for the xorg config didn't work for me.

I do have team viewer so if you would like to connect and have a look around I don't mind.

If you need any other hard information let me know.

I'll have a look at headless servers around the forums. Headless, new terminology for me. :???:

---

### Post by steeldriver on 2013-03-11
you may have better luck with something like vnc4server instead of teamviewer

---

### Post by sudodus on 2013-03-11
> **offroadguy56 said:**
> ...
What I'm trying to do is setup my machine to automatically startup Team Viewer 8, which I've already done, and then I'll use Team Viewer to restart the server I'm running off the machine or run any updates that are needed.

[COLOR=#ff0000] Of course Ubuntu won't boot up if it does not detect a monitor and the xorg-config edit's I've found don't do squat.[/COLOR]

Am I missing something important? 
...
I think you can get much better advice now, when you have described what you want to do.

It used to be possible to run a computer without a monitor and mouse, but some really want a keyboard (it depends if there is a menu entry for it in the BIOS). Did you try that (keyboard, but no monitor)?

---

### Post by sudodus on 2013-03-11
I was just checking: I switched off a computer running Ubuntu desktop 12.04 LTS with sshd (the ssh server). Then I pulled out the cable to its monitor and booted it. Now I have connected to it via ssh, and it works. (I still have the keyboard and mouse connected.)

The local connection sits at the log in screen (and uses very little RAM). If I would have selected direct login without a password, it would have been sitting at the desktop waiting for any command to run. Would this be a good way to run for you?

---

### Post by offroadguy56 on 2013-03-11
Yea the problem with running with no monitor is that Ubuntu won't load up the desktop but the computer is still functional. It's running the computer with no GUI I believe. Even though I can't see the desktop, my server still shows up as online on the team speak computer list. I can't connect to it though.

It's just that I prefer a windows style GUI to help me navigate.

But I've decided that I'm going to completely scrap this computer except for the peripherals and build a budget gaming PC.

but I'm still interested in the challenge of setting up this server. Who doesn't like trying something new?
I plan on going into computer repair for a profession so I'd like to learn as much as I can. Even if it doesn't pertain to repair. I might come across a system like this that I might have to help fix.

 
What I have plugged in. DVD drive (IDE), hard drive (IDE), 2gb DDR2 ram (two 1gb), laser mouse (USB), an old '95 keyboard (PS/2). No monitor and no floppy drive. As far as I can tell the floppy drive only affects G-Partitioner. 

I'll look into the things yall mentioned before.

Thanks for your time.

---

### Post by sudodus on 2013-03-12
One alternative, that I think will be independent of the local monitor is the following:

- Run ***xrdp*** on the server

- Run ***rdesktop*** on the local desktop or laptop computer and connect via your LAN to the server. This will probably fit better than Teamviewer in your case, while Teamviewer is easier to connect reasonably safe via the internet.

You can install xrdp and rdesktop from the repos with
```
sudo apt-get install xrdp rdesktop
``` and read the manual pages ```
man xrdp
``` and ```
man rdesktop
```

---

