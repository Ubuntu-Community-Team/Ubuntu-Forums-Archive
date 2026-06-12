---
title: "Firestarter requires manual start"
date: 2008-01-07
forum: General Help
---

### Post by drewcoon on 2008-01-07
Hey, I'm having a problem with getting Firestarter to start after login, I've used a work-around to get Firestarter to start without requiring a sudo password, and it works great, but only if I start it manually through the GUI or terminal.

[IMG]http://i16.photobucket.com/albums/b23/Drewc2k5/Screenshot-Failedtostartthefirewall.png[/IMG]

This is the error box that i'm presented with everytime I log in. My best guess is that Firestarter is trying to start before my wireless is ready. After I close this box, I open up the Firestarter GUI and find that the firewall is locked and I have to start it manually. It works fine after the manual start, fortunately :)

Anyone have a solution?

---

### Post by Steveway on 2008-01-07
You don't need Firestarter running.
1. It's only a Graphical-Configuration-Tool for IPtables. (IPtables is your Firewall and runs always.)
2. You won't need a Firewall for a Personal Computer, unless you are running a server.


3. This is not Windows.

---

### Post by erfahren on 2008-01-07
if you do want the Firestarter GUI starting up, you could create a little script to start it after a delay. 

just in a text editor something like (using your command line to start it):
```

#/bin/bash
 sleep 10
sudo firestarter --start-hidden

```
save it as "start_firestarter" (or whatever)

create a folder named "bin" in your /home/*username* directory and save it into there - right-click on the saved scipt and under "Permissions" check the box to make it executable.

Then in the Session Startup you can just put the name of the script ("start_firestarter") as the command.

It should work when you reboot - Ubuntu's .~/.bash_profile (actually just ~/.profile ) already includes the path to the user's ~/bin by default.

for more info on that see: 
[http://www.linuxcommand.org/wss0010.php](http://www.linuxcommand.org/wss0010.php)
[http://ubuntuforums.org/showthread.php?t=363796](http://ubuntuforums.org/showthread.php?t=363796)

(you *could*  put the scipt in /usr/bin instaed if you wanted I guess)

---

### Post by drewcoon on 2008-01-07
> **Steveway said:**
> You don't need Firestarter running.
1. It's only a Graphical-Configuration-Tool for IPtables. (IPtables is your Firewall and runs always.)
2. You won't need a Firewall for a Personal Computer, unless you are running a server.


3. This is not Windows.

That's not what I've heard, I've been told that instead of an antivirus like Windows would need, I should use a firewall instead. iptables is a bit hard to configure without a GUI, isn't it? 
And who knows, I might serve things off my computer someday, and it never hurts to get experience with making servers run with firewalls.

@erfahren That script looks pretty good, I'll try it and see if it works.

I'm new to scripting with Linux, but i'm learning :)

---

### Post by bodhi.zazen on 2008-01-07
> **drewcoon said:**
> That's not what I've heard, I've been told that instead of an antivirus like Windows would need, I should use a firewall instead. iptables is a bit hard to configure without a GUI, isn't it? 
And who knows, I might serve things off my computer someday, and it never hurts to get experience with making servers run with firewalls.

@erfahren That script looks pretty good, I'll try it and see if it works.

I'm new to scripting with Linux, but i'm learning :)

Yes, all that is true.

Your firewall is iptables. Firestarter is a GUI tool to configure your firewall.

The problem is that Firestarter runs as root and is a security risk. 

So ... Launch Firestarter, configure IP Tables, close Firestarter.

Once iptables is configured it is active without Firestarter running, it remains active if you reboot. It remains active until you either turn it off or re-configure it with Firestarter.

Why would you want to run firestarter all the time ? To monitor network traffic ? If so, use a tool that does not run as root (such as wireshark). Monitoring tools are not simple to use, I understand, but IMO firestarter is a security risk and you should not run it all the time nor configure sudo to allow it to run without a password.

Here is a link on Security : [[color=black]Ubuntu Security[/color]](http://ubuntuforums.org/showthread.php?t=510812)

---

