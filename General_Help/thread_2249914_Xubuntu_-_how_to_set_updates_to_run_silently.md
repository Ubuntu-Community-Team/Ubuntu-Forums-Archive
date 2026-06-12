---
title: "Xubuntu - how to set updates to run silently"
date: 2014-10-25
forum: General Help
---

### Post by neilajarn on 2014-10-25
How to set Xubuntu updates to run silently ? i.e. no prompt for password and set to run in the background.

---

### Post by ian-weisser on 2014-10-25
Look in /etc/apt/apt.conf.d :

```
$ ls /etc/apt/apt.conf.d/
00aptitude            10periodic      20listchanges.disabled
00trustcdrom          15update-stamp  50unattended-upgrades
01autoremove          20archive       70debconf
01autoremove-kernels  20changelog     99update-notifier
01-vendor-ubuntu      20dbus
```

Change 50unattended-upgrades to include the -updates repository. Simply uncomment the line.
Do not enable -proposed. That's meant for testing before it reaches -updates
Do not enable -backports. Those do not receive security updates.

You may need to edit a bit more to capture unattended upgrades from non-Ubuntu repositories (google, etc). Those I prefer to do manually anyway.

Updates will run with cron.daily jobs. If daily is too frequent, edit 10periodic.

Documentation on apt using cron is -strangely enough- in the actual apt cronjob script: /etc/cron.daily/apt

[EDIT] Upon reflection, I advise against this change for users who lack the skills to change these files comfortably. It would be easy for a typo in the config file to break the system in a way that would be very difficult to track down.

---

### Post by neilajarn on 2014-10-26
Thanks for the reply. I am not accustomed to using the command prompt so am accessing this through file manager but its not letting me edit the file......

---

### Post by mikodo on 2014-10-26
> **neilajarn said:**
> Thanks for the reply. I am not accustomed to using the command prompt so am accessing this through file manager but its not letting me edit the file......

I'll probably get "smacked" for this. I don't know if "pkexec" is the default yet, or what?

Try:

```
sudo apt-get install gksu
```

Then, in terminal:

```
gksu thunar
```

Then, navigate to where you want to edit.

Be careful with editing with gksu because,  you are in essence editing things as root and can make a mess of your system, if not careful. Be sure to close the terminal after using it.

---

### Post by vasa1 on 2014-10-26
> **neilajarn said:**
> How to set Xubuntu updates to run silently ? i.e. no prompt for password and set to run in the background.How important is this for you? I feel you could break things trying to do this.

---

### Post by ian-weisser on 2014-10-26
No smackdown.

However, I recommend against  this particular customization (well, really any customization) to users that do not understand exactly what they are customizing.

Apt, the Debian/Ubuntu package manager, is _not_ a flexible, robust, user-friendly, customizable application that sits on top of your stable system.
It's a core element of that stability, and screwing it up with a typo in the wrong config file can expose you to known vunerabilities, break your system beyond easy repair, and perhaps even cause data loss. And there's no 'Reset' button.

It's certainly worth exploring the possibilities and playing with it (I did, I do, I love it).
But you must have the skills to do it safely.
That includes understanding how to safely read and edit shell scripts, cron jobs, file permissions, file ownerships, and root-owned text config files.

Analogy: It's not hard to disassemble and reassemble the motor in your car...once you already know how to use the tools and have looked over the manual. That disassembly may not be the job you want to learn those skills during, especially if you want to drive someplace later.

[EDIT]: Also, remember to document your customization in your notes (er, you *do *keep notes?) so you can undo the change someday.

---

### Post by HermanAB on 2014-10-27
It may not be a good idea to run updates silently.  Once in a while, there are issues with the updates and then you will have no idea why something is broken.  The 'But it worked yesterday!?' lament.

---

### Post by neilajarn on 2014-10-27
Thanks for the tips. I've worked with Microsoft products for almost 20 years and am quite comfort with them but these days enjoy learning Linux as it seems more robust and a good alternative to Windows especially now support for XP has stopped. Don't want to get out of my depth so perhaps its best to leave the updates as they are for now, was never that keen on using DOS let alone UNIX commands.

The main reason I asked for the silent updates is for a few old computers in my friends internet cafe which I've installed with Xubuntu. They work very well and are popular with customers but there are just a couple of things that we don't like: one was the updates and the other is a need for a script to delete temporary internet files and and downloads at the end of every day.

---

### Post by ian-weisser on 2014-10-27
> **neilajarn said:**
> The main reason I asked for the silent updates is for a few old computers in my friends internet cafe which I've installed with Xubuntu. They work very well and are popular with customers but there are just a couple of things that we don't like: one was the updates and the other is a need for a script to delete temporary internet files and and downloads at the end of every day.

This is a great use case for testing the setup or customization in a VM.
As a bonus, it's a good excuse to play with a VM for a couple days.

I wasn't trying to say "I think this is too hard for you"; I don't think that at all.
I have mucked with those settings without getting burned. Quite happy with completely automatic updates.
I didn't want to give future searchers who happen upon this thread the idea that it's safe to try without basic precautions (like a backup and notes).

---

### Post by neilajarn on 2014-10-27
If the updates are set to run silently and one of them fails - what's the simplest way to resolve this ? Will the update automatically be re-run the next time or does it need to be installed manually ?

---

### Post by ian-weisser on 2014-10-27
It depends upon the type of failure.

If apt cannot get a connection, it will simply try again the next day. Every day. It won't tell you that it failed.

If apt downloads a package that cannot be installed (it's corrupt or incomplete), it will fail silently.
Then it will retry (and silently fail again) each day. Apt won't send you an e-mail telling you that it failed.
You will discover the problem days/weeks/months later when you try to install/uninstall something manually and it fails.

Apt fails silently because it's designed to be used interactively. Most users seem happy with Software Updater, so nobody has written something better for automated use.

---

