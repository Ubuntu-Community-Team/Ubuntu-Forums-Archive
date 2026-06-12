---
title: "[SOLVED] gnome-settings-daemon doesn't work with xdmcp"
date: 2008-04-25
forum: General Help
---

### Post by AHall1983 on 2008-04-25
Well, I was hoping an update would fix it but it's up to release and didn't. I've been running Hardy since about the time it went beta. I primarily use the ubuntu machine remotely with xdmcp with xming on windows.

The problem is it's not working. I had gutsy before and upgraded but the upgrade got botched, on gutsy it worked fine. I didn't have a disc to waste burning hardy, so I reinstalled gutsy when that happened and upgraded to hardy again, it worked this time.

I've been running hardy on that machine for some time now pretty stable more or less. The one problem however is that when I remote in with xming and log in, gnome settings daemon errors out on login. Most of the problems I've seen searching related to this happen to the use all the time not just remotely so not sure what to think.

I've tried more than a few things to fix it but can't think of all of them off the top of my head. I do know it's not just my account though I tried making a dummy and it didn't work either.

Anyhow the error is as follows:
```

There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in.

```

Thanks in advance.

---

### Post by AHall1983 on 2008-04-25
bumpin' it up, any ideas anyone? :popcorn:

---

### Post by AHall1983 on 2008-04-28
Any ideas? pleaaaase :o

---

### Post by jrasmussen0 on 2008-04-30
I'm getting the same issue after my last reboot.  I also started with Hardy when it was still in beta (by only 2-3 days).

When I try logging in locally I get a gnome desktop background with a white square in the upper left corner where I can move an arrow mouse icon but can't get anything to respond (Alt-F2 didn't work).  

If I wait for 1-2 minutes, then the gnome-settings-daemon will timeout and allow me to see and interact with the entire desktop.

When I try to run 'gnome-settings-daemon' from the command line I get these errors:

```
** ERROR **: You can only run one xsettings manager at a time; exiting

aborting...
Aborted
```

I'm going to see if there is a way to uninstall and reinstall gnome-control-center which it looks like gnome-settings-daemon replaced.

---

### Post by jrasmussen0 on 2008-04-30
Take a look at bug report #146946.  I haven't tried adding gnome-settings-daemon to the startup list manually but currently I'm trying to work on modifying /etc/X11/Xinitrc.d/55gnome-session or something like that.

[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/146946](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/146946)

---

### Post by eombah on 2008-05-11
I experience the same behavior connecting via xdmcp to my new Hardy server from Xnest running on Gutsy .
Connecting to a Gutsy server never gave me problems.

/var/log/messages says:
```
May 11 11:27:53 hardy kernel: [1279412.373268] gnome-settings-[1397]: segfault at 10 rip 7f4c941f573d rsp 7fffa9548cb0 error 4
May 11 11:27:59 hardy kernel: [1279418.455413] gnome-settings-[1405]: segfault at 10 rip 7fc0432ce73d rsp 7fff5861fd80 error 4
May 11 11:28:06 hardy kernel: [1279424.928967] gnome-settings-[1415]: segfault at 10 rip 7fc8a403573d rsp 7fffb9388af0 error 4
May 11 11:28:11 hardy kernel: [1279430.516466] gnome-settings-[1427]: segfault at 10 rip 7f96e6e8e73d rsp 7ffffc1df940 error 4
May 11 11:28:17 hardy kernel: [1279436.358181] gnome-settings-[1437]: segfault at 10 rip 7f6f81b6c73d rsp 7fff96ebe620 error 4

```

I see on the screen that gnome-settings keeps on trying and failing, as you see in the messages above.

I will try to open a bug.

By the way, when connecting to the Hardy server from a NoMachine NX client, I don't have any problems. Hm...

---

### Post by eombah on 2008-05-11
[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/229238](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/229238)

---

### Post by AHall1983 on 2008-06-05
Another try, annnnyone?

---

### Post by nic-stange on 2008-06-13
I had exactly the same problems as AHal1983, i had not experienced the segfaults eombah had.

I used tcpdump to capture my network traffic and saw several unsuccessfull trys of my xdmcp server (Ubuntu Hardy) to connect to the windows box (XP, service pack 3) to port 16001 (googleing tells me that this is used by esd).
Solution: Manually unblock Port 16001 for the xdmcp server within the windows firewall.

Regards

Nicolai

---

### Post by AHall1983 on 2008-06-14
You sir, win a cookie! It still errors out and takes longer than it should to log in but it eventually loads now, go figure!

I was going to mark this solved but I didn't see the control for it on the newer forum. There is still a minor bit to it but it's more or less working now, I still don't get why the rest is happening though.

---

### Post by nic-stange on 2008-06-14
> It still errors out and takes longer than it should to log in but it eventually loads now,

Same here, too. I had experienced the 'blank', that is ubuntu red, screen once but it's mostly working now. It doesn't "error out" here. Do you mean the same error message you quoted above (regarding gnome-settings-daemon)?
It takes long for the Gnome desktop to load for me, too.

> I was going to mark this solved but I didn't see the control for it on the newer forum. 
Just for my interest: What newer forum? 

> There is still a minor bit to it but it's more or less working now, I still don't get why the rest is happening though.

So, don't close it, maybe we can work through it and file a bug when we have gathered further symptom information.
Which rest is happening?


I've run tcpdump with my working, that is non-firewalled port 16001 on windows box, but slow configuration another time.
The attempts to connect to port 16001 from ubuntu to windows differ now:
They appear far more often, but they become reset each time immediately.
Maybe that's the point why things slow down.
Could you install the esd on windows for testing purposes (to make the connection to port 16001 successful)? I don't want to do that, as the windows laptop is owned by a friend of mine not at home now and I don't want to clutter his system with my testing packages.

My suspicion is, that gnome-settings-daemon is waiting for this connection to 16001 to be established and in turn does not respond to dbus request from the gnome clients and they time out resulting in the error message you quoted above. 
Unblocking 16001 makes the connection attempts to fail more quickly and maybe that's the reason why gnome-settings-daemon is back more quickly and answers its dbus requests.
But: That's only my personal unvalidated suspicion.

Regards

Nicolai

---

### Post by AHall1983 on 2008-06-28
You know after running it through a few times it doesn't error out at all now. So glad this problem is finally solved. :popcorn:

As for the forum, it was upgraded a few months ago and ever since then I don't know where the magical little solved button is... Oh there it is lol.

---

### Post by kemikal on 2008-09-01
Guys, I just came across this thread, and I've found out one of the reasons why it's happening. Check this post here.

[http://www.starnet.com/xwin32kb/Ubuntu_hangs_when_logging_in_via_XDMCP/]("http://www.starnet.com/xwin32kb/Ubuntu_hangs_when_logging_in_via_XDMCP/")

I made these adjustments on the xdmcp box and it fixed it up fine. 

Oh, and it's Hardy Herron I was using too. 

Cheers.
Pete

---

