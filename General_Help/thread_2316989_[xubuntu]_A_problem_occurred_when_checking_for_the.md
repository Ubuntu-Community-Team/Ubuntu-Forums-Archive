---
title: "[xubuntu] A problem occurred when checking for the updates"
date: 2016-03-12
forum: General Help
---

### Post by vegetusformator on 2016-03-12
I am running Xubuntu 15.10.
I know this has been posted a million times, but my issue seems to be different. As normal, I get this an annoying red circle with a white bar through it.
The red circle gives a list of options which do nothing when clicked. (Showing, installing, and checking for updates).

I have searched it a billion times and when people have this problem it is usually because there really is a problem when updating, however

```
apt-get update
```

gives absolutely no errors or issues

```
apt-get upgrade
```

also gives no errors.

Essentially, there are no problems when checking for updates, yet this obnoxious red circle will not go away.

---

### Post by Bashing-om on 2016-03-12
vegetusformator; Hello;

Let's go a step deeper and see what the package manager thinks ,
Post back = Between Code Tags = the outputs of terminal commands:
```

sudo apt-get -f install
sudo dpkg -C

```

Be aware if 'dpkg' finds no fault, there will be only a return to prompt .

[INDENT][INDENT]if the package manager is not happy
[INDENT][INDENT][INDENT]nobody is happy
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by vegetusformator on 2016-03-12
```
 ray@gilberts:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
```

The 3 not upgraded are held back because I just did a dist-upgrade to see if that would change anything.

```
sudo dpkg -C
```

Returns to the prompt. No errors.

---

### Post by Bashing-om on 2016-03-12
vegetusformator; Ho KAy ;

" 3 not upgraded" and that after a 'dist-upgrade' indicates to me the presence of a PPA that is non-responsive.

Let's return to square one and show us:
```

sudo apt update
sudo apt upgrade
cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```

So we find the nature of the held back packages .

[INDENT][INDENT][INDENT]all in the process
[/INDENT][/INDENT][/INDENT]

---

### Post by vegetusformator on 2016-03-12
The 3 not upgraded were from intel for my graphics. I did a dist-upgrade again and they upgraded.
I ended up opening my task manager and removed the task *update-notifier* and the obnoxious circle disappeared. I'll see if it comes back, but for the sake of testing I went ahead and preformed those codes.
```

ray@gilberts:~$ sudo apt-get update
[sudo] password for ray: 
Ign http://dl.google.com stable InRelease
**removed a bunch to condense, no errors in any**       
Hit http://us.archive.ubuntu.com wily-proposed/universe Translation-en         
Fetched 1,397 kB in 6s (217 kB/s)                                              
Reading package lists... Done

```

```

ray@gilberts:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

```

ray@gilberts:~$ cat -n /etc/apt/sources.list
     1    # deb cdrom:[Xubuntu 15.10 _Wily Werewolf_ - Release amd64 (20151021)]/ wily main multiverse restricted universe
     2    
     3    # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     4    # newer versions of the distribution.
     5    deb http://us.archive.ubuntu.com/ubuntu/ wily main restricted
     6    deb-src http://us.archive.ubuntu.com/ubuntu/ wily main restricted
     7    
     8    ## Major bug fix updates produced after the final release of the
     9    ## distribution.
    10    deb http://us.archive.ubuntu.com/ubuntu/ wily-updates main restricted
    11    deb-src http://us.archive.ubuntu.com/ubuntu/ wily-updates main restricted
    12    
    13    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14    ## team. Also, please note that software in universe WILL NOT receive any
    15    ## review or updates from the Ubuntu security team.
    16    deb http://us.archive.ubuntu.com/ubuntu/ wily universe
    17    deb-src http://us.archive.ubuntu.com/ubuntu/ wily universe
    18    deb http://us.archive.ubuntu.com/ubuntu/ wily-updates universe
    19    deb-src http://us.archive.ubuntu.com/ubuntu/ wily-updates universe
    20    
    21    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22    ## team, and may not be under a free licence. Please satisfy yourself as to 
    23    ## your rights to use the software. Also, please note that software in 
    24    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    25    ## security team.
    26    deb http://us.archive.ubuntu.com/ubuntu/ wily multiverse
    27    deb-src http://us.archive.ubuntu.com/ubuntu/ wily multiverse
    28    deb http://us.archive.ubuntu.com/ubuntu/ wily-updates multiverse
    29    deb-src http://us.archive.ubuntu.com/ubuntu/ wily-updates multiverse
    30    
    31    ## N.B. software from this repository may not have been tested as
    32    ## extensively as that contained in the main release, although it includes
    33    ## newer versions of some applications which may provide useful features.
    34    ## Also, please note that software in backports WILL NOT receive any review
    35    ## or updates from the Ubuntu security team.
    36    deb http://us.archive.ubuntu.com/ubuntu/ wily-backports main restricted universe multiverse
    37    deb-src http://us.archive.ubuntu.com/ubuntu/ wily-backports main restricted universe multiverse
    38    
    39    deb http://security.ubuntu.com/ubuntu wily-security main restricted
    40    deb-src http://security.ubuntu.com/ubuntu wily-security main restricted
    41    deb http://security.ubuntu.com/ubuntu wily-security universe
    42    deb-src http://security.ubuntu.com/ubuntu wily-security universe
    43    deb http://security.ubuntu.com/ubuntu wily-security multiverse
    44    deb-src http://security.ubuntu.com/ubuntu wily-security multiverse
    45    
    46    ## Uncomment the following two lines to add software from Canonical's
    47    ## 'partner' repository.
    48    ## This software is not part of Ubuntu, but is offered by Canonical and the
    49    ## respective vendors as a service to Ubuntu users.
    50    deb http://archive.canonical.com/ubuntu wily partner
    51    # deb-src http://archive.canonical.com/ubuntu wily partner
    52    deb http://ppa.launchpad.net/bartbes/love-stable/ubuntu wily main
    53    # deb-src http://ppa.launchpad.net/bartbes/love-stable/ubuntu wily main
    54    deb http://us.archive.ubuntu.com/ubuntu/ wily-proposed multiverse main universe restricted

```

```

ray@gilberts:~$ tail -v -n +1 /etc/apt/sources.list.d/*
==> /etc/apt/sources.list.d/florian-rival-ubuntu-gdevelop-wily.list <==
deb http://ppa.launchpad.net/florian-rival/gdevelop/ubuntu wily main
# deb-src http://ppa.launchpad.net/florian-rival/gdevelop/ubuntu wily main

==> /etc/apt/sources.list.d/florian-rival-ubuntu-gdevelop-wily.list.save <==
deb http://ppa.launchpad.net/florian-rival/gdevelop/ubuntu wily main
# deb-src http://ppa.launchpad.net/florian-rival/gdevelop/ubuntu wily main

==> /etc/apt/sources.list.d/google-chrome.list <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main

==> /etc/apt/sources.list.d/google-chrome.list.save <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main

==> /etc/apt/sources.list.d/intellinuxgraphics.list <==
deb https://download.01.org/gfx/ubuntu/15.10/main wily main #Intel Graphics drivers

==> /etc/apt/sources.list.d/intellinuxgraphics.list.save <==
# deb https://download.01.org/gfx/ubuntu/15.10/main wily main #Intel Graphics drivers

==> /etc/apt/sources.list.d/steam.list <==
deb [arch=amd64,i386] http://repo.steampowered.com/steam/ precise steam
deb-src [arch=amd64,i386] http://repo.steampowered.com/steam/ precise steam

==> /etc/apt/sources.list.d/steam.list.save <==
deb [arch=amd64,i386] http://repo.steampowered.com/steam/ precise steam
deb-src [arch=amd64,i386] http://repo.steampowered.com/steam/ precise steam

==> /etc/apt/sources.list.d/wine-ubuntu-wine-builds-wily.list <==
deb http://ppa.launchpad.net/wine/wine-builds/ubuntu wily main
# deb-src http://ppa.launchpad.net/wine/wine-builds/ubuntu wily main

==> /etc/apt/sources.list.d/wine-ubuntu-wine-builds-wily.list.save <==
deb http://ppa.launchpad.net/wine/wine-builds/ubuntu wily main
# deb-src http://ppa.launchpad.net/wine/wine-builds/ubuntu wily main

```

If you don't see any errors, I guess I will mark this as solved. Like I said, I just had to kill the task in the task manager. If it comes back, I will try again.

---

### Post by Bashing-om on 2016-03-12
vegetusformator; welp;

The only fault I can point at :
> 
==> /etc/apt/sources.list.d/steam.list <==
deb [arch=amd64,i386] [http://repo.steampowered.com/steam/](http://repo.steampowered.com/steam/) [color=red]precise[/color] steam
deb-src [arch=amd64,i386] [http://repo.steampowered.com/steam/](http://repo.steampowered.com/steam/) [color=red]precise[/color] steam

Giving precise libraries in a wily install ... ouch ! As to what you can do about it - as this PPA only supports precise - I really do not know. No experience with steam.

and I would question the advisability of running with Intel's "testing"  graphic's driver. As it is now installed can be a real challenge to revert back in the event of a problem. In Intel's page(s) they do so warn of this .

[INDENT][INDENT]there is that path that seems right
[INDENT][INDENT][INDENT]and leads to a broken system
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by vegetusformator on 2016-03-15
Its been a few days, but I decided to close the notifier and open it back up using terminal. When I do, I get these errors:

```
ray@gilberts:~$ update-notifier

** (update-notifier:2084): WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-5TjCWr5ydQ: Connection refused
Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.

** (apport-gtk:2097): WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-5TjCWr5ydQ: Connection refused

```

When I go to */tmp/ *there is no file/folder named *dbus-5TjCWr5ydQ*

---

