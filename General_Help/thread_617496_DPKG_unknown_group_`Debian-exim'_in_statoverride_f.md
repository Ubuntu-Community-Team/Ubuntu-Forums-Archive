---
title: "DPKG unknown group `Debian-exim' in statoverride file"
date: 2007-11-19
forum: General Help
---

### Post by clear_sky on 2007-11-19
When trying to install a new package i get the following error:

Need to get 0B/5349kB of archives. After unpacking 22.3MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
dpkg: syntax error: unknown group `Debian-exim' in statoverride file 
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initialising package states... Done
Building tag database... Done      

Any idea on how to fix the syntax error?

---

### Post by NateHott on 2007-12-28
I ran into a similar problem on my server. I installed webmin and deleted a user "postgrey" from there. I thought that I had already uninstalled postgrey, but I guess not. My error was "dpkg: syntax error: unknown user `postgrey' in statoverride file". Here's what I did:
sudo apt-get update
sudo /etc/init.d/webmin stop
sudo vi /var/lib/dpkg/statoverride (I deleted the line with postgrey)
sudo apt-get -f install
sudo apt-get install postgrey (I wanted to make sure everything was installed correctly before uninstalling this time)
sudo apt-get purge postgrey
sudo apt-get update
sudo /etc/init.d/webmin start

That's it. I'm a new user to Linux so there's most likely a better way to do it, but it worked for me.

---

### Post by saeid on 2008-01-22
Thanks NateHott :lolflag:
It's work for me :)

---

### Post by MianoSM on 2008-06-18
This also helped me out. What exactly is the /var/lib/dpkg/statoverride file used for that aptitude gets hung up on?

---

### Post by tr333 on 2008-07-07
You can fix this by running the following command in a terminal:

```
dpkg-statoverride --remove /etc/exim4/passwd.client
```

This will update /var/lib/dpkg/statoverride

---

