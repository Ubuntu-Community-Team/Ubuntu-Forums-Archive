---
title: "Can't delete a file unless my user and my user's group own the entire folder"
date: 2022-06-20
forum: General Help
---

### Post by bgway on 2022-06-20
[COLOR=#232629][FONT=-apple-system][FONT=inherit]I have an index.php file in /var/www/html:[/FONT]
```
myuser@ubuntu:/var/www/html$ ls -l
-rwxrwxr--  1 www-data     www-data       26 Jun 19 22:50 index.php
[FONT=inherit]
```

But I can't delete it unless I use sudo. I get permission denied. But I added myuser to the www-data group (And signed out and signed in):[/FONT]
```
myuser@ubuntu:/var/www/html$ getent group www-data
www-data:x:33:myuser,www-data

```

[FONT=inherit]And the group has all the necessary permissions on the /var/www/html:[/FONT]
> drwxrwxr-x  4 www-data www-data html/


[FONT=inherit]and index.php:[/FONT]
> -rwxrwxr-x  1 www-data www-data index.php*


[FONT=inherit]The only way I can delete this file without using sudo is if I own the entire /var/www with my user and my user's group:[/FONT]
sudo chown -R /var/www/html myuser:myuser
[FONT=inherit]I also noticed another weird behaviour, as if myuser is completely ignored: as you can see in the permissions above, all users have the execute (r-x) permissions. And if I remove the execute permission from all users, myuser's access is denied completely. So it's like his permissions in the www-data group are ignored[/FONT]
[FONT=inherit]But why? I thought that if I am inside a group, and the group has the appropriate permissions I should be able to delete it as well.[/FONT]


[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system][FONT=inherit][FONT=inherit][/FONT]
[/FONT]
[/FONT][/COLOR]

---

### Post by TheFu on 2022-06-20
I need to see the parent directory and file ownership clearly to determine the issue.  An example:
```
$ \ls -la /var/www/splat.domain34921.com
total 16
drwxr-xr-x  3 root root 4096 Sep 29  2019 .
drwxr-xr-x 16 root root 4096 Mar  5  2020 ..
-rw-r--r--  1 root root   57 Sep 29  2019 index.html
```
That's what I need to see.  Of course, the root:root owner:group isn't your goal.

The output from 'id' would be useful too.

There are some ACLs which aren't shown, that could be set.  The **getfacl** command will show those. Again, the parent directory and file ACLs matter.  For example:
```
$ getfacl index.html 
# file: index.html
# owner: root
# group: root
user::rw-
group::r--
other::r--
```
Nothing funny in that example, but there could be multiple owners or multiple groups, each with different permissions.  Complex ACLs are an abomination, but very powerful. In 25+ yrs, I've only needed to use them twice.  I see lots of newer people using ACLs because they can make a problem easier to solve in the short term, but because the ACLs aren't usually displayed, it is easy for us to forget they exist, even when we know about their existence.  Once someone put some ACLs on a file just to screw with me.  Took me 2 days to finally figure out what they'd done.

If the files are located on NFS or CIFS storage or using a non-native Linux file system, that could get in the way.  Permissions aren't always clear with CIFS mounts.

We've seen where people sharing a local directory over Samba also had their expected permissions modified.  When they disabled samba, all the normal, expected, behaviors happened again. Samba was preventing them from removing a directory that was currently being shared.

---

### Post by bgway on 2022-06-20
Thank you! Update: I found the issue: my user was not added to the www-data group even though I added it and did a sign-out and sign-in. After a reboot my user was added to the list:

id output BEFORE reboot:

```

myuser@ubuntu:/var/www$ id
uid=1000(myuser) gid=1000(myuser) groups=1000(myuser),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),122(lpadmin),134(lxd),135(sambashare)

```

id output AFTER reboot:
```

myuser@ubuntu:/var/www$ id
uid=1000(myuser) gid=1000(myuser) groups=1000(myuser),4(adm),24(cdrom),27(sudo),30(dip),33(www-data),46(plugdev),122(lpadmin),134(lxd),135(sambashare)

```

Is there any way to refresh the group list without having to reboot, as signing out and in didn't work?

---

### Post by TheFu on 2022-06-20
Rebooting isn't needed, unless there is a bug. 

Logging out and back in will force the refresh across all parts of the user's session - seeing any changes to user/group databases.  If that didn't actually work, I suspect there's something wrong with session management in the setup there.  It appears that some Gnome systems have this bug: [https://unix.stackexchange.com/questions/607629/why-are-user-groups-not-updating-when-logging-out-and-in-again](https://unix.stackexchange.com/questions/607629/why-are-user-groups-not-updating-when-logging-out-and-in-again)  Gnome is an abomination, I'm sorry to say.   Or perhaps it is a systemd problem. I cannot say and I'm not willing to test it here, since my system is setup just how I like it and I probably won't logout until the next kernel update, perhaps in 2 weeks.

Or you can use the **newgrp** command, but that is only active inside 1 bash session. Basically, it creates a subshell. None of the menus (assuming you use a desktop) or any other window/terminal would magically see the group changes.  It is possible that the systemd-logind is the issue.  Hummmm. Perhaps just forcing it to -HUP or restart would work too?
[https://ask.fedoraproject.org/t/why-dont-supplemental-groups-take-effect-without-a-reboot/11252](https://ask.fedoraproject.org/t/why-dont-supplemental-groups-take-effect-without-a-reboot/11252) has some other suggestions related to the /etc/systemd/logind.conf.d/ config.  The suggested setting probably has ramifications, which might not be desired. The logind.conf manpage has a long explaination. Think I'd rather not touch that, but I routinely have long running processes and might logout, but want those processes to continue to completion.

On a remote server, this isn't a big deal, but if you use ssh to connect into the server, just drop the connection and reconnect.  If you use ssh-keys for authentication, it is less than 1 second of effort.

I don't have any desktops running web servers, so all my web files are remotely accessed, usually through ssh methods.

---

### Post by HermanAB on 2022-06-20
Is this a web server?  Is AppArmor enforcing?

---

### Post by bgway on 2022-06-20
thank you! Btw, I did have a few bugs after installing GNOME Tweaks, I had to uninstall it, but perhaps it caused some damage? Ubuntu UX is so bad compared to Windows, and it's all the small things that add up

---

### Post by TheFu on 2022-06-20
I think the OP solved it by getting the group recognized. Seems that systemd-logind don't re-read /etc/group at each login, like the old methods did. One of the posts blames Gnome/gdm for not doing this.

I've always just used the **newgrp** method and have used gnome-whatever, beyond play stuff for a few days at a time, so I don't know the real state of Gnome breakage or even if there is any.  Gnome has been breaking lots of thing, IMHO, but that is a matter of perspective, I suppose.

It would really help the community if this is SOLVED, to use the thread tools button and mark it as SOLVED, so people looking to help don't waste their time and people looking for answers know that it was solved and probably has a solution in the thread.

The real issue was that a userid added to a group wasn't recognized after a logout/login, which has always been the way that Unix systems worked.  I'd think that the systemd guys, since they change all sorts of things anyway, would fix that too.

---

### Post by mIk3_08 on 2022-06-21
> **bgway said:**
> thank you! Btw, I did have a few bugs after installing GNOME Tweaks, I had to uninstall it, but perhaps it caused some damage? Ubuntu UX is so bad compared to Windows, and it's all the small things that add up
Is this a server release of Ubuntu Operating System right? Just want to clarify. Regards and cheers.

---

### Post by TheFu on 2022-06-21
> **bgway said:**
> thank you! Btw, I did have a few bugs after installing GNOME Tweaks, I had to uninstall it, but perhaps it caused some damage? Ubuntu UX is so bad compared to Windows, and it's all the small things that add up

Sorry. I don't know. I don't use Gnome and have never use gnome tweaks.  

My servers are headless and don't have GUIs.  GUIs make for slightly unstable servers with many more attack vectors (GUIs require lots and lots of code - LOTS and LOTS).  Some people have GUIs on servers and for a LAN-only server, I wouldn't mind that too much.  The lower stability isn't a 'crash weekly' thing - more like crash yearly. Since we reboot due to kernel patches at least 12, and probably 26 times, over a year,  the less stability may not matter at all.  For people after the highest possible uptimes and using livepatching of kernels, it would definitely matter, however.

What a good GUI is, is very much an opinion choice.  Saying you prefer Windows' GUI is like saying you prefer Blue over Green.  Or how some people prefer poodles over bulldogs. ... matters of taste.

Plus, there isn't just 1 Ubuntu GUI.  There are 50 and each can be customized in millions of ways.  I suspect most people on these forums have never seen the same GUI I use on my Ubuntu systems. It is small, light, extremely fast and extremely customizable.  There aren't any menubars and I've customized all the keyboard accel keys to launch the programs I use daily.  Anything not in those customizations is launched from an xterm window, which means **anything** can be run.

I think all the Linux DEs are bloated, even those claiming to be 'light'.  

To each their own.  Try out 15 different Linux GUIs and pick the one you find most acceptable.  If you don't look, how will you know that purple is your favorite, when you've never seen purple before?  ;)

Plus, if you dump Gnome, you'll likely leave gdm behind which may be the issue for the logout/login updating of group membership? Who knows?

---

