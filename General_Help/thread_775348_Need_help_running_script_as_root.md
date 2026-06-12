---
title: "Need help running script as root"
date: 2008-04-30
forum: General Help
---

### Post by dlovley on 2008-04-30
Hello,

I'm trying to run a pearl script as root. When I run it in regular console it says I need root and I must be root to run it. Can I run a pearl script from the root console and make it work or would I need to log in as root? I need to know what to type in the console to run it from a newb perspective. I'm also having trouble understanding what permission 755 is and how it relates to this running properly after googling this issue. 

Here is the path /home/darrel/mscript

here is the text from regular console

iptables v1.3.8: can't initialize iptables table `filter': Permission denied (you must be root)
Perhaps iptables or your kernel needs to be upgraded.
iptables v1.3.8: can't initialize iptables table `filter': Permission denied (you must be root)
Perhaps iptables or your kernel needs to be upgraded.

---

### Post by sdennie on 2008-04-30
I think you can run the script as root via: "sudo perl /home/darrel/mscript".  However, I would be very certain that it's a script that you trust before doing that.

---

### Post by dlovley on 2008-04-30
> **vor said:**
> I think you can run the script as root via: "sudo perl /home/darrel/mscript".  However, I would be very certain that it's a script that you trust before doing that.

I'm not sure that worked I may have been unclear about the path.

path: /home/darrel/mscript/myscript.pl 

I get this 

darrel@darrel-desktop:~$ sudo perl/home/darrel/mscript/myscript.pl
sudo: perl/home/darrel/mscript/myscript.pl: command not found
darrel@darrel-desktop:~$

This is nothing funky the script is harmless.

---

### Post by sdennie on 2008-04-30
You will need a space between "perl" and the path of the command you want to run.  So:

```

sudo perl /home/darrel/mscript/myscript.pl

```

---

### Post by dlovley on 2008-04-30
> **vor said:**
> You will need a space between "perl" and the path of the command you want to run.  So:

```

sudo perl /home/darrel/mscript/myscript.pl

```

Ok I did that and when I hit enter the cursor just went to the next line and started blinking. I think it is running but how can I verify it and then how do I shut it off? Thank you for the help.

---

### Post by howlingmadhowie on 2008-04-30
if the first line of the script contains a hashbang (something like:
```
#!/usr/bin/perl
``` ) and is marked executable ( ```
ls -o ~/mscript/myscript.pl
``` should result in a line starting with 10 characters with a number of x's. if not, ```
chmod 755 ~/mscript/myscript.pl
``` will fix that)

then you only need to type:

```
sudo ~/mscript/myscript.pl
```

---

### Post by natrixgli on 2008-04-30
You could open another terminal and type:

```

ps aux | grep perl

```

to see if it's running

and you should be able to interrupt it with CTRL+C but it will halt it immediately regardless of what it's doing.

-n8

---

### Post by howlingmadhowie on 2008-04-30
it would help if you posted the script. to check if the script is running:

in another shell window:
```

ps aux | grep myscript

```
if that returns a line, it means it's running :)

if you want to stop the script, enter ctrl+C in the window running the script.

---

### Post by dlovley on 2008-04-30
I'm all set now thank you all for the help. :)

---

### Post by howlingmadhowie on 2008-04-30
by the way, if you ever have the problem that a program totally runs out of control, you can close it by finding the process number: 
```
ps aux | grep PROCESS_NAME
```

and then entering:
```
kill PROCESS_NUMBER
```

if that doesn't work, you can try:
```
kill -9 PROCESS_NUMBER
```
which really should work.

---

### Post by jaxstraww on 2008-06-14
Trying to run sensors to monitor CPU temps. I had it working once but getting a root issue now. Not sure what path I key to get sensors to open up

shane@shane-folding:~$ sensors
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.
shane@shane-folding:~$ sudo apt-get install lm-sensors
[sudo] password for shane: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
lm-sensors is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
shane@shane-folding:~$ sensors-detect
You need to be root to run this script.
shane@shane-folding:~$ sensors
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.
shane@shane-folding:~$ sensors-detect
You need to be root to run this script.
shane@shane-folding:~$

---

