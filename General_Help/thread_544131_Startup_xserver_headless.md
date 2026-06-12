---
title: "Startup xserver headless"
date: 2007-09-05
forum: General Help
---

### Post by GarethEvans on 2007-09-05
So  I'm trying to get a headless server going, which I'll then VNC into.  I've got VNC going fine with resumable sessions, my only problem is that I want to be able to boot the machine with no monitor attached.  Right now, if I do try to boot it without a monitor attached xserver will lock up and then when I reattach a monitor to see what's going on it's crashed with the error "Fatal error: no screens found".

Is there any way I can just force xserver to assume the monitor I had connected previously is still connected, rather than having it probe for it again at startup (and then find that it's not there)?  I've already tried putting my HorizSync and VertRefresh numbers in my Xorg.conf as that supposedly circumvents the monitor probing, but that apparently didn't do anything.

Thanks in advance.

---

### Post by stuartt on 2007-09-06
I thought that VNC required a monitor. Running a VNC server on a computer with the monitor turned off won't work so I would assume that VNC requires the graphics to be displayed on the server monitor.

Anyway, headless servers are always run via SSH and the command line. I'd just go that route (it's what I do with my headless server).

---

### Post by cwaldbieser on 2007-09-06
> **GarethEvans said:**
> So  I'm trying to get a headless server going, which I'll then VNC into.  I've got VNC going fine with resumable sessions, my only problem is that I want to be able to boot the machine with no monitor attached.  Right now, if I do try to boot it without a monitor attached xserver will lock up and then when I reattach a monitor to see what's going on it's crashed with the error "Fatal error: no screens found".

Is there any way I can just force xserver to assume the monitor I had connected previously is still connected, rather than having it probe for it again at startup (and then find that it's not there)?  I've already tried putting my HorizSync and VertRefresh numbers in my Xorg.conf as that supposedly circumvents the monitor probing, but that apparently didn't do anything.

Thanks in advance.

If you ssh into the server with the -X option, any graphical apps you run will show up on your local X Display server.  That way, you don't even need X to run on the server.

---

### Post by GarethEvans on 2007-09-06
> **stuartt said:**
> I thought that VNC required a monitor. Running a VNC server on a computer with the monitor turned off won't work so I would assume that VNC requires the graphics to be displayed on the server monitor.

Oh?  Well, if I boot the machine with a monitor attached and have the xsession start up with the monitor attached then detach it, it works fine.
> **cwaldbieser said:**
> If you ssh into the server with the -X option, any graphical apps you run will show up on your local X Display server.  That way, you don't even need X to run on the server.
> **stuartt said:**
> Anyway, headless servers are always run via SSH and the command line. I'd just go that route (it's what I do with my headless server).

I'd do this, but unfortunately I have two things that (I think?) are dependent on an X session - utorrent and Xchat.  Any ideas?  At worst, I can just attach a monitor to it while it boots and then remove it once X has probed the monitor, it's just a bit of a pain.  I won't really be rebooting very much at all though.

---

### Post by cwaldbieser on 2007-09-07
> **GarethEvans said:**
> Oh?  Well, if I boot the machine with a monitor attached and have the xsession start up with the monitor attached then detach it, it works fine.



I'd do this, but unfortunately I have two things that (I think?) are dependent on an X session - utorrent and Xchat.  Any ideas?  At worst, I can just attach a monitor to it while it boots and then remove it once X has probed the monitor, it's just a bit of a pain.  I won't really be rebooting very much at all though.

If you are running a local X server, the programs can run on the remote server, but the GUIs appear on your local server if you forward X11 traffic.

---

### Post by thatcooldude on 2007-12-14
I don't know if anyone's made any progress on this, but I'd like to do the same thing.

I have a monitor attached and everything works wonderfully, then I disconnect the monitor; everything continues to work just fine.

After a reboot, however, if the monitor isn't attached, X won't start and I am unable to SSH or VNC in to check out what's wrong.  I have to then reconnect a monitor, reboot, and then login...at which point everything works fine again.

Like the previous poster mentioned, it isn't necessarily a HUGE deal to have to connect a monitor on boot, but we recently had a few blackouts and it's getting a little annoying :)

Any ideas on how to spoof the xorg.conf into thinking I have a monitor connected so it'll create a virtual monitor if there isn't a physical monitor attached on boot?

Thanks for all your help!

---

### Post by bodhi.zazen on 2007-12-14
On the headless box you should disable GDM. It will then boot to the command line.

If you need X you can attach a monitor and either startx or start GDM.

You will still be able to vnc into the box, although not with vino (the default vnc server). You will need vncserver or similar.

If you use a vnc server I advise you do NOT run it all the time. Rather ssh in, start the vnc server, and forward over ssh.

---

### Post by thatcooldude on 2007-12-14
Thanks for the quick reply.  Unfortunately, my problem resolved itself apparently.

I think what was happening was my router didn't pick up Ubuntu's hostname.  I changed to the direct IP and everything worked just fine.  I used the "Resumable Sessions" guide, and it all works perfectly fine on boot now.

---

