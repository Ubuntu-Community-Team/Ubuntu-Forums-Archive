---
title: "Problems with post-installation setup"
date: 2006-12-29
forum: General Help
---

### Post by samjh on 2006-12-29
This is my third installation of Ubuntu 6.10.  The previous two installation were perfectly fine, but this one is causing a few problems.  Immediately after installation, I allowed adept-notifier to automatically update the installation, and then proceeded to install nvidia-glx, firefox, thunderbird, and finally sun-java.

Firstly, ubuntu (specifically Kubuntu) is not detecting the correct screen resolution and refresh rate after installing nvidia-glx.  Previously both Ubuntu and Kubuntu were able to correctly set my screen resolution at 1024x768 and refresh rate to 85Hz without any manual configuration.  However in this installation, following the exact process I have always followed (no hardware changes either), this doesn't work.  I have had to manually select a roughly similar monitor from the monitor and display settings applet, manually select the nvidia driver and graphics card model, and force the resolution and refresh rate, which was not necessary in previous installations of 6.06 or 6.10.

Secondly, I'm trying to find the sun-java packages.  I have enabled all the standard Ubuntu repositories: main, restricted, and universe; for binaries, source, update, and security repos.  Adept, Synaptic, apt-get, and aptitude all fail to find the sun-java packages.  I know that the programs are reading from the repos because I can get them to retrieve update headers and the repos get listed on the screen as updated lists are being received.  I have also installed other packages  from restricted and universal repos.  It's puzzling why the sun-java packages are not being picked up by any of the packaging programs.  Have the sun-java packages been removed?

Any help or answers would be gladly received.

---

### Post by meng on 2006-12-29
sun-java5-bin, sun-java5-jre, etc.
are in multiverse

---

### Post by samjh on 2006-12-29
Thanks for that.

Strange though... I had to manually type "multiverse" in synaptic.  Before, they were just selectable among a list of available of repositories in one of the menu dialogs.  Perhaps there were some updates made to adept and synaptic in the past few days?

---

### Post by meng on 2006-12-29
I seem to recall that multiverse wasn't a Synaptic option last I looked, I too thought that was strange.

---

