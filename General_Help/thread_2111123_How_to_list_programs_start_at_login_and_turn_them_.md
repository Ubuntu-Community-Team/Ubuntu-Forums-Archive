---
title: "How to list programs start at login and turn them on/off ?"
date: 2013-02-01
forum: General Help
---

### Post by ashwin_cse on 2013-02-01
I see that logining in ubuntu is slower that in other linux i have seen like arch linux or rhel5.5. Though i find that bootup is faster in ubuntu. I think it is starting many programs in the background which is the cause of slow login. One thing i can see that is launching on login is update manager. I set update manager check for updates to never. But still it keeps popping up. How do i find the list of programs that start on login and choose to turn off/on. I tried clicking on startup programs in the system tray, but it has nothing. Also how do i turn off updates checking. I see that even text loging is delay because it checks for updates before it allows you to login. I am using ubuntu 12.04.1 lts.

---

### Post by pholden on 2013-02-01
> **ashwin_cse said:**
> How do i find the list of programs that start on login and choose to turn off/on.
System > Preferences > [Startup Applications]("http://linux.die.net/man/1/gnome-session-properties")
> **ashwin_cse said:**
> Also how do i turn off updates checking.
System > Administration > [Update Manager]("https://launchpad.net/ubuntu/+source/update-manager") > Settings > Automatic Updates

---

### Post by Schnappi1989 on 2013-02-01
The upstairs method is right! I am agree with him! Have you solved your trouble ?

---

### Post by ashwin_cse on 2013-02-01
> **pholden said:**
> System > Preferences > [Startup Applications]("http://linux.die.net/man/1/gnome-session-properties")

Thats where the problem is. Its list nothing. But still there are application are launched during start up. Like the update manager.


System > Administration > [Update Manager]("https://launchpad.net/ubuntu/+source/update-manager") > Settings > Automatic Updates

I did that, still update manager pops up during login.

I did my basic searching before posting this help. So dont think i am asking without doing my bit of homework.

---

### Post by gifford on 2013-02-01
You might check here /etc/xdg/autostart to see what is listed.

---

### Post by stinkeye on 2013-02-01
> I see that logining in ubuntu is slower that in other linux i have seen like arch linux or rhel5.5.
This is more likely due to loading the window manager compiz/unity than anything else.

Show all startup apps in startup applications.
In terminal...
```
cd /etc/xdg/autostart/
sudo sed --in-place 's/NoDisplay=true/NoDisplay=false/g' *.desktop
```

---

