---
title: "chmod at startup"
date: 2019-06-07
forum: General Help
---

### Post by lragan2 on 2019-06-07
I have composed a g++ program, using "borrowed" code that facilitates taking action upon a left mouse click.  It runs great, but requires access to /dev/input/mice.   I can run the program as root by invoking sudo when I invoke the executable, but had rather not have stuff running as root.   I can provide access manually with sudo chmod 766 dev/input/mice, but each time the computer boots up, the permissions are reset.  I edited rc.local.service and appended chmod 776 /dev/input/mice at the end, but it has no effect on reboot.  I am running Kernel: 4.15.0-51-lowlatency x86_64.  I am a bit reluctant to edit sudoers with visudo to run a bash script, so surely there is a simpler way??

Thanks in advance for your advice...

---

### Post by TheFu on 2019-06-07
That chmod above isn't helpful. Also, different versions of Ubuntu support rc.local in different ways. You didn't say which you were running, so a trivial command to enable rc.local may or may not be possible.

```
$ ll /dev/input/mice 
crw-rw---- 1 root input 13, 63 Jun  2 19:29 /dev/input/mice
```
A 666 would help or just make the program a setuid-root program. You've been vague about the purpose, so perhaps you'd want to limit the userids which can run it. Use group permissions for that.  What is a g++ program?  Is that a compiled program in some language?

---

### Post by kpatz on 2019-06-08
g++ is GNU's C++ compiler.  I think he meant to say his program is written in C++.

Depending on what the program does and how much the OP wants to customize it, it could be made setuid root and either use group permissions to allow access, or some code to check who's running it and allow or disallow it to run.

It's possible to set up systemd to execute rc.local but it's multiple steps, there are tutorials online on how to enable it.

Another option is to use the @reboot option in crontab to run a script on boot.  I would assume this would run after /dev/input/mice is set up by udev, so you could put the chmod command there.

Is this a CLI or GUI program?  If it's GUI, there's probably a way to respond to a mouse click using GUI events.  I'm not real familiar with GUI programming in C++ so I don't know, but that might eliminate the need to chmod the device file in the first place.

---

### Post by lragan2 on 2019-06-08
It is CLI.  Not GUI. Will search out method to set up systemd on-line.  Yes it is C++ routine.  Thanks for the suggestion. The program as compiled responds to mouse clicks exactly as I want it to, once permissions have been set on /dev/input/mice.  I can do that each time before I launch the program, but would like to avoid that step, in that I eventually may want others to run it.   Will post result in a few days...

---

### Post by kpatz on 2019-06-08
Have you tried adding your user id to the input group?  When I look at /dev/input/mice on my 18.04 system, I see:
```
crw-rw---- 1 root input 13, 63 Jun  5 20:42 /dev/input/mice
```So, if you add yourself to the group **input**, you should have the access you need to /dev/input/mice without chmoding it at all.

Use the command **sudo adduser *yourusername *input**, replacing *yourusername *with, well, you guessed it, your user name. ;)  You'll have to log out and back in for the change to take effect.

---

### Post by lragan2 on 2019-06-10
OMG! Simple solutions are always best.  THANKS, kpatz!!

---

