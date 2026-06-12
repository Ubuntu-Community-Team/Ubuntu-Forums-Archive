---
title: "'files' no longer working"
date: 2018-03-31
forum: General Help
---

### Post by jgw on 2018-03-31
'files' is no longer working  When I click on it the little circle just goes round and round but it never really starts.  On the other hand Thunar is working just fine.  I have done something very clever and, hopefully, somebody can tell me how to fix thing.

Thank you...................

---

### Post by Yellow Pasque on 2018-03-31
WHat happens when you try and start it from terminal?
```
nautilus
```

---

### Post by jgw on 2018-04-01
Thanks for the reply.

It just hangs.  However with sudo nautilus it works but I get:
greg@movies:~$ sudo nautilus
[sudo] password for greg: 

(nautilus:30086): Gtk-WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

** (nautilus:30086): CRITICAL **: Another desktop manager in use; desktop window won't be created
^C
greg@movies:~$ gksu nautilus  
This too works but without notices above.  (the ^C was to stop the command)

---

### Post by #&amp;thj^% on 2018-04-01
> **jgw said:**
>  However with sudo nautilus it works but I get:
greg@movies:~$ sudo nautilus
[sudo] password for greg: 

(nautilus:30086): Gtk-WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

** (nautilus:30086): CRITICAL **: Another desktop manager in use; desktop window won't be created
^C

Using "sudo" alone with any GUI is really a bad idea/practice! :(
However this is better "gksu nautilus"
You may have permission problems now.
show the output from the terminal of this:
```
cd && ls -la
```[B]
EDIT:[/B]While we are at it please include this also:
```
cd ~/.config/Nautilus && ls -la
```
with code tags please.:)

---

### Post by jgw on 2018-04-01
The results are here: [https://pastebin.com/2ukTEhV0](https://pastebin.com/2ukTEhV0)

There was no Nautilus in .config but there was a nautilus so I gave the the results of both.  I also did a locate on Nautilus which is included.  I also did a locate on 'nautilus' (all lower case).  That one was close to 300 lines which I can put up if you want.  

I also found 1 .nautilus:
greg@movies:~$ locate .nautilus
/usr/share/glib-2.0/schemas/org.gnome.nautilus.gschema.xml

I am tempted to just reinstall nautilus but will hold off on that one.

---

### Post by Yellow Pasque on 2018-04-01
> I am tempted to just reinstall nautilus but will hold off on that one.

Unless you were editing related system config files (like in /etc), that's probably not going to help. More likely is an issue in your user's nautilus config (in your /home dir).
Is it possible for you to create another user and check nautilus function for that user?

---

### Post by #&amp;thj^% on 2018-04-01
> **jgw said:**
> 
**_There was no Nautilus in .config_** but there was a nautilus so I gave the the results of both. 
I am tempted to just reinstall nautilus but will hold off on that one.
Good Catch :D I need to slow down with my typing....LOL
Your ".Xauthority" and ".ICEauthority" looks good, but nautilus has a root owned entry "**-rw-r--r--  1 root root   96 Apr  1 08:10 desktop-metadata**"
So that explains why nautilus is not behaving as expected.
For example my Thunar reads as follows:
```
cd ~/.config/Thunar && ls -la
total 20
drwxr-xr-x  2 me me 4096 Mar 29 07:49 .
drwxr-xr-x 41 me me 4096 Apr  1 07:37 ..
-rw-r--r--  1 me me 5537 Apr  1 05:22 accels.scm
-rw-------  1 me me  845 Mar 29 07:49 uca.xml

```
You can try to fix this with:
```
sudo chown $(id -u):$(id -g) /home/greg/~/.config/nautilus
```
This just happened today with **"sudo nautilus"**

---

### Post by jgw on 2018-04-01
Ok, here is what I did.  I went into synaptic and installed some nautilus stuff (I do this kind of thing and have learned over time that I can REALLY screw things up doing this)  Anyway, after synaptic finished there was a box with a bunch of stuff (below):
W: Target Packages (universe/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:23
W: Target Packages (universe/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:23
W: Target Packages (universe/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:23
W: Target Translations (universe/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:23

I ran iY PPA manager and searched for duplicates and could find none.  Then I went to software & updates and did find a couple that were unchecked (source).  I cleaned that up.  I guess I could go into the sources list and mess with that but, I think, that would be a really bad idea so I am leaving it alone. 

I am only including this stuff for your amusement as I have absolutely no idea what it all means but I thought to just leave it all alone.  I also clicked on the files/nautilus icon to open it and, this time, I was told that I had to restart nautilus.  I thought that was pretty interesting in that I didn't have any nautilus running.  I then went into the system monitor to see if there was actually one running.  There was and I ended it.  I then went back and clicked on the icon again and, this time, IT RAN!  Then opened a couple of other instances just to see if I could.  As far as I can tell its working just fine.  Only time will tell if I have screwed anything up.

I wonder if the problem was actually a copy of nautilus running that didn't tolerate any more and the one running was somehow hidden in the background.  I guess I wlll never know (mysteries abound?)

All in all I am a happy camper and appreciate all your time and effort to help me out - thank you!

Thanks again!

---

