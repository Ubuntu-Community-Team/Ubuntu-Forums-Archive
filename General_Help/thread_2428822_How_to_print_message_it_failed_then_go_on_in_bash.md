---
title: "How to print message it failed then go on in bash?"
date: 2019-10-09
forum: General Help
---

### Post by dora5 on 2019-10-09
I want to create a script to install post Ubuntu install stuff like codecs and software.   

The only problem is, when a script comes to a command it can't execute it just stops and falls into hyperspace.

I want my script to do something like this.

sudo apt-get install kde-wallpapers

If kde-wallpapers install succeeds, echo 'kde-wallpapers installed'

If kde-wallpapers does not install, 
-----echo 'kde-wallpapers did not install'
-----Continue on to the next item.   


What is the code to write this?    

Even though everyone necessarily wants to do it, it seems to be far too obscure for the bash manuals.  The only thing I've found would tell the computer to completely ignore the fact that kde-wallpapers did not install - and logically, it also would not tell me it didn't install.   People point that out on forum posts on this subject, and then noone ever replies with the rest of the answer.   I also get the distinct idea that the answer looks far more like assembly or machine language than bash.  

Thanks!

---

### Post by TheFu on 2019-10-09
Use Ansible.  It handles failures.  It is designed to be used over and over and over and doesn't modify anything that doesn't actually need modification.

Assuming you will ignore my Ansible advice, you can test whether a package is install using **dpkg -l** The first 2 characters in each output line denote how installed the package is.  Nothing more than bash is needed - actually, Bourne Shell is more than sufficient for this sort of thing, though using a function would be more compact.

Do you know about checking return codes from programs? 
[https://www.tldp.org/LDP/abs/html/exit-status.html](https://www.tldp.org/LDP/abs/html/exit-status.html) 
From the apt-get manpage:```

DIAGNOSTICS
       apt-get returns zero on normal operation, decimal 100 on error.
```
Error checking is part of all scripts and programs. That's the difference between a hobby and professional.  There are literally thousands of examples on every Unix system.  A zero return means it worked as requested. A non-zero means something is wrong.

If you post some bash code, I will help fix it.

---

### Post by HermanAB on 2019-10-09
You can use Zenity to make pretty scripts.

[https://www.aeronetworks.ca/2015/09/zenity-progress-dialogue.html](https://www.aeronetworks.ca/2015/09/zenity-progress-dialogue.html)

---

### Post by Holger_Gehrke on 2019-10-10
Actually the man page is more a reference or a reminder for users who already know how things are done. If you look in the section "SHELL GRAMMAR" in the paragraph "Compound Commands" you'll find the description of "if". It says
```

if list; then list; [ elif list; then list; ] ... [ else list; ] fi
              The if list is executed.  If its exit status is zero, the then list is executed.  Otherwise, each elif list is executed in turn, and if its exit status is zero, the corre&#8208;
              sponding then list is executed and the command completes.  Otherwise, the else list is executed, if present.  The exit status is the exit status of the last  command  exe&#8208;
              cuted, or zero if no condition tested true.

```
So in your case
```

if apt install kde-wallpapers; then
  # commands in case the installation worked
  ;
else
  # commands to execute in case of installation failure
  ;
fi

```

A bit earlier in the page - in the paragraph on lists - you can find the description of AND and OR lists: 'command1 && command2' executes command2 only if command1 succeeded, 'command1 || command2' executes command2 only if command1 failed.

A bit later in the page - in the section on Parameter, paragraph on special parameters - you'll find "$?", a parameter (or variable) that holds the exit status of the last command executed (a status of 0 means success, all other values describe some kind of failure) ...

Instead of trying to use the man page for learning the basics - which is not what it's there for - you might want to take a look at [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) - a book about the Linux command line by William Shotts, available both in a printed Version and in a free version for download.

Holger

---

### Post by TheFu on 2019-10-10
For bash stuff, I use this as a clearer reference: [http://www.tldp.org/LDP/abs/html/](http://www.tldp.org/LDP/abs/html/) than the manpage, but for apt-get, the manpage really is the best reference that I've found.

For beginners, [https://www.tldp.org/LDP/Bash-Beginners-Guide/html/](https://www.tldp.org/LDP/Bash-Beginners-Guide/html/)

I like TLCL book too.  Great resource.  A few people at my LUG are working their way through it to get the background before we help them learn administration stuff.

---

### Post by kevdog on 2019-10-10
I'm going to also throw my hat into the ring here and say that I think ansible (that's what I use) (alternatives are puppet/chef) is what you want to use based on your description.  Ansible is a pretty quick read -- meaning it took me a few days of trying some things, but I found it pretty easy to pick up.  If you can do some bash scripting or some basic programming --- you can do ansible.

---

### Post by TheFu on 2019-10-10
After watching a 20 min video from Ansible - "Quick Start" - something like that, I had ansible on my desktop able to control 15 servers for trivial things like installing and removing packages.

The great thing about ansible is that if you admin any Unix systems, then you probably already have ssh setup so it is just installing the current Ansible and creating about 5 yaml files to do simple things like pushing a custom /etc/hosts file to each system, modified dynamically for each box.  Getting data back about almost any configuration question you might ask is also trivial. Ansible does that through the "setup" module.

---

### Post by kevdog on 2019-10-10
@TheFu

Hmm -- you have me thinking -- possibly a I can use Ansible to distribute Let's Encrypt certs after renewal -- I might have to look into that.  In terms of updating packages -- yes very easy with the apt plugin.  

Only think I hate about Ansible is the use of the yaml format.  However actually came up with this format with two spaces for line tabs should be shot.  Reminds me of modifying the netplan in Ubuntu -- some thing.  Very easy to make mistakes in this format.  I've modified my vim config to help limit the errors, but even so...argh

---

### Post by TheFu on 2019-10-11
Yaml doesn't require 2 spaces. It just requires consistent spaces.

I suppose you could use Ansible to copy certs around. I use a tiny bash script for that, but because I mix static, dynamic, and front-end servers on the same reverse proxy, it is best for me to take all the sites down and have acme.sh get all the certs at 1 time. Each cert is a separate transaction, which takes about 90 sec each, so being off-line about 20 minutes when I'm renewing certs is a significant outage for all the different services using certs.

For patching systems, I use a bash script too. A simple loop, but the order that the systems are patched matters greatly to me.  I use ansible mostly for post-install configurations and for keeping the /etc/hosts files current.  Some day I might trust internal DNS enough to end the use of hosts files, but I've been burned previously.

I've played with all the other DevOps tools. Most are 10x worse than the problem they are supposed to solve. Some releases of Ansible break enough things that I'm cursing that team too. Seems they were like the Ruby/Rails guys, deprecating things every 2 yrs, so stability was always a moving target.  And they'd deprecate STUPID things that didn't matter (Ansible project). Changing things for the sake of change and no other reason bothers me greatly.  systemd, resolvconf, netplan, all fall into that same category.  Oh, how I miss 10.04. That was the best Ubuntu Server from a "meets expectations" standpoint.  No surprises. No Wayland. No Unity. No netplan. No Snapd.  I miss releases that were stable, without surprises and without foolish changes.

---

### Post by HermanAB on 2019-10-11
"No surprises. No Wayland. No Unity. No netplan. No Snapd. I miss releases that were stable, without surprises and without foolish changes." - I'm sorry to say, but if you want stability, then you should use Slackware or OpenBSD, not Ubuntu.

---

### Post by TheFu on 2019-10-11
> **HermanAB said:**
> "No surprises. No Wayland. No Unity. No netplan. No Snapd. I miss releases that were stable, without surprises and without foolish changes." - I'm sorry to say, but if you want stability, then you should use Slackware or OpenBSD, not Ubuntu.

I did run Slackware for about a decade, after moving off SLS. Slackware was the easier release. ;)  I don't miss the lack of package management. APT is really good.  20.04 will help me determine which servers we choose for the next round of upgrades. If netplan is still broken and snapd are forced, we'll be leaving Canonical.  So long and thanks for the memories.  Their goals and our goals don't seem to align any longer.

BSD needs much better hypervisor support to be considered.

---

