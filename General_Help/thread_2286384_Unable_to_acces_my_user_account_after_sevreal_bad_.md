---
title: "Unable to acces my user account after sevreal bad manipulation"
date: 2015-07-11
forum: General Help
---

### Post by dsx2 on 2015-07-11
Hi all,

Well all started when i tried yesterday to download virtual box on my ubuntu14.04 

So i went to the website downloaded the version for ubuntu and got a .deb i clicked into it then got redirected to the software center when it started to download.
When the installation was about to end the software center icon bugged an interrogation mark was shown instead of the original icon.
The virtual box was installed then software center disappeared completely i restarted the computer then my panel was missing and only the document was shown in the desktop.
Even the (ctrl alt t )doesn't work so i opened the tty (ctrl alt f1) then decided to uninstall the virtual box with a sudo apt-get autoremove vritualbox, nothing except that the shell returned me that 0 to install 0 to upgrade and 2x to remove i clicked yes thinking that will remove the last software i installed.
The command ended then i quit the tty.

So now im not even able to start my cession i enter the wright password on several user account but it doesn't open it it return me to the same page to enter to pass again, well im left with the safe mode to try to repair everything but i m kind of afraid messing again :(and im looking for your help 
Any idea how this can be fixed ???

---

### Post by Bucky Ball on 2015-07-11
I haven't got a lot to offer, but I can bump your thread and give you a tip for future reference: virtualbox is in the official Canonical repositories. You can install it directly from Software Centre, unless you have a specific reason not to. Best to look there first for any open-source app prior to getting it from elsewhere. 

What do you get when you boot to the recovery kernel, drop to a shell when you get to that option, and:

```

sudo apt-get remove --purge virtualbox
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```

Can you get through that error free? Report any and all errors.

---

### Post by dsx2 on 2015-07-11
i went to root prompt in safe mode titled 
 (recovrey menu) file system state read only 
i got this message after the command apt-get remove --purge virtualbox

W:not using locking for read only lock file /var/lib/dpkg/lock
E:unable to write to /var/cache/apt
E:the package list or status could not be parsed or opened

---

### Post by Bucky Ball on 2015-07-11
Hold on, safe mode? Then went to recovery mode? I'm not following. You boot the computer and get a list of kernels to boot from, yes? Second on the list should be the Ubuntu recovery kernel. Choose that. When at the options, drop to shell and run those commands. 

Are you talking about safe graphics mode when you say 'safe' mode?

You might be missing this:

```
mount --all
```

Issue that before you run those commands in the root shell.

```
mount --all
sudo apt-get remove --purge virtualbox
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

You won't need the sudo at the beginning.

---

### Post by dsx2 on 2015-07-11
i not sure wich mode im on 

Actually from the grub menu (Gnu Grub verion 2.02...)
  ubuntu
  advanced option for ubuntu 
  memory test (memory test 86)
  memory test (memory test 86+serial...

 Once i get to advanced option for ubuntu i end up with this :

 ubuntu with linux3.16.0-34 generic 
 ubuntu with linux3.16.0-34 generic (recovery mode)
 ubuntu with linux 3.16.0-30
 ubuntu with linux 3.16.0-30 ( recovery mode)

then i choose 3.16.0-34 [recovery mode] (file system state :read only)

  resume
  clean:                              try to make free space
  dpkg :repair broken package
  failsafex:                         run in a fail safe graphic mode 
  fsck                                  :check all file system 
  grub                                   :update grub boot loader 
  network              :enable networking 
  root :                                   drop to root shell prompt 
  system summary  :system summary

---

### Post by Bucky Ball on 2015-07-11
root : drop to root shell prompt 

Then:

```
mount --all
sudo apt-get remove --purge virtualbox
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

---

### Post by dsx2 on 2015-07-11
same error msg even after the mount --all
W:not using locking 

i wonder if the previous autoremove deleted something that is needed to acces the user account 
When i do    find virtualbox i get location where it is but as the message saysunable to write it ??!!

---

### Post by dsx2 on 2015-07-11
is there a way to reinstall the /boot since i installed ubuntu  manually and y slash /home in a different partition if really there is no way to remove the corrupted virtualbox :? and also because of the previous autremove i runned who remove many thing :|

---

### Post by dsx2 on 2015-07-11
bump!

---

### Post by Bucky Ball on 2015-07-11
Do not bump your threads once and hour. Wait at least 12. Thanks.

---

