---
title: "no gdm password box on login"
date: 2014-08-04
forum: General Help
---

### Post by ishottya on 2014-08-04
When booting up I get to where I should be able to login and no password box shows up underneath the username.
[ATTACH=CONFIG]255243[/ATTACH]
I am currently running Ubuntu 12.04.4
I have done a little searching and have found this.
[http://ubuntuforums.org/showthread.php?t=1529189](http://ubuntuforums.org/showthread.php?t=1529189)
every time i sudo serice gdm stop it freezes at

* Stopping System V runlevel compatibility 

I still get the blinking line but nothing else, i cannot type or do anything.
If i then hit the power button command lines show the system shutting down and the machine turns off just fine. 
When i boot up again everything is the same as when i booted up previously.
I tried to run sudo apt-get upgrade and get

Reading package lists...done
Building dependancy tree
Reading state information...done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
  linux-image-generic-lts-raring : Depends : Linux-image-3.8.0-44-generic but it is not installed
E: Unmet dependencies. Try using -f.

Any help would be appreciated.

---

### Post by Bucky Ball on 2014-08-04
Dumb question, but what happens when you click the username? Anything? Does it off one for the guest account? What happens when you hit return?

BTW, [post #6]("http://ubuntuforums.org/showthread.php?t=1529189&p=10403519&viewfull=1#post10403519") was the fix. When at the login screen, ctl+alt+F1 and:

```
sudo apt-get update
sudo apt-get upgrade
sudo reboot -h now
```

Does your password work there? Any different after these commands and reboot?

---

### Post by ishottya on 2014-08-04
When I click the username it show the current ubuntu version. There is only one account on the pc as far as I know.

> [COLOR=#000000]I tried to run sudo apt-get upgrade and get[/COLOR]

[COLOR=#000000]Reading package lists...done[/COLOR]
[COLOR=#000000]Building dependancy tree[/COLOR]
[COLOR=#000000]Reading state information...done[/COLOR]
[COLOR=#000000]You might want to run 'apt-get -f install' to correct these.[/COLOR]
[COLOR=#000000]The following packages have unmet dependencies:[/COLOR]
[COLOR=#000000]linux-image-generic-lts-raring : Depends : Linux-image-3.8.0-44-generic but it is not installed[/COLOR]
[COLOR=#000000]E: Unmet dependencies. Try using -f.[/COLOR]


---

### Post by Bucky Ball on 2014-08-04
Did you run 'sudo apt-get install update' first? Always do that first. ;)

There seems to be a mix up here as it is saying linux-image-generic-lts-raring has unmet dependencies. That is 13.04 and that release is no longer supported. Is this a recent install of 12.04 and you had 13.04 installed previously? Have you manually installed the 13.04 kernel Linux-image-3.8.0-44-generic?

---

### Post by ishottya on 2014-08-04
12.04 was installed about a year ago. I did run update first. same conclusion.

---

### Post by Bucky Ball on 2014-08-04
> **Bucky Ball said:**
>  Have you manually installed the 13.04 kernel Linux-image-3.8.0-44-generic?

?

Have you recently installed a package or software that might have caused the error? I'm rethinking this because 'linux-image-generic-**lts**-raring' mentions 'lts', but 13.04 wasn't an LTS release. :-k So perhaps this is normal. Perhaps check your Software Sources and see if you have a 13.04 repo in there anywhere. Untick that if so and try again.

---

### Post by ishottya on 2014-08-04
not that i am aware of. I had previously had windows pc's and our last one crashed and my friend gave me this one. He installed everything on it and I have not installed anything since. it worked fine untill a week and a half ago. I post about it now because i was on vacation.

---

### Post by ishottya on 2014-08-04
ok so i looked around a bit and tried a few different things but i think <sudo apt-get install linux-image-3.8.0-44-generic> solved them problem because i am now able to log in. Thank you for the help and I will post back if any the problem persists.[COLOR=#000000]
[/COLOR]

---

### Post by Bucky Ball on 2014-08-06
Good news that you got things going. If you have any further issues, please post a new thread and mark this one as 'solved' to help others, as it is by the sounds. ;)

Good luck.

---

