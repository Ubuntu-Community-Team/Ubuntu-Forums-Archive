---
title: "Wubi Log in issues"
date: 2008-04-25
forum: General Help
---

### Post by hardcastle1 on 2008-04-25
Hey, I've installed Wubi on my laptop however, it won't allow me to log in.

First off, from all of the videos I've seen, people generally log in from like a proper Wubi/Ubuntu log in screen with orange B/G etc, on my laptop a black screen comes up and says 'Hardcastle Login:' or something to that effect, I type Hardcastle in there, my chosen Wubi username and then my chosen wubi p'word in the following password input ,anyways after putting the correct password in, this comes up : 

-bash: /dev/null: permission denied 

It fills the screen with that message and then I have to reboot, well I don't have to, it's just I don't know what else I can do.

Anyways, why would this happen and are there any possible sollutions?

I've installed Wubi twice and this has happened both times.

Thanks in advance.

---

### Post by ago on 2008-04-25
do you mean you end up in a terminal?
what is the first menu item when you press esc when you press esc at boot after ubuntu?

PS I do not think that upper case in username is allowed

---

### Post by hardcastle1 on 2008-04-25
> **ago said:**
> do you mean you end up in a terminal?
what is the first menu item when you press esc when you press esc at boot after ubuntu?

PS I do not think that upper case in username is allowed

Errrrrrrr.

Basically, at the boot screen, I have an option of choosing either Vista or Ubuntu, If I choose Ubuntu, the terminal comes up and Im prompted to enter username and password, If I press esc, I can either go into ubuntu 7.(insert version) Recovery mode, some other mode and then ubuntu 8 i think.

I've not been anywhere near the Orange boot screen or anything like that yet, I've not got past the terminal..

---

### Post by ago on 2008-04-25
uninstall reinstall, at first boot press esc and select safe graphic mode

---

### Post by hardcastle1 on 2008-04-25
> **ago said:**
> uninstall reinstall, at first boot press esc and select safe graphic mode

okay, I'll give it a go.

Thanks

---

### Post by hardcastle1 on 2008-04-25
There was no 'safe graphic mode' option available.

Grrr.

---

### Post by hardcastle1 on 2008-04-25
Hey, the attached file, is what comes up on the screen upon attempting to log in.

---

### Post by ago on 2008-04-26
There should be a rescue mode then

---

### Post by hardcastle1 on 2008-04-26
> **ago said:**
> There should be a rescue mode then

I've tried rescue mode, that just brings up a load of checks and then stops. doesn't allow  me to log in or anything, this is getting frustrating,ha.

---

### Post by ago on 2008-04-26
Uninstall, run chckdsk /r on the target partition and run wubi.exe again.
When you boot press esc and select safe graphic mode. If it is not there you did something wrong.

---

### Post by hardcastle1 on 2008-04-26
> **ago said:**
> Uninstall, run chckdsk /r on the target partition and run wubi.exe again.
When you boot press esc and select safe graphic mode. If it is not there you did something wrong.

Err, you've lost me after the uninstallation part. I can do that, haha but not quite sure how/where to do the diskcheck.

I thought the point of Wubi was that installed on the Windows partition, thus saving any potential HDD woes?

---

### Post by ago on 2008-04-26
Yep but sometimes the windows fs is corrupted to begin with... And you have to clean it up from windows. 

Open a dos box, go to the drive where you have wubi and run

chkdsk /r

---

### Post by hardcastle1 on 2008-04-26
> **ag
o said:**
> Yep but sometimes the windows fs is corrupted to begin with... And you have to clean it up from windows. 

Open a dos box, go to the drive where you have wubi and run

chkdsk /r

It says -

Cannot lock current drive

 chkdsk cannot run because the volume is in use by another process, would you like to run a chkdsk at restart?

I'll restart in a bit and see what happens.

Thanks for all your help so far, by the way, Im not the most computer literate,as you can tell, so this is really helping me out :)

---

### Post by hardcastle1 on 2008-04-26
Okay, so I did a checkdisk and it did it and I don't think it came back with any issues? 

I just want Ubuntu! I tried just installing Ubuntu and that messed up my partitions on the my HD or something and lead to me having to  reinstall windows and now Wubi won't even work.

Soooo frustrating.

---

### Post by ago on 2008-04-27
See if any of that helps: [https://wiki.ubuntu.com/WubiGuide#head-d3367ee1f59fcc5e1b086e090abdd86a0bfd5925](https://wiki.ubuntu.com/WubiGuide#head-d3367ee1f59fcc5e1b086e090abdd86a0bfd5925)

Let me know exactly how you get stacked and we'll see what we can do.

---

### Post by hardcastle1 on 2008-04-27
Im going to give it a go reinstalling later.

I have no idea if this is a minor and insignificant detail or what, but after installation and being prompted to reboot, I always choose to go straight into ubuntu from the OS selection part upon rebooting, Im sure I read somewhere last night that I need to go back into windows first or something?

Also, Im running it straight off the desktop download, I've not burnt it onto a bootable cd? I don't know if that might cause issues either?

---

### Post by hardcastle1 on 2008-04-27
Alsoooo, I've just been looking through some guides, that clearly show upon installation in windows and rebooting and selecting Ubuntu that some sort of installation or unpacking sequence should commence, with a blue background, what I had when I originally attempted to install Ubuntu as a standalone OS, with my Wubi installer,theres none of that, upon rebooting, it goes through some checks, and then brings up the login, which never works?

I'm using, or attempting to use 'Wubi 8.04 beta rev501'

Is the right version for a Windows vista laptop?

---

### Post by ago on 2008-04-27
> **hardcastle1 said:**
> Im going to give it a go reinstalling later.

I have no idea if this is a minor and insignificant detail or what, but after installation and being prompted to reboot, I always choose to go straight into ubuntu from the OS selection part upon rebooting, Im sure I read somewhere last night that I need to go back into windows first or something?

Also, Im running it straight off the desktop download, I've not burnt it onto a bootable cd? I don't know if that might cause issues either?

The above is correct. Normally you have to go into windows, chkdsk /r and reboot from menu if the filesystem is corrupted.

---

### Post by hardcastle1 on 2008-04-27
> **ago said:**
> The above is correct. Normally you have to go into windows, chkdsk /r and reboot from menu if the filesystem is corrupted.

I've just give it another go and im dangerously close to giving up now. It just doesn't seem to want to work for me :(:(:confused:

I've done the checkdisk, tried in reinstalling, same issue.

Re-downloaded a non beta version, same issue.

Im considering doing it again, but this time putting it onto a different drive, not the C drive, do you think that would/could make any difference?

---

### Post by ago on 2008-04-27
Trying again does not help.

The best thing would be if you could provide more accurate error messages. 

There are a few logs, normally /casper.log and /var/log/syslog are the relevant ones. See [https://wiki.ubuntu.com/WubiGuide#head-75dd343d07563f995715cdfec3ec938499b5a124](https://wiki.ubuntu.com/WubiGuide#head-75dd343d07563f995715cdfec3ec938499b5a124)

Also at boot, after selecting Ubuntu you can press esc for more boot options. Those sometime help.

---

### Post by hardcastle1 on 2008-04-27
> **ago said:**
> Trying again does not help.

The best thing would be if you could provide more accurate error messages. 

There are a few logs, normally /casper.log and /var/log/syslog are the relevant ones.

Also at boot, after selecting Ubuntu you can press esc for more boot options. Those sometime help.

Er, there are no error messages...

I'm also totally new to Linux/ubuntu, so I wouldn't really know where to start.

I'll take some photo's of the boot screens etc.

---

