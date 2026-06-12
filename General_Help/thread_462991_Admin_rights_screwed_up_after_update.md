---
title: "Admin rights screwed up after update"
date: 2007-06-03
forum: General Help
---

### Post by jamyskis on 2007-06-03
Hi all,

I've just come back from a weekend away to discover a couple of updates waiting for me on my PC. Everything was working fine, until I decided to install the updates. After that, I couldn't do anything admin related. I tried to add a user, the window opened, but none of the existing users could be seen. Although I was a little confused, I tried to add her anyway, and the window just disappeared. It then refused to give me access to any of the admin apps.

When I rebooted to see if that would solve the problem, I discovered that my GDM login screen was screwed up (I have multiple instances of the same user in the list) and when I logged in, I found that all my admin rights were gone. In fact, all of the users on this computer, three of whom were admins, were normal desktop users and there wasn't a single admin among them.

I tried going through sudo, no dice - apparently I wasn't in the sudoers file. No problem, I thought. I went into recovery mode, typed sudo myusername admin, and went back into normal mode. Sure enough, my admin menus were there again, and my sudo was working, but when I went into the Users and Groups app, again there were no users and again I lost my admin rights. I also don't have any sound (I do in recovery mode if I start the X server as root) and it seems as though all of group memberships are being arbitrarily erased.

Does anyone know what this could be linked with, and if anyone else is suffering the same problem?

Thanks,
J

---

### Post by jamyskis on 2007-06-03
Anyone? It's quite desperate...my Ubuntu box is as good as useless at the moment.

---

### Post by CyberRaven on 2007-06-03
Same problem here, running Xubuntu 7.04 on a Dell D300XT... Lost sudo privileges after updating. Thx in advance for any tips.

/CyberRaven

---

### Post by zvacet on 2007-06-03
Boot in recovery mode and type

```
adduser username admin
```

Of course username is your username

---

### Post by CyberRaven on 2007-06-03
^^ tried that, but the admin group had somehow disappeared..! (To check, use
```
root@console: cat /etc/groups
```

I worked it out by booting into recovery, and
```
root@console: groupadd admin
```
then
```
root@console: usermod -a -G admin username
```
where username of course is your regular user name.

Worked for me when doing normal boot again - hopefully helpful to others as well:-)

/CyberRaven

---

### Post by jamyskis on 2007-06-04
> **CyberRaven said:**
> ^^ tried that, but the admin group had somehow disappeared..! (To check, use
```
root@console: cat /etc/groups
```

I worked it out by booting into recovery, and
```
root@console: groupadd admin
```
then
```
root@console: usermod -a -G admin username
```
where username of course is your regular user name.

Worked for me when doing normal boot again - hopefully helpful to others as well:-)

/CyberRaven


I'd done this already, and it works fine until you try to perform something in the Users and Groups applet. You'll find that none of the users show up if you have the same problem as me. I found it interesting that I didn't have /etc/groups but I did have /etc/group and /etc/group-, so I tried creating a symbolic link to /etc/group with /etc/groups - no joy though. I still have no sound, and I now have to use sudo to start my internet connection because I'm apparently no long a member of the dip group. I tried usermod -a -G dip dlecount but that didn't do a thing.

Somebody really screwed up with the updates.

EDIT: Right, after logging out and in again with the groups dip and audio added, the internet works fine (not tried it after a reboot yet) and the audio begins to play before it cuts out unceremoniously and announces that no devices could be found.

EDIT 2: Sorry, the audio does work now, but the volume control applet doesn't.

---

### Post by CyberRaven on 2007-06-04
Yep, something is definitively messed up...  Haven't tried sound and user management much yet, but it seems locate is affected as well;
```
user@box:~$ sudo locate file
locate: warning: Could not find the group: slocate in the /etc/group file.
locate: fatal error: This is a result of the group missing or a corrupted group file.

```

By the way, I don't have /etc/groups neither, only /etc/group and /etc/group- ;
```
user@box:~$ ls -la /etc/ | grep group
-rw-r--r--   1 root   test      398 2007-06-04 00:04 group
-rw-------   1 root   test      384 2007-06-04 00:04 group-

```

And why they belong to the group "test", I have no idea... But it's weird, I'll second that.

---

### Post by jamyskis on 2007-06-04
That is weird. From my side the volume applet has suddenly started working again, but the issue with the users and groups applet is still there. Locate works fine with me. I'm going to ask around in IRC and see if anyone has any answers there. I'll be back (to be said in strong Arnie accent)

---

### Post by jamyskis on 2007-06-07
Right, my question was being outright ignored in IRC and nobody seems to be able to find an answer in here. Can't anyone even suggest what might be going wrong?

---

### Post by jamyskis on 2007-06-09
Bump *sigh*

---

### Post by CyberRaven on 2007-06-11
Hi again, jamyskis and all,

I really appreciate your efforts to solve this, and sorry I coundn't contribute more. Last night I finally got so tired of trying that I went to the last resort; reinstallation. (As a former Wintendo user I tend to think of that as a normal way of solving things ;) )

Well, anyhow, I have now reinstalled Xubuntu 7.04 on my laptop, and made all the appropriate updates, and admin rights still seem to work normally(!). That means, I'm not able to reproduce the problem i experienced last time (as described above). I've added a lot of users, and done other super user stuff, and still everything seems fine. So that might be one (maybe too crude) solution...

I'll keep you posted if I stumble upon something of interest!

Sorry my lack of patience, and all the best
/CyberRaven

---

### Post by jamyskis on 2007-06-11
Hi Cyberraven,

I can understand your solution to this problem. I must admit that i've been quite disheartened by the lack of willingness or ability by anyone to respond to this or most of the other remotely technical problems that I've posted to this board. Some will doubtless say that if I want proper support I should buy a support package but the kind of support offer is quite frankly out of my price range. I may take the opportunity to switch to Debian, as the support community seems to be better equipped to handle more technical issues.

---

### Post by jamyskis on 2007-06-30
Right, well, apparently after an another update the problem has automatically resolved itself, although root seems to be now included in the users list (not really an issue).

---

