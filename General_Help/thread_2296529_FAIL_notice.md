---
title: "FAIL notice"
date: 2015-09-26
forum: General Help
---

### Post by mayagrafix on 2015-09-26
Yesterday in the Top Menu Bar, an alert icon appeared as per Thumbnail #1.

After following instructions, I get the Other Software tab from the Software & Updates utility as per Thumbnail #2 were you can see that all repositories are disabled except for Canonical and Librecad. 

Is the Software&Update manager acting up because of the new version coming shortly?

---

### Post by Bucky Ball on 2015-09-26
It asked you to show updates. Please run these in a terminal and post any and all errors.

```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```

I suspect the librecad-dev repo might be the issue but we'll soon find out. Nothing enabled down the page and out of view? Incidentally, you don't need the Canonical Partners source code repo enabled. You don't need any source code repos enabled unless you are actively developing the software and need the source code. You can also kill the 'disabled on upgrade to ...' repos. They are no longer of any use. 

You are using 15.04?

(* Please use 'Adv Reply' or 'Go Advanced' and attach screenshot using the paperclip icon rather than inserting them in the body of your posts. Thanks.)

---

### Post by mayagrafix on 2015-09-27
Thanks for the advice to run apt-get. Seems that the only repository other than Canonical is at fault. 
> W: Failed to fetch [http://ppa.launchpad.net/librecad-dev/librecad-stable/ubuntu/dists/vivid/main/binary-amd64/Packages](http://ppa.launchpad.net/librecad-dev/librecad-stable/ubuntu/dists/vivid/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/librecad-dev/librecad-stable/ubuntu/dists/vivid/main/binary-i386/Packages](http://ppa.launchpad.net/librecad-dev/librecad-stable/ubuntu/dists/vivid/main/binary-i386/Packages)  404  Not Found


Will uncheck Librecad and source-code options from Software & Updates utility.

---

