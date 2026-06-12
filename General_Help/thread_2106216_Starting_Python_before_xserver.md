---
title: "Starting Python before xserver"
date: 2013-01-18
forum: General Help
---

### Post by archarank on 2013-01-18
I have been an avid Ubuntu user since 2010, and I have not been able to  figure this one out: After my BIOS splash, there is just a black screen.  Then, after 12 seconds, my login screen pops up and all is well.  However, I was wondering if there was any way to start the Python-thingy  before Xorg or even when the machine is first turned on. Help is most  appreciated.

---

### Post by archarank on 2013-01-18
I have been an avid Ubuntu user since 2010, and I have not been able to  figure this one out: After my BIOS splash, there is just a black screen.  Then, after 12 seconds, my login screen pops up and all is well.  However, I was wondering if there was any way to start the Python-thingy  before Xorg or even when the machine is first turned on. Help is most  appreciated.

---

### Post by coffeecat on 2013-01-18
@archarank, I have moved your two identical posts to their own thread and given the thread what I hope is a suitable title. You posted to threads that had nothing to do with your question.

Please do not post the same thing in different places as this dilutes community effort and please do not hijack other people's threads.

---

### Post by Cheesehead on 2013-01-18
You can start anything you wish at system startup, and there are several ways to do it. The answer depends upon what you wish to start, why you wish to start it, and what services it depends on to work properly.

Generally, best practice for a system-level daemon that needs to run all the time (like ntp) is to use Upstart. System level services that don't need to run all the time, or root scripts, should usually be started by cron or dbus or Upstart.

User-level scripts and applications have even more options for start-upon-login, or start-after-boot.

---

