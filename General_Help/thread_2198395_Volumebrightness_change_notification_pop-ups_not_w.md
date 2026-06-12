---
title: "Volume/brightness change notification pop-ups not working"
date: 2014-01-08
forum: General Help
---

### Post by ggodone on 2014-01-08
I'm using Ubuntu GNOME with both the GNOME 3 and Unity desktop environments. In both the notification when I change my volume, brightness, or keyboard brightness doesn't appear which makes it hard to use. For clarification, I'm talking about [these notifications]("http://i.imgur.com/Zdfescj.png"). They worked before, and other notifications still work (at least on my GNOME 3 side). I tried reinstalling notify-osd and I've uninstalled notification-daemon, but it still won't work.

---

### Post by ggodone on 2014-01-12
Bump, would really like to have this fixed.

---

### Post by cdysthe on 2014-03-09
I'm having the same problem. The OSD for volume and brightness is gone and I can't fine out how to get it back.

---

### Post by keldwud on 2014-10-17
The notification program responsible for the pop-up with the volume and the brightness is notify-osd. It is called by the dbus service under the name org.freedesktop.Notifications and executed with the command Exec=<path to notification program of your choice>. In my case, I had installed xfce and then there were two files in /usr/share/dbus-1/services/<naming scheme foreign to me>.service that called the org.freedesktop.Notifications. I checked the whole folder by grepping for Name= and counting the results of non-unique results and found that every namespace in that directory was unique except for my notifications namespace. This led me to the solution of renaming the file that executed the xfce notifyd to service.disabled which made the file unreadable to dbus and then after a restart my volume and brightness notifications came back.


So a general more abstract method of resolving this issue for multiple users might involve grepping for org.freedesktop.Notifications in the /usr/share/dbus-1/services folder and then renaming any of the offending entries to anything that doesn't end in .service leaving only the path to the actual executable you wish to load and if it's not available, you can create one using the template below as a guide for adding your desired notification service. One could also theoretically call bash and use conditionals in the dbus service file as it allows for that and you could also use environment variables against a boolean check to select which notification program you want based on your desktop environment but I haven't finished getting that to work yet, I was just glad to get my volume and brightness indicators back. Anyway, here's the code, this is specific to my 64 bit ubuntu, there will be some slight modifications based on your environment and make sure you have installed notify-osd if it isn't installed already. I tried looking for an update-alternatives type method to switch it but this is the best I could come up with so far. This method will allow you to keep whatever other programs you installed that disabled it in the first place. I found other methods that just brute forced the issue by completely purging the programs that took its place but if you wish to keep the programs then this method is for you.


    grep org.freedesktop.Notifications /usr/share/dbus-1/services/*
    mv <offending entries to same filename>.service.disabled


    vim /usr/share/dbus-1/services/org.freedesktop.Notifications.service
    [D-BUS Service]
    Name=org.freedesktop.Notifications
    Exec=/usr/lib/x86_64-linux-gnu/notify-osd


Hope that helps. Forgive my poor editing, feel free to improve my presentation to make it easier to read.

---

