---
title: "Half uninstalled program"
date: 2007-06-23
forum: General Help
---

### Post by B-Con on 2007-06-23
I'm trying to re-install the program Privoxy, but apparantly it's "stuck" between installed and uninstalled:

> b-con@beacon:~/Desktop$ sudo apt-get install privoxy
Reading package lists... Done
Building dependency tree       
Reading state information... Done
privoxy is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up privoxy (3.0.6-1) ...
chown: cannot access `/etc/privoxy/user.action': No such file or directory
chown: cannot access `/etc/privoxy/trust': No such file or directory
dpkg: error processing privoxy (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 privoxy
E: Sub-process /usr/bin/dpkg returned an error code (1)

Note "1 not fully installed or removed."

How do I fix this? How can I make it fully installed or (I presume more easily) fully removed?

---

### Post by Maxtorm on 2007-06-23
I had the same problem with samba.  Resolved it via Synpatic Package Manager.  Searched for the package in question and chose it for "Reinstall"ation (from right-click menu on package).

---

### Post by B-Con on 2007-06-24
I tried that. "Re-install", "remove", "complete remove", they all failed with errors similar to what I got at the command prompt.

---

### Post by r0ck80y on 2007-06-24
Try updating apt-get first. Or do this:```

apt-get -f install privoxy
```
You may have to do this several times

---

### Post by Maxtorm on 2007-06-24
A bit of a stab in the dark here, but have you tried the Fix Broken Packages option in Synaptic (under Edit menu)?

---

### Post by B-Con on 2007-06-24
Tried Fix Broken Packages, nothing changed.

Tried forcing the install, but still got problems:

> b-con@beacon:~$ sudo apt-get -f install privoxy
Reading package lists... Done
Building dependency tree       
Reading state information... Done
privoxy is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up privoxy (3.0.6-1) ...
chown: cannot access `/etc/privoxy/user.action': No such file or directory
chown: cannot access `/etc/privoxy/trust': No such file or directory
dpkg: error processing privoxy (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 privoxy
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

### Post by Maxtorm on 2007-06-25
I just remembered one other thing I had to do to fix my similar samba issue.  In my case, I had deleted the smb.conf file and got the same sort of error.  Try doing this right before you execute the apt-get install:
```
sudo touch /etc/privoxy/user.action
sudo touch /etc/privoxy/trust
```

---

### Post by B-Con on 2007-06-25
Cool, that helped. But now I have a single error left:
>  subprocess pre-removal script returned error exit status 1
Jun 25 13:41:32 Privoxy(b7ded6c0) Fatal error: can't check configuration file '//config':  No such file or directory
Jun 25 13:41:32 Privoxy(b7ded6c0) Fatal error: can't check configuration file '//config'

I get this when I try to both install and remove Privoxy. "//config" -- ? Where's that coming from?

---

### Post by Maxtorm on 2007-06-25
Hmmm... Odd path format.  Literally (I think) //config is the same as /config.  This may not be the best of ideas, but perhaps sudo touch //config before you try to remove?

---

### Post by B-Con on 2007-07-16
> **Maxtorm said:**
> Hmmm... Odd path format.  Literally (I think) //config is the same as /config.  This may not be the best of ideas, but perhaps sudo touch //config before you try to remove?
Oh, hey, I never got back to you on this.

Yes, touch //config worked and privoxy is now successfully uninstalled. I'm not sure if installing it works yet, but I'm just glad to have it off. It was seriously annoying me, because every time I ran apt-get it would end by throwing a privoxy-related error.

Weird, but it worked... thanks.

---

