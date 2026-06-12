---
title: "Running Linux script from Windows desktop"
date: 2008-05-21
forum: General Help
---

### Post by strikenowhere on 2008-05-21
Hello,

I am curious to know if there is a way for a script residing on a Linux server to be run from a Windows desktop?  As part of our company's backup system, we rotate two sets of disk enclosures from an Ubuntu 6.06 LTS server (we are NOT looking to upgrade to allow for hotswap with Hardy Heron) and I need to find a way that a non-technical user on a Windows machine can remotely execute a shutdown script to power down the Linux server so that the enclosures can be rotated.

Anyone have any ideas?

Thanks,
Greg

---

### Post by pytheas22 on 2008-05-21
As long as the users are comfortable with the command line, it's as simple as using ssh to log in to the Ubuntu machine from Windows and run whatever commands you want using an ssh client like putty.

If they don't like the command line, you should be able to set up putty so that a given command would automatically run on the Ubuntu machine when a user logs in via ssh.  All they'd have to do is log in and the commands you need would run.

---

### Post by bingoUV on 2008-05-21
ssh into the linux machine and run the script.

---

### Post by fsmithred on 2008-05-21
Install putty on the windows machine, have the person log in to the linux box through ssh and run the script. They should be capable of typing a username, password and a single command.

---

### Post by strikenowhere on 2008-05-21
Thanks for the help guys but I was actually able to find a better solution....I found that Putty's website offers plink.exe which seems to be a command line version of Putty.  I'm able to create a .bat script that a user can run from their Windows desktop that will launched plink.exe along with a shutdown command.

Greg

---

### Post by deartejas on 2011-07-28
can anyone write down the actual command line for this ?

---

### Post by Habitual on 2011-07-28
[http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html)

---

### Post by deartejas on 2011-07-29
I am looking for actual command line to remotely connect to linux box from windows box and remotely shutdown linux box on power outage.
 
can anyone send a steps with sciprt for this ? :confused:

---

### Post by pytheas22 on 2011-07-29
> **deartejas said:**
> I am looking for actual command line to remotely connect to linux box from windows box and remotely shutdown linux box on power outage.
 
can anyone send a steps with sciprt for this ? :confused:

You need to download an ssh client the runs on Windows, such as [Putty]("http://putty.org"), then connect to the Linux machine run the command:
```

shutdown -h now
```

In most cases you would probably need to be logged in to the Linux machine as root to run that command, or prefix it with "sudo".

---

### Post by Habitual on 2011-07-29
> **deartejas said:**
> ...connect to linux box from windows box and remotely shutdown linux box on power outage....

say what?
```
if [[ $power = "out"; then
ssh not possible
else
exit
fi
```

---

