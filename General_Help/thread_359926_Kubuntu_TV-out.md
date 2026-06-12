---
title: "Kubuntu TV-out"
date: 2007-02-12
forum: General Help
---

### Post by Morientes on 2007-02-12
I have recently followed this guide [http://ubuntuforums.org/showthread.php?t=98456](http://ubuntuforums.org/showthread.php?t=98456) to enable my TV-out in Kubuntu 6.10. It seems to be working fine, however there are a few things I would like to change.

As it is now I have it as two screens, meaning that when I move my curser to the right of the monitor it moves to the TV.
I would like however to be able to somehow easily disable this feature when I dont want to use the TV-out, because f.ex when scolling on a web-page, it is annoying that the mouse can move over the edge of the screen.
So is there a way to disable the TV-out easily without editing xorg.conf again?

Also I would like to know if there exists some sort of "media center" application for (K)Ubuntu? I am thinking something along the lines of the Windows Media Center...

---

### Post by barney_1 on 2007-02-12
I use MythTV which has media center capabilities.  You can setup it up to use the plugins for music, video, pictures, weather, netflix, and a ton of other features that all can be used from your sofa.

Check out the project webpage:  [www.mythtv.org](www.mythtv.org)

If you want to try it out, I'd suggest using the ubuntu wiki: [https://help.ubuntu.com/community/MythTV](https://help.ubuntu.com/community/MythTV)

This being said, I still think the media center features of my Xbox running [XboxMediaCenter]("http://www.xboxmediacenter.com") are far superior.  You might keep looking for another linux solution if MythTV doesn't suit your needs.

---

### Post by Morientes on 2007-02-13
Yeah I have taken a look at MythTV and it looks quite ok.

When starting it wants to connect to a mysql database. Since I don't want to make a mythtv user, how should I create the database so that my normal user has access to it?

Also, any ideas about the disabling tv-out thing?

---

### Post by Morientes on 2007-02-14
bump:-)

---

### Post by FluffyElmo on 2007-02-14
The username and password for MySQL is completely separate from your regular user account. Myth can be run as any user and still access the database provided it knows the correct username/password. Basically, you can set the MySQL username/password to whatever you want. Then you enter that information into Myth. 

By default I think MySQL uses username *root* with no password and that is fine if you're running on the same machine and have a firewall like Firestarter installed.

The TV-Out will differ depending on your video hardware. Recent versions of the Nvidia control panel let you enable/disable and auto-detect displays without rebooting and is probably your best bet. It's usually at *Applications->System Tools->Nvidia X-Server Settings*.

In the past, with my Nvidia 7600GT I could always remove the TV dongle from the port and reboot the TV-Out will be disabled, plug it in and reboot and it is re-enabled.

---

### Post by fenian on 2007-02-14
> By default I think MySQL uses username root with no password and that is fine if you're running on the same machine and have a firewall like Firestarter installed.

Thats like saying its o.k. to leave your doors unlocked because you have a big dog.Setting up mysql with no password is a security risk.It takes less than 2 minutes to set the mysql password I see no reason not to.

---

### Post by FluffyElmo on 2007-02-14
Not really. By default it's configured for local access only, the firewall is an extra precaution. The only attack vector is via your user account, in which case they can reset the MySQL passwords in under two minutes. They can also do much worse damage than looking at my database of recorded TV shows. It's more like leaving a desk drawer unlocked inside my locked house because I don't have anything but office supplies in it to begin with.

Don't get me wrong, on a production machine I *always* set suitably cryptic passwords but for a new desktop user who just wants Myth to run I think there are worse security sins. And as someone who has several newbie friends with new Myth boxes, it's *always* the MySQL stuff that has them calling me...

---

### Post by Morientes on 2007-02-14
Thanks for the replys!

By the way: In order to make the display properly fit my TV I have to change the overscan settings in the NVIDIA control panel. However for the overscan settings to be remembered I have to open the NVIDIA panel every time I have rebooted the computer. If I don't do that it is at default value.
Is there a way to make it remember the settings without having to open the panel?

---

### Post by FluffyElmo on 2007-02-14
By default the Nvidia utility doesn't run with root privileges so it can't save any changes to your configuration. You can try running *sudo nvidia-settings* from a terminal and then saving the settings to the xorg.conf. In the display section.

If that doesn't work let us know since you can modify the xorg.conf file directly to specify over/underscan values but the details escape me right now...

---

### Post by Morientes on 2007-02-14
Hm no it didn't really do anything. When started with sudo it just has the same value that I set before but it doesn't remember it in that way either unfortunately...

There isn't some way it can be set manually in xorg.conf?

---

### Post by FluffyElmo on 2007-02-14
I found this ([http://gentoo-wiki.com/TV-Out_with_GeForce]("http://gentoo-wiki.com/TV-Out_with_GeForce")) and the key line seems to be: *Option      "TVOverScan" "0.6"* or whatever value you choose  in the device section of xorg.conf. Also, if I remember correctly Nvidia has a read-me file downloadable from the driver page with more information.

You probably already know this but just in case, to back-up and then edit your xorg.conf do the following. Then after saving use *Ctrl-Alt-Backspace* to restart X.
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old
sudo gedit /etc/X11/xorg.conf
```

---

### Post by Morientes on 2007-02-14
That did the trick! Thank you!

By the way, do you know how I might run the command "sudo hidd --server" on startup?

It's because I have to run that to be able to connect my phone to the computer as a remote control. It's no biggy but would be nice if it did it automatically! :-)

---

### Post by FluffyElmo on 2007-02-14
*System->Preferences->Sessions* will let you specify start-up commands but I don't know if they will run as root. 

If not */etc/init.d/* contains start-up scripts and the */etc/rcX.d/* directories are run in order. For scripts (or typically links to scripts) in */etc/rc5.d/* are run last and a script starting with say *S10* is run before a script starting with *S30*. So if you were to put a shell script containing that command (minus the sudo) in */etc/rc5.d/* that followed the naming convention it should run with root privileges. 

It's been a very long time since I had to mess with that though, and I'm probably being less than clear anyways. So try the Session GUI and if that doesn't work then the forum search or Google is probably a better source of information than I ;)

---

### Post by Morientes on 2007-02-14
Ok, thank you for your help.:-)

---

