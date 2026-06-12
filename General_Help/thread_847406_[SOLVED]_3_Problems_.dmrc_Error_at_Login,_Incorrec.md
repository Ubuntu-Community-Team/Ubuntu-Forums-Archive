---
title: "[SOLVED] 3 Problems: .dmrc Error at Login, Incorrect Minimization, and Essential Proc"
date: 2008-07-02
forum: General Help
---

### Post by wkdude18 on 2008-07-02
I have many problems so I'll make them quick

1. When I login, I get an error screen saying there is something wrong with my .dmrc file, and I can't save sessions and default languages or seomething. It says the problem must be that either the ownership is wrong, or it should have a "signature? (I forget)" of 644. I looked at the files permissions, it;s hidden though, I'm the owner. So I guess I need to go to the Terminal and chmod .dmrc 644 or something like that. But when I ls in my home directory where the file is, It doesn't show up? What is the terminal command for unhiding files, and would chmod 644 .dmrc be the correct command to change the permissions?

2. When I click the minimize button, instead of just shrinking to a taskbar, the entire window disappears, and I cannot find the window. It behaves almost exactly the same as te close button except the a black empty rectangle quickly descends into and shrinks into the lower right-hand corner.

3. I'm trying to decrease the amount of services that run automatically to speed up boot times and allow my computer to run faster. Do I need two Power Managements (acpid and apmd, I'm using a laptop) two Computer activity loggers (klogd and sysklogd) and two action schedulers (anachron and atd). Also do I need avahi and hotkey-setup?

Thanks in advance :)

---

### Post by drs305 on 2008-07-02
> **wkdude18 said:**
> I have many problems so I'll make them quick

1. When I login, I get an error screen saying there is something wrong with my .dmrc file, and I can't save sessions and default languages or seomething. It says the problem must be that either the ownership is wrong, or it should have a "signature? (I forget)" of 644. I looked at the files permissions, it;s hidden though, I'm the owner. So I guess I need to go to the Terminal and chmod .dmrc 644 or something like that. But when I ls in my home directory where the file is, It doesn't show up? What is the terminal command for unhiding files, and would chmod 644 .dmrc be the correct command to change the permissions?

You have some files with incorrect permissions. To reset them log on as the user with the problem and run the following commands. If you can't sudo or can't log on at all, you will have to boot from grub to the recovery mode to a command line to run them:

This will change permissions and then reboot. Substitute your second user's username (log-on name) if it is not "*newuser*". Only files owned by the second user will be changed, including that user's home and that user's /home/.dmrc file:
```

sudo chmod 644 /home/*newuser*/.dmrc
sudo chown *newuser*: /home/*newuser*/.dmrc
sudo chmod 755 /home/*newuser*
sudo chown *newuser*: /home/*newuser*
sudo shutdown -r now

```

---

### Post by wkdude18 on 2008-07-02
Ok, well that worked like a charm! Thank you for clearing up the chown and chmod commands for me!:) I also appreciate you teaching me the reboot command! Anyways, I have come to the realization of what the second problem is, I did not have the open window applet on the GNOME menu bar, I remember now deleting it not realizing what it was. That is my new record for stupidest problem of all time!!! I will make a new post for the third question.

Sorry about the incorrect title.

UPDATE:If I have this right, anacron schedules long-term events, atd shorter ones, sysklogd monitors messages from system and makes a log, klogd does that or something similar from the kernel, (although I'm not sure is klogd is a part of sysklogd, but I doubt it is double-running),acpid is the normal power management, apmd is more advanced tends to be more for laptops. Hotkeys-setup is probably (or obviously) for hotkeys, which I do not use much.

---

