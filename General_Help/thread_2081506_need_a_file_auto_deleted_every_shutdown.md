---
title: "need a file auto deleted every shutdown"
date: 2012-11-07
forum: General Help
---

### Post by Dn4mycrownj on 2012-11-07
Im running a flavor of Ubuntu 10.04 Lucid.  I have it installed on a 16G persistent flash drive. with only the boot file not encrypted I use this on many different laptops and computers for the tools that i have installed on this build.  For me to be able to get wifi or local connection i have to delete the file located at

"/etc/udev/rules.d/70-persisten-net.rules" 

then reboot. Is there any way i can have this file auto delete on shut down. The file is auto regend if missing at reboot. When it regens the network connection either wifi or local area works on what every laptop or desktop that i am using. 

i thought about cron but that is a time thing and i dont think i can make it run at shutdown. What i am wanting to do is add a line in to the shutdown files to tell the OS to delete that file before it sends all its kill sig. 

now is this possible and if so what file and maybe want line number do i need to edit.  if not possible anyone get any ideas.

---

### Post by Lars Noodén on 2012-11-07
You could put the script you want in an [Upstart](http://upstart.ubuntu.com/cookbook/) script and set it to run for runlevels 0 and 6. 

```

...
start on runlevel [06]
...

```

---

### Post by Dn4mycrownj on 2012-11-07
do i need to put

#stop on run level ??

or just start and then my script

---

### Post by Lars Noodén on 2012-11-07
[Runlevel 0](http://www.debianadmin.com/debian-and-ubuntu-linux-run-levels.html) is shutting down, runlevel 6 is rebooting.  So I think you'll want to start your script on those events.  It will call for a little experimentation and there are several ways of getting the right timing.  There are also [pre-start and post-stop](http://upstart.ubuntu.com/getting-started.html) capablities.  You can also tie the action to some other service's state or whether it is starting up or shutting down.

---

### Post by Dn4mycrownj on 2012-11-07
thank you very much for the info

---

