---
title: "Hardy Heron Failure Partial Upgrade"
date: 2008-06-23
forum: General Help
---

### Post by logoodnix on 2008-06-23
Hi,
There seem to be a lot of problems for people upgrading from 7.10 to 8.04. I am having one of them but having trouble finding a helpful thread. Can anyone point me in the right direction?
Here's what happened.
I began the upgrade  from the upgrade manager on my laptop and as it was scanning new packages to be installed the system froze. I waited a 20 minutes or so to see if it was just taking its time but nothing. So I restarted the laptop. When I did so I was told by the Upgrade Manager that "not all upgrades can be installed"  to run only a partial upgrade  due to  "a previous upgrade that didn't complete." I went ahead with the partial upgrade that asked me to restart after it was complete. Upon doing so, the Human theme would not load and i'm forced to log in on an unfamiliar login page. After logging in, the OS still acts like 7.10, the windows have no window bars and can not be maximized etc.
When I go to system> admin> system monitor> system it tells me I have...
"release 8.04 (hardy)
Kernel Linux 2.6.22-15
GNOME2.22.2"
If I try a partial upgrade from the update manager it tells me that an, "upgrade from 'Hardy to Gutsy' is not supported with this tool."

I considered uninstalling ubuntu but i have a dual partition and no XP CD to reboot from. Also if there is a way to finish a complete up grade that would be preferred.

Toshiba A-100
Genuine Intel T2400
:confused:

---

### Post by maheshasolkar on 2008-06-23
I have had similar upgrade problems when I started off with a non-up-to-date installation. If you had pending updates to 7.10 when you started a dist-upgrade, this might happen.

To address the problem at hand, could you open the Synaptic Package Manager. Reload the sources and click the 'Mark All Updates' button. Apply the changes. After updates marked are installed, you may have to repeat this one more time to get all updates.

I would like to point out though, that I followed this process to get me out of the 'partial update' cycle. It's not a known solution. Your mileage may vary..

---

### Post by logoodnix on 2008-06-24
Thanx for the tip but before i could try it i tried updating packages through the terminal and now after logging in I get a black screen. 

Not sure where to satrt from the fail safe terminal... anyone?:confused:

---

### Post by tribble222 on 2008-06-24
I'm not sure if I understand your latest question but if you're trying to upgrade your packages from the terminal then you would run:

$ sudo apt-get update
$ sudo apt-get upgrade

---

### Post by logoodnix on 2008-06-24
tribble, 
that's what I tried to do earlier. But now I get a black screen after logging in (in recovery mode).
Though I CAN log-in to the "fail safe" terminal.
Now,when I try your suggestion I get...
> dpkg was interruped, you must manually run 'dpkg --configure -a' to correct the problem

then when i do...
> dpkg:requested operation requires superuser privilege

I'm hoping there is some kind of action I can take from the terminal. Either to  finish  the upgrade or to be able to log-in again.

---

### Post by tribble222 on 2008-06-24
I see.  Does running either of those commands give you any interesting output?

---

### Post by logoodnix on 2008-06-24
Nothing. Just those messages.

---

### Post by tribble222 on 2008-06-24
You don't get something like this?

```
$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

If not, maybe your terminal is messed up?  What if you try it on a virtual terminal? (press ctrl-alt-f1 and log in.  To get back to gnome press either ctrl-alt-f7 or ctrl-alt-f9)

---

### Post by conscious on 2008-06-24
You should run it with superuser privilege:
```
**sudo** dpkg --configure -a
```

Another useful command is
```
sudo apt-get dist-upgrade
```
(it's "distribution upgrade").

---

### Post by logoodnix on 2008-06-24
Went to the virtual terminal (ctrl-alt-f1) and logged in. 
typed in...
> sudo dpkg --configure -a
got alot of output ended with...
 > ldconfifig deferred processing now taking place 

logged back into GNOME successfully (still in recovery I assume) and I have I have lots of crash and restart notices to look at but at least I'm back in.
:) thanx for your help!!!!!!!:)

---

### Post by caljohnsmith on 2008-06-24
You may also want to try doing a "sudo apt-get install -f" to see if apt-get needs to fix any broken packages. In case you're wondering what that command will do, according to the man page for apt-get, the -f option is to "Fix; attempt to correct a system with broken dependencies in place. This option, when used with install/remove, can omit any packages to permit APT to deduce a likely solution."

After that, I would also run "sudo apt-get update" and then "sudo apt-get upgrade" to make sure your system is truly up-to-date.

---

