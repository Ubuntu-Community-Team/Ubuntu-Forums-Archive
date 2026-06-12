---
title: "help for a noob!"
date: 2021-07-20
forum: General Help
---

### Post by torz2 on 2021-07-20
Hey guys,

very new at trying to trouble shoot when issues happen on ubuntu so hoping someone is willing to give me a hand to trouble shoot my current problem....

recently updated a bunch of packages from CLI with apt, ever since the machine seems to become unresponsive within 30minutes or so of being turned on.
I say seems to become unresponsive because I can no longer putty into it & if I'm on the machine itself pressing keys and mouse buttons wont get the screen to turn on to login.


How do I go about finding out which package is causing this?


many thanks in advance!!!!

---

### Post by TheFu on 2021-07-20
Check the system log files.

---

### Post by ActionParsnip on 2021-07-20
If you boot an older kernel is it OK?

---

### Post by torz2 on 2021-07-20
wouldn't even have a clue how to do that :)

---

### Post by deadflowr on 2021-07-20
When you reboot your machine is there a boot menu for Ubuntu? (Usually purple in color)
You can select an older kernel here.

The boot menu top entry is the current entry that will be booted into,
but under is usually an entry marked something like Advanced Options.

This is a submenu and within it will list the current kernel as well as any older kernels and recovery mode options with the kernel version strings.
Typically you can select the second non-recovery mode entry,
you can tell which is older by the kernel number string.

As an example, if the top entry has something like 5.11.0-12 and the next down has 5.11.0-11,
then the 5.11.0-11 is the older kernel. Just press enter to select it.


Hope it helps or makes sense.

---

### Post by torz2 on 2021-07-20
yeah thank you :)

So it is ubuntu mate if that makes a difference, from memory all I see while booting is the usual raid hardware initialization, additional sata cards etc and first thing that is OS related is just the mate logo / loading screen... do i have to hit a key just prior to this to get to the menu you are talking about? similar to the old f8 for windows safe mode type idea?


Also an alternative would be if there is a simple way to reverse all packages back to what they were prior to updates and I just update one at a time until i find the offending one... most of what i've found on google for this though is really manual :(

---

### Post by deadflowr on 2021-07-20
> do i have to hit a key just prior to this to get to the menu you are talking about? similar to the old f8 for windows safe mode type idea?
Sometimes it can boot directly and bypass the menu all together, so to get the menu you need to tap the ESC key right around when the machine's statrtup logo(?) goes black.  
But what I typically do is rapidly tap the ESC key and hope I did it at the right time for the menu to appear.

Since this is mate the menu might be green.

I hope that makes sense.


Edit: I forgot, if it's an older machine it might use the Shift key instead of the ESC key.

---

### Post by TheFu on 2021-07-20
> **torz2 said:**
>  Also an alternative would be if there is a simple way to reverse all packages back to what they were prior to updates and I just update one at a time until i find the offending one... most of what i've found on google for this though is really manual :(

There's a very simple way to revert packages.  It is by restoring from the backup you created.  Unix people generally don't make specialized tools when the common solution that everyone should have will provide the needed capability.  

Do you have sufficient backups where you can restore the OS in 30-45 minutes?  If not, might I recommend that as your next task?
If the backup solution being used doesn't allow moving back to a specific point in time, might I suggest that a better backup solution is needed?


BTW, we can't tell who you are replying to unless you quote a little of that person's post. It is like being in a crowd and yelling for "Mike" - 30 people will look and the person you seek is probably in the toilet. ;)

---

### Post by dragonfly41 on 2021-07-20
You will have to start devising methods for eliminating possibilities using intuition.

> Once you eliminate the impossible, whatever remains, no matter how improbable, must be the truth.

Arthur Conan Doyle

Start by reviewing the steps you took to arrive at this position.

You wrote .

> Also an alternative would be if there is a simple way to reverse all packages back to what they were prior to updates and I just update one at a time until i find the offending one

Run this command in terminal.

```
history | grep apt
```

This will give you a list of historical commands containing "apt" which you ran since your last stable configuration.

Can you reverse this order of installation until your arrive back to stable system?

You can use Synaptic Package Manager to uninstall packages you installed. And in future to install packages. With Synaptic you can go to File > History to see all installations by date.

Install glogg, run it and use this to view your system log files.

Look for keywords such as ERROR, WARNING

Study the errors in reverse listing.

Can you create a new guest account to test if guest account experiences same symptoms?

Can you run your LiveUSB in try Ubuntu mode to see if it works in stable manner?

Take note of the frequent advice on backups so that in future you can more easily reverse your steps and recover

---

### Post by TheFu on 2021-07-20
> **dragonfly41 said:**
>  
Run this command in terminal.

```
history | grep apt
```

This will give you a list of historical commands containing "apt" which you ran since your last stable configuration.
 

Almost.  This will only show the history for the current bash session and the prior ones inherited, upto the default count of history retained.  If you use multiple terminals or installed packages using commands that don't have "apt" in the name (dpkg or gnome-software, for example), then those will not be shown.  People who use the terminal are likely to have multiple terminals on the same system and which ever is closed last will close the ~/.history file - overwriting any other prior changes from other terminal sessions being closed.
If looking through 'what was installed', there must be an APT package manager installation log somewhere.  Probably in /var/apt or /var/lib/apt somewhere.  Think I've used that twice since 2000.  A quick web search found this answer: [https://askubuntu.com/questions/21657/how-do-i-show-apt-get-package-management-history-via-command-line](https://askubuntu.com/questions/21657/how-do-i-show-apt-get-package-management-history-via-command-line)  Read the log file with
```
 less /var/log/apt/history.log
```
It gets rotated, so older versions are likely.  Use
```
zless /var/log/apt/history.log.1.gz
```
to read the prior history. Appears these are rotated monthly and 12 log files are kept, so there's almost 1 yr of logs for packages installed into APT.  On my system, it appears that even going from a 16.04 --> 18.04 release upgrade was captured.

I don't use GUI package manager tools on any of my systems, so I have no idea if any GUI tool package management commands are put into that log or not. Sorry.  For me, GUI programs just add a complex layer of junk, provide fewer controls, and hide important details.  For almost all administrative tasks, I skip the GUI stuff - with 1 exception, gparted. Of course, that wouldn't apply here.

---

