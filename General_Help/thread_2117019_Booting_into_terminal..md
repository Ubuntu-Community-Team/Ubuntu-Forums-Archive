---
title: "Booting into terminal."
date: 2013-02-17
forum: General Help
---

### Post by mdunks on 2013-02-17
Hello, I have just recently downloaded Ubuntu; and was using it without any problems for a cay, play games ect... Then i decided to shut my computer down and restart because i just installed a new game, and it boots into a black screen and asks me to log in through there. I do not know what it exactly said but it was like 

Something something
something
Username:  Dunks
password:
Then i would log in and it just stays on the termainal.

---

### Post by howefield on 2013-02-17
Post moved to its own thread.

Your are more likely to get help in your own thread especially when it is a completely different subject to the one you posted in.

---

### Post by snowpine on 2013-02-17
Welcome to the forums! What is the name of the game that your Ubuntu stopped working after you installed it, and how did you install it?

Anyways, to get back to the GUI desktop you should be able to type:

```
startx
```

If there are error messages please share them here so we can assist you. :)

---

### Post by mdunks on 2013-02-17
Well when I log in and do startx i get 

/etc.X11/xinit/xserverrc: 3: exec: /usr/bin/x: not found


xinit: giveingup
xinit: unable to connect to x derver: no such file r directory
xinit: server error

My friend said this happened to him but it was because of his graphics drivers.

so i do not know what to do.

---

### Post by Habitual on 2013-02-17
[What is a terminal?]("http://en.wikipedia.org/wiki/Terminal_emulator")
[What is the console?]("http://en.wikipedia.org/wiki/System_console")

---

### Post by mdunks on 2013-02-17
> **Habitual said:**
> [What is a terminal?]("http://en.wikipedia.org/wiki/Terminal_emulator")
[What is the console?]("http://en.wikipedia.org/wiki/System_console")

i do not get how it was supposed to help linking what terminal and console is.
On the top of the black screen i am getting it clearly said tty1. unless that doesn't mean terminal?

---

### Post by Crossbow on 2013-02-17
I am having the exact same problem. startx gave me "no such file or directory." Writing this on my phone.

---

### Post by snowpine on 2013-02-17
Crossbow, try:

```
sudo apt-get update
sudo apt-get install ubuntu-desktop
```

It sounds like you may have accidentally deleted X, and the commands above will restore your Ubuntu to the default set of packages.

---

### Post by Crossbow on 2013-02-17
Thanks.

Now I've got:

errors were encountered while processing:
bnetdE: sub-process /usr/bin/dpkg returned an error code (1)

Should I reboot or do I have to fix this?

edit: rebooted. same problem.

unable to connext to x server: no such file or directory.

---

### Post by Crossbow on 2013-02-17
This worked for me: 
[http://ubuntuforums.org/showpost.php?p=12203831&postcount=18](http://ubuntuforums.org/showpost.php?p=12203831&postcount=18)

```

sudo apt-get update
sudo apt-get purge nvidia-*
sudo apt-get install nvidia-current
sudo apt-get purge nvidia-common
sudo apt-get install xserver-xorg-video-nouveau
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

```

Actually that last one returned the error that there was no such location but anyway my GUI is back. It's the old Nvidia so I still have to change it to 173, and I'm sort of scared to because that's how this all started, but it's the old one no longer has the right resolution.

---

### Post by Habitual on 2013-02-18
> **mdunks said:**
> i do not get how it was supposed to help linking what terminal and console is.
On the top of the black screen i am getting it clearly said tty1. unless that doesn't mean terminal?It won't help if you don't read it and understand what you've read.

Clearly, it did NOT say "tty1". 
> **mdunks said:**
> Hello, I have just recently downloaded Ubuntu;  and was using it without any problems for a cay, play games ect... Then i  decided to shut my computer down and restart because i just installed a  new game, and it boots into a black screen and asks me to log in  through there. I do not know what it exactly said but it was like 

Something something
something
Username:  Dunks
password:
Then i would log in and it just stays on the termainal.

Terminal is a PROGRAM.
console is well, console.

I merely wanted to point out the differences based on your usage of the word "terminal". > **mdunks said:**
> 
Then i would log in and it just stays on the terminal. 	is not an accurate statement.

Yes, it is used today "interchangeably" by newcomers and old-timers never correct the bad habit.
And yes, I know what you meant.

What I suspect is that I have spent more time replying than you did reading 2 wiki entries.

Have a Good Day.

---

### Post by oldos2er on 2013-02-18
Crossbow, next time instead of "hijacking" someone else's thread, please start your own.

---

