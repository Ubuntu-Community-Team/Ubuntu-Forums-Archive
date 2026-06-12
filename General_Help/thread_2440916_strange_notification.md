---
title: "strange notification"
date: 2020-04-16
forum: General Help
---

### Post by derek99 on 2020-04-16
For the last few days I have been intermittently getting the following notification:
The update information is outdated. This may be caused by network problems or a repository that is no longer available. Please update manually by selecting "show updates" from the indicator menu, and watching for any failing repositories.


I looked up Ubunto repositories but could find no information about how to determine if a repository is "failing". What "show updates" tells me is:
The software on this computer is up to date.
Tip: You can use Livepatch to keep your computer more secure between restarts.


I followed Livepatch down a rabbit hole and ended up with a 3 page document that told me nothing I could comprehend and included the line "For further information on enabling the Canonical Livepatch Service please read the documentation." What documentation? Where? I suspect I don't need it because I shut down the computer daily. Please let me know if I am wrong about that, and tell my why.


Does the above information say I have a problem with my computer? If so, what should I do about it? If not, how can I get rid of the notification?


I have been using Ubunto for a few months but, aside from e-mail and internet, I am still a rank beginner. I still need a Ubunto user's guide written for somebody with no prior knowledge but have been unable to find one. Back in the eighties I did some work on a Unix system. It has not made Linux any easier for me, aside from making me aware that serious problems can result from uninformed use of Terminal.

---

### Post by Autodave on 2020-04-16
Can you please tell us what version of 'buntu you are using?

Generally, I just run these 2 commands in a terminal and everything stays/gets updated:

sudo apt-get update       
sudo apt-get upgrade

---

### Post by TheFu on 2020-04-16
If you shutdown you computers daily, you have no need at all for livepatch or the complexity it brings.
GUIs for patching hide all sorts of details. When troubleshooting, best to skip GUIs completely and use shell commands in a terminal.  

First, run
```
sudo apt update
```
If there aren't any errors, then run
```
sudo apt upgrade
```

Any issues?  Please post the relevant parts only.  We don't need to see 50 of the same errors or similar errors over and over here. Please. Also, please use _code tags_ as I've done above.  This will make the output easier to read.

Those two commands are what I run weekly to patch my desktops and servers.  Every 2-4 weeks, I'll also run 
```
sudo apt autoremove
sudo apt autoclean
```
a few hours after the patches are finished and everything seems fine.

Ninja'd by  Autodave - which is common. ;)

If you google "ubuntu desktop guide", that's a fairly easy thing.  But really, no casual user will ever read a computer book from end-to end.  My home-office is full of books that I'm certain are good, but they are used only for reference and only when I know a specific topic is well covered.  You know, like JSP from 1997. ;)

If you want to unlock the other 80% of the capabilities your Ubuntu system has, then you need to learn/use the shell.  
[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) is the normal, no-hassle, free, book I and others recommend here.  I've used it in my Beginning Linux classes. and for Admin 101 refreshers.

---

### Post by grahammechanical on 2020-04-16
Ubuntu has a utility called Software & Updates. In the Updates tab we can set how often Ubuntu will automatically check for updates. If the time for Ubuntu to do an automatic check for updates arrives and Ubuntu is not connected to the internet then we will get the error message that you see.

If you run in a terminal the first command recommended by TheFu then the terminal output will show what repository (if any) cannot be accessed. The utility that produced the notification is not smart enough to determine which of two possibilities is causing the problem so it suggests both.

Think of the recommendation to install Livepatch as a kind of advert. The service is free for personal use and can be installed on 3 machines. Business users have to buy the service.

The company I used to work for never switched off its computers. Not even the screens. The directors were looking for ideas on how to save money but when I recommended switching off computer screens they seemed unable to grasp that it could be a real energy (and therefore cost) saver.

Getting back to the point. A service that allows an OS to be upgraded without the need for a reboot and so done automatically without human intervention could be useful to business users.

[https://ubuntu.com/livepatch](https://ubuntu.com/livepatch)

Regards.

---

