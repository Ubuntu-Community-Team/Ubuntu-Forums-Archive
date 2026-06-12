---
title: "recovery of drive after accidental chown -R /  on only /bin, /boot, /etc, /dev"
date: 2019-10-23
forum: General Help
---

### Post by bvargo on 2019-10-23
I'm not sure which directory the command stopped on but I accidentally ```
chowned -R / 
``` and then sent SIGINT to stop.  After using a find -user -group, I identified all of the files that are owned by the following owner:group and filtered out the ones changed in the last day, removed the ones that are ok and was left with the directory listings of the following:

I've seen solutions to get sudoers back which would need to be my first step.  After that, is it possible to assume the owner:group for items in the following should be root:root?  Permissions are unchanged.

```
drwxr-xr-x   4 bvargo         media            12288 Oct 21 17:41 bin/
drwxr-xr-x   6 bvargo         media             4096 Oct 21 17:49 boot/
drwxrwxr-x   2 bvargo         media             4096 Aug  2  2016 cdrom/
-rw-------   1 bvargo         media          1101824 Mar  4  2019 core
drwx------   2 bvargo         media             4096 Aug  4  2016 Desktop/
drwxr-xr-x  22 bvargo         media             4680 Oct 22 08:59 dev/
drwxr-xr-x 211 bvargo         media            16384 Oct 22 08:58 etc/

```

I know how bad this is and if I just have to reinstall, so be it.  As of right now, the machine has not been rebooted so aside from not being able to use sudo, the computer is still running.

---

### Post by TheFu on 2019-10-23
Either restore from backups which must include the permissions, ownership, groups, and ACLs
or
reinstall.

---

### Post by bvargo on 2019-10-23
No current backup is available.
```
chown -R root:root
``` for each of those directories isn't going to do it I take it?

---

### Post by Tadaen_Sylvermane on 2019-10-23
Nope. Some things are owned by other system users or groups depending on the service. You would have to practically go through the files one by one, and there are thousands.

Technically possible, but total waste of time since a fresh install = 15-20 minutes tops. Backup configs and /home dirs if you can and away you go.

---

### Post by oldfred on 2019-10-23
While in / (root) is the owner of many files, there are a lot of other users and they must be correct for entire system to work.

fred@Bionic-Z170N:~$ id
uid=1000(fred) gid=1000(fred) groups=1000(fred),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),116(lpadmin),126(sambashare)

---

### Post by TheFu on 2019-10-23
First, learning the commands would make sense. These are incorrect/ambiguous uses:
```
chown -R root:root
chowned -R /
```

There is no substitute for having daily, automatic, versioned, "pulled", backups.  Nothing less is acceptable.  Backups have 1001 uses.  Most of those are protection against stupid user commands.  This week, I've saved hassles twice thanks to versioned backups.

---

### Post by bvargo on 2019-10-23
Thanks for the suggestion about backups.  We can always hope that someday I'll learn!

Ok, one last idea and then I'll copy a few directories and reinstall 18.04:  Can I just do a release upgrade to 19.04 or 19.10?  Would that be enough to replace the changed ownership in just those directories?  I'm assuming that it won't but...

---

### Post by TheFu on 2019-10-23
> **bvargo said:**
> Thanks for the suggestion about backups.  We can always hope that someday I'll learn!

Ok, one last idea and then I'll copy a few directories and reinstall 18.04:  Can I just do a release upgrade to 19.04 or 19.10?  Would that be enough to replace the changed ownership in just those directories?  I'm assuming that it won't but...

It isn't like you have anything to lose.  Try it.  I wouldn't hold my breath, since some files are untouched and would have incorrect permissions.  Plus, if you are so new as to make this mistake, then you really shouldn't be using non-LTS releases which have 9 months (at most) support.

---

### Post by bvargo on 2019-10-23
This is more of a knowing enough to get myself in trouble error:  My ignorance isn't in the poor choice of using chown that way but rather in my shell scripting.  I should have chained the sudo chown to the previous cd, i.e., cd /music/folder && chown ... .  You may therefore question the wisdom of having commands like that in scripts!

---

### Post by TheFu on 2019-10-23
> **bvargo said:**
> This is more of a knowing enough to get myself in trouble error:  My ignorance isn't in the poor choice of using chown that way but rather in my shell scripting.  I should have chained the sudo chown to the previous cd, i.e., cd /music/folder && chown ... .  You may therefore question the wisdom of having commands like that in scripts!

Well, as a Unix admin mentor of mine 20+ yrs ago said, "never assume the CWD if you don't need to."

Meaning, if a command accepts a path, USE IT!  Especially in scripts.
```
$ sudo chown -R xyz:abc /music/folder
```

If that path doesn't exist, no harm done.  If I let the command assume a PWD, **ouch**.

The only time a script should expect any directory to actually exist is when the script creates the directory AND validates it exists before any use.  It is usually just easier to put the paths in the commands.  Safer too. 

I've made a few other whoppers over the decades and have seen many, many, more from others.   We all make these sorts of mistakes.  Hopefully, only once.

---

### Post by bvargo on 2019-10-23
Live and learn...  I'm fairly ok with this actually; I have other problems that have accumulated.  I plan on taking a good look at this next week:  [https://askubuntu.com/questions/917562/backup-linux-configuration-scripts-and-documents-to-gmail/922493#922493](https://askubuntu.com/questions/917562/backup-linux-configuration-scripts-and-documents-to-gmail/922493#922493)

---

### Post by TheFu on 2019-10-23
Please don't use tar for system backups.  Please.  Don't.
There are so many easier, better, faster, more efficient, tools, today.  tar is like ZIP.  Anything over 250MB in size shouldn't be in a tar file, unless you are doing a sneaker-net.

---

### Post by bvargo on 2019-10-24
> **TheFu said:**
> Please don't use tar for system backups. Please. Don't.
There are so many easier, better, faster, more efficient, tools, today. tar is like ZIP. Anything over 250MB in size shouldn't be in a tar file, unless you are doing a sneaker-net.

For instance?  It needs to be something fairly easy to follow and move to free off-site storage as in the script I linked to.

At any rate, I went ahead and rebooted in order to fix ownership of sudoers but missed GRUB and ended up logging in.  Since the problem was localized to the subject directories, I went in and changed everything back to root:root for /bin, /boot, cdrom/ and /etc (including /etc/sudoers).  From there I compared what was in those directories on my laptop (eg., find . -not -user root ; find . -not -group root) and they proved to be a very manageable group of ownerships to change:

```
/etc $ sudo find . -not -user root
./openvpn/config.ovpn
./openvpn/client.conf
./mpd.conf
./opt/chrome/native-messaging-hosts/...
./chromium/policies/managed/lastpass_policy.json
./chromium/native-messaging-hosts/...
./xrdp/rsakeys.ini

/etc $ sudo find . -not -group root
./cups
./cups/subscriptions.conf.O
./cups/printers.conf
./cups/classes.conf.O
./cups/ppd
./cups/ppd/HP_Officejet_Pro_X476dw_MFP_35BFC7_.ppd.O
./cups/ppd/HP-Officejet-Pro-8600-2.ppd
./cups/ppd/HP_Officejet_Pro_X476dw_MFP_35BFC7_.ppd
./cups/ppd/Officejet_Pro_8600_555929_.ppd.O
./cups/ppd/Dell-B1160w-Mono-Laser-Printer.ppd
./cups/ppd/Officejet_Pro_8600_555929_.ppd
./cups/ppd/B1160W.ppd
./cups/ppd/B1160W.ppd.O
./cups/ppd/Dell-B1160w-Mono-Laser-Printer.ppd.O
./cups/ppd/HP-Officejet-Pro-8600-2.ppd.O
./cups/ssl
./cups/classes.conf
./cups/printers.conf.O
./cups/subscriptions.conf
./ssl/private
./ssl/private/...
./openvpn/config.ovpn
./openvpn/client.conf
./chatscripts
./chatscripts/provider
./mpd.conf
./shadow-
./opt/chrome/native-messaging-hosts/...
./shadow
./gshadow
./chromium/policies/managed/...
./chromium/native-messaging-hosts/...
./gshadow-
./ppp/peers
./ppp/peers/provider


```

I'm fairly sure I will have intermittent problems (I already fixed one with Icecast2), but so far it is proving manageable.

---

