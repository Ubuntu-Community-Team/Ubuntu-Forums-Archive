---
title: "Why Bnetd, why?"
date: 2008-06-17
forum: General Help
---

### Post by EvilMoustache on 2008-06-17
I recently upgraded to Hardy Heron from Gutsy Gibbon.
 
When I try to update via the Update Manager, I get an error regarding the Bnetd package.  The package is in a very bad or inconsistent state you should reinstall before attempting a removal.

This is what I have tried.

I tried removing it via Synaptic. No go.  Displays the above error.

Tried via the terminal and dpkg.  No go.  I got the following output.


WARNING - use of options marked [!] can seriously damage your installation.
Forcing options marked [*] are enabled by default.
hyugaricdeau@HAL9000:~$ sudo dpkg --purge --force-remove-reinstreq bnetd
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 132661 files and directories currently installed.)
Removing bnetd ...
[: 17: ==: unexpected operator
Stopping Battle.net(R) gaming server: invoke-rc.d: initscript bnetd, action "stop" failed.
dpkg: error processing bnetd (--purge):
 subprocess pre-removal script returned error exit status 1
chown: cannot access `/var/run/bnetd': No such file or directory
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 bnetd

I tried removing it via aptitude. No go.  Can't find the package.  Is there a way to force the removal or reinstallation of the package?  I'm at a complete loss on what to try next. 

Any help will be greatly appreciated.

---

### Post by jwillson on 2011-10-12
EvilMoustache,

Check out this bug report:

[https://bugs.launchpad.net/ubuntu/+source/bnetd/+bug/846560](https://bugs.launchpad.net/ubuntu/+source/bnetd/+bug/846560)

Here's what ACTUALLY WORKED for me:
Note: XXX should be replaced with the actual PID number that you get.

sudo /etc/init.d/bnetd stop
ps -e -o pid -o args | grep bnetd
XXX bnetd
sudo kill -9 XXX
rm /etc/init.d/bnetd
sudo apt-get remove bnetd

Notice the "rm /etc/init.bnetd". That's necessary to be able to actually remove it. I hope this helps!

---

### Post by laurahartwell on 2011-10-15
FINALLY a fix that WORKS! 'I've been fighting with this forever. Thank you thank you thank you.

Laura

 				 				**Re: Why Bnetd, why?** 			
 			 			 		   		 		 		EvilMoustache,

Check out this bug report:

[https://bugs.launchpad.net/ubuntu/+s...td/+bug/846560]("https://bugs.launchpad.net/ubuntu/+source/bnetd/+bug/846560")

Here's what ACTUALLY WORKED for me:
Note: XXX should be replaced with the actual PID number that you get.

sudo /etc/init.d/bnetd stop
ps -e -o pid -o args | grep bnetd
XXX bnetd
sudo kill -9 XXX
rm /etc/init.d/bnetd
sudo apt-get remove bnetd.

---

