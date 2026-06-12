---
title: "Issues with gedit"
date: 2017-05-08
forum: General Help
---

### Post by jgmtl80 on 2017-05-08
Hi, 
I recently installed Ubuntu on my laptop and it worked well the first day. I just re-opened the program and tried running gedit (which worked well previously) but I get the following errors: 

```
** (gedit:143): dconf-WARNING **: failed to commit changes to dconf: Failed to execute child process "dbus-launch" (No such file or directory)

** (gedit:143): dconf-WARNING **: failed to commit changes to dconf: Failed to execute child process "dbus-launch" (No such file or directory)

** (gedit:143): dconf-WARNING **: failed to commit changes to dconf: Failed to execute child process "dbus-launch" (No such file or directory)

** (gedit:143): WARNING **: Could not load theme icon user-bookmarks-symbolic: Icon 'user-bookmarks-symbolic' not present in theme

** (gedit:143): WARNING **: Could not load theme icon user-home-symbolic: Icon 'user-home-symbolic' not present in theme

** (gedit:143): WARNING **: Could not load theme icon drive-harddisk-symbolic: Icon 'drive-harddisk-symbolic' not present in theme
```

I've tried installing the fonts for Xming, which I did but this doesn't solve the problem.

I can run gedit even with the warnings, but I can't save anything.

Any ideas?
Thanks!

---

### Post by RobGoss on 2017-05-08
Have you tried uninstalling Gedit and installing a fresh installation it might be worth a try

To remove gedit run this command:
```
sudo apt-get remove gedit
```


To remove the gedit package and any other dependant package which are no longer needed

```
sudo apt-get remove --auto-remove gedit
```

You can install gedit by running the following command

```
sudo apt-get install gedit 
```

---

### Post by Impavidus on 2017-05-08
I see a lot of warnings, but no errors. Warnings are quite common with gedit and some other gnome applications. So, if it works, you can ignore those warnings. Developers should make sure they disappear one day.

---

### Post by vasa1 on 2017-05-08
OP wrote that "I can run gedit even with the warnings, but I can't save anything."

I suspect the dconf-WARNING indicates possible misuse of sudo.

What does the output of```
find . -user root -ls
``` show when *run from your home folder*? In my case, there weren't any results.

---

### Post by ishtar2 on 2018-01-29
Had a similar problem. Installing dbus helped getting rid of the dbus warning.
```
 sudo apt install dbus-x11
```

---

### Post by ruanchao on 2018-06-27
> **ishtar2 said:**
> Had a similar problem. Installing dbus helped getting rid of the dbus warning.
```
 sudo apt install dbus-x11
```
Thank you! It works.

---

### Post by nwhite53 on 2019-06-02
I wanted to add for anyone else that this fixed my issue with Nautilus not showing hidden files after a fresh install of Kubuntu 19.04 Disco. Nautilus threw this error in Konsole every time I clicked Show Hidden Files, or CTRL+H. The dbus-x11 package seems to not have installed for whatever reason from the installation media.

---

### Post by oldos2er on 2019-06-03
Old thread closed.

---

