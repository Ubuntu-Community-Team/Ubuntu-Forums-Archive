---
title: "Attempting to install Tor"
date: 2014-12-27
forum: General Help
---

### Post by AlyssaVS on 2014-12-27
I am trying to install Tor. I keep getting this error:

"(gedit:7726): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files"

These are the directions I'm using substituting trusty (I've also tried trusty tahr) for <distribution>:

[COLOR=#1A1A1A][FONT=Helvetica]"/etc/apt/sources.list file:
[/FONT][/COLOR]
deb     [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) <DISTRIBUTION> main
[COLOR=#1A1A1A][FONT=Helvetica]where you put the codename of your distribution (i.e. lenny, sid, saucy or whatever it is) in place of <DISTRIBUTION>.[/FONT][/COLOR][COLOR=#1A1A1A][FONT=Helvetica]Then add the gpg key used to sign the packages by running the following commands at your command prompt:[/FONT][/COLOR]
gpg --keyserver keys.gnupg.net --recv 886DDD89
gpg --export A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89 | sudo apt-key add -
[COLOR=#1A1A1A][FONT=Helvetica]Now refresh your sources, running the following command (as root) at your command prompt:[/FONT][/COLOR]apt-get update
[COLOR=#1A1A1A][FONT=Helvetica]If there are no errors you're good to continue."

[/FONT][/COLOR]I can't seem to get anywhere past the initial step of loading into my source list. This is all I get. Any help would be greatly appreciated.

Have a great day,
Alyssa

---

### Post by Frogs Hair on 2014-12-27
There are some different options listed in this recently replied to thread. 
[http://ubuntuforums.org/showthread.php?t=2221571&highlight=Tor](http://ubuntuforums.org/showthread.php?t=2221571&highlight=Tor)

---

