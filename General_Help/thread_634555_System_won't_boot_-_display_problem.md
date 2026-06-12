---
title: "System won't boot - display problem"
date: 2007-12-07
forum: General Help
---

### Post by Robotman on 2007-12-07
I just tried to use an old video card in my main Ubuntu system..... it uses integrated video (VIA) normally:  When I booted the computer with this old video card, I had to plug the monitor into it, because that's where the video signal was.  I decided not to keep that video card installed, so I shut down and removed it.  Now when I try to boot back up, Ubuntu loads up to a certain point then stops and gives the following error message:
```
Starting up ...
Loading, please wait...
kinit: name_to_dev_t(/dev/disk/by-uuid/(UUID number)) = hda5(3,5)
kinit: trying to resume from /dev/disk/by-uuid/(UUID number)
kinit: No resume image, doing normal boot...

Ubuntu 7.10 mike-desktop tty1

mike-desktop login:
```
I should also note that when I booted the system with the old video card installed, Ubuntu loaded in reduced graphics mode, and I had to specify the monitor make and screen resolution.
How can i fix my system like it was before?

---

### Post by theDaveTheRave on 2007-12-08
Robotman.

it sounds like you have a similar problem to me, when I boot up I don't have a graphical logon screen, unless I boot into the system restore mode, when I can login fine as root.

I started a thread here [http://ubuntuforums.org/showthread.php?t=625230]("http://ubuntuforums.org/showthread.php?t=625230")
whcih has a workaround solution, that I am now using.

briefly the solution is this.

Disable the graphical logon, so as you start up into a "terminal" type mode.

re-configure the x-manager , for anybody to run.


for some extra information do you get this error when you run <startx> from the CLI of your normal user logon??



> 

davem@Planchet:~$ startx
xauth: creating new authority file /home/davem/.serverauth.4809
X: user not authorized to run the X server, aborting.
xinit: Server error.



here is the process for my workaround solution.

first reconfigure X to be used by "anybody", just follow the on screen instructions.

> 
sudo dpkg-reconfigure x11-common


then to remove the GDM (or if you are uding KDM I assume it will remove that by simply changing <gdm> to <kdm>) run the command
> 
sudo update-rc.d -f gdm remove


The reason I think that this may be the same problem is that now when I start up I get the error message that you are reporting.

when did this error first occur?

for me everything was fine, then I did a load of updates (via synaptic), and lost my login! One of the things that I have noticed since loging in to the CLI is that the boot procedure takes considerably longer than before, I assume this is because it is attempting to find a restore image that isn't there any longer? Then of course I still need to start the window system (whic is in fact quite quick), but adds another delay to my login procedre.

I wonder if I can speed things up by having it as a login script?

which oddly enough now make me wonder if once I have done that if it was just a prblem with the splash screen startup?? hmmmm??:confused:

anyway good luck in finding a solution, tell me if the above works for you though

Dave

---

### Post by Robotman on 2007-12-08
Hm.... looks like the error message is the same, but the problems are different.  I'm not so much interested in a workaround as I am a complete fix, so I've just backed-up my important files and reinstalled Ubuntu.  That will fix an unrelated issue I had with another program as well. ;)
Thanks for the help though.

---

