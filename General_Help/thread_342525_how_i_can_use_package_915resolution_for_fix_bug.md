---
title: "how i can use package 915resolution for fix bug"
date: 2007-01-20
forum: General Help
---

### Post by ryon on 2007-01-20
i use Dell inspiron 640m i can't boot to Ubuntu.the website say i must use package 915resolution but i don't know how to use that.help me :frown: 
thanks a lot

---

### Post by bodhi.zazen on 2007-01-20
See this link:

[https://help.ubuntu.com/community/i915Driver](https://help.ubuntu.com/community/i915Driver)

To install the driver, enable your repositories:

[http://ubuntuguide.org/wiki/Dapper#Repositories](http://ubuntuguide.org/wiki/Dapper#Repositories)

Then :```
sudo aptitude update
sudo aptitude upgrade
sudo aptitude install 915Resolution
```

You can also look here: [http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)

But the site is down at the moment :(

---

### Post by bodhi.zazen on 2007-01-20
It's up now:

[http://ubuntuguide.org/wiki/Dapper#How_to_install_Graphics_Driver_.28Intel.29](http://ubuntuguide.org/wiki/Dapper#How_to_install_Graphics_Driver_.28Intel.29)

---

### Post by ryon on 2007-01-20
Thanks but i can't start X-server. How i can install that ? i'm a begin to use linux and ubuntu is a first linux i use.sorry because my English is limited.

---

### Post by bodhi.zazen on 2007-01-20
Did you install (and configure) 915Resolution ?

If so, you need to reboot ;)

If you are having problems after rebooting, you start X from a terminal with:

startx

Post any error messages. You will get a gray screen with a black "X" To exit Ctrl-Alt-Backspace.

To start your gui, in a terminal:

sudo gdm

OR

gnome-session

---

### Post by ryon on 2007-01-20
My problem is 
[IMG]http://i107.photobucket.com/albums/m290/ryon_handsome/16012007512.jpg[/IMG]
then
[IMG]http://i107.photobucket.com/albums/m290/ryon_handsome/16012007513.jpg[/IMG]
then
[IMG]http://i107.photobucket.com/albums/m290/ryon_handsome/16012007514.jpg[/IMG]
and
[IMG]http://i107.photobucket.com/albums/m290/ryon_handsome/16012007515.jpg[/IMG]

i trial to install 915resolution by 
> sudo apt-get install 915resolution 
but it can't find package  915resolution.
i download package 915resolution in my windowns hard disk.how ubuntu can't find that.so i can't start X-server because that i can't install ubuntu to my hdd. Can you help me?
thanks a lot

---

### Post by bodhi.zazen on 2007-01-20
First lets see if we can fix your gui, then 915 resolution ;)

Go to the command line, tty2:

Ctrl-Alt-F2

Login

Enter:```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Select a resolution by moving up and down with the arrow keys, use the space bar to select ;)

You will get a message "warning ...." , ignore it ;)

Now lets see of we can start X:

Enter this command:```
sudo /etc/init.d/gdm restart
```

You man need to hit Ctrl-Alt-F7 to return to the gui.

If that works at the resolution you need you may not need 915resolution at all [-o<

=============================

915Resolution is not too bad. 

We need to enable some repositories.

Open a terminal (if your gui is working)

Enter:```
sudo nano -B /etc/apt/sources.list
```

Remove the # from the lines that continue with a deb

> deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

Your file will be different because I am running feisty, don't worry about that.

For more detailed directions see here:

[http://ubuntuguide.org/wiki/Dapper#Repositories](http://ubuntuguide.org/wiki/Dapper#Repositories)

Now:```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install 915resolution
```

Be sure to configure 915resolution (see this link 

[http://ubuntuguide.org/wiki/Dapper#H...er_.28Intel.29](http://ubuntuguide.org/wiki/Dapper#H...er_.28Intel.29) ).

---

