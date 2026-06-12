---
title: "Ubuntu unix 14.04.02 crashes while playing minecraft"
date: 2015-04-20
forum: General Help
---

### Post by sebastiaan5 on 2015-04-20
So I have a problem while I play minecraft, my screen goes black, I hear a plop and my computer powers off.
When I reboot ubuntu doesn't give error logs.

I use nvidia geforce GTX 860m and nvidia X server Settings package.

I use ubuntu for 2 weeks now and never had a problem like this.

---

### Post by sebastiaan5 on 2015-04-20
I think it's java, because some other games won't work anymore. what can I do to help this?

greetings.

---

### Post by Bucky Ball on 2015-04-20
Is it only when playing games this happens and usually when it's fast and furious (lots of PC resources being used)?

---

### Post by sebastiaan5 on 2015-04-20
only when playing this games, it happened suddenly. I have minecraft for almost 1 week and never had a problem with it 250fps+ playing very smoothly and today it continues crashing my PC.

how can I see the last packages I have installed?

greetings

---

### Post by ajgreeny on 2015-04-20
These two commands run one at a time, will show you which packages have been installed and updated recently with the date it occurred.
```
grep -iw install /var/log/dpkg.log.1 /var/log/dpkg.log
grep -iw upgrade /var/log/dpkg.log.1 /var/log/dpkg.log
```
My suspicion would be either a new kernel or new graphic driver so look for those in the lists.
It is also probably worth booting to a previous kernel from the grub menu to see if that gets rid of the problem.

---

### Post by sebastiaan5 on 2015-04-20
will try to boot a previous kernel,

btw I got a a lot packages half-installed, can I delete them completely?

```
/var/log/dpkg.log:2015-04-20 12:30:54 status half-installed kde-runtime:amd64 4:4.13.3-0ubuntu0.2
/var/log/dpkg.log:2015-04-20 12:30:54 status half-installed kde-runtime:amd64 4:4.13.3-0ubuntu0.2
/var/log/dpkg.log:2015-04-20 12:30:54 status half-installed kde-runtime:amd64 4:4.13.3-0ubuntu0.2
/var/log/dpkg.log:2015-04-20 12:30:54 status installed oxygen-icon-theme:all 4:4.13.0-0ubuntu1
/var/log/dpkg.log:2015-04-20 12:30:55 status half-installed oxygen-icon-theme:all 4:4.13.0-0ubuntu1
/var/log/dpkg.log:2015-04-20 12:30:55 status half-installed oxygen-icon-theme:all 4:4.13.0-0ubuntu1
```


greetz

---

### Post by Bucky Ball on 2015-04-20
> **sebastiaan5 said:**
> will try to boot a previous kernel,

btw I got a a lot packages half-installed, can I delete them completely?

/var/log/dpkg.log:2015-04-20 12:30:54 status half-installed kde-runtime:amd64 4:4.13.3-0ubuntu0.2
/var/log/dpkg.log:2015-04-20 12:30:54 status half-installed kde-runtime:amd64 4:4.13.3-0ubuntu0.2
/var/log/dpkg.log:2015-04-20 12:30:54 status half-installed kde-runtime:amd64 4:4.13.3-0ubuntu0.2
/var/log/dpkg.log:2015-04-20 12:30:54 status installed oxygen-icon-theme:all 4:4.13.0-0ubuntu1
/var/log/dpkg.log:2015-04-20 12:30:55 status half-installed oxygen-icon-theme:all 4:4.13.0-0ubuntu1
/var/log/dpkg.log:2015-04-20 12:30:55 status half-installed oxygen-icon-theme:all 4:4.13.0-0ubuntu1


greetz

Best to:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get autoremove
```

Report any and all errrors.

* Please use [CODE] tags for terminal output. See the last link in my signature for how. ;)

---

### Post by sebastiaan5 on 2015-04-20
So I did the command ```
sudo apt-get autoremove
```. But what does this command really do? It deleted 300files it feels like I did damage to my computer.

And I got no errors from all the commands.

I will remember to use CODE tags from now on thank you :)

greetings

---

### Post by sebastiaan5 on 2015-04-20
So after reboot and some usual programming in netbeans and surfing the net I tried the autoremove again to check

```
sudo apt-get autoremove
```

and these files he wants to remove again:

```
  linux-headers-3.16.0-33 linux-headers-3.16.0-33-generic
  linux-image-3.16.0-33-generic linux-image-extra-3.16.0-33-generic
  linux-signed-image-3.16.0-33-generic


```

is this normal?

---

### Post by Bucky Ball on 2015-04-21
> **sebastiaan5 said:**
> 
is this normal?

Yes. Type:

```
uname -a
```

... in a terminal and check the kernel you are using currently. It won't be the .33. That is probably redundant.

---

### Post by sebastiaan5 on 2015-04-21
I have 3.16.0-34-generic :)

---

