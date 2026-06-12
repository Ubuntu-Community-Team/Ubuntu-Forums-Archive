---
title: "Xfce Power Manager not running"
date: 2014-07-16
forum: General Help
---

### Post by pretty_whistle on 2014-07-16
I have Ubuntu 14.04 LTS with Xfce DE.

The power manager isnt running and wont run when I hit the run button.  Here's the message it gives me:

[IMG]http://i60.tinypic.com/9t0h7c.png[/IMG]

---

### Post by pretty_whistle on 2014-07-16
Update:

I see it's running in the System Monitor but I cant pull its window up.  It's still giving the above message about it not running.

---

### Post by Toz on 2014-07-16
What does the following return:
```
ps -ef | grep power-manager | grep -v grep
```

---

### Post by pretty_whistle on 2014-07-16
```
nutin     1681  1841  0 13:44 ?        00:00:00 xfce4-power-manager
nutin     2103  1841  0 Jul08 ?        00:00:00 xfce4-power-manager --restart --sm-client-id 2b36a3f27-61c2-4e94-ac36-c8bb64dd04b0
nutin     2273  1841  0 Jul08 ?        00:00:00 xfce4-power-manager


```

---

### Post by pretty_whistle on 2014-07-16
I just did an "end process" on all the power managers that were running but it didnt help (3 were running).  Now only 1 is running:

```
nutin     2905  1841  0 15:41 ?        00:00:00 xfce4-power-manager


```

---

### Post by Toz on 2014-07-16
> **pretty_whistle said:**
> ```
nutin     1681  1841  0 13:44 ?        00:00:00 xfce4-power-manager
nutin     2103  1841  0 Jul08 ?        00:00:00 xfce4-power-manager --restart --sm-client-id 2b36a3f27-61c2-4e94-ac36-c8bb64dd04b0
nutin     2273  1841  0 Jul08 ?        00:00:00 xfce4-power-manager


```
Yeah, not good. I wonder how 3 instances got to run at the same time? I didn't think that was possible.

> **pretty_whistle said:**
> I just did an "end process" on all the power managers that were running but it didnt help (3 were running).  Now only 1 is running:

```
nutin     2905  1841  0 15:41 ?        00:00:00 xfce4-power-manager


```
Try clearing out your sessions cache from outside of Xfce. First log out then go to the first tty (Ctrl+Alt+F1) and log in to the text console there. Once logged in, run:
```
cd .cache
rm -rf sessions
```
...then return to the gui (Ctrl+Alt+F7) and log back in again and check to see if its any better. Also check to see how many instance of xfce4-power-manager are running.

---

### Post by pretty_whistle on 2014-07-16
Done.

It's doing the same thing except now there's 2 running:

```
nutin     2905     1  0 15:41 ?        00:00:00 xfce4-power-manager
nutin     3881  3563  0 17:03 ?        00:00:00 xfce4-power-manager


```

---

### Post by Toz on 2014-07-16
Do you have it set to run in your autostartup as well (Settings Manager >> Session and Startup >> Application autostart)?

Or alternatively, do you have an xfce4-power-manager entry in ~/.config/autostart?

Try as I may, I cannot get 2 instances to run simultaneously.

> ```
nutin     2905     1  0 15:41 ?        00:00:00 xfce4-power-manager
nutin     3881  3563  0 17:03 ?        00:00:00 xfce4-power-manager
```
Who is the parent of your second instance? In the above results, the first power-manager's PID is 2905 and its parent 1 (init). In the second instance (PID 3881) its parent is 3563. What process is 3563? Make sure you re-run the command to get the proper PIDs to check.

---

### Post by pretty_whistle on 2014-07-16
> **Toz said:**
> Do you have it set to run in your autostartup as well (Settings Manager >> Session and Startup >> Application autostart)?

Or alternatively, do you have an xfce4-power-manager entry in ~/.config/autostart?

Try as I may, I cannot get 2 instances to run simultaneously.


Who is the parent of your second instance? In the above results, the first power-manager's PID is 2905 and its parent 1 (init). In the second instance (PID 3881) its parent is 3563. What process is 3563? Make sure you re-run the command to get the proper PIDs to check.

Do you have it set to run in your autostartup as well (Settings Manager  >> Session and Startup >> Application autostart)?
Yes.  Should it??

Or alternatively, do you have an xfce4-power-manager entry in ~/.config/autostart?
No.

3563 shows up as init.

Re-run the command?  Re-run cd .cache, rm -rf sessions??

---

### Post by Toz on 2014-07-16
> **pretty_whistle said:**
> Do you have it set to run in your autostartup as well (Settings Manager  >> Session and Startup >> Application autostart)?
Yes.  Should it??
No. It should start automatically by default. No need to add to autostart. If it doesn't start up automatically, clearing the sessions cache like we did earlier will reset it to autostart.

Try removing it from your autostart sessions, then log out and clear the sessions again as we did earlier. Log back in and check the power manager again.

---

### Post by pretty_whistle on 2014-07-16
> **Toz said:**
> No. It should start automatically by default. No need to add to autostart. If it doesn't start up automatically, clearing the sessions cache like we did earlier will reset it to autostart.

Try removing it from your autostart sessions, then log out and clear the sessions again as we did earlier. Log back in and check the power manager again.

Done.

It was still running 2 of them so I did "end process" on both and then cleared sessions again.  This time grep turned up nothing running so I went to power manager and clicked it and that message from post 1 came up so I hit run.  Now grep shows 1 instance running but I still cant pull up the window to it and it's still giving me that message from post 1 claiming it's not running.

---

### Post by Toz on 2014-07-16
What happens if you try to run from the terminal:
```
xfce4-power-manager-settings
```

Any error messages?

---

### Post by pretty_whistle on 2014-07-16
> **Toz said:**
> What happens if you try to run from the terminal:
```
xfce4-power-manager-settings
```

Any error messages?

It says:

```
Xfce power manager is not running
```
... and the same little message from post 1 comes up too.

---

### Post by Toz on 2014-07-16
Hmmm.

What does the following return:
```
xfce4-power-manager --dump
```

And to confirm, an instance of xfce4-power-manager is running when you run the above command. Correct?

Maybe also:
```
apt-cache policy xfce4-power-manager
```

---

### Post by pretty_whistle on 2014-07-16
> **Toz said:**
> Hmmm.

What does the following return:
```
xfce4-power-manager --dump
```

And to confirm, an instance of xfce4-power-manager is running when you run the above command. Correct?

Maybe also:
```
apt-cache policy xfce4-power-manager
```

xfce4-power-manager --dump produces this:

```
(xfce4-power-manager:7384): xfce4-power-manager-WARNING **: could not map keysym 1008ffa8 to keycode

---------------------------------------------------
       Xfce power manager version 1.2.0
With policykit support
With network manager support
With DPMS support
---------------------------------------------------
Can suspend: True
Can hibernate: True
Can spin down hard disks: True
Authorized to suspend: True
Authorized to hibernate: False
Authorized to shutdown: True
Authorized to spin down hard disks: True
Has battery: True
Has brightness panel: True
Has power button: True
Has hibernate button: True
Has sleep button: True
Has LID: True


```

Yes, an instance is running while I did this.


apt-cache policy xfce4-power-manager produced this:
```
xfce4-power-manager:
  Installed: 1.2.0-3ubuntu5~trusty~ppa3
  Candidate: 1.2.0-3ubuntu5~trusty~ppa3
  Version table:
 *** 1.2.0-3ubuntu5~trusty~ppa3 0
        500 http://ppa.launchpad.net/xubuntu-dev/ppa/ubuntu/ trusty/main i386 Packages
        100 /var/lib/dpkg/status
     1.2.0-3ubuntu4.1 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/universe i386 Packages
     1.2.0-3ubuntu4 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/universe i386 Packages


```

---

### Post by pretty_whistle on 2014-07-16
Whoa it's working now.  I just decided to try it..........  that surprised me.  I wonder what did it.

---

### Post by Toz on 2014-07-16
> **pretty_whistle said:**
> Whoa it's working now.  I just decided to try it..........  that surprised me.  I wonder what did it.

The stars must have aligned.

I also notice that you are running the development version of xfce4-power-manager from the xubuntu-dev PPA. You've probably stumbled upon some sort of bug.

---

### Post by pretty_whistle on 2014-07-16
> **Toz said:**
> The stars must have aligned.

I also notice that you are running the development version of xfce4-power-manager from the xubuntu-dev PPA. You've probably stumbled upon some sort of bug.

Oh yeah? :)  Is it possible to install a non-development one?  I got a hold of it by accident..........

---

### Post by Toz on 2014-07-16
That PPA also houses the light-locker-settings package. Not sure if that was what you were after and got a newer xfce4-power-manager as a bonus. lol. Actually, there's an even newer version now, 1.3, and its looking pretty good with alot of bug fixes and enhancements. Hopefully will make it to 14.10.

I just fired up my development version of Xfce (built from git) and I notice that xfce4-power-manager now runs 2 instances. I'll look into why and see what I can come up with.

---

### Post by pretty_whistle on 2014-07-17
> **Toz said:**
> That PPA also houses the light-locker-settings package. Not sure if that was what you were after and got a newer xfce4-power-manager as a bonus. lol. Actually, there's an even newer version now, 1.3, and its looking pretty good with alot of bug fixes and enhancements. Hopefully will make it to 14.10.

I just fired up my development version of Xfce (built from git) and I notice that xfce4-power-manager now runs 2 instances. I'll look into why and see what I can come up with.

If the new power manager makes it to 14.10 will it be available in synaptic? because I'd like to upgrade it when the time comes............

---

### Post by Toz on 2014-07-17
Yes, it should be available in the official ubuntu repositories if it makes it in time for 14.10 release. If not in the official repositories, there may be a PPA that would house it.

---

