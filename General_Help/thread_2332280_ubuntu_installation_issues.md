---
title: "ubuntu installation issues"
date: 2016-07-30
forum: General Help
---

### Post by sriharryster on 2016-07-30
hi there,

i have installed ubuntu 16.0.4 on lenova 3gb RAM dual core 64 bit 250gb hdd computer....

facing lot of issues with installing ubuntu sw, third-party sw and plugins....

tried through terminal with all sorts of commands from forums and google....

nothing seems to work.... also have an update in ubuntu store that is also not working...

internet connection is pretty good , have dowloaded couple of movies in no time...

but installtion sucks.... have a - symbol in red at top right of desktop it says pre-dependency problem...


can you help me?

Many thanks..
srihari

---

### Post by nikefalcon on 2016-07-30
Hi Srihari, welcome to the Ubuntu community!
Could you provide the output of the following commands: 
```
lsb_release -a
```
and
```
uname -a
```
This will tell us which version of Ubuntu and the kernel you are using, just in case it is required.

> **sriharryster said:**
> hi there,
facing lot of issues with installing ubuntu sw, third-party sw and plugins....

tried through terminal with all sorts of commands from forums and google....

Please paste in the commands that you used and their corresponding output so we can take a look at the errors. Use code tags for proper formatting.
This shouldn't take very long to resolve IMO.

Example of command and output:
```

ak@infineos:~$ uname -a
Linux infineos 4.4.1-xanmod5 #1 SMP Wed Feb 17 11:45:31 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

```

---

### Post by grahammechanical on 2016-07-30
Please post the output from these commands.

```
sudo apt update
sudo apt upgrade
```

At the moment we do not know what you wanted to do or what you actually did or what the present problem is. We do not even know what software & plugins you tried to install.

Regards

---

