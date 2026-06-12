---
title: "owners screwed up, now no networking"
date: 2006-10-30
forum: General Help
---

### Post by kflorek on 2006-10-30
On the off-chance that I won't have to wipe everything and reinstall, here's the situation:

 Some files in my home directory (kflorek) had root-only permission after I copied them from another partition as root. So I tried to fix that using chown -R -c while in my home directory; only I used wildcards and it ended up changing file ownership above my home directory. (Before I hit ctl-C) Nearly every file and directory in many of the top directories ( usr, var, dev, media, ...) went to kflorek:kflorek. ](*,)  So then I used chown to change every directory that had signs of misplaced kflorek:kflorek back to root:root. I then fixed the owners in /dev that are not root:root by comparing them to another installation of Ubuntu Dapper. 

 Unfortunately that does not work completely. I couldn't get Internet access or network access. Since this is the only thing that has changed -ownership that is- there must be something I did not find. Anyone have any insight on what that might be? I mean, pertaining to networking. And I think I got the /dev owners OK.

---

### Post by ltmon on 2006-10-31
Are there any hints to the problem either in "dmesg" or in the file "/var/log/syslog"?

---

### Post by kflorek on 2006-10-31
OK, its fixed. Looking at those log files turned out to be enough of a clue.

 I didn't have much hope of figuring out anything by the system log. When I've looked at logs before for other unsolvable mysteries, I've found practically none of it is comprehensible to myself. For one thing, since 99% of it is normal, you need to know what is normal and what isn't, and I don't. However, examining each of hundreds of lines one by one looking for something abnormal about networking, whatever that might be, I found a near giveaway with "permissions denied."

Oct 29 21:50:07 Ubuntu-MSI dhclient: execve (/lib/dhcp3-client/call-dhclient-script, ...): Permission denied

And it gave me an actual file spec. 8) So I fired up suse and compared the owners on the two versions of Ubuntu. It is somewhat confusing if you try this from within one of the versions of Ubuntu, because some owners get changed while it is up, as I found out.

The working Ubuntu -> root:messagebus
non-working Ubuntu -> root:root

(BTW, the name suse attached to the user ID was different than in Ubuntu. In Ubuntu it's dhcp.)

 So I corrected it, and expected Ubuntu networking to work. But it didn't. OK, so what else? Well, I was sure this HAD TO be it. So there are also attributes, and on the working one "set user ID" was checked, but not on the non-working. And that did it. Of course, I had not changed any attributes, let alone this one, so something was done automagically.

 I don't know what "set user ID" does, or why it was critical here.

 It is somewhat odd to put an executable script in the /lib  directory which is almost totally library files, it seems to me. And if there are more of these kind of things strewn about, I might have missed them too.

 This makes the second time I have successfully tracked down a screw up using Ubuntu, with the help I got on a forum, which makes it totally unlike  any other linux experience I have had before. And I like it! ;)

---

### Post by ltmon on 2006-10-31
I'm pretty sure the "set user id" stuff is the "suid" flag.  This sets the given executable to always run as it were called by root - kind of like "sudo" but no password required, and the file _always_ runs as root.

```

sudo chmod +s file
sudo chmod -s file

```

sets and removes this flag.

Anyway, well done for fixing it up :)

---

### Post by kalahari875 on 2007-12-02
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/173503](https://bugs.launchpad.net/ubuntu/+bug/173503) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				This problem happened to me yesterday out of the blue--I didn't change or reconfigure anything or install any updates. It started with not being able to sudo commands, and I had to change the owners and setuid permissions on /usr/bin/sudo and /bin/su as indicated in [this post]("http://ubuntuforums.org/showthread.php?t=251358"). Then I had to fix the owners and permissions on /lib/dhcp3-client/call-dhclient-script as follows:

FROM:
```
-rwxr-xr-- root myuser
```

TO:
```
 -rwsr-xr-- root dhcp
```

By using the commands:
```

sudo chown root:dhcp /lib/dhcp3-client/call-dhclient-script
sudo chmod u+s /lib/dhcp3-client/call-dhclient/script

```

This fixed my networking, but I am perplexed why this occurred. sudo, su, and call-dhclient-script all lost the appropriate owners and permissions out of the blue. :confused: I filed a bug on Launchpad for good measure.

---

### Post by tanas on 2008-01-27
Thanks!!! It solved my problem,too! (The cause was exactly the same, after a wrong chown, I chowned everything back to root)
And thanks Itmon for your help on the "set user id" thing that I didn't get from the previous post.

kflorek: just wondering ,did you get any problems besides the dhcp? Haven't tried the all system by now, so I'm still afraid I will have to do a clean installment

---

### Post by kalahari875 on 2008-02-02
Wow, this problem was more widespread than I thought. It happened to me AGAIN yesterday. Permissions all over a number of paths were screwed up--setuid bits lost, and the group was reset to my user account instead of root or whatever it was supposed to be. It wasn't just sudo and su...

I took a few hours and looked at the permissions on the live CD and on an Ubuntu Server 7.10 installation I manage and created the attached script to fix all the permissions that got reset on my machine. To use this, unzip and copy it to your computer somewhere (like /tmp) and reboot into a recovery console. Then:

chmod +x /tmp/recoverubuntulostpermissions
./tmp/recoverubuntulostpermissions

Hope this helps, but be advised the script recursively resets group owners to root in the paths that were mangled on my installation before changing specific group owners and setuid bits back. I can't warrant that I won't mess up things I didn't have installed. However, it did work for me.

An aside: my USB disks had stopped mounting automatically when inserted, and now that problem is fixed.

---

### Post by tanas on 2008-02-03
Thanks for your script!
Just ran it on my laptop. Besides some missing files and directories (no wonder), just had this mistake on the non-existence of the postdrop group.. No clue if that's important.
And I confirm that problem with the USB, automatic mount is back (I had it since I chowned everything to root).

---

### Post by chaeron on 2008-05-15
> **kalahari875 said:**
> 
I took a few hours and looked at the permissions on the live CD and on an Ubuntu Server 7.10 installation I manage and created the attached script to fix all the permissions that got reset on my machine. To use this, unzip and copy it to your computer somewhere (like /tmp) and reboot into a recovery console. Then:

chmod +x /tmp/recoverubuntulostpermissions
./tmp/recoverubuntulostpermissions

An aside: my USB disks had stopped mounting automatically when inserted, and now that problem is fixed.

Brilliant!  Many thanks for this script.  It resolved the CD automount problem (superuser required) issues I was having on my laptop.

---

### Post by chaeron on 2008-05-25
I spoke too soon!  I did resolve the CD mounting issue, but then seemed to caused downstream problems with the Hardy Heron policy manager, where I was unable to open the Network, User/Groups and other admin applets.

Check out this thread for the problems that were caused:

[http://ubuntuforums.org/showthread.php?p=5038999&posted=1#post5038999](http://ubuntuforums.org/showthread.php?p=5038999&posted=1#post5038999)

If you see the "Config not found" errors after running this script, you'll need to restore from a backup or do a clean reinstall.

Just FYI.

---

