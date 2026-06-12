---
title: "can't click on next button on installation"
date: 2008-04-16
forum: General Help
---

### Post by drmoore1 on 2008-04-16
I have found the answer to this many time in the guide but it does not seem to be there anymore or I am just blind today. What is the code for this? I remember it is 
ubiquity something, can't remember. Thanks

---

### Post by ago on 2008-04-16
I removed it from the guide since it was fixed (or at least should have). Please use the latest desktop daily ISO.

---

### Post by drmoore1 on 2008-04-16
I did and I still have the same issue.

---

### Post by ago on 2008-04-16
Then I will need full logs and preseed.cfg

Plese uninstall/reinstall
before rebooting copy c:\ubuntu\install\custom-installation\preseed.cfg
select verbose mode by pressing esc after choosing Ubuntu at reboot

When you see the migration-assistant dialog, hit CTRL+ALT+F2 and run

sudo sh /custom-installation/hooks/failure-command.sh

Then pls attach preseed.cfg and c:\ubuntu\installation-logs.zip here:

[https://bugs.launchpad.net/wubi/+bug/195905](https://bugs.launchpad.net/wubi/+bug/195905)

---

### Post by ago on 2008-04-16
What is your user name in Windows? Any strange char/whitespace in there?

---

### Post by drmoore1 on 2008-04-16
Alright, I reinstalled it and ran it in verbose, but before I went to the terminal, the dialogue was working correctly.I must have messed something up on the first install, because this time I noticed the dialogue box was different.. aka asking who I am and asking for a password... Do you still need to file the bug report?

---

### Post by evan d on 2008-04-16
You shouldn't see any question dialogs in the second phase of the install (the first phase being in Windows).  If you do, it's a bug and the full logs from the live environment would be much appreciated.

---

### Post by jimgeiser on 2008-04-19
> **ago said:**
> Then I will need full logs and preseed.cfg

Plese uninstall/reinstall
before rebooting copy c:\ubuntu\install\custom-installation\preseed.cfg
select verbose mode by pressing esc after choosing Ubuntu at reboot

When you see the migration-assistant dialog, hit CTRL+ALT+F2 and run

sudo sh /custom-installation/hooks/failure-command.sh

Then pls attach preseed.cfg and c:\ubuntu\installation-logs.zip here:

[https://bugs.launchpad.net/wubi/+bug/195905](https://bugs.launchpad.net/wubi/+bug/195905)

This did not work for me. Every time I get to the end of the Terminal program It reboots and goes into the Installation checking mode and ends up at the Migrating page without a "Forward" button. 
If I cancel and it finishes out into the live session user version. On that desktop it shows my USB drive (where I want it to be installed), a folder called "Examples" with a lock beside it, and shortcut marked "install". If I run this it goes to Guided partition and stops with a windoe with ? as title and a stop sign and OK as a choice. I hit OK and it goes away and I am at "Prepare Partitions" window with 1 choice "/dev/loop2" and Forward button is okay, but if I hit it I end up where I was without the window changing. If I high lite the /dev/loop2 and hit change it switches to "/dev/sda" Does same and now it will not let me change the "/dev/sda"

---

### Post by ago on 2008-04-20
I need to know your windows username.
Also see last comment in 
[https://bugs.launchpad.net/wubi/+bug/195905](https://bugs.launchpad.net/wubi/+bug/195905)

Please attach all required info ASAP, or it will be impossible to fix this before release

---

