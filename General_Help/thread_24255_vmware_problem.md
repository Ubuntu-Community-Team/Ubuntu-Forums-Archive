---
title: "vmware problem"
date: 2005-04-06
forum: General Help
---

### Post by A-star on 2005-04-06
I have installed vmware 4.5.2 in hoary but whenever I start it I always get this message
```

VMware Workstation is installed, but it has not been (correctly) configured for your
running kernel.  To (re-)configure it, your system administrator must find and run
"vmware-config.pl".  For more information, please read the VMware Workstation
documentation.

```
After this it works fine, the problem is that I have to repeat this step every time I reboot.

Anyone got an idea how to solve this?

Kind regards
A-star

---

### Post by lao_V on 2005-04-06
Have you tried doing what it says? I.e., cd to the directory where vmware-config.pl is and running sudo ./vmware-config.pl??

---

### Post by A-star on 2005-04-06
Yes I did,
but when I reboot I have to do it again and this shouldn't be happening.

---

### Post by lao_V on 2005-04-06
Is there anything in the VMWare doc about this?

---

### Post by A-star on 2005-04-06
it only says that you have to run it to make certain kernel modules.
but that's it.

---

### Post by lao_V on 2005-04-06
When you run vmware-config.pl does it give you any errors?

---

### Post by A-star on 2005-04-06
When I run it the very first time (just after I installed it) it doesn't give me any errors.
Whe I run it the second time (or more), it displays some messages that it has some things already configured and installed.

I can give you a list of the messages but I can only do that this evening (no access to my pc at home now).

---

### Post by lao_V on 2005-04-06
See if you can post the message(s). If it says you need to make certain kernel modules then normally you would need the kernel headers. Do you have those installed? (/usr/src/linux-`arch`)

---

### Post by A-star on 2005-04-06
They are installed, 
like I said vmware works but after each reboot of my computer (once a day), I have to run vmware-config.pl again and this is unacceptable.

I'll give you the messages this evening and will also try to make a default installation of ubuntu and see if that works (can't guarantee this, because I have a limit amount of time availabe in the evenings.)

---

### Post by lao_V on 2005-04-06
There's another person who's having the same problem. It could well be something to do with Hoary

---

### Post by A-star on 2005-04-06
do you have a link to the thread?

---

### Post by lao_V on 2005-04-06
Not much in that thread apart from a link to this one :-) [here ]("http://www.ubuntuforums.org/showthread.php?t=24258")it is

---

### Post by A-star on 2005-04-06
hehe :)
that's me also :)

kind regards
A-star

---

### Post by lao_V on 2005-04-06
[QUOTE=A-star]hehe :)
that's me also :)

kind regards
A-star[/QUOTE]

Are you planning to take over the forum?? :-)

---

### Post by A-star on 2005-04-06
[QUOTE=lao_V]Are you planning to take over the forum?? :-)[/QUOTE]
 not really (although I plan to take over the world :) )
the mailing list and the forum are both good ways to get help.
And some people do not read the forums.

---

### Post by lao_V on 2005-04-06
[QUOTE=A-star]not really (although I plan to take over the world :) )
the mailing list and the forum are both good ways to get help.
And some people do not read the forums.[/QUOTE]

People like me live and sleep in this forum! :-)

---

### Post by A-star on 2005-04-06
Just a little update,

Installed a clean version of ubuntu and immediatly installed vmware on it.
Same problem.

So I don't know where the problem comes from.

Will post the output of the command "vmware-config.pl" this evening.

---

### Post by StacyWebb on 2005-04-06
This problem is not specific to Ubuntu, but rather to the newer kernels. I had the same thing happen in Fedora 3. The only that I found to solve is after running the vmware-config.pl then remove the config file. Disclaimer I haven't tried this in Ubuntu yet.

---

