---
title: "ubuntu wont log in to main (only) user."
date: 2013-11-08
forum: General Help
---

### Post by arranskye on 2013-11-08
Hi I have logged in as a guest to post this.  _upgraded to Ubuntu 13.10_. No problems all worked fine.  a few days later installed Updates. Now when the PC is switched on and Ubuntu 13.10 selected the screen goes black as usual, then flashes another black screen appears with a black/white cross in the centre. About 20 seconds later a log in screen appears  showing my user name, password box, guest session. When I highlight my user name and enter password there is another long delay but eventually a screen appears with my wallpaper ( A photo) filling the whole screen, No launcher icons, and again log in details user name password box & guest session. This continues everytime I highlight my user name and enter my password I just get repeated login screens.

Using the guest desktop looked at user accounts which shows the correct user name & type "administrator."  I do not have any guest accounts on my PC.

Tried Ubuntu recovery mode  with networking/fix packages.  This took about 8 minuters to complete and appeared to be installing/checking the updates installed immediately before the problem began, but problem remained.

Tried selecting Ubunto 13.04 kernel at boot up but failed to work.   messages received: System programe problem detected & Unable to load failsafe system.

All my data is on my main account/desktop.  Please can anyone adise me how to get it back.  thanks.

---

### Post by TheFu on 2013-11-08
This is a guess and only a guess, but I would guess that the desktop settings were screwed in some way.  Either create a new account and move all the "data" over ... not the settings .... or install a new DE (xfce, lxde, .... ) and select one of them before logging in on the system.

Or
an initialization file may have been corrupted ... had this issue for lxpanel yesterday - the panel refused to start because I had left off an '=' in the pulse-audio settings file.  Fortunately, there was an error displayed with the file and line number causing the issue.

Can you ssh into the machine from a different computer? might be able to fix things that way too.  This would be the easiest for me, but is you are a point-n-click person, it is probably too hard.

---

### Post by arranskye on 2013-11-08
Thanks Fu, Yep im a bit of a point & click lass but I am more then willing to try.  i have a laptop that i could use.   dont know how to move the data when I cant access it.   sorry

---

### Post by TheFu on 2013-11-08
I should have asked this before ... is there any encryption involved?  If not, you should backup your data ASAP.  Then everything else is gravy after that.

The shortest distance from where you are to a working system again is probably to reinstall, given the point-n-click aspect. Hopefully, someone more familar with PnC and 13.10 will swoop in and help.  **Perhaps you would be happier running an LTS release?** See my signature.  New != Better.

The openssh-server package would have needed to be installed. It is unlikely that would have already happened unless you use ssh all-the-time as people like me do.

On a new computer (any new OS), the first things I do are:
* purge nano - hate that editor
* install an ssh-server
Then we can use any ssh client to access the machine remotely ... ssh, scp, sftp ... all come for free.  These are all secure, support key-based authentication, and have been considered extremely secure over the years. Secure enough to use from anywhere in the world. 

But if an ssh-server is not already installed, it doesn't help you.

There is good news.  The CLI commands do not change very often, so I'm using the exact same commands today as 20+ yrs ago. All the GUI changes really dno't matter to me. Learned once - done.

---

### Post by arranskye on 2013-11-08
HI   No encryption.  data all saved to Ubuntu One.   Will consider the LTS  got another message that might help

Unable to determine failsafe system name.    Possible causes:

xfconfd isnt running.         (D_Bus setup problem)    environment variable 

$XDZ_CONFIG_DIRS is set incorrectly.  must include "/ etc" or xfce4 session is installed incorrectly.


Thanks

---

### Post by TheFu on 2013-11-08
> **arranskye said:**
> HI   No encryption.  data all saved to Ubuntu One.   Will consider the LTS  got another message that might help

I've read about a few people here that lost all their data on Ubuntu-1.  I wouldn't trust it.  Use a local, USB spinning HDD.

---

