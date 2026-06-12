---
title: "Please help with error message."
date: 2007-08-12
forum: General Help
---

### Post by brader on 2007-08-12
I tried installing updates and got the following message.  i also receive it when opening the synaptic package manager.  What is it and what do i do?  Any help will be greatly appreciated.


[B]Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:The package buddi needs to be reinstalled, but I can't find an archive for it.'[/B]

---

### Post by be4truth on 2007-08-13
Which Ubuntu version do you use? How do you update? Which program do you use?

---

### Post by brader on 2007-08-15
I use ubuntu 7.04.  Up date manage will not open.  Synaptic package manager will not open.  Sudo apt-get also gives me the error.  I'm not sure what else to do.  I simply want to run the updates, but I get this error message.

---

### Post by be4truth on 2007-08-15
Can you first try 

```
sudo apt-get check
```

After that pls post the content of the  /etc/apt/sources.list

```
 sudo gedit /etc/apt/sources.list
```

---

### Post by shad0w_walker on 2007-08-15
By the looks of the message something has happened to your update-manager package that requires it to be reinstalled but it can't find the package file to install it again.

Go to this link and select a server near you to download the update-manager package.

[http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Fmain%2Fu%2Fupdate-manager%2Fupdate-manager_0.59.20_all.deb&md5sum=6ca0e13ea48d6f095494369289a0abc4&arch=all&type=main]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Fmain%2Fu%2Fupdate-manager%2Fupdate-manager_0.59.20_all.deb&md5sum=6ca0e13ea48d6f095494369289a0abc4&arch=all&type=main")

When you have the package, open up a terminal (Applications > Accessories > Terminal) change to the directory you downloaded the package to and run this command:

```

sudo dpkg -i update-manager_0.59.20_all.deb

```

This should reinstall the update-manager package for feisty and hopefully set you right again.

---

### Post by brader on 2007-08-16
I use ubuntu 7.04. Up date manage will not open. Synaptic package manager will not open. Sudo apt-get also gives me the error. I'm not sure what else to do. I simply want to run the updates, but I get this error message.

Thanks for the suggestion.  Unable to get it to install.  I get this error:  
darb@Charlie-desktop:~$ sudo dpkg -i update-manager_0.59.20_all.deb
dpkg: error processing update-manager_0.59.20_all.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 update-manager_0.59.20_all.deb

---

### Post by brader on 2007-08-16
First of all thanks for your help and suggestions.  This is really confusing to me.  I had a good install and have been using 7.04 for several months without problems.  Now I have a unique opportunity to learn more about Ubuntu beta distro.  

  Results of sudo apt-get check:

darb@Charlie-desktop:~$ sudo apt-get check
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package buddi needs to be reinstalled, but I can't find an archive for it.
darb@Charlie-desktop:~$  sudo gedit /etc/apt/sources.list
ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card 'Headset'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3968:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card 'Headset'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3968:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card 'Headset'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3968:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card 'Headset'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3968:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default

darb@Charlie-desktop:~$ 
darb@Charlie-desktop:~$

---

