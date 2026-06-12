---
title: "How to set Ubuntu to Suspend on Logout?"
date: 2015-06-04
forum: General Help
---

### Post by DanielWEWO on 2015-06-04
Hey guys! When I ssh into my desktop (I'm the only person using it, no need to worry about other users) I'd like to be able to logout from the session, and then immediately have the computer suspend once I've logged out. Is there an easy way to do this? A way to run a script that doesn't halt after I logout? Also, don't worry about me being able to log back in, I've got wake on LAN already set up.

Thanks for the help guys =]

---

### Post by TheFu on 2015-06-04
echo "sudo pm-suspend" | at now + 1 min

It won't be immediate, but 1 min later isn't so bad?
Or you could just setup the lock screen to suspend.

Be certain to setup the pm-suspend program in the sudoers file to not require your password.

---

### Post by DanielWEWO on 2015-06-09
Well, that doesn't work if I logout after typing that command. It's all right, I'll just have to deal with having to kill the last session I had when I SSHd in and suspended remotely.

---

### Post by TheFu on 2015-06-09
Have you tried not logging out? But that shouldn't really matter. 

Does logout kill all user-owned processes, or only those connected to the session? A detached process shouldn't be killed. It doesn't here, but I don't really logout.

Perhaps making it 2 min delay would be enough time for the logout to complete?  The "at" command doesn't work to second resolution, but to minutes.  If you say "now + 1 min" and it is 1:00:50 am, in 10 sec, the trigger will happen. "now + 2 min" would be 1 min, 10 sec later. Does that make sense? That is a limitation of cron.  You can add in a 30 sec delay in the command using sleep, if you like. That should allow time for the logout process to finish.

Or another option, is to make it a cron-job that looks for the existence of a file in your HOME every 5 min ... if it exists, suspend. If not, don't.  Of course, if HOME directory encryption is enabled, that won't work (logging out removes the encrypted mount for HOME), but if you have full drive encryption, it will work.

There are many different ways to solve this. That's all I'm getting at.

I really like suspending and coming back later with all the windows and programs where I left them. It is more convenient.

Of course, if I'm on-the-move, I completely shutdown any laptops/netbooks for travel. From a security perspective, suspend doesn't offer enough protection for encrypted partitions/mounts.

---

