---
title: "Your session has lasted less than 10 seconds..."
date: 2007-12-29
forum: General Help
---

### Post by Virgilio on 2007-12-29
When i try to start a gnome session that message appears then brings me back to the GDM
the exact message is 
"(process:6025): Gtk-WARNING**:this process is currently running setuid or setgid this is not a supported use of GTK+. You must create a helper program instead. For further details visit:
[www.gtk.org/setuid.html](www.gtk.org/setuid.html)
(process:6029): GTK-WARNING**:This process is currently running g setuid or setgid this is not a supported use of GTK+. You must create a helper program instead. For further details visit:
[www.gtk.org/setuid.html](www.gtk.org/setuid.html)

Refusing to initialize GTK+
/etc/gdm/xsession: Beginning session setup
/etc/profile:20:[[: not found
.:22:can't open /home/virgilio/desktop/docbook-xsl-1.73.2/.profile.incl"
Ok soo anything i can do to fix it?Tried the solutions in the other threads similar to mine but none seem to work:confused:

---

### Post by solarwind on 2007-12-29
chown -R <username>:<username> /home/<username>

Try that.

---

### Post by Virgilio on 2007-12-29
after every line it says operation not permitted 
chown: changing ownership of `/home/virgilio/.java/deployment/cache/6.0/5/4dab3f85-68499723': Operation not permitted
chown: changing ownership of `/home/virgilio/.java/deployment/cache/6.0/5': Operation not permitted
chown: changing ownership of `/home/virgilio/.java/deployment/cache/6.0/16': Operation not permitted
chown: changing ownership of `/home/virgilio/.java/deployment/cache/6.0/29': Operation not permitted
chown: changing ownership of `/home/virgilio/.java/deployment/cache/6.0/51': Operation not permitted
chown: changing ownership of `/home/virgilio/.java/deployment/cache/6.0/12': Operation not permitted
chown: changing ownership of `/home/virgilio/.java/deployment/cache/6.0/17': Operation not permitted
chown: changing ownership of `/home/virgilio/.java/deployment/cache/6.0/56': Operation not permitted
chown: changing ownership of `/home/virgilio/.java/deployment/cache/6.0/2': Operation not permitted
chown: changing ownership of `/home/virgilio/.java/deployment/cache/6.0/40': Operation not permitted
chown: changing ownership of `/home/virgilio/.java/deployment/cache/6.0/35': Operation not permitted
chown: changing ownership of `/home/virgilio/.java/deployment/cache/6.0/26': Operation not permitted
chown: changing ownership of `/home/virgilio/.java/deployment/cache/6.0/62': Operation not permitted
chown: changing ownership of `/home/virgilio/.java/deployment/cache/6.0/39': Operation not permitted
chown: changing ownership of `/home/virgilio/.java/deployment/cache/6.0/54': Operation not permitted
chown: changing ownership of `/home/virgilio/.java/deployment/cache/6.0/24': Operation not permitted
chown: changing ownership of `/home/virgilio/.java/deployment/cache/6.0/28': Operation not permitted
chown: changing ownership of `/home/virgilio/.java/deployment/cache/6.0/18': Operation not permitted
chown: changing ownership of `/home/virgilio/.java/deployment/cache/6.0/63': Operation not permitted
chown: changing ownership of `/home/virgilio/.java/deployment/cache/6.0/11': Operation not permitted
chown: changing ownership of `/home/virgilio/.java/deployment/cache/6.0/27': Operation not permitted
chown: changing ownership of `/home/virgilio/.java/deployment/cache/6.0/tmp': Operation not permitted
...etc but everything ends with operation not permitted is that normal?

---

### Post by solarwind on 2007-12-29
Put a sudo in front of your command.

---

### Post by andoni on 2008-03-24
> **solarwind said:**
> chown -R <username>:<username> /home/<username>

Try that.
Ok, I will try this, i have the same problem, unfortunely...
EDIT: It doesn't work, I did it on the fail safe terminal mode.
greetings.

---

### Post by solarwind on 2008-03-24
> **andoni said:**
> Ok, I will try this, i have the same problem, unfortunely...
EDIT: It doesn't work, I did it on the fail safe terminal mode.
greetings.

Remember the sudo.

---

### Post by andoni on 2008-03-25
> **solarwind said:**
> Remember the sudo.
Yeah, i did it with sudo, and restarted, and it doesn't work.
Any suggestion?

---

### Post by mrhammad on 2008-03-25
This happen to me too and what I think is it happens after some last update. how to check the logs of last update there may be some bug in last update that might have caused it.

My error is also

(process:6823): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.

(process:6827): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
/usr/bin/ssh-agent: error while loading shared libraries: libgssapi_krb5.so.2: cannot open shared object file: Input/output error

sudo chown -R <username>:<username> /home/<username>

I tried this command also in Gnome Failsafe mode no error but not helped

---

### Post by andoni on 2008-03-26
> **mrhammad said:**
> This happen to me too and what I think is it happens after some last update. how to check the logs of last update there may be some bug in last update that might have caused it.

My error is also

(process:6823): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.

(process:6827): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
/usr/bin/ssh-agent: error while loading shared libraries: libgssapi_krb5.so.2: cannot open shared object file: Input/output error

sudo chown -R <username>:<username> /home/<username>

I tried this command also in Gnome Failsafe mode no error but not helped
I also tried this, and it doesn't work to me...
Please, someone who solved it, post the solution here, i'm getting desperated...
Greetings;).

---

### Post by kwunderlich on 2008-03-29
I was receiving the same issue as well, but for some reason my issue was with an extra 'fi' in the ~/.profile.  Once I removed it, gdm loaded without any problems.

---

### Post by mrhammad on 2008-03-29
> **kwunderlich said:**
> I was receiving the same issue as well, but for some reason my issue was with an extra 'fi' in the ~/.profile.  Once I removed it, gdm loaded without any problems.

it has nothing to do with it.

---

### Post by mrhammad on 2008-04-01
I feel like lost and linux is not that stable after all. I dont know what the hell has happened with it. I cant find solution any where and so much what I updated it and all the installation will be lost. I feel very bad about it.

---

