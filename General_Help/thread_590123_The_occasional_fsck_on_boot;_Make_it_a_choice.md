---
title: "The occasional fsck on boot; Make it a choice?"
date: 2007-10-24
forum: General Help
---

### Post by qix on 2007-10-24
I've been with Ubuntu for almost a year now, and I really like it. Today was one of those days that Ubuntu decided to check my 500GB partition for errors. It basically means, that when I boot my computer to quickly check for mail, I have to wait ~10 minutes before I've entered the Ubuntu desktop. That is rather annoying, especially if I don't have a lot of time.

I remember that in Windows, if I was quick, I could skip the disk-check and postpone it to the next boot. Can't I get such an option in Ubuntu? Or change the configuration in a similar way, so my disk still is being checked occasionally, but at the same time giving me a little more control about when to do it?

It's one of those small things that still annoys me about Ubuntu.

---

### Post by -Zeus- on 2007-10-24
I think that by the time it forces a check, it's really needed.  I don't know how you would bypass it.

---

### Post by qix on 2007-10-24
It checks the disk once every X boots. Not if it is suspicious about something. If that would be the case, it wouldn't be a problem (as it would occur rather infrequently). But as it is now, I'm just the loser every X boot.

---

### Post by NilsE on 2007-10-24
If you want you can change the annoyance frequency.  For example the following will change the frequency to 50 boots

sudo tune2fs -c 50 /dev/sdb2   (change /dev/sdb2 to whatever yours is)

50 = number of boots between checks. Could be more could be less.

---

### Post by por100pre1 on 2007-10-24
> **-Zeus- said:**
> I think that by the time it forces a check, it's really needed.  I don't know how you would bypass it.

I agree with you. A good workaround is just to run it at a good time occasionally:

```
sudo touch /forcefsck && sudo reboot
```

---

### Post by Matakoo on 2007-10-24
> **qix said:**
> 
I remember that in Windows, if I was quick, I could skip the disk-check and postpone it to the next boot. Can't I get such an option in Ubuntu? Or change the configuration in a similar way, so my disk still is being checked occasionally, but at the same time giving me a little more control about when to do it?

Well, I don't know if there is an option for "Hit esc if you want to skip the check" but it is easy enough to re-schedule how often it happens. 

This is for ext3 only, but there are similar methods available for say reiserfs.

You need to use the terminal for this, and the command you need is called tune2fs.

The options that are of interest are -c and -i.

-c is used to alter how many times a given volume can be mounted before the automatic check is triggered, while -i is time-based.

Example:

```
sudo tune2fs -c 60 -i 30 /dev/sdb1 
```Triggers the automatic check every 60 mounts and every 30 days.

```
sudo tune2fs -c 0 -i 30 /dev/sdb1
```Turns off the number-of-mounts check but checks every 30 days.

```
sudo tune2fs -c 0 -i 0 /dev/sdb1
```Turns off the checking completely (NOT recommended). Just replace /dev/sdb1 for your partition(s), and remember that you need to do this for every partition if you have several (and preferably different values for each - or the boot-up process can get very long indeed).

There are more options, but you can look the others up using man tune2fs. Those two should be a good starting point.

Note: there is supposedly a script available somewhere that checks when you turn off the computer, and if it detects that a check is scheduled for next boot it asks if you want that or if you want to postpone it. If I could only remember where I saw it mentioned...

---

### Post by qix on 2007-10-24
I appreciate your feedback guys. But your not really addressing my problem. I need to make this problem change so it behave in a convenient way. It's ofcourse a solution to change the frequency to every 50 or 100 boots, but that is not really solving it.. It's just postponing the problem.

It's not really an option to issue the ```
sudo touch /forcefsck && sudo reboot
``` because it doesn't really make anything more convenient. On the contrary, it only makes it more troublesome to keep the system fresh and installed.

I would hope that there is a solution to this? If not, it should really be adressed in the next release, because it is one of those situations where Windows just does it better. Remember that the OS is here for you. It's not the other way around...

---

### Post by por100pre1 on 2007-10-24
> **qix said:**
> I appreciate your feedback guys. But your not really addressing my problem. I need to make this problem change so it behave in a convenient way. It's ofcourse a solution to change the frequency to every 50 or 100 boots, but that is not really solving it.. It's just postponing the problem.

It's not really an option to issue the ```
sudo touch /forcefsck && sudo reboot
``` because it doesn't really make anything more convenient. On the contrary, it only makes it more troublesome to keep the system fresh and installed.

I would hope that there is a solution to this? If not, it should really be adressed in the next release, because it is one of those situations where Windows just does it better. Remember that the OS is here for you. It's not the other way around...

Sorry to differ but, the fsck schedule is there as a file system integrity measure. If you disable it you could end up needing it badly one day.

---

### Post by -Zeus- on 2007-10-24
i think the reasoning is that all users would skip the check... and then all these complaints would occur when the data starts dying.  I think that the time of the fsck is worth the security of knowing I don't have bad blocks on my system.  Perhaps they could make it so it will try to do fsck... and if you want you can postpone to the next reboot, at which point it will be forced.

---

### Post by qix on 2007-10-24
Thanks for the reply Matakoo (didn't see it when I wrote my previous post).

Wouldn't it be simple to create a bash script to ask? You would need to turn of the normal check, but execute the bash script upon boot?
...or is it naive? I don't know of the check-on-boot is too integrated with the system (ie. needs to be checked before the stuff is mounted, or similar).

-edit-
Thanks por100pre1 and -Zeus- aswell. I see your point of view. However I'm not one of those guys that always skip, so in my situation I wouldn't abuse such an option. And speaking of which, isn't one of the pro-arguments for linux the fact that it gives you much more control of your system? That doesn't seem to be the case here.

It's not to be rude (I really appreciate your replys, it makes me understand the system better aswell), but it just sounds strange that there doesn't exist a solution...

---

### Post by Matakoo on 2007-10-24
> **qix said:**
> 
Wouldn't it be simple to create a bash script to ask? You would need to turn of the normal check, but execute the bash script upon boot?
...or is it naive? I don't know of the check-on-boot is too integrated with the system (ie. needs to be checked before the stuff is mounted, or similar).

No, it's not naive. It is quite possible - well, for someone better at shell-scripting than me that is. Okay, maybe not dead simple but it doesn't sound too difficult either since the boot-sequence wouldn't need to be altered at all. And consequently, the normal check wouldn't need to be turned off.

A brief outline of what the script need to do is:

1. Check if a error control will take occur during the next boot. A tune2fs -l /dev/sdb1 can reveal that and one can always grep for Mount count and Maximum mount count and do a comparison.
2. If it is scheduled, ask the user if that's what he/she wants; something like "One or more of your partitions is scheduled for a check next boot. Do you want that?", since I think it would be too intrusive if the script asked the same thing several times if more than one was scheduled for a check. If the answer is no, then decrease the mount count by one on the corresponding partition (i.e. use tune2fs -C current-count-minus-one). 

That's the simplified basics. Then it would need a GUI, some error-checking and stuff like that. And preferably it should run without asking the user for the password. It would be quite annoying if the sudo-dialog popped up everytime you want to reboot/turn off the computer, which the tune2fs -l approach would cause regardless if a check is needed or not.

And I don't think this would be abused. If it's asked at every reboot until you do a check, people are bound to let it check sooner or later - if only to stop being bugged about it.

---

### Post by frbe0101 on 2007-10-26
for those that don't have a sdb# file, Just search for a primary partition name under disk drives using:
```
 sudo lshw -C volume 
```
just so anyone other newbies like me know.

---

