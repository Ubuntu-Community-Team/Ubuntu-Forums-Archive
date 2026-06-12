---
title: "Computer sometimes hangs on shutdown"
date: 2007-07-10
forum: General Help
---

### Post by Corfy on 2007-07-10
I am having an occasional problem when shutting down my computer. The computer will occasionally get part-way through the shutdown process and just hang. I don't know enough about Linux yet  to know where to look for log settings or error messages.

I am running Kubuntu 7.04, and I shut down via the Logout on the "start" menu (I saw some other threads with people having problem when shutting down via the power button, but I only use the power button to force it to shutdown when the regular shutdown doesn't work). I have a Dell D620 Latitude laptop that I am dual-booting with WinXP Pro.

Most of the time it works fine, but every now and then (about once a week), about the time the Kubuntu logo would normally be on the screen with the status bar showing shutdown progress, I get a blank screen and nothing happens, and nothing continues to happen. The first time I noticed this was when I saw my laptop monitor was still on the next morning (9 hours later). I had to force it to shut down by holding in the power button for five seconds. The next time I saw it, it was an hour and a half after I told it to shut down. I have since learned to sit with it as it shuts down to make sure it shuts down. Fortunately, when it works, it shuts down in less than a minute, so I don't have to wait around forever.

And then on the next boot after a failed shutdown, I get filesystem errors on startup, presumably because it wasn't shut down properly. I had to reinstall K/Ubuntu on that laptop once already because the filesystem got so corrupted it didn't work right anymore. When I reinstalled, I used Reiserfs as my file system because I thought the journaling would help, and it has helped the restart afterwards, but not the shutdown process.

If there is a log I can look at or something, or if you have any ideas what might be causing this, I would appreciate any help I can get. It is getting rather annoying.

---

### Post by loserboy on 2007-07-10
I dunno if this is relevent but I saw this

[http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/Hang_on_reboot](http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/Hang_on_reboot)

---

