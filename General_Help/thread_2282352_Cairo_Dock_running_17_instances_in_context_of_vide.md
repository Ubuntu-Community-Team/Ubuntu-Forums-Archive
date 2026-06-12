---
title: "Cairo Dock running 17 instances in context of video driver oops"
date: 2015-06-13
forum: General Help
---

### Post by dora5 on 2015-06-13
0         down vote          [URL="http://askubuntu.com/questions/636076/multiple-instances-of-cairo-dock-in-context-of-video-driver-oops#"[/URL]            

 I'm looking for specifically what would cause Cairo Dock to run 17  instances and how to fix it.   Is in context of video driver driven  system crashes and could be part of the same problem.  However it does  not look like the direct source of a video driver issue and could  conceivably cause one.
  I'm having trouble with Kubuntu.  It gives system error messages on  bootup and then hangs and has to shut off with power button.  Syslog  contains Oops errors.  I showed it to people at a local Linux meetup,  and we all agree it is focusing on the video driver, which should be  nvidia and is system driver nouveau.  I was advised to make sure I've  really installed the nvidia driver then blacklist nouveau, practiced  this in my Mint install which also was using the wrong driver, and then  logged into Kubuntu to make the fix.


  But something is also going on with Cairo Dock.   Oops erros in  syslog show Cairo dock always gets tainted downstream (on the second  pass before no more oops errors generated because the system hung).   Cairo mostly is high end graphics; it could be caught in or cause a  graphics driver issue.  In my Mint install, which is on other HD, same  computer, also was using the wrong driver, pgrep cairo yields one  process.   In Kubuntu, this yields 17 processes.   I killed all 17 of  them and cairo dock died and the system hasn't crashed yet, which was  the point.  I was hoping stopping Cairo would avoid overstressing the  system long enough to fix the driver issue if that's what the problem  is.


  But Cairo dock is also loading strangely.  First it loads half of one  instance, then it appears to run two more, so it ends up looking as if  either multiple instances are running or it has a shadow.    What is the  cause of so many instances running at once,  and how fix?  Online I  find only issue with 2 instances running at once, occasionally as many  as four instances.

Online I've found extensive discussion of cairo dock loading twice because turned on in more than one place, occasionally four times.  This looks like a different issue.   


  Conceivably the entire problem is Cairo Dock.  In any case this is definitely abnormal behavi or that needs fixing, would appreciate how to do that.  

  Thanks!

---

### Post by dora5 on 2015-06-13
Thanks to everyone who helped me so quickly.

Here is how I fixed it.   Or I think I fixed it.    It still loads funny, but only one instance running, no oops, no system crashes.  

I had installed xscreensaver shortly before all the oops graphics driver issues started.   Never thought those video driver issues started
 all by themselves...  not necessarily unreasonable to think upgrading which drivers in use wouldn't fix it, however.

I had removed screensaver but not its dependencies.  That and uninstalling Cairo dock removed alot.   It turns out that with xscreensaver 
had evidently installed a second set of linux headers; wonder if that created a conflict.   They got autocleanedup or whatever the correct term is by my more
 thorough purge/ remove/ autoclean of xscreensaver.    

I checked in the driver control feature the box to use the most up to date nvidia driver, which was already there.   I added a set
 of blacklist commands to /etc/modprobe.d/blacklist.conf by gksudo gedit, couldn't figure out the redirect/ piping procedure and didn' twant to mess it up.

blacklist nouveau
blacklist lbm-nouveau
options nouveau modeset=0
alias nouveau off
alias lbm-nouveau off

I rebooted.

I had something goofy going on with system trying to update gambas from the wrong place, so I uninstalled it.

Didn't all uninstall; some of it goes with Cairo dock.

I found (Kubuntu doesn't make that easy) the autostart - KDE control module and the session management, and 
set the system to not load the previous
sessoin's whatever at startup.

Could not clear the ~/.cache/sessions/x* folder, which allegedly is in the HOME directory; found /.cache
but no sessions folder, and none of the sessions
folders I found contained anything to do with it.

Reinstalled cairo dock.

Rebooted (rebooted alot while I was doing all of this)

Cairo dock autostarted, and loaded funny, but once I clicked on it it settled down.  Can't find the option in Cairo Dock to not autostart 
and probably that configuration feature does have autostart Cairo if I looked for it at this minute.

But only one instance of Cairo dock is running, and I've got no system error message, no oops, and no apparent video driver issues.

---

