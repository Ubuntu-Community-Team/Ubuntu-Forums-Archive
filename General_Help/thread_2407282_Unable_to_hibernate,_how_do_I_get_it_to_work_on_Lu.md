---
title: "Unable to hibernate, how do I get it to work on Lubuntu?"
date: 2018-12-01
forum: General Help
---

### Post by MechaMechanism on 2018-12-01
Hibernate when selected from the menu does nothing.  Nothing happens.  The desktop just sits there.  Suspend works just fine.  Stock unmodified OS, brand new install.  No CLI action.  Only changes made, were to theme.

18.10 32 bit on 32 bit machine.
1GB ram
16GB SSD hard disk with a little over 8GB free space.
Dell Mini 10v

So what does a guy got to do to get some Zzz around here ;)

---

### Post by TheFu on 2018-12-02
Is the swap larger than the RAM?

swapon -s
free -mh

---

### Post by MechaMechanism on 2018-12-02
> **TheFu said:**
> Is the swap larger than the RAM?

swapon -s
free -mh

A-ha, thank you for those commands.  They showed me that I did not have a sawpfile at all.  So I used this website to create one... [https://www.digitalocean.com/community/tutorials/how-to-add-swap-space-on-ubuntu-18-04](https://www.digitalocean.com/community/tutorials/how-to-add-swap-space-on-ubuntu-18-04)

But, I still cannot hibernate :( ```
systemctl hibernate [COLOR=#ff0000]_***(After entering this command I got a password prompt, I entered my password and it hibernated, but, I cannot hibernate from the GUI buttons menu.  And Lubuntu is supposed to allow hibernating without password prompting I think, not sure.)***_[/COLOR]
Failed to hibernate system via logind: Access denied
```

When I hibernate from the command line with applications open they are not there when I turn the computer back on.  Is hibernating different in Linux than Windows?

No what does this all mean :confused:

P.S.  Ram=1GB, Swap=2GB

---

### Post by TheFu on 2018-12-02
I've never used Windows hibernation.  Actually, I don't use Linux hibernation either due to security considerations.  I do use standby on a laptop, provided it isn't being physically moved out of the building.  Standby mode has security considerations.

If the programs that were running are gone after you request to hibernate, then it isn't working.   I'd guess that if hardware reinitialization fails, which can happen for many different reasons, then coming back successful from hibernation fails.

Anyways, google found this: [https://fitzcarraldoblog.wordpress.com/2018/07/14/configuring-lubuntu-18-04-to-enable-hibernation-using-a-swap-file/](https://fitzcarraldoblog.wordpress.com/2018/07/14/configuring-lubuntu-18-04-to-enable-hibernation-using-a-swap-file/)
I'd use a swap partition, not a swap file, to avoid many of the added complications.

Also, instead of posting an interpretation of the setup, please post the commands used with the output.  Basically, prove it. Sometimes we misinterpret outputs. Happens to everyone.

---

### Post by MechaMechanism on 2018-12-02
What I meant was that after entering, "systemctl hibernate", I got a [SIZE=3]"GUI password prompt[/SIZE]" upon which entering the correct password produced the output in the terminal of [SIZE=3]"Failed to hibernate system via logind: Access denied[/SIZE]".  That's it.  There was nothing else on screen in the terminal or GUI.  The OS proceeded to shutdown, a regular shutdown.  Because you pointed me in the direction of that blog, I believe it is too much work to make hibernate work for too little pay off.  And you brought up security considerations.  My Windows laptop in encrypted with 2 factor bitlocker encryption.  This little netbook has no encryption.  So in light of security considerations, I think I'll abandon the hibernate idea for now.  Maybe in the future with some encrypted laptop?

So with that I'll mark the thread as solved.  See post number 4 for solution. [https://ubuntuforums.org/showthread.php?t=2407282&p=13820780&viewfull=1#post13820780](https://ubuntuforums.org/showthread.php?t=2407282&p=13820780&viewfull=1#post13820780)

---

### Post by TheFu on 2018-12-03
Full disk encryption is pretty easy on Ubuntu provided you choose it during the installation.  It has the added bonus that your decryption keys aren't sent to Microsoft's cloud storage automatically.

The reason setting up hibernation is difficult is because, somehow, your installation didn't make a swap partition, which has been the standard setup method for all Linux installs 20+ yrs.  At least as far as the swap file/partition stuff is involved.  This is definitely something new in 18.04 and later releases.

While the error you posted is good to know, on Linux, the system logs will show much more detailed information for any issues.  Check the log files in /var/log/ for any warnings or errors before, during, and after, trying to hibernate. There will be some log entries, I'm positive.  Those logs will likely say something about a missing swap partition or it could be a different issue. Won't know until taking a look.

---

