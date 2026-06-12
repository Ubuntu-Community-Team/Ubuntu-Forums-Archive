---
title: "apt-get upgrade - when to reboot?"
date: 2006-10-27
forum: General Help
---

### Post by boncey on 2006-10-27
Hi, I am building a server that runs Xubuntu 6.06.
It will be administered remotely so has no X Windows.

I have set up cron to run the following command weekly to let me know if there are any new packages.
/usr/bin/apt-get -s -u upgrade
This emails me a list of packages that have changed.

The theory is that when I see some new packages are available I run 'apt-get upgrade' via a remote shell (I prefer to do things this way than to have the machine update itself via cron so I can see what's going on).

The only problem being, how can I tell if any of those package changes require me to reboot.
I am running Ubuntu on my desktop too and after doing an update there's an icon that tells me I need to reboot - is there a terminal equivalent of this?

I'd rather not reboot after every apt-get if I can help it.

Thanks in advance for any help.
Darren.

---

### Post by tzulberti on 2006-10-27
It is quite rare to reboot after apt-get upgrade... You should only reboot if it has only installed a new kernel... all the other programs should be stopped and restarted...

---

### Post by boncey on 2006-10-29
Hi thanks for answering, that makes a lot of sense.

---

### Post by boncey on 2006-11-28
Hi, I'm not finding this theory to be borne out in practice.

Today my home install of Ubuntu ran an update then requested that I reboot - I checked and there were no kernel updates.

If I now run the update on my Xubuntu server how will I know if I need to reboot or not?
I don't know what particular package triggered the reboot - it may be something specific to gnome that won't affect my server.

My server is a live server that is in use, I can't reboot it just on the off chance every time I run an update - I need to *know*.

Does anyone have any insight into how I can find out what triggers the "Reboot required" icon please?

Thanks in advance, Darren.

---

### Post by bmillsap on 2006-11-28
After reading this thread, I guess I have the same question.  I have gnome installed, but rarely log into it, so I did this morning and I have the "restart required" icon.  I probably haven't logged into the gui for at least a couple weeks, so I have no idea what update triggered the message, but I don't recall that upgrading using apt-get at a command line ever produces any kind of message that a restart is required.

---

### Post by CaptSaltyJack on 2008-02-28
I'd like to revive this thread.  I'm curious when the system needs to reboot, because if you're logged into the Gnome interface, it just prompts you to restart.  But if you're ssh'd in and do apt-get upgrade, how can you tell if you need to reboot?

---

### Post by g474h4d on 2008-04-02
According to this page...
[http://linux.derkeiler.com/Mailing-Lists/Ubuntu/2007-04/msg01493.html]("http://linux.derkeiler.com/Mailing-Lists/Ubuntu/2007-04/msg01493.html")
... */usr/share/update-notifier/notify-reboot-required* is executed - if it exists - whenever a reboot is necessary. This short script essentially creates */var/run/reboot-required* but might not be present on a server system with a GUI.

I hadn't the opportunity to validate this yet.

---

### Post by jonabyte on 2008-04-02
maybe the xwindow needs rebooting when updating packages in gnome/kde.

for the server version, I am pretty sure you just need to reboot when a kernel update is done.

what I do whenever an update is done, is to make sure the critical programs are still running (samba, apache, etc).

---

### Post by siouzi on 2008-07-21
Systems with GUI have the file /var/run/reboot-required when a reboot is required. Systems without GUI, i.e. servers, do not have the file. So **when do you have to reboot a server?**

- Only when then kernel is upgraded?
- Upgrade kernel from 2.6.XX to 2.6.YY, reboot yes, of course!
- Upgrade kernel from 2.6.22-14 to 2.6.22-15, reboot... hmm yes?
- How about upgrade from 2.6.22-15.XX to 2.6.22-15.YY, reboot... maybe no?

Also why doesn't Ubuntu's aptitude tell when to reboot? I remember on an old Debian system the aptitude always made it very clear when to reboot with a big message!

---

