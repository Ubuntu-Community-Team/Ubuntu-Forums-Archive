---
title: "Remote Desktop &amp; SSH Tunneling"
date: 2008-06-09
forum: General Help
---

### Post by ubtBaba on 2008-06-09
Hello,

I was having some trouble with connecting to my Linux Box running Hardy Heron from Windows.

I read this great tutorial on [http://altitude5.blogspot.com/](http://altitude5.blogspot.com/) for Remote Desktop & SSH Tunneling.  I got to step 7 where I get a login terminal and I can login.  However, I am not able to use VNC viewer.

Any help would be great, thanks

---

### Post by HalPomeranz on 2008-06-09
I recommend you first try testing whether the VNC connection works without the complication of SSH.  Are you in a position to try connecting to your Ubuntu desktop without using SSH?  If so, run VNC viewer and enter the name or IP address of your Ubuntu machine into the "Server:" box (instead of 127.0.0.1 as it tells you in the instructions you downloaded).  If it works, then you know the issue is somehow related to the SSH setup and we can go from there.

---

### Post by ubtBaba on 2008-06-13
So I finally got VNC to work with and without SSH Tunneling.

I also got this using my local ip address and my dns hostname.

I am pretty excited, the firewall program Firestarter allowed me to configure my traffic easily. Firestarter is a God-send for newbies like me.

My new issue is when I connect to my linux box everything I do is visible; after I login remotely my linux box is open to whomever is in my room at the moment.

When I used Remote Desktop on my Windows machine the screen would lock and that gave me some sense of security and saftey.

Can I do something about this security issue?

---

### Post by Vivaldi Gloria on 2008-06-13
Why don't you lock your ubuntu screen? Click the power button and you get the option at the top middle.

---

### Post by ubtBaba on 2008-06-13
The problem with that is when I remote desktop into that machine I will unlock that machine.

I want to be able to remote desktop but have my machine locked at home.

---

### Post by Deadheded on 2008-06-13
It works great for me on the local network but for some reason I get connection refused from outside the network...  Checked all the setting in my linksys router but can't seem to figure it out...

---

### Post by jimv on 2008-06-13
Turn off your monitor before you leave?

:D

---

### Post by ubtBaba on 2008-06-13
:lolflag:, that would be the most wise solution, but in my situation I am using my laptop as a server.

So I still need a solution if any exist.

---

### Post by ubtBaba on 2008-06-14
Tried to look more on the internet, still no hope.  Any linux experts out there know of a solution.

---

### Post by HalPomeranz on 2008-06-14
> **ubtBaba said:**
> Tried to look more on the internet, still no hope.  Any linux experts out there know of a solution.

I don't think there is one.  When you connect with VNC you are viewing/controlling the primary desktop of the system (as opposed to Windows RDP where you're manipulating what is essentially a separate desktop).  Thus anything you do is going to be visible on the primary desktop and there's no way to lock the screen without locking your VNC session as well.

Sorry to be the bearer of bad news...

---

### Post by wormser on 2008-06-14
> **Deadheded said:**
> It works great for me on the local network but for some reason I get connection refused from outside the network...  Checked all the setting in my linksys router but can't seem to figure it out...

Directions to Port Forward your router should be here: [http://portforward.com/routers.htm](http://portforward.com/routers.htm)

---

### Post by darkkith on 2008-06-14
i might have missed it - but specifically why are you using VNC ?  have you tried nomachine?

---

