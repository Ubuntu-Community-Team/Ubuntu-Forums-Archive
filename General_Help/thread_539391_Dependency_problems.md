---
title: "Dependency problems??"
date: 2007-08-31
forum: General Help
---

### Post by doctorbrowder on 2007-08-31
I'm desperately trying to install the printer driver for my new Brother DCP-130C printer / scanner  / copier. I have downloaded the Linux Debian driver from the Brother website, a file called "dcp130ccupswrapper-1.0.0-10.i386.deb". I have tried installing it through the terminal, but it came back with "dependency problems":

"Dependency problem: dcp130ccupswrapper-1.0.0-10.i386.deb depends on dcp130clpr; however, Package dcp130clpr is not installed."

Should I just take the printer back to the store and do without a printer? I've already had to give away one printer / scanner / copier (a Canon) because it didn't have any Linux drivers at all. I thought this Brother model would solve my problems... it hasn't.

---

### Post by kesman on 2007-08-31
just install the package with synaptic or type in to console "sudo apitude install packagename" and then try installing the driver again. You could also try to google or search this forum with that packagename to see if someone else has had the same kind of problems with that printer.

---

### Post by doctorbrowder on 2007-08-31
OK, I found the dcp130clpr file on Brother's website, and downloaded the file "dcp130clpr-1.0.0-9.i386.deb". When I tried to depackage it in the terminal, here's what I got:

Setting up dcp130clpr (1.0.0-9)...

mkdir: cannot create directory 'var/spool/lpd/dcp130c': no such file or directory
chown: cannot access 'var/spool/lpd/dcp130c': no such file or directory
chgrp: 'var/spool/lpd/dcp130c': no such file or directory
chmod: 'var/spool/lpd/dcp130c': no such file or directory

OK, so now what?

---

### Post by bmorency on 2007-08-31
how about trying to install lpr/lpd?

```
sudo aptitude install lpr
```

---

### Post by Seisen on 2007-08-31
Put this in the terminal

```
sudo mkdir /var/spool/lpd
sudo mkdir /var/spool/lpd/dcp130c
```

---

### Post by doctorbrowder on 2007-08-31
Thank you, one and all. After following all of the above suggestions, I now have the printer working on my Brother 130DCPC printer / scanner / copier. 

Now, if I can just get Xsane Image scanner to communicate with it. I have installed Sane Xsane, but when I call up the Xsane program, it says

[I]Failed to open device 'brother2:bus1;dev1':
Error during device I/O[/I]

I will try reinstalling the scanner driver and see if that works...

---

### Post by Seisen on 2007-08-31
Here is what you need, I attached the file. Also here are the directions to set it up, just pick which ever link you need.

For USB user
[http://solutions.brother.com/linux/sol/printer/linux/sane_install.html]("http://solutions.brother.com/linux/sol/printer/linux/sane_install.html")

For network user
[http://solutions.brother.com/linux/sol/printer/linux/sane_install-net.html]("http://solutions.brother.com/linux/sol/printer/linux/sane_install-net.html")

---

