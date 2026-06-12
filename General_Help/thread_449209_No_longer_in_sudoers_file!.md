---
title: "No longer in sudoers file!"
date: 2007-05-20
forum: General Help
---

### Post by The Iron Curtain on 2007-05-20
Help!

I was trying to install Virtualbox and I was following (or at least trying to follow) some instructions in teh lateset Linux format magazine. It told me that I needed to add myself to the vboxusers group by doing the folowing:
> 
Add your normal user account to the 'vboxusers' group by entering
```
usermod -Gvboxusers <username>
```
as root, then, as your normal user, run /opt/VirtualBox-1.3.6/VBox.sh


This is what I did:
```
sudo usermod -Gvboxusers dfoer
```

and now this is what I get when I try to sudo:
```

dfoer@dfoer-desktop:~$ sudo nano
dfoer is not in the sudoers file.  This incident will be reported.
dfoer@dfoer-desktop:~$

```

I am the original and only user fro this system. There are no other admins on my box.

---

### Post by taurus on 2007-05-20
What's the output of this command from a terminal?

```
id
```
To use sudo, you need to belong to _both_ adm and admin.

---

### Post by The Iron Curtain on 2007-05-20
```

dfoer@dfoer-desktop:~$ id
uid=1000(dfoer) gid=1000(dfoer) groups=**4(adm)**,20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),106(lpadmin),110(scanner),**111(admin)**,502(4ster),1000(dfoer)
dfoer@dfoer-desktop:~$

```

I seem to be both adm and admin...o_?

BTW, kdesu doesn't work either.

---

### Post by bapoumba on 2007-05-20
Can you boot in recovery mode ? You'll be rootwith a # prompt.

```
# cat /etc/sudoers
```

Here is the default one:
```
# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

```
I snipped comments.

Make sure the admin group has ALL permissions.
You can edit the file with visudo:
[http://www.die.net/doc/linux/man/man5/sudoers.5.html]("http://www.die.net/doc/linux/man/man5/sudoers.5.html")

---

### Post by The Iron Curtain on 2007-05-20
I will attempt that now.

---

### Post by The Iron Curtain on 2007-06-06
I could not boot in recovery mode. It just hangs.

Since then, I checked my id. here's what I got:
```

dfoer@dfoer-desktop:~$ id
uid=1000(dfoer) gid=1000(dfoer) groups=1000(dfoer),1001(vboxusers)

```

Looks like I'm no longer an admin. :(

So, I decided to wipe the slate, but I can't back anything up. K3b can't burn a DVD, and my external hardrive is not recognised. 

Well, all I can say is that at least my box is secure. Nobody is root now!

I'll attempt recovery mode again.

---

### Post by bapoumba on 2007-06-07
> **The Iron Curtain said:**
> I could not boot in recovery mode. It just hangs.

Recovery mode is from grub menu:
```
Ubuntu, kernel 2.6.20-9-generic (recovery mode)
```
You should see something like that when booting ubuntu, on line under your default kernel line.

From recovery mode:
1- make sure admin group is set up right in the sudoers file
2- add yourself in the admin group (**adduser <your_login> admin**)
3- **reboot**

Once back on tracks, you can add yourself back to the default groups:
```
~$ groups
<your_login> adm dialout cdrom floppy audio dip video plugdev netdev lpadmin powerdev scanner admin
```
**sudo adduser <your_login> <group_to_be_added_in>**

If recovery mode really not working, you'll have to use a LiveCD.

---

