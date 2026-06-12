---
title: "[SOLVED] Startup program before login (with root priv. required)"
date: 2007-07-30
forum: General Help
---

### Post by DivineOmega on 2007-07-30
I need to have a command run at start up (during system start up, before login). The command I need to run is:

```
sudo /opt/lampp/lampp start
```

I intend to use the next piece of code to pipe my password to sudo. Is this (or even sudo) required if I the command is running before login?

```
echo "yourpasswordhere" | sudo -S yourcommandhere
```

I read that I need to put this somewhere in /etc/, but my main question really is where do I have to put the command so it runs during startup (and before login)?

Thanks! :D

---

### Post by eggdeng on 2007-07-30
Paste the command (with a trailing ampersand) into /etc/init.d/rc.local just after the #!/bin/sh, as follows

```
#!/bin/sh 
/opt/lampp/lampp start &
```

It will automatically run as root.

---

### Post by DivineOmega on 2007-07-30
Perfect. Exactly what I was after. :) Thank you very much.

---

### Post by ashishgoel on 2007-08-07
i also need the same.... 

I'm novice totaly to ubuntu/linux...

can u please add the exact line/command to do that...

thanx in advance

---

### Post by eggdeng on 2008-01-23
To open the file
```
sudo gedit /etc/init.d/rc.local
```
then copy and paste the command from the original post. Save and reboot.

---

