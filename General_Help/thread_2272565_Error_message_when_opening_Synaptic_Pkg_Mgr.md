---
title: "Error message when opening Synaptic Pkg Mgr"
date: 2015-04-07
forum: General Help
---

### Post by gb962214 on 2015-04-07
When I try opening the Synaptic Pkg Mgr, I get this Error Message..... [B]
"Unable to get exclusive lock"[/B]
"This usually means that another package management application (like apt-get or aptitude) is already running. Please close that application first."

How do I go about finding out what package is running?  How do I stop it?
I know just enough about Ubuntu to be dangerous 

Any suggestions or instruction would be appreciated.

I am running 12.04 LTS. 32 bit

thanks, Greg

---

### Post by dragonfly41 on 2015-04-07
If you are trying to launch Synaptic Package Manager either with an instance already running or Ubuntu Software Centre running you will get that error message.

Use Alt + Tab to skip through your running apps.

---

### Post by gb962214 on 2015-04-07
I used Alt + Tab, and the only app running is my browser - Chrome.  Nothing else is shown, and when attempting to open "SPM" again, I received the same message.
When I opened Ubuntu Software Center, there is a "Progress icon" spinning.  When I clicked on the icon, it shows that it is Searching with a "cancelling" notation directly under it.  Is that the problem?  Its been spinning for 10 - 15 minutes now.

---

### Post by deadflowr on 2015-04-07
Go to the Update Manager app.
it's probably running, but not actually open/viewable.
Try opening it, and then close it.

---

### Post by gb962214 on 2015-04-07
Nope, it didn't work. Got this message  "Not all upgrades can be installed. Run a partial upgrade to get as many updates as possible.  This could be cause by:  *Previous upgrade which did not complete, *Problem with some of the installed updates, *Unofficial software packages not provided by Ubuntu, *Normal changes of a previous version of Ubuntu." 

After I hit the "Close" button I received this message: "Software index is broken.  It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first."

I then opened up a Terminal window and ran the suggested command, at which I received this message:  "E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?"

It seems as though I'm in a vicious loop....

Another Suggestion?
thx,  greg

---

### Post by dragonfly41 on 2015-04-07
If you dig around .. some more tips/warnings found here ..

[http://askubuntu.com/questions/253925/how-to-safely-abort-apt-get-install](http://askubuntu.com/questions/253925/how-to-safely-abort-apt-get-install)

[http://askubuntu.com/questions/498102/how-do-i-unlock-var-lib-dpkg-lock](http://askubuntu.com/questions/498102/how-do-i-unlock-var-lib-dpkg-lock)

run killall dpkg

> 
sudo rm /var/lib/dpkg/lock should do the trick. You can use ps afx|grep dpkg to check if there is still a process running at the same time. 
sudo killall dpkg will stop all running dpkg processes.


Then ... sudo apt-get update

However killing running processes may cause further problems.

Perhaps the easiest way is to just reboot and then only launch command terminal for a package installation.

...

Note that I had a similar earlier problem where there were missing GPG keys and I followed a tip to install Y PPA Manager

Get it from here ..

[http://www.webupd8.org/2010/11/y-ppa-manager-easily-search-add-remove.html](http://www.webupd8.org/2010/11/y-ppa-manager-easily-search-add-remove.html)

sudo add-apt-repository ppa:webupd8team/y-ppa-manager
sudo apt-get update
sudo apt-get install y-ppa-manager

Then find launcher under Applications > System Tools > Y PPA Manager

---

### Post by gb962214 on 2015-04-07
I'll give it a try and see what happens.
Keep you fingers crossed !!

---

### Post by ian-weisser on 2015-04-07
> **dragonfly41 said:**
> However killing running processes may cause further problems.

Perhaps the easiest way is to just reboot and then only launch command terminal for a package installation.

Agreed.
rm-ing lockfiles or killing processes is not a great habit to get into.
For the first time you run across this problem, a reboot is a safe, appropriate way to resolve it.

The whole 'partial upgrade' message indicates other problems to solve once the lock is fixed.
Might be easy, might be hard.
I prefer to solve such problems from the termianal - I find the error messages, and their context, more helpful in Terminal.

---

### Post by gb962214 on 2015-04-08
To Dragonfly41, Deadflwr, and Ian:
Thanks for your help.  I went to the couple of threads suggested by Dragonfly and worked through it.
Using a Terminal window, and the ps afx command I was able to figure out it was the Dropbox package trying to update and configure that was hanging things up.  I stopped the process, removed the Dropbox app altogether, then rebooted.  Everything so far seems to be running normally.  Time will tell.
I really appreciate your tips & suggestions.  These Forums are a good source of information and instruction.
I couldn't have done it without you all.
Thanks again,
Greg

---

