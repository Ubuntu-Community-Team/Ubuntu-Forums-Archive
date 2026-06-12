---
title: "Terminal"
date: 2016-11-05
forum: General Help
---

### Post by plumb on 2016-11-05
Thanks for the reply, have loaded mediatomb. But when I run the terminal it gives me this fault when I type in this steve@steve-DIXONSXP:~$ sudo nano /etc/mediatomb/config.xml)(sudo: unable to resolve host steve-DIXONSXP
[sudo] password for steve: 
Sorry, try again.
[sudo] password for steve: 
Sorry, try again.
[sudo] password for steve: )


sudo: 3 incorrect password attempts
steve@steve-DIXONSXP:~$
Sorry to be so thick but is there a guide on how to use terminal.
Regards Plumb

EDIT:
Post moved from [https://ubuntuforums.org/showthread.php?t=2342349&p=13566305#post13566305](https://ubuntuforums.org/showthread.php?t=2342349&p=13566305#post13566305)

---

### Post by plumb on 2016-11-05
Hi can somebody tell me how to get past this error when I try to put in a command in terminal program. I am the only user of my pc. I need somebody to tell me in none tech terms how to get past the problem, as I can't network my pc to tv. This is what I get and then have to come out of the terminal as I can't type into it after the error (steve@steve-DIXONSXP:~$ sudo apt-get updatesudo: unable to resolve host steve-DIXONSXP
[sudo] password for steve: )

Please some body help it is driving me crackers, I have been trying for weeks now.
Regards Plumb

---

### Post by oldos2er on 2016-11-05
When you enter your password for a sudo command, it's normal that nothing is echoed to the screen. Just type it in and press Enter.

---

### Post by plumb on 2016-11-05
> **oldos2er said:**
> When you enter your password for a sudo command, it's normal that nothing is echoed to the screen. Just type it in and press Enter.

sorry for being so thick, but when I start a terminal I get this 
steve@steve-DIXONSXP:~$ How do I proceed from here to enter a sudo command without me getting the password error

---

### Post by oldrocker99 on 2016-11-05
The steve@steve-DIXONSXP"~$ is the command prompt. From it you type```
sudo {name of command}
```

You'll be asked for your password, which does NOT show as you type. If you made an error while typing the password, hold down the BACKSPACE key and try again.

---

### Post by oldos2er on 2016-11-05
What password error? I don't see any in post #2, but it looks as though *sudo apt-get update* failed because it couldn't find an internet connection (the "unable to resolve host"). Or there could be an error in your /etc/hosts file. Could we see it? ```
 cat /etc/hosts
```

---

### Post by plumb on 2016-11-05
> **oldrocker99 said:**
> The steve@steve-DIXONSXP"~$ is the command prompt. From it you type```
sudo {name of command}
```

You'll be asked for your password, which does NOT show as you type. If you made an error while typing the password, hold down the BACKSPACE key and try again.

Well done your the man now I have got it. This is probably the wrong section but I have now got up this.
steve@steve-DIXONSXP:~$ cat /etc/hosts
127.0.0.1 localhost
127.0.1.1 steve-DIXONSXP.talktalk


# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
192.168.1.3 tv kitchen
Can you help how I get my smart panasonic to link with my pc. It runs with DLNA
If you can point me in the right direction that would be great.
My very best regards Plumb

---

### Post by oldos2er on 2016-11-05
> Can you help how I get my smart panasonic to link with my pc.

Please start a new thread for that. Since this one appears to be solved, use Thread Tools at the top of the page to mark it so. Thanks!

---

