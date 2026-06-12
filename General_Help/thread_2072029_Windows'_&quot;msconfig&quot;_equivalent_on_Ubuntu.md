---
title: "Windows' &quot;msconfig&quot; equivalent on Ubuntu 12.04"
date: 2012-10-16
forum: General Help
---

### Post by jorgl on 2012-10-16
Hello eveybody!

I would like to know what is the function on Ubuntu 12.04 equivalent to "msconfig" on Windows (so I could define which aplication should start with Ubuntu or not).

Thank you! Hugs.

---

### Post by wojox on 2012-10-16
> **jorgl said:**
> (so I could define which aplication should start with Ubuntu or not).

Ctrl+Alt+T, They hid them, unhide them
```
sudo sed -i 's/NoDisplay=true/NoDisplay=false/g' /etc/xdg/autostart/*.desktop
```
```
gnome-session-properties
```

---

### Post by jorgl on 2012-10-16
> **wojox said:**
> Ctrl+Alt+T 
```
gnome-session-properties
```
They hid them, unhide them
```
sudo sed -i 's/NoDisplay=true/NoDisplay=false/g' /etc/xdg/autostart/*.desktop
```

Thank you, wojox! But it doenst show everything that starts with my computer. 

How do I know that? Because when I open gnome-system-monitor is shows A LOT of running aplications, even applications that wasnt started by myself.

So it has to be another way. Could anyone else help me with this?

---

### Post by lykwydchykyn on 2012-10-16
There is no equivalent to msconfig on Ubuntu.

Some of those processes are likely started by the init system at boot; those configurations are in /etc/init.


Is there a particular program you're wanting to prevent from starting?

---

### Post by jorgl on 2012-10-17
> **lykwydchykyn said:**
> There is no equivalent to msconfig on Ubuntu.

Some of those processes are likely started by the init system at boot; those configurations are in /etc/init.


Is there a particular program you're wanting to prevent from starting?

I dont know. I would like to prevent form starting "bluetooth-applet" for example. 

But it seems preventing from starting some stuff would be much harder than it is in Windows. I am using a netbook. All I wanted to was prevent some apps from starting to make my computer a little bit faster.

---

### Post by lykwydchykyn on 2012-10-17
> **jorgl said:**
> I dont know. I would like to prevent form starting "bluetooth-applet" for example. 

But it seems preventing from starting some stuff would be much harder than it is in Windows. I am using a netbook. All I wanted to was prevent some apps from starting to make my computer a little bit faster.

You can try the program "bum" (boot-up-manager) from the repositories; it's for managing system services.  I don't know how well it works.

---

### Post by jorgl on 2012-10-18
> **lykwydchykyn said:**
> You can try the program "bum" (boot-up-manager) from the repositories; it's for managing system services.  I don't know how well it works.

It seems to be a good app. I am gonna try it! Thank you for you attention,lykwydchykyn! Big hug, man!

---

### Post by cmcanulty on 2012-10-18
go to startup applications in classic

---

### Post by oldos2er on 2012-10-18
I'm pretty sure bluetooth is controlled by upstart. See [http://askubuntu.com/questions/19320/whats-the-recommended-way-to-enable-disable-services](http://askubuntu.com/questions/19320/whats-the-recommended-way-to-enable-disable-services)

---

