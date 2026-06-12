---
title: "Freeze on black screen on boot, recovery will freeze too"
date: 2013-03-06
forum: General Help
---

### Post by Thomar on 2013-03-06
I recently was mucking around with my graphics drivers on Ubuntu 12.10 (I have a Radeon HD 6950 and I was getting borderless windows and no lenses). After I rebooted, now Ubuntu will show the logo and the orange dots for a minute, then the screen will go black and everything will freeze. Not even the NumLock key changes any lights on my keyboard, and Ctrl+Alt+Delete does nothing.

When I run in recovery mode (by selecting Advanced Options for Ubuntu in the GRUB boot menu) I will get to the purple text Recovery Menu. If I Resume, I get the black screen described above. If I select Dpkg, then it will try to fsck on my Ubuntu partition and never finish (it will act like a command prompt with an unresponsive process, and when I hit Ctrl+Alt+Delete it will reboot just fine). If I try to Fsck it will run fsck and never finish. If I select Network it will run fsck and never finish (just like Dpkg).

However, if I select Root, I will get a shell prompt. And running fsck -f on my Ubuntu partition runs and finishes quickly, unlike the ones that the other Recovery Menu options try. Then I can mount my Ubuntu partition to get read/write access (using "mount /dev/sda# / -o remount,rw") because it only gives me read-only to start. And then when I run "ifconfig eth0 up" and "sudo dhclient eth0" I get Internet, and I can run apt-get to update things.

Okay, that's great, but I'm still not booting into a graphical interface. If I run "startx" then I will get the same black screen freeze described above. How do I repair my graphics drivers so that I can use my operating system again?

---

### Post by c2tarun on 2013-03-06
Try uninstalling the driver you installed before reboot.

---

### Post by Thomar on 2013-03-06
How do I know which one that is? I was just trying different things and wasn't paying too much attention to which. :(

EDIT: It might have been the AMD Catalyst drivers.

Isn't there a set of fallback or default drivers I can use?

---

### Post by c2tarun on 2013-03-06
> **Thomar said:**
> How do I know which one that is? I was just trying different things and wasn't paying too much attention to which. :(

EDIT: It might have been the AMD Catalyst drivers.

Isn't there a set of fallback or default drivers I can use?

Well if you were fiddling in terminal then great news :) there is a history command. [Here]("http://www.thegeekstuff.com/2011/08/bash-history-expansion/") is a tutorial for that.
If you were fiddling with UI then you might give a shot by viewing /var/log/syslog file, it will store most of your system activities.

---

### Post by c2tarun on 2013-03-06
For the list of installed packages there is also something /var/log/dpkg.log
Try checking which were the packages installed and purge them

---

### Post by Thomar on 2013-03-06
Running the history command only shows me my root command history (stuff I've done from the recovery console).

The end of /var/log/syslog shows some stuff, but the only stuff from today is a time update and some IP6 messages.

Anything else I can do to get into a graphical interface? I hate using the command line, it reminds me too much of my day job.

---

### Post by c2tarun on 2013-03-06
> **Thomar said:**
> Running the history command only shows me my root command history (stuff I've done from the recovery console).

The end of /var/log/syslog shows some stuff, but the only stuff from today is a time update and some IP6 messages.

Anything else I can do to get into a graphical interface? I hate using the command line, it reminds me too much of my day job.

Check out my last post about /var/log/dpkg.log
And your day job required use of command prompt :o what do you do?

---

### Post by Thomar on 2013-03-06
--- double post

---

### Post by Thomar on 2013-03-06
I work at a job where I build hardware so expensive that I shouldn't be allowed to touch it if I'm making mistakes like these.

Looks like it was libgl1-mesa-glx (unless I read itwrong) but... When I ran "apt-get purge libgl1-mesa-glx" (which is wrong) it removed all sorts of packages it shouldn't have. I cancelled it, but it looks like it was going through things starting with "gnome-" at the time. That should have been "apt-get remove --purge libgl1-mesa-glx", right?

So is this the point where I should just reinstall?

---

### Post by c2tarun on 2013-03-06
try running apt-get remove [COLOR=#000000] libgl1-mesa-glx
This should remove the package. and then reboot.[/COLOR]

---

### Post by c2tarun on 2013-03-06
Please let us know any updates

---

### Post by Thomar on 2013-03-06
> **c2tarun said:**
> try running apt-get remove [COLOR=#000000] libgl1-mesa-glx
This should remove the package. and then reboot.[/COLOR]

No change.

EDIT: Tried it again just to make sure. Now it's freezing on a purple screen with the ubuntu logo and five orange dots. Progress?

EDIT: Rebooted and got a black screen this time.

---

### Post by c2tarun on 2013-03-07
> **Thomar said:**
> No change.

EDIT: Tried it again just to make sure. Now it's freezing on a purple screen with the ubuntu logo and five orange dots. Progress?

EDIT: Rebooted and got a black screen this time.


hmm... That was the best help I could give, please stick around, someone who can help you will surely reply.

---

### Post by Thomar on 2013-03-10
Well, I guess I'll just reinstall Ubuntu tomorrow.

---

