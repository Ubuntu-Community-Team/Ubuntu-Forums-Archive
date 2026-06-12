---
title: "Reinstall base packages?"
date: 2015-12-22
forum: General Help
---

### Post by SimonHGR on 2015-12-22
Hi all, I had a strange situation that uninstalled some core packages (see previous thread [http://ubuntuforums.org/showthread.php?t=2307062](http://ubuntuforums.org/showthread.php?t=2307062) explaining some, probably not important, background). Well, it turns out that many more packages are missing, and I don't know how to determine which / or to reinstall those.

Now, I could, in theory just reinstall from scratch, but one piece of paid software (yeah, never a good idea!) has a bizarrely draconian license, and if I do that, I'll have to pay for it again (several hundred bucks). So, I'm hoping to be able to reinstall just the missing base packages.

Can anyone tell me how I would determine what's missing, or run a wholesale "install if missing" kind of command?

FWIW, my current situation is that I'm able to log in, but I get no window manager whatsoever, so I can only open a directory that happens to be on my desktop, then use the file manager to launch /usr/bin/gnome-terminal, then play command-line games to launch whatever else I might need. Hence, I have enough to run the various software installers (apt-get, and the GUI-based tool) but I don't know how to find out what needs replacing...

TIA
Simon

---

### Post by Bucky Ball on 2015-12-22
*Thread moved to **General Help**.*

You only need to get to a CLI (control+alt+F1 from the login screen or desktop) or a terminal. You need to be online, and once you are, try:

```
sudo apt-get install ubuntu-desktop
```

If you are running another flavour, say Xubuntu, replace 'ubuntu-desktop' with 'xubuntu-desktop'. Once this is done, reboot and see how you go.

Good luck.

---

### Post by SimonHGR on 2015-12-22
Thanks, that got the window manager stuff back nicely.

I realized that there were other things missing too, though they didn't necessarily show up as obviously as gross missing controls. So, here's what I've started doing (it's taking some time, so I don't know the total outcome, but it seems promising).

I have a VM with a base install of the same (14.04LTS) version of ubuntu. So, on both the host and the VM, I ran:

apt list --installed | cut -d/ -f1 | sort > list.txt

Then I did a diff on the two list files, and looked for just the files that were specific to the host system:

diff host-list.txt vm-list.txt | egrep "^>" | cut -c3 > replacelist.txt

(the egrep finds the lines that were in the vm-list.txt file, but not in host-list.txt.)

That gave me a list of package names (without versions or source locations, since some of those differed between the two systems) that were present on the base install on the VM, and not present on my "real" machine.

Then I set this running:

for i in $(cat replacelist.txt)
do
sudo apt-get install $i
done

and tried to see if it was destroying anything, or simply installing. It seems to want to removing a lot of things it thinks are now redundant having been autoinstalled, but I'm not letting it right now in case they're needed by some other package that will be added later in the list.


Fingers crossed...

---

### Post by SimonHGR on 2015-12-22
That seems like it finished the job. I guess this might be a generally useful technique. The only thing that would perhaps make it slicker is if there's a published list of all the standard packages, so one doesn't have to hijack a copy from another install.

Anyway, many thanks for your help "Bucky" (love that geometry! love that guy :D )

---

### Post by oldos2er on 2015-12-22
Not sure why you have this tagged "10.04," which is end-of-life and no longer supported. Did you mean to type "14.04"?

---

### Post by SimonHGR on 2015-12-22
> **oldos2er said:**
> ...Did you mean to type "14.04"?

Bother. Yes, I did. Actually, I didn't type it. Such are the perils of mindlessly "recognizing" things on lists instead of thinking and typing. I don't see an obvious route to change it. Any hints?

---

### Post by oldos2er on 2015-12-23
I changed it.

---

