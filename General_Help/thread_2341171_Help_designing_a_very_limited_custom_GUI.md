---
title: "Help designing a very limited custom GUI"
date: 2016-10-25
forum: General Help
---

### Post by dorianstarbuck on 2016-10-25
I’m tasked with a project that is significantly beyond my skills as a relative newcomer to Linux. I’m hoping that some of you can at least point me in the right direction. It’s possible that Ubuntu is not the right tool for this project, but it’s what I’m most comfortable with, so I figured I’d start here.

I’m trying to develop what amounts to essentially a thin client with its own embedded Web browser (Firefox or Chromium). This machine will be used for two purposes: to connect via RDP to a remote Windows 10 machine and to do Web browsing.

I’d like this machine to have a very simple GUI (no colorful background needed) with, ideally, only two available buttons. One to start the RDP client, and one to start the Web browser. Nothing else should be available from the GUI. Ideally, there won’t even be a “Start” menu or any right-click context menus.

There are additional needs on the RDP side (I’d like to be able to connect a USB device and have it recognized by the remote computer, but I can deal with these items once this simple interface is finished).
Is this something that can be done by a non-programmer with limited Linux experience? Any help offered is appreciated.

---

### Post by TheFu on 2016-10-25
So, you can do anything you have the skills to accomplish.  I think both the "limited Linux experience" and "non-programmer" aspects will be extremely limiting for the result you seek.  Some scripting will definitely be necessary at a minimum.  And you probably don't want to start with Ubuntu - you need a much smaller footprint to keep the users out of trouble with the OS.  A custom Linux distro is probably what you want - take a look on distrowatch for the smallest distros. Those will be the easiest to modify for your specific needs.

Why must Windows10 be the remote machine if just running a browser is desired?  There are better, linux-only, solutions for this.  With a Linux solution, you could force only the browser to be available to the specific users and if they are on the same LAN, it sorta "just works" provided video and audio aren't required. Both are possible, but it is a little more work.

Part of the issue is that almost every program has a way to drop to a shell and non-beginners will know that.  So, depending on why this is being sought as a solution, there might be better alternatives than what is being proposed. That doesn't mean it won't work or isn't good, just there might be better ways.

Welcome to the forums.

---

### Post by dorianstarbuck on 2016-10-26
Thank you for the response!

> **TheFu said:**
> So, you can do anything you have the skills to accomplish. I think both the "limited Linux experience" and "non-programmer" aspects will be extremely limiting for the result you seek. Some scripting will definitely be necessary at a minimum. 

I don't mean to imply that I'm *afraid *to take on a task that requires learning. A small part of my reason for doing this project is to gain experience with Linux. Also, I do light coding on a regular basis as a system administrator, and am willing to try to do what it takes. Programming is not what I do for a job, but I'm not afraid of it.

> **TheFu said:**
> Why must Windows10 be the remote machine if just running a browser is desired? There are better, linux-only, solutions for this. With a Linux solution, you could force only the browser to be available to the specific users and if they are on the same LAN, it sorta "just works" provided video and audio aren't required. Both are possible, but it is a little more work.

I may not have been clear in my post. This machine will be used as a way of accessing a remote workstation for 99% of the work that will be done. The Windows 10 machine that it connects to via RDP will have lots of software and tools that will be used. But the remote Windows 10 machine will be on a LAN with no access to the Internet, so any Web browsing will have to be done on this local machine, not on the remote machine. Does that make sense?

Thus, the simple, two-button GUI. One to take users to the remote machine, and one to access the Web browser on the local machine.

> **TheFu said:**
> Part of the issue is that almost every program has a way to drop to a shell and non-beginners will know that.

For this project, that won't be an issue. If there's a less difficult way to do this with a pre-existing distro, that's an acceptable flaw.

Thanks much for the welcome!

---

### Post by TheFu on 2016-10-26
Ah - that helps and clarifies.
* Remote to Win10 to run Windows-only programs. It is not able to get on the internet.
* Do everything else local, on Ubuntu.  Is only browsing the web expected? Nothing else, like local ways to replace Windows tools?

If you need more than 1 user to connect to Win10 concurrently, then I think you'll need a Windows-Server and terminal server license, but I don't know. Windows Desktops only allow 1 remote connection at time last time I checked.  OTOH, having limited access to Windows **is** a good way to encourage people to try Linux-versions of tools.  If the CEO is behind this migration, fantastic.  I've seen non-IT people get really frustrated over something like this. Just a warning. At my company, they decided to leave.

Also, the number of users/systems involved could alter the way I solved this.  If more than a few systems, I'd definitely use devops techniques. Ansible is the tool I'd use, but there are others.  Trialing a few users at a time, if possible, would make sense too.

I think the hardest part in my mind is getting the RDP credentials and security working correctly. [https://ubuntuforums.org/showthread.php?t=2287213](https://ubuntuforums.org/showthread.php?t=2287213) - seems the issue still exists, but I won't have Win10 here and can't check it.

---

### Post by dorianstarbuck on 2016-10-26
Thank you again for the help with this. 

> **TheFu said:**
> Ah - that helps and clarifies.
* Remote to Win10 to run Windows-only programs. It is not able to get on the internet.
* Do everything else local, on Ubuntu.  Is only browsing the web expected? Nothing else, like local ways to replace Windows tools?

I can probably simplify this even further:
* Remote to Win10 machine for everything *except *Web browsing. If user has to enter credentials to connect, this is fine. This is the part that I'm most comfortable with.
* Do Web browsing *only *on local machine. Local machine will do nothing else. It would be helpful if there were a way to *minimize* the RDP window so that the user could switch back and forth between the remote session and the local machine, that'd be ideal.

> **TheFu said:**
> If you need more than 1 user to connect to Win10 concurrently, then I think you'll need a Windows-Server and terminal server license, but I don't know. Windows Desktops only allow 1 remote connection at time last time I checked.

This is exactly correct, and I've already resolved this issue. For now, it will be one user connecting to one remote machine at a time, and in the future we'll be using a 3rd-party solution (that we've already tested) to allow multiple users to connect to the Windows 10 machine. 

> **TheFu said:**
> OTOH, having limited access to Windows **is** a good way to encourage people to try Linux-versions of tools.  If the CEO is behind this migration, fantastic.  I've seen non-IT people get really frustrated over something like this. Just a warning. At my company, they decided to leave.

Understood, and thanks for the warning! In this case, it's our CIO who's pushing this research, and we have a very specific end goal in mind that could potentially be extremely valuable to us *and *to the end users. It's a very specific scenario we're designing for here. Designing this front end is the biggest challenge.

> **TheFu said:**
> Also, the number of users/systems involved could alter the way I solved this.  If more than a few systems, I'd definitely use devops techniques. Ansible is the tool I'd use, but there are others.  Trialing a few users at a time, if possible, would make sense too.

I think the hardest part in my mind is getting the RDP credentials and security working correctly. [https://ubuntuforums.org/showthread.php?t=2287213](https://ubuntuforums.org/showthread.php?t=2287213) - seems the issue still exists, but I won't have Win10 here and can't check it.

It's possible that you're still overthinking it. It's not important that the RDP connection be invisible to the user. Let me try to explain by describing what I imagine a typical workflow will be:

User turns on the local machine in the morning. When it boots, they may (or may not...not important) be prompted to enter credentials to sign in to the local Linux machine (which has this custom GUI that I'm hoping to develop)

Once user is signed in to the local machine, they are presented with a GUI with two available options: 1) RDP session to remote Win 10 workstation, and 2) Web browser (Firefox/Chromium, I assume).

User uses button 1 to connect to remote Win 10 machine, entering credentials when prompted. Does work using various typical office applications; Microsoft Office stuff, etc. 

After an hour or so, user minimizes the RDP window to use button 2 and open a Web browser to check email, Twitter, Facebook, whatever the kids are doing these days. After 10 minutes or so, user returns to the RDP session to keep working. 

I've got a really good handle on how the RDP stuff is going to work, assuming I can develop this front end machine.

I have to admit...DevOps is a term I've heard many times, but have never really looked into. I'll read about it now. And Ansible is new to me.

---

### Post by steeldriver on 2016-10-26
I'd start by looking at some of the available kiosk solutions e.g.

[https://thepcspy.com/read/building-a-kiosk-computer-ubuntu-1404-chrome/](https://thepcspy.com/read/building-a-kiosk-computer-ubuntu-1404-chrome/)

[http://www.instructables.com/id/Setting-Up-Ubuntu-as-a-Kiosk-Web-Appliance/](http://www.instructables.com/id/Setting-Up-Ubuntu-as-a-Kiosk-Web-Appliance/)

---

### Post by TheFu on 2016-10-26
Great idea!  Kiosks.

My concern over win10 security is that Linux RDP clients can't connect without reducing the default Win10 RDP security/encryption level.  Remote desktops are a common thing in corporate environments - look up "VDI" - for solutions.  citrix is usually on the short-list for Windows.  [https://www.youtube.com/watch?v=qXJSeusVtaI](https://www.youtube.com/watch?v=qXJSeusVtaI) is an example using tinycore. Could be any remote desktop client, I suspect.

I don't think you need to develop a "GUI" to limit the ability to just the 2 programs
a) Remote desktop to Windows
b) Browser

TinyCore with 2 desktop icons would be easier as a starting point, I suspect. Plus it should load REALLY, REALLY, fast. The workstations could be disk-less.
[http://forum.tinycorelinux.net/index.php?topic=12709.0](http://forum.tinycorelinux.net/index.php?topic=12709.0) is what someone else did.

Whatever the programs are on Windows, it might be good to make similar programs available on Linux for people to try out.  I'm afraid the CIO isn't high enough up for the political support needed for a migration from Windows to Linux.  I've seen that fail. The CEO and BoD will need to want this.  OTOH, this is a good migration effort starting point.

---

### Post by dorianstarbuck on 2016-10-26
The Kiosk options are a great suggestion. I'll definitely take a look at those links. 

Tiny Core also looks extremely promising. I think I'll start with that. If I can figure out how to make it work with sound (for the local Web browser), it might be just good enough to make this work. I'd played with Tiny Core at one point a year or so ago, but had completely forgotten about it.

And I appreciate the thoughts and advice on management. I'm fortunate to be in an environment where those concerns are fully handled before the project even got to me. I'm a lucky guy!

Thanks so much for the advice, both of you!

---

