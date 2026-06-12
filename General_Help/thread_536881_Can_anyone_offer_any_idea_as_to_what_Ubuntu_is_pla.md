---
title: "Can anyone offer any idea as to what Ubuntu is playing at?"
date: 2007-08-28
forum: General Help
---

### Post by Gleep on 2007-08-28
I am utterly confused, the other day Ubuntu just decided to stop working...

If I boot into Ubuntu, I get the ubuntu startup screen (probably not what it's called), I get a plain background and a mouse pointer, but the splash screen never appears and no matter how long I leave it, the desktop simply doesn't want to show up.

This just happened out of the blue... it worked fine one day, I shut down for the night, the next day it wouldn't work!

I have no idea what's wrong to fix it, so if no one has any ideas I guess I'm gonna just have to reformat :(

I'm sick of using Windows, but glad I at least have the option to.

Thanks for taking a look.

---

### Post by Wolki on 2007-08-28
> **Gleep said:**
> 
I have no idea what's wrong to fix it, so if no one has any ideas I guess I'm gonna just have to reformat :(


It's probably a broken session file. After the login screen appears, press ctrl-alt-F1 and you should be able to get a console login. login there, then enter the following command: "mv ~/.gnome2/session ~/.gnome2/session.bak". Then logout ("exit"), press ctrl-alt-F7 and you should be back at the normal login screen. login and try if it works.

If it doesn't, something else in your configuration is likely causing the problem. No matter what it is, it shouldn't be too hard to fix, but please try this first and report whether it worked or not.

---

### Post by be4truth on 2007-08-28
Boot into rescue mode.

You need to enable boot logging by opening a terminal and typing the following:

```
sudo gedit /etc/default/bootlogd
```

Edit the line 

# Run bootlogd at startup ?
BOOTLOGD_ENABLE=No

to 

# Run bootlogd at startup ?
BOOTLOGD_ENABLE=Yes

Save the file.
Reboot your machine in normal mode.
Then reboot your machine in rescue mode and check the log file in  /var/log/boot. with 

```
tail /var/log/boot
```

Read it and see if it makes sense to you. Write down the last 2 lines and post it here.

---

### Post by Gleep on 2007-08-28
> **Wolki said:**
> It's probably a broken session file. After the login screen appears, press ctrl-alt-F1 and you should be able to get a console login. login there, then enter the following command: "mv ~/.gnome2/session ~/.gnome2/session.bak". Then logout ("exit"), press ctrl-alt-F7 and you should be back at the normal login screen. login and try if it works.

If it doesn't, something else in your configuration is likely causing the problem. No matter what it is, it shouldn't be too hard to fix, but please try this first and report whether it worked or not.
I have login screen disabled, so I'm not sure if it would even appear at all. 

Should I give it a try anyway?

> **be4truth said:**
> Boot into rescue mode.

You need to enable boot logging by opening a terminal and typing the following:

```
sudo gedit /etc/default/bootlogd
```

Edit the line 

# Run bootlogd at startup ?
BOOTLOGD_ENABLE=No

to 

# Run bootlogd at startup ?
BOOTLOGD_ENABLE=Yes

Save the file.
Reboot your machine in normal mode.
Then reboot your machine in rescue mode and check the log file in  /var/log/boot. with 

```
tail /var/log/boot
```

Read it and see if it makes sense to you. Write down the last 2 lines and post it here.
Cheers I'll give it a go.

---

### Post by tgalati4 on 2007-08-28
Since it happened on reboot, it's possible that you upgraded several packages weeks ago and now after rebooting something is broken.  How long was your system up since the last reboot?

I had a Dapper system running for 165 days straight.  I had 100 overdue patches.  I applied them in batches of 33 each then rebooted. And it worked.  Had I not rebooted but left the system running another 165 days (still running the old code), I would certainly be confused if I rebooted and the system was broken.

Look for error messages in /var/log and in your home directory:  .xsession-errors to see what's unusual.

---

### Post by Gleep on 2007-08-28
> **tgalati4 said:**
> Since it happened on reboot, it's possible that you upgraded several packages weeks ago and now after rebooting something is broken.  How long was your system up since the last reboot?

I had a Dapper system running for 165 days straight.  I had 100 overdue patches.  I applied them in batches of 33 each then rebooted. And it worked.  Had I not rebooted but left the system running another 165 days (still running the old code), I would certainly be confused if I rebooted and the system was broken.

Look for error messages in /var/log and in your home directory:  .xsession-errors to see what's unusual.I thought it might have been to do with packages too, although I haven't had it running for a long time in ages, I've been shutting down every night for a few weeks (because apparently the 'hum' my computer makes keeps my mother awake... I personally find it quite soothing hah) so it won't be that, but it could still have been an upgrade that did it, generally when it breaks, that's why. I did get a few upgrades the day before it stopped working, can't remember what they were though. Mainly compizfusion stuff I think...

---

### Post by Wolki on 2007-08-28
> **Gleep said:**
> I have login screen disabled, so I'm not sure if it would even appear at all. 

Should I give it a try anyway?

Yes, but it's probably best to make sure that Gnome isn't running then. After logging in to the terminal, execute "sudo invoke-rc.d gdm stop", this should stop the x server and thus gnome. after you're done with the mv command, do a "sudo invoke-rc.d gdm start" to start the graphical interface again.

---

### Post by Gleep on 2007-08-28
> **be4truth said:**
> Boot into rescue mode.

You need to enable boot logging by opening a terminal and typing the following:

```
sudo gedit /etc/default/bootlogd
```

Edit the line 

# Run bootlogd at startup ?
BOOTLOGD_ENABLE=No

to 

# Run bootlogd at startup ?
BOOTLOGD_ENABLE=Yes

Save the file.
Reboot your machine in normal mode.
Then reboot your machine in rescue mode and check the log file in  /var/log/boot. with 

```
tail /var/log/boot
```

Read it and see if it makes sense to you. Write down the last 2 lines and post it here.

Ok this didnt work because I can't reboot properly when in normal mode, so I just hit the reset button, which probably means it didnt save? Either way all it was showing when I entered ```
tail /var/log/boot
``` the next time was from Apr 22..

> **Wolki said:**
> Yes, but it's probably best to make sure that Gnome isn't running then. After logging in to the terminal, execute "sudo invoke-rc.d gdm stop", this should stop the x server and thus gnome. after you're done with the mv command, do a "sudo invoke-rc.d gdm start" to start the graphical interface again.

Ok I'll try this next, cheers.

---

### Post by be4truth on 2007-08-28
Can you boot in rescue mode? Up to the prompt?

---

### Post by Gleep on 2007-08-28
> **be4truth said:**
> Can you boot in rescue mode? Up to the prompt?

As in recovery mode? Yeah :)

---

### Post by be4truth on 2007-08-28
> **be4truth said:**
> Boot into rescue mode.

You need to enable boot logging by opening a terminal and typing the following:

```
sudo gedit /etc/default/bootlogd
```

Edit the line 

# Run bootlogd at startup ?
BOOTLOGD_ENABLE=No

to 

# Run bootlogd at startup ?
BOOTLOGD_ENABLE=Yes

Save the file.
Reboot your machine in normal mode.
Then reboot your machine in rescue mode and check the log file in  /var/log/boot. with 

```
tail /var/log/boot
```

Read it and see if it makes sense to you. Write down the last 2 lines and post it here.

You could try this in recovery mode. Instead of "sudo gedit ..." you could try "sudo nano ...."

---

### Post by Gleep on 2007-08-28
> **be4truth said:**
> You could try this in recovery mode. Instead of "sudo gedit ..." you could try "sudo nano ...."Yeah I worked that out when I did it, but of course, I still can't properly reboot when I boot into normal mode... cos I have no interface to do so.

---

### Post by Wolki on 2007-08-28
To reboot, do a "sudo reboot"

---

### Post by Gleep on 2007-08-28
> **Wolki said:**
> To reboot, do a "sudo reboot"I can't do that when I just have a curser and background, but I guess I could drop down into er... whats it called. God I'm a n00b today :( Totally got mental block.

---

