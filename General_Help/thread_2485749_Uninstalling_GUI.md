---
title: "Uninstalling GUI"
date: 2023-04-08
forum: General Help
---

### Post by johndid on 2023-04-08
hi,
I've just found out that my headless Ubuntu server 20.04 LTS got a GUI, kind of.

It must be GNOME. I don't remember what I exactly did. Maybe it is becasue I ran these commands:

```
sudo apt install deb libnotify-bin
sudo apt install libnotify-bin0 upgraded, 387 newly installed, 0 to remove and 19 not upgraded.
sudo apt install deb libnotify-bin sudo apt install deb libnotify-bin
```

It is not a big deal, but I'd like to know if I can uninstall it without damaging my server somehow.
Could you help me please?
Thanks

---

### Post by MAFoElffen on 2023-04-08
Yes. If you look in your apt logs... Specifically /var/log/apt/term.log. I would first do
```

grep -n -m 1 'xorg' /var/log/apt/term.log | sed  's/\([0-9]*\).*/\1/'

```
That will return the line number where xorg-xserver was installed so you can quickly go to that line and see exactly what else was installed with it at that time... That way you can remove everything that got installed with it, with all the other dependencies.

libnotify-bin depends on libnotify4, which one of the depends is gnome-session... So you, it installed a whole lot of desktop pieces from that. If you have troubles finding exactly what, I have a generic 3 liners that will remove most of that, but still leaves some bloat. The above is the "right way".

---

### Post by johndid on 2023-04-08
> **MAFoElffen said:**
> Yes. If you look in your apt logs... Specifically /var/log/apt/term.log. I would first do
```

grep -n -m 1 'xorg' /var/log/apt/term.log | sed  's/\([0-9]*\).*/\1/'

```
That will return the line number where xorg-xserver was installed so you can quickly go to that line and see exactly what else was installed with it at that time... That way you can remove everything that got installed with it, with all the other dependencies.

libnotify-bin depends on libnotify4, which one of the depends is gnome-session... So you, it installed a whole lot of desktop pieces from that. If you have troubles finding exactly what, I have a generic 3 liners that will remove most of that, but still leaves some bloat. The above is the "right way".


I ran the command and got **1082 **as a result

The line seems to be this one, if I got it right:

```
Selecting previously unselected package xserver-xorg-core
```


Thanks

---

### Post by MAFoElffen on 2023-04-08
In that process, look right before that to see what was installed, and what other packages were installed with it.

---

### Post by johndid on 2023-04-08
> **MAFoElffen said:**
> In that process, look right before that to see what was installed, and what other packages were installed with it.


```
Selecting previously unselected package libxcb-icccm4:amd64.
Preparing to unpack .../353-libxcb-icccm4_0.4.1-1.1_amd64.deb ...
Unpacking libxcb-icccm4:amd64 (0.4.1-1.1) ...
Selecting previously unselected package libxcb-image0:amd64.
Preparing to unpack .../354-libxcb-image0_0.4.0-1build1_amd64.deb ...
Unpacking libxcb-image0:amd64 (0.4.0-1build1) ...
Selecting previously unselected package libxcb-keysyms1:amd64.
Preparing to unpack .../355-libxcb-keysyms1_0.4.0-1build1_amd64.deb ...
Unpacking libxcb-keysyms1:amd64 (0.4.0-1build1) ...
Selecting previously unselected package libxcb-render-util0:amd64.
Preparing to unpack .../356-libxcb-render-util0_0.3.9-1build1_amd64.deb ...
Unpacking libxcb-render-util0:amd64 (0.3.9-1build1) ...
Selecting previously unselected package xserver-xephyr.
Preparing to unpack .../357-xserver-xephyr_2%3a1.20.13-1ubuntu1~20.04.8_amd64.deb ...
Unpacking xserver-xephyr (2:1.20.13-1ubuntu1~20.04.8) ...
**Selecting previously unselected package xserver-xorg-core.**
Preparing to unpack .../358-xserver-xorg-core_2%3a1.20.13-1ubuntu1~20.04.8_amd64.deb ...
Unpacking xserver-xorg-core (2:1.20.13-1ubuntu1~20.04.8) ...
Selecting previously unselected package xserver-xorg-input-libinput.
Preparing to unpack .../359-xserver-xorg-input-libinput_0.29.0-1_amd64.deb ...
Unpacking xserver-xorg-input-libinput (0.29.0-1) ...
Selecting previously unselected package xserver-xorg-input-all.
Preparing to unpack .../360-xserver-xorg-input-all_1%3a7.7+19ubuntu14_amd64.deb ...
Unpacking xserver-xorg-input-all (1:7.7+19ubuntu14) ...
Selecting previously unselected package xserver-xorg-input-wacom.
Preparing to unpack .../361-xserver-xorg-input-wacom_1%3a0.39.0-0ubuntu1_amd64.deb ...
Unpacking xserver-xorg-input-wacom (1:0.39.0-0ubuntu1) ...
Selecting previously unselected package xserver-xorg.
Preparing to unpack .../362-xserver-xorg_1%3a7.7+19ubuntu14_amd64.deb ...
Unpacking xserver-xorg (1:7.7+19ubuntu14) ...
Selecting previously unselected package xserver-xorg-video-amdgpu.
Preparing to unpack .../363-xserver-xorg-video-amdgpu_19.1.0-1ubuntu0.1_amd64.deb ..


```

---

### Post by MAFoElffen on 2023-04-08
In the term.log file, in that section, each line that says "Preparing to unpack", is where it installed a package, with that package version. The package generic_name is on the next line where it says "Unpacking <package_name>"

If you trace that back further... To the line that starts with "Log started: YYYY-MM-DD HH:MM:SS". Copy the date/timestamp (only). Search for that date/timestamp in the /var/log/apt/history.log file. 

For example in term.log:
```

Log started: [COLOR=#ff0000]2023-04-04  06:46:08[/COLOR]

```
In the history.log file:
```

Start-Date: [COLOR=#ff0000]2023-04-04  06:46:08[/COLOR]
Commandline: /usr/bin/unattended-upgrade
Upgrade: libldb2:amd64 (2:2.4.4-0ubuntu0.22.04.1, 2:2.4.4-0ubuntu0.22.04.2), python3-ldb:amd64 (2:2.4.4-0ubuntu0.22.04.1, 2:2.4.4-0ubuntu0.22.04.2)
End-Date: 2023-04-04  06:46:09

```
That cross-references back to the action that started and caused it. And if self-inflicted by a user that installed something, there is going to be another line below the "Commandline: ", that says "Requested by: user_name(UUID)"...

---

### Post by johndid on 2023-04-08
> **MAFoElffen said:**
> 
In the history.log file:
..
That cross-references back to the action that started and caused it. And if self-inflicted by a user that installed something, there is going to be another line below the "Commandline: ", that says "Requested by: user_name(UUID)"...

**Log started:   2023-04-02  12:44:59**

```
**Start-Date: 2023-04-02  12:44:59**
Commandline: apt install libnotify-bin
Requested-By: luke (1000)
Install: gkbd-capplet:amd64 (3.26.1-1, automatic), libgoa-backend-1.0-1:amd64 (3.36.1-0ubuntu1, automatic), xserver-xorg-input-all:a>
End-Date: 2023-04-02  12:54:03

Start-Date: 2023-04-02  13:39:55
Commandline: apt-get install libnotify-cil-dev
Requested-By: luke (1000)
Install: libmono-system-numerics4.0-cil:amd64 (6.8.0.105+dfsg-2, automatic), libdbus2.0-cil:amd64 (0.8.1-2, automatic), libmono-syst>
End-Date: 2023-04-02  13:41:56

Start-Date: 2023-04-02  13:42:50
Commandline: apt-get install notification-daemon
Requested-By: luke (1000)
Install: notification-daemon:amd64 (3.20.0-4)
End-Date: 2023-04-02  13:42:53
```

---

### Post by MAFoElffen on 2023-04-08
So, back in the term.log, all those packages that were unpacked between 2023-04-02  12:44:59 and 2023-04-02  13:42:53 need to be removed and purged.

Those packages are for a Desktop, not console.

---

### Post by johndid on 2023-04-08
> **MAFoElffen said:**
> So, back in the term.log, all those packages that were unpacked between 2023-04-02  12:44:59 and 2023-04-02  13:42:53 need to be removed and purged.

Those packages are for a Desktop, not console.

ok thanks

---

### Post by MAFoElffen on 2023-04-08
Not sure why you installed GUI notification packages. Got me thining how I have done that in the past, and why I did that for my servers.

I have installed Minimal X on my old servers, which did not have a desktop installed, to send popup notifications remotely to my Desktop Machine, which was the Management Console for all my servers. That didn't mean that the servers were running a desktop, They, themselves were Console. That in itself, will not install a Desktop to your servers. Just mentioned that in case that is what you are trying to accomplish.

But for both Windows and Linux Servers (later), I used scheduled status alerts that triggered threshold scripts that sent me messages to my pager, and/or emails to my Admin email account if there was a problem. No GUI needed, nor anything else except access to my mail server to send out an email.

---

### Post by johndid on 2023-04-10
> **MAFoElffen said:**
> Not sure why you installed GUI notification packages. Got me thining how I have done that in the past, and why I did that for my servers.

I have installed Minimal X on my old servers, which did not have a desktop installed, to send popup notifications remotely to my Desktop Machine, which was the Management Console for all my servers. That didn't mean that the servers were running a desktop, They, themselves were Console. That in itself, will not install a Desktop to your servers. Just mentioned that in case that is what you are trying to accomplish.

But for both Windows and Linux Servers (later), I used scheduled status alerts that triggered threshold scripts that sent me messages to my pager, and/or emails to my Admin email account if there was a problem. No GUI needed, nor anything else except access to my mail server to send out an email.

I installed it because someone suggested me to install a few libraries useful for notifications or something like that, and I somehow ended up with a GUI. In a few words it was not intentional. Anyway, it doesn't seem to affect my ubuntu server performance, and I also found out that I can run Timeshift on it, which could come in handy someday, so I haven't yet made up my mind about uninstalling it or not.
Thanks

---

### Post by TheFu on 2023-04-10
GUIs have a client-side and a server-side.  X/Windows is a client/server architecture, even when running on the same physical system. It is handy when running GUI programs on remote systems.

About the minimal way to install X/Client libraries on a remote system is to install something like **xterm**.  The dependencies for it will be minimal for an X/Client setup.  The X/Server runs on the machine you sit behind that has a GUI.

As for notifications, the Gnome programs seem pretty lazy to me when it comes to avoiding bloat and include all sorts of convenience libraries that add to bloat without much thought.  They barely consider that for the last 40+ yrs, Unix has supported running client applications remotely using X11.  This happens more and more with programmers trained with MS-Windows programming first. They just don't know any better.  There are some amazing things that GTK+ libraries have provided for cross-platform software development, but most cross-platform development libraries tend to be bloated to make things easier.  They are split up like the original X/Windows libraries where.

What sort of notification were you seeking?  If you wanted a windows to pop up related to the server, I'd say you are doing it wrong.  What you want is a messaging service to send an event to a tiny client that runs on your local desktop.  X/Windows has methods for doing this, but I doubt they'd work under Wayland.

---

### Post by johndid on 2023-04-10
> **TheFu said:**
> 
What sort of notification were you seeking?  If you wanted a windows to pop up related to the server, I'd say you are doing it wrong.  What you want is a messaging service to send an event to a tiny client that runs on your local desktop.  X/Windows has methods for doing this, but I doubt they'd work under Wayland.

I don't remember it now. I have to look through my notes.
it happens that I experiment with ubuntu so much...to the extend that I often forget what I was for exactly :-)

by the way,
what is your thought about snap? Should I uninstall it from my Ubuntu server too?

Thanks

---

### Post by TheFu on 2023-04-10
> **johndid said:**
>  what is your thought about snap? Should I uninstall it from my Ubuntu server too?

There are many long threads here where people complain about snaps and provide reasons.  Best to go find those and read them rather than re-hashing the same stuff here.

Whether you should or shouldn't do anything on your server is up to you.  Things that I consider huge mistakes because I've been burned by using them may not be any issue for you.  When the server fails at 4am, nobody is going to be calling my phone.

---

### Post by johndid on 2023-04-10
Ok, it sounds like it is something you have already discussed lively about. :-)

Thanks

---

### Post by MAFoElffen on 2023-04-10
@TheFu -- You'll love this! LOL

RE: [https://news.itsfoss.com/ubuntu-ditch-snap/](https://news.itsfoss.com/ubuntu-ditch-snap/)

The current news releases say that Canonical has abandoned "their push" on using Snaps in any future LTS releases. It will not be a part of 24.04 LTS. They said that if someone wants to fork it to continue their use of it... But for them, it's going to dead-end. So I personally wouldn't invest much time and effort in Snaps.

---

### Post by #&amp;thj^% on 2023-04-10
> **MAFoElffen said:**
> @TheFu -- You'll love this! LOL

RE: [https://news.itsfoss.com/ubuntu-ditch-snap/](https://news.itsfoss.com/ubuntu-ditch-snap/)

The current news releases say that Canonical has abandoned "their push" on using Snaps in any future LTS releases. It will not be a part of 24.04 LTS. They said that if someone wants to fork it to continue their use of it... But for them, it's going to dead-end. So I personally wouldn't invest much time and effort in Snaps.

Drinks all around, Way to go Canonical, hip hip hooray.
Now if it only rings true.

---

### Post by TheFu on 2023-04-10
> **MAFoElffen said:**
> @TheFu -- You'll love this! LOL

RE: [https://news.itsfoss.com/ubuntu-ditch-snap/](https://news.itsfoss.com/ubuntu-ditch-snap/)

The current news releases say that Canonical has abandoned "their push" on using Snaps in any future LTS releases. It will not be a part of 24.04 LTS. They said that if someone wants to fork it to continue their use of it... But for them, it's going to dead-end. So I personally wouldn't invest much time and effort in Snaps.

Any stories on April 1 are suspect as an Aprils Fool's Joke.  It will take them at least 2-4 more years to admit it was a mistake, going on the Unity DE debacle.  At least with Unity, we didn't have to use it.

---

### Post by MAFoElffen on 2023-04-10
LOL. The Link to "Read the The Official Announcement" goes to the "April Fool's Day" page of Wikipedia... LMAO! (Yes is was an April's Foools Joke!!!)

But is is a good read with many good points. LOL

Snaps is losing ground very day to Flatpaks, with FlatPaks being accepted as the way to go, if you were to do something like that. There is still very large resistance to Snaps.

---

