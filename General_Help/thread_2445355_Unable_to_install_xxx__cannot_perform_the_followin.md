---
title: "Unable to install xxx  cannot perform the following tasks"
date: 2020-06-12
forum: General Help
---

### Post by ironmanx5600 on 2020-06-12
Ubuntu 18.04.4 LTS   This happened after yesterdays update.

No matter what software I try to install either from the command line or GUI I keep getting the same error.

~$ sudo snap install openresizer
error: cannot perform the following tasks:
- Download snap "openresizer" (2) from channel "stable" (unexpected EOF)


I tried  sudo apt update   and it ended like this>>

Reading package lists... Done                                                                     
E: The repository 'http://ppa.launchpad.net/hsoft/ppa/ubuntu bionic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

Any Ideas??   
Thx!

---

### Post by CelticWarrior on 2020-06-12
Welcome.

Ubuntu 14.04 is out of support for mire than a year. It no longer has online repositories from where to download and install software and also security updates which is a much greater problem.

Please upgrade to a supported release.

---

### Post by deadflowr on 2020-06-12
Mismatched information.
You state it's 14.04.4, which is really old,
(14.04.4 came out around 4 years ago and was immediately replaced with 14.04.5 six months later)
yet the apt ppa error is for 18.04.

Remove the hsoft ppa and retry apt again.

Not sure about the snap error, you'd probably need to try contacting the publisher for that.
But that might also get fixed with fixing apt and applying any updates, since the snapd package is an apt package and gets periodic fixes through apt.

---

### Post by ironmanx5600 on 2020-06-12
Forgive my dyslexia!

I am at Ubuntu 18.04.4 LTS

---

### Post by CelticWarrior on 2020-06-12
OK, Ubuntu 18.04 is supported.

The PPA mentioned in the error message has no contents for 18.04. Remove it.

---

### Post by ironmanx5600 on 2020-06-12
Thank you for your patience. I know I need to purge the ppa, but here is where I am confused:
E: The repository 'http://ppa.launchpad.net/hsoft/ppa/ubuntu bionic Release' does not have a Release file.

What is the PPA name?  bionic?  (Isn't that the code name for this release?

sudo ppa-purge ppa:???

---

### Post by CelticWarrior on 2020-06-12
There are two ways to add/remove PPAs. For your specific case:
[LIST=1]
[*]Via GUI: Open Software & Updates, Other software tab. Find it, select it and remove. 
[*]```
sudo add-apt-repository --remove ppa:hsoft/ppa
``` 
[/LIST]

This [quick tip]("https://itsfoss.com/how-to-remove-or-delete-ppas-quick-tip/") has pictures for #1.

---

### Post by ironmanx5600 on 2020-06-15
Thank you  I tried the command "
sudo add-apt-repository --remove ppa:hsoft/ppa

but when I tried to install software I still had the error message

---

### Post by CelticWarrior on 2020-06-16
Doing 'sudo apt update' are there still errors?

---

### Post by ActionParsnip on 2020-06-16
openresizer looks like a GUI for imagemagick

What is the output of:

```

sudo grep -r hsoft /etc/apt/*

```

Thanks

---

