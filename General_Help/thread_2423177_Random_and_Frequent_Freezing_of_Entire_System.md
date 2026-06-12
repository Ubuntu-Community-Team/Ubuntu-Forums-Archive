---
title: "Random and Frequent Freezing of Entire System"
date: 2019-07-18
forum: General Help
---

### Post by drsaamah on 2019-07-18
I am at my wits end with this one...
My computer freezes constantly.  So badly that I can't even Ctrl+Alt+F6 to try to work from the terminal line. The mouse pointer moves (although there exists a stationary mouse pointer wherever it was when it froze) and that is it.  I cannot Ctrl+Alt+Del or anything.  I just did a clean install (not an upgrade) from 18.04 LTS to 19.04 (both the Ubuntu Studio variant).  I still have exactly the same problem.  This is on a Dell XPS 502l with the i5 core processor (2410m).
I have the dmesg output saved but the forum isn't allowing me to upload it.

---

### Post by TheFu on 2019-07-19
I would check all the log files first. ALL OF THEM, for warnings and errors. Troubleshoot any of those messages.

Next, I'd see if the system has the issue when I never login at all.  On the login screen, instead of the userid, I'd type in the current time.  I'd plan on this being untouched at least overnight. 

If it freezes from that, then I know it isn't anything to do with a login. If it doesn't, then I'd setup ssh-server and login remotely to look around. While I'm there, I'd create a new user-account and login using that without any modifications.  Leave it logged in until the system freezes.  If that doesn't happen quickly, I'd assume it was my normal account with the issue and remove any non-data-files from the original userid HOME directory.  Old settings often aren't compatible with new programs.

If the new userid also freezes, I'd try to ssh into the machine, because a frozen GUI doesn't mean a frozen OS.  About 90% of the time, a stuck GUI is just a stuck GUI. The other 90%, we can ssh in and see what happened.  Sometimes it is the GUI (gnome/kde/whatever) and sometimes it is the GPU drivers.  In step one (warnings/errors), you should have seen any GPU driver issues, but you might have missed them somehow.

BTW, nobody wants to see entire log files here. Only the relevant parts should be posted.  If you want me to look at them in whole, that's called "work for hire" and we'd need to get into a contract for minimal hours (usually about 500 hrs/yr or more) at my current hourly rate.  OTOH, we like helping people learn to solve their own issues. That is free from the volunteers here.

---

### Post by drsaamah on 2019-07-19
@TheFu That sounds totally fair, but honestly I would prefer to hire someone who can read before they spout off 3 paragraphs of irrelevancy.  Also, I've been on the forums a little longer than you have.  I am more than glad to solve my problems myself.  Just looking for an avenue of diagnostic, which I will gladly take from someone who knows what they're talking about.

As I have already stated: The entire OS is frozen.  As I have already stated: Even after a clean install so the username being used is already unmodified (again, reading is really important).

Has anyone experienced anything like this?  This issue haunted me on 18.04 LTS on the 4.x kernel and now exactly the same thing on 19.04 with kernel 5.x.  I would assume a hardware issue but I have run hardware diagnostic via the BIOS and everything checks out.  I have also performed fsck on the Linux partition of the harddisk and it comes out clean no bad blocks or anything.

---

### Post by dragonfly41 on 2019-07-19
> [COLOR=#000000]I would assume a hardware issue but I have run hardware diagnostic via the BIOS and everything checks out.[/COLOR]

You need to develop the intuitive powers of Sherlock Holmes.  There are many posts on freezing seen in this forum and there is no magic wand.
There is a log filtering tool **petit** which searches for frequent patterns in log files rather than posting them here.
Another game plan is to look at your memory card(s) and I have resorted in past freezing incidents on an older laptop to remove them, clean the edges with a clean rubber, and reinsert. If you have two memory cards you can try inserting one by one to see if freezes reoccur.
Then there is the commonly reported fix of changing drivers.   If you have a LiveUSB does it freeze?
You get the general idea .. process of elimination. And I must not forget possible faulty power supply/cables?

These ideas should be added to the list provided by @TheFu.

Perhaps one day we might publish a diagnostic decision tree as a tool.

---

### Post by TheFu on 2019-07-19
I should have asked for more details and explanation like we are old, have poor eyesight and are a little dumb. Sorry.

Didn't see any proof that "the entire OS is frozen", only that changing terminals wasn't working after the current GUI stopped being responsive. It happens all the time that people believe the entire OS is frozen when it is only the input or GUI interface.  Have you seen anything that would say it isn't just an interface/input freeze?  Would you care to expand on the explanation and timing?  Does it freeze after a few minutes of boot, pre-login?  Post-login?  Or immediately after the first reboot post-install?

A "fresh install" doesn't say when it happened.

Last month, I had a machine appear to lock up.  I went to a different machine and ssh'd in. Turned out that it was just really, really, low on available RAM.  Looked in the logs and didn't find anything, so for me, that ruled out hardware as the prime issue.  Looked at the swap partition and noticed it was less than 1 GB in size which I guess is the default for an install like mine. That size freaked me out. For my desktop needs, between 4-5G  swap is the correct size, so after that was fixed, no more apparent lock ups since.   Might want to check the amount of swap available and total virtual memory used on your box.

To check all the current log files, use ```
sudo egrep -i 'error|warn' /var/log/*g
``` if you don't have some other preferred method.

---

### Post by rbmorse on 2019-07-19
If the mouse pointer moves, the entire O/S is not frozen.

---

### Post by ajgreeny on 2019-07-19
Unless things have changed I believe the Ubuntu-Studio variant uses a low latency kernel, and depending on the uses to which you put the computer I wonder if you might manage better with the standard generic kernel series.

I hasten to add that my knowledge of kernels and their uses is very limited so I may be totally wrong about this; worth trying though, surely.

---

### Post by drsaamah on 2019-07-19
Okay, thank you all.  I am at work and away from the computer at issue but I will try the suggestions provided.  I apologize if I seemed like I was for free support; I would prefer to resolve the issue myself but I really didn't know what else to look.  I will check the ram usage and swap partition sizes and try to ssh into the machine.  As far as when it freezes, it is completely random which is part of what leaves me baffled.  Sometimes heavy browser usage, but other times as soon as I log in.  Some nights there are no problems at all.  The only thing that is consistent is that the freezes occur when I am using the computer.  I have never left the computer idle and come back to find it frozen.  Oh, I will also check the PSU as recommended. Thank you again for your suggestions.

---

### Post by CatKiller on 2019-07-19
> **drsaamah said:**
> The mouse pointer moves (although there exists a stationary mouse pointer wherever it was when it froze) and that is it.  I cannot Ctrl+Alt+Del or anything.

An X hang can give symptoms exactly like this: often the computer is still running stuff fine, but only the hardware cursor can draw to the screen, and you can't interact with windows and stuff because X has hung. Not having keyboard input either is a pain, but not insurmountable if you can still ssh in.

> **drsaamah said:**
> Has anyone experienced anything like this?  This issue haunted me on 18.04 LTS on the 4.x kernel and now exactly the same thing on 19.04 with kernel 5.x.

As far as I can tell, that laptop has a GT 540M. Are you using the proprietary driver? The last driver branch that supported that card was 390. Incompatibilities between old drivers and new kernels is a thing that happens, although it seems a bit early for that to be the case here.

I have no experience of Optimus graphics; it looked like a complete mess before I got my first laptop, so I steered well clear.

---

### Post by drsaamah on 2019-07-19
@CatKiller, thank you for the reply.  I was using the proprietary driver on 18.04.  When installing 19.04 I did select to download proprietary drivers but did not check if it recognized and installed the Nvidia driver or not and which version. I will look into this as well.  Thank you again.  Just to clarify, are you saying that I should use branch 390 of the driver or am I better off staying away from the proprietary driver altogether?

---

### Post by CatKiller on 2019-07-19
> **drsaamah said:**
>  Just to clarify, are you saying that I should use branch 390 of the driver or am I better off staying away from the proprietary driver altogether?
As I understand it, Optimus is less bad with the proprietary driver.

---

### Post by TheFu on 2019-07-20
Last week, nvidia and Canonical got together on how the proprietary drivers would be available for LTS releases. It doesn't apply to non-LTS releases, however.  [https://www.omgubuntu.co.uk/2019/07/install-nvidia-driver-update-ubuntu-its#comment-4546804827](https://www.omgubuntu.co.uk/2019/07/install-nvidia-driver-update-ubuntu-its#comment-4546804827) is the article.

I know it is working on 16.04. My only system with nvidia got an GPU driver update last Saturday.

---

### Post by Autodave on 2019-07-20
I looked your machine up and found that it was built many different ways: at least 2 Nvidia and a Radeon GPU, anywhere from 2 to 8 gig of RAM.  Do you know how much RAM you actually have?

As already suggested, try to ssh in when it appears to be locked/frozen.  If you cannot ssh in, my first thought would be a RAM issue.

---

### Post by drsaamah on 2019-07-22
Hi everybody,

Sorry for the delayed update.  So CatKiller inadvertently nailed the problem.  I was in fact using the proprietary driver for the NVidia graphics card but it seems that may have been problem.  I decided to inactivate it and go with the open source Nouveau driver and its been 3 days without any issues. So my guess is the NVidia driver is no longer being updated/maintained to account for whatever changes in the last few kernel update.  Or maybe I've just been lucky the last few days haha.  If the problem returns I'll update the thread in case anyone else is experiencing this problem.  Thank you everyone here for your suggestions and wisdom.

---

