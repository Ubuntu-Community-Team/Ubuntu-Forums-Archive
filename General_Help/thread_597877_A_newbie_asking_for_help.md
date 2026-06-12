---
title: "A newbie asking for help"
date: 2007-10-30
forum: General Help
---

### Post by ~D~ on 2007-10-30
Hi there.

I am new to these forums and utterly new to linux and am having a few problems.

I have just installed Kubuntu 7.10 preferring the KDE interface over GNOME but a few things have gone awry. 

Firstly, it seems that all my files and directories are owned by 'root' and not my username, this includes my 'Home' folder (but not the files inside) and my  'Storage Media' drive where I want to keep all my files to share between Windows and Kubuntu, therefore I cannot modify any files or folders outside of Home as it seems Kubuntu does not allow logging in as root.

I have a friend and he told me to change the UID to 1000 for the drive in question (sda2) so i typed 'sudo kate /etc/fstab to bring up the file, and while the file opened as normal, there were the following errors in the terminal (as a side note, changing the fstab file did not work):

Error: "/var/tmp/kdecache-USERNAME" is owned by uid 1000 instead of uid 0
Error: "/tmp/kde-USERNAME" is owned by uid 1000 instead of uid 0
Error: "/tmp/ksocket-USERNAME" is owned by uid 1000 instead of uid 0

Another problem is that my internet connection seems to disconnect after a certain amount of time. I cannot tell you the length of this time, but when I glance at the taskbar sometimes, I notice that it is disconnected. 

This is a completely new and clean install of Linux and I have not made any modifications to anything. I hope you can help and thank you in advance for your time.

Edit: Sorry, just to add, during installation, there was a, error message regarding security.ubuntu, something relating to the fact that it was not accessible and that something was commented out in file, which i should check after the installation. Sorry for not being more specific but I have forgotten what it said.

---

### Post by LaRoza on 2007-10-30
> **~D~ said:**
> Hi there.

I am new to these forums and utterly new to linux and am having a few problems.

I have just installed Kubuntu 7.10 preferring the KDE interface over GNOME but a few things have gone awry. 

Firstly, it seems that all my files and directories are owned by 'root' and not my username, this includes my 'Home' folder (but not the files inside) and my  'Storage Media' drive where I want to keep all my files to share between Windows and Kubuntu, therefore I cannot modify any files or folders outside of Home as it seems Kubuntu does not allow logging in as root.



Another problem is that my internet connection seems to disconnect after a certain amount of time. I cannot tell you the length of this time, but when I glance at the taskbar sometimes, I notice that it is disconnected. 



Yes, files that are not yours personally belong to root. This is a good thing. You can easily alter root's files (all but your own), if you explicitly state so. In the command line, using "sudo" before a command will prompt you for your password (which you can not see as you type, just type and press enter).

For gui apps, type "gksudo", or the similar K command for running a GUI as root.

```

adduser LaRoza

```

This will not work, because you don't have permission.

```

sudo assuser LaRoza

```

This will work, after you give the correct password.

You can change ownership, or rather, root can. Do not do this, except in a few circumstances. (the command for this is "chown", which must be run as root.)

---

