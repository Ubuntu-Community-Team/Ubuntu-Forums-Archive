---
title: "No more hibernate in 14.04? Polkit script no longer works."
date: 2014-04-23
forum: General Help
---

### Post by scottbomb on 2014-04-23
Ever since Canonical, in all their wisdom, removed hibernation (a feature I use a lot with the laptop) I have used the following advice to re-enable it from [http://askubuntu.com/questions/94754/how-to-enable-hibernation](http://askubuntu.com/questions/94754/how-to-enable-hibernation)

sudo nano /etc/polkit-1/localauthority/50-local.d/com.ubuntu.enable-hibernate.pkla

Fill it with this:

[Re-enable hibernate by default]
Identity=unix-user:*
Action=org.freedesktop.upower.hibernate
ResultActive=yes

This has worked well ever since 12.04. Unfortunately, it does not work with 14.04. Even after a reboot, there is no hibernate button in the log-out dialogue. And yes, the computer is capable and sudo pm-hibernate does indeed work. I'll create a launcher icon to execute this command until I can find a real fix.

---

### Post by Toz on 2014-04-24
You have to create an entry for both upower and systemd. Change that code to read:
```
[Re-enable hibernate by default in upower]
Identity=unix-user:*
Action=org.freedesktop.upower.hibernate
ResultActive=yes

[Re-enable hibernate by default in logind]
Identity=unix-user:*
Action=org.freedesktop.login1.hibernate
ResultActive=yes
```
...then:
```
sudo restart systemd-logind
xfce4-panel -r
```
...or reboot

---

### Post by trag on 2014-04-26
Try this  [COLOR=#333333][FONT=Helvetica Neue]This simple and brief tutorial is going to show you how to enable the hibernate feature in Ubuntu 14.04 Trusty Tahr.[/FONT][/COLOR][COLOR=#333333][FONT=Helvetica Neue]Hibernate is disabled by default in Ubuntu, when the computer hibernates, all of your applications and documents are stored and the computer completely switches off so it does not use any power, but the applications and documents will still be open when you switch on the computer again.
[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica Neue][[IMG]http://ubuntuhandbook.org/wp-content/uploads/2013/10/hibernate-ubuntu1310.jpg[/IMG]]("http://ubuntuhandbook.org/wp-content/uploads/2013/10/hibernate-ubuntu1310.jpg")
[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica Neue]**Test if hibernate works in your case:**
[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica Neue]Before getting started, press Ctrl+ALt+T on your keyboard to open the terminal. When it opens, run:
[/FONT][/COLOR]
sudo pm-hibernate[COLOR=#333333][FONT=Helvetica Neue]After you computer turns off, switch it back on. Did your open applications re-open? If hibernate doesn&#8217;t work, check if your swap partition is at least as large as your available RAM.
[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica Neue]**Enable Hibernate in System Tray Menu:**
[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica Neue]The indicator-session was updated to use logind instead of upower. Hibernate is disabled by default in both upower and logind.
[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica Neue]To re-enable hibernate, run the commands below one by one to edit the config file:
[/FONT][/COLOR]
sudo -i

cd **/var/lib**/polkit-1/localauthority/50-local.d/

gedit com.ubuntu.enable-hibernate.pkla[COLOR=#333333][FONT=Helvetica Neue]*Tips: if the config file does not work for you, try another one by changing **/var/lib** to**/etc** in the code.*
[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica Neue]Copy and paste below lines into the file and save it.
[/FONT][/COLOR]
[INDENT][Re-enable hibernate by default in upower]
Identity=unix-user:*
Action=org.freedesktop.upower.hibernate
ResultActive=yes

[Re-enable hibernate by default in logind]
Identity=unix-user:*
Action=org.freedesktop.login1.hibernate
ResultActive=yes

Good luck
trag
[/INDENT]

---

### Post by SkhSh on 2014-05-01
It works. It is going to request password for any action - poweroff, hibernate... 

How to skip password request while going to hibernate, or powerof, or else? 

I'm launching lxsession-logout, choosing hibernate and it will request password via gksudo (or smth. with similar interface). Then it will lock the screen. I may unlock screen, enter the password into the "gksudo" form and now it will go into hibernate.   

How it can be simplified?

---

### Post by benawhile on 2014-07-08
Trag, this is fantastic! It works. I now have hibernation in ubuntu for the first time since I started using it in 2012. It worked on my dualboot XP desktop and my ancient dualboot XP laptop, which has Lubuntu.

The similar solution in the link to askubuntu didn't work but this does.

For what it's worth i got these warnings (minus emoticons, cute?) but I ignored them:

(gedit:2516): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

(gedit:2516): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

---

### Post by jasom on 2014-09-24
I had a similar problem (no hibernation ). In my case swap space was not configured and therefore hibernation didn't work. I wrote an tutorial how to solve it: [How to enable hibernation in Lubuntu 14.04]("http://www.jasom.net/how-to-enable-hibernation-in-lubuntu-14-04") (It works also for Xubuntu, Ubuntu, Kubuntu)

---

### Post by Michael_McKenney on 2014-09-24
(gedit:2516): Gtk-WARNING

It is a bug in using Sudo Gedit.  I ignore them.  I wish I could suppress them.  I googled it and found its a bug.

---

### Post by ajgreeny on 2014-09-25
You should not use **sudo gedit**, it should be **gksudo gedit** for now at least, which requires that you install gksu.

There may be a move to using policykit and **gedit-pkexec** in future, but that is not yet current.

---

### Post by RickKnight on 2015-06-20
Thanks Jasom, That tutorial works perfectly.

---

