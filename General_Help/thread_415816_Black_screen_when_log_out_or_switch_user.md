---
title: "Black screen when log out or switch user"
date: 2007-04-20
forum: General Help
---

### Post by bustergonad on 2007-04-20
HI, hope this is in the correct section.
I got Beryl working perfect with mt ATI x200 graphics card using the guide [here]("http://ubuntuforums.org/showthread.php?t=399643&highlight=x200m")

However since then, whenever i log out or switch user, i get a black screen, and i have to press my off switch on the computer to turn it off, then on, and i can then log on again with no problem.

Does anyone have a solution for this ???

Thank~you :)

---

### Post by bettermentflux on 2007-04-20
I have the same results using an ATI Mobility Xpress 200M. The only "solution" I've found is to disable the proprietary driver using the "restricted Drivers" control panel.

---

### Post by xombie on 2007-04-20
Their is a bug report on this problem. A work around is in the bug report.
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.8.1/+bug/107115](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.8.1/+bug/107115)

---

### Post by bettermentflux on 2007-04-21
If I can save someone the time of searching it out...

type this in a terminal:

sudo gedit /etc/X11/gdm/gdm.conf

find the line that begins with
#AlwaysRestartServer=false and change it to read
AlwaysRestartServer=true

reboot and you should now be able to log out.

The importance of this bug is currently "undecided". If it affects you I'd suggest adding your own comments to the bug so that we can get this one squashed.

---

### Post by bustergonad on 2007-04-21
Thanks for the Kind help and advice :)

Unfortunately that has not worked for me :(
I note that it also does not work for someone else in the bug report.

Can anyone offer any more suggestions/advice to fix the problem, or will i have to be patient untill the bug is fixed.

Thank~you :)

---

### Post by EP2007 on 2007-04-23
This black screen is also happening for me and was actually the cause of data loss (no longer able to start Ubuntu or Gnome).

I have reinstalled Ubuntu 7.04 and the problem still occurs... This has been happening on two of my computers, which are both running ATI cards.

My wife and I can't trust Ubuntu anymore as we both use separate user accounts and have to switch users on a regular basis.

---

### Post by bettermentflux on 2007-04-23
I wonder if anyone's had luck using the recently updated ATI drivers (V 8.36.5 - more info available at [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.36.5.html]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.36.5.html") ).

The one currently shipping with Feisty is V 8.34.8.

In the meanwhile, make sure you try the workaround posted a few messages above. Results have been mixed but it worked for me.

---

### Post by EP2007 on 2007-04-23
> **bettermentflux said:**
> I wonder if anyone's had luck using the recently updated ATI drivers (V 8.36.5 - more info available at [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.36.5.html]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.36.5.html") ).

The one currently shipping with Feisty is V 8.34.8.

In the meanwhile, make sure you try the workaround posted a few messages above. Results have been mixed but it worked for me.

It's interesting that the following is listed as fixed in this latest version:

"In certain AGP graphics cards the system no longer ceases to respond when switching from the X-Server display to a text console. "

The problem is, my wifes computer does not have an AGP card and the crashing does not happen with switching to text mode, only when switching users in Gnome (and even sometimes when logging out).

The 'fix' that ATI lists sounds similar to my problem, but with different variables from what I have here... :(

---

### Post by rsay on 2007-04-23
I used ctrl-alt-backspace to restart the x-server and get back to a login screen.  Not elegant but prevents a shutdown.  This starts a new session though which is not what I'm after. 

I need to get this fixed because this is a showstopper on my main family computer.

---

### Post by coffee-n-cream on 2007-04-23
looks like im having the same kind of problem too

---

### Post by rsay on 2007-04-24
I seem to have solved my problem by disabling desktop effects. I'm going to miss the cube :(

---

### Post by EP2007 on 2007-04-24
> **rsay said:**
> I seem to have solved my problem by disabling desktop effects. I'm going to miss the cube :(

You may have avoided the problem, but if desktop effects is causing this problem, it should be fixed... I also want cube :)

---

### Post by castylx on 2007-04-25
I'm seeing the exact same thing... I had to disable my effects for it to work too...however I'm not using an ATI card, but an Nvidia6200LE.

Forgot to mention that I tried the workaround, it didn't work and also gave me an annoying password to enter the second time.

---

### Post by kristjans on 2007-04-25
I am having the same problem.

Specifications:
Ubuntu Feisty Fawn 7.04 
ATI Radeon Xpress 200
ATI proprietary drivers

I need the proprietary drivers, because the open source drivers do not support any real 3D other than the cube, which I don't consider necessary. Because of the proprietary drivers, I can't run the desktop effects though, so it also cannot be the cause for the log in problem.

Switching the user and logging out is the only annoying bug I have on this desktop.

---

### Post by rsay on 2007-04-25
My card is also nvidia - GeForce 6200 and I am using the nvida driver installed by the restricted drivers manager.

---

### Post by Vajra Vrtti on 2007-04-27
My hardware/software configuration seems to be exactly the same as **rsay**'s, as well as his description of the problem in the bug report.

---

### Post by Vajra Vrtti on 2007-04-28
I found the following suggestion in the thread
[http://ubuntuforums.org/showthread.php?t=366282&highlight=switch+user+desktop+effects]("http://ubuntuforums.org/showthread.php?t=366282&highlight=switch+user+desktop+effects")

> [B]*mannheim*
Re: Compiz / Beryl switch user problems[/B]
For some people (including me!) an effective cure is to turn off the option "Sync to Vblank" in beryl-settings (for both users, if both are using beryl).
Using recent versions of compiz, the same workaround almost works: sometimes one or two windows are corrupted after the switch.

That worked for me too! Now I am able to fast switch between a user using Beryl and another with a standard desktop.

---

### Post by Doughy on 2007-04-28
Same problem here.

I posted a separate bug on this issue before I knew about this one: [https://bugs.launchpad.net/ubuntu/+bug/109357](https://bugs.launchpad.net/ubuntu/+bug/109357)

There is also another forum thread on the matter here: [http://ubuntuforums.org/showthread.php?p=2517231](http://ubuntuforums.org/showthread.php?p=2517231)

---

### Post by maddee on 2007-05-28
The work around posted by bettermentflux worked perfectly for me. My symptoms were exactly the same as the other posters. I simply changed the value to true and saved the changes, rebooted and then tried to replicate the blank screen but couldn't!! Ubuntu Linux Rocks! Hey Willy G....kiss my Ubuntu!!

---

### Post by borimrr on 2007-07-18
> **bettermentflux said:**
> If I can save someone the time of searching it out...

type this in a terminal:

sudo gedit /etc/X11/gdm/gdm.conf

find the line that begins with
#AlwaysRestartServer=false and change it to read
AlwaysRestartServer=true

reboot and you should now be able to log out.

The importance of this bug is currently "undecided". If it affects you I'd suggest adding your own comments to the bug so that we can get this one squashed.

Worked perfectlt, thx.

---

### Post by distortedstar on 2007-12-21
On Log out or switch user, my screen often goes blank, with my monitor displaying an error message as if it's being fed wrong resolution info. Boot up is fine, happens only on log out and switch user.

I can confirm that this happens to me  with an Nvidia GeForce 6200 A-LE, with the nv or nvidia driver, regardless of desktop effects.

---

### Post by distortedstar on 2007-12-30
This is obviously a gdm/kdm bug...I have no issues when using xdm as the login manager!

---

