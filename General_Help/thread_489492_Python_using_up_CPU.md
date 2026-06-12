---
title: "Python using up CPU"
date: 2007-07-01
forum: General Help
---

### Post by jdogzilla on 2007-07-01
Hello, I have feisty.  For some reason, every now and then, python uses up 100% of my CPU.  If I happen to notice it and stop it, things are good.  If it goes unnoticed for a while, the computer freezes and I have to reboot.  Any way I can figure out what is causing this?  Top doesn't tell me what program is causing python to run.  I do not have baegle installed either.

---

### Post by Ragazzo on 2007-07-01
You could try **pstree**

I created a file test.sh that runs python and this is what pstree outputs:

```

     &#9500;&#9472;gnome-terminal&#9472;&#9516;&#9472;bash&#9472;&#9472;&#9472;test.sh&#9472;&#9472;&#9472;python
     &#9474;                &#9500;&#9472;bash&#9472;&#9472;&#9472;pstree
     &#9474;                &#9500;&#9472;gnome-pty-helpe
     &#9474;                &#9492;&#9472;{gnome-terminal}

```

Edit: 
Take the PID of the process and go to **/proc/pid** where pid is replaced by the number. Then you can run **cat cmdline** or **sudo file exe** to see what the executable file is.

---

