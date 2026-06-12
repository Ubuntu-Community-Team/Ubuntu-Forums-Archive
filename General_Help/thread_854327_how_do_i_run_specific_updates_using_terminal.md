---
title: "how do i run specific updates using terminal?"
date: 2008-07-09
forum: General Help
---

### Post by bluepowder7 on 2008-07-09
so, i've relegated myself to using only the terminal when it comes to installing, removing, or updating the OS on my desktop machine.  why?  so that i get forced to learn more about the power of the terminal!  i only open up synaptic to check package names and descriptions, then close it and run the "sudo aptitide install" command in terminal.  anyhoo....

when it comes to doing updates (security, required, recommended, patches, blah blah blah), how do i do them in the terminal?  using the gui update manager, i can select which ones to apply and which ones to skip (checkmarks - which is nice enough to then tell me that i can't have those other 4 updates if i don't do this 1 update over here), but is there a way of doing that in terminal?

also, how can i tell the terminal "do security updates only", or "do updates and patches to the packages and libraries, but don't install a newer version of the top level package"? (example, don't upgrade my openoffice to 2.5 if i have 2.4.1, or don't upgrade my firefox-2 to firefox-3.0, and certainly don't ever upgrade my 8.04 to 8.10 when it becomes available)

as a bonus question - what types of updates / upgrades should i do when it comes to my file server?  on that one, i am 100% stuck to using terminal.  it's currently running 7.10, but i'll install 8.04LTS soon since i have to rework some of the stuff on it anyways (LVM, CUPS)

---

### Post by Dansaycool on 2008-07-09
is 

sudo apt-get update
sudo apt-get upgrade

any help to updating your computer through terminal?

---

### Post by lamego on 2008-07-09
On this particular case, using the terminal is more a paranoia than an useful purpose.
You can install the updates for just a list of packages with:
```
sudo apt-get install package1 package2...
```
Yes, if the packages are installed by there is an updated availabled the apt-get install with install those updates and related dependencies.

---

### Post by avtolle on 2008-07-09
If I understand the question, from the CLI```
sudo aptitude update && sudo aptitude install NAMEOFUPDATE
```to be sure the dependencies are also installed.

---

### Post by bluepowder7 on 2008-07-09
well, so far i've been doing

```
sudo aptitude update && sudo aptitude safe-upgrade
```

which from what i can see does all the security and recommended updates, but doesn't do JUST security, and it doesn't let me pick which recommended updates i want to apply.

also, on the server to which i only connect via SSH, how can i even know which updates are available so that i can manually do ```
sudo aptitude install <package_name>
```?

---

### Post by avtolle on 2008-07-09
Yes, using the sudo aptitude safe-upgrade command will install all security and recommended updates. 

As to your question about the server, that is without my competence to answer. Generally, how is one notified of updates on a server set-up with no GUI?

EDIT: It seems to me, from memory, that when one does a sudo aptitude safe-upgrade command that a list of available updates is provided, and then one is asked whether to proceed. If my recollection is correct, a user might run the command manually when on the box from which the SSH connection is had shows updates available, and then see what options there are, and (for lack of a better way) write down the ones desired; then abort the safe-upgrade command, and do the install command with the package names for those desired.

---

### Post by cariboo on 2008-07-09
The aptitude manual is your friend .

```
man aptitude
```

I don't have any updates pending, so I'm not sure if it will work:

```
sudo apttitude --visual-preview
```

Jim

---

### Post by Hooya on 2008-07-09
> **cariboo907 said:**
> The aptitude manual is your friend .

```
man aptitude
```

I don't have any updates pending, so I'm not sure if it will work:

```
sudo aptitude --visual-preview
```

Jim

(fixed a line of code for you, but that's not my point)

The visual-preview is nice, but I don't see why that's any better than just doing [sudo synaptic] and doing it that way, since that interface is the same concept only it's better in synaptic...  Seems silly to me.

safe-upgrade seems to be what the OP is looking for.

Just out of curiosity, if when 8.10 is released I do [sudo apt-get update && sudo apt-get upgrade] it's not going to upgrade me to 8.10 is it?  Otherwise how are people still sticking to their 6.06 releases so frequently if they have an "up to date" 6.06 release?  I wouldn't think it would upgrade me to 8.10, but the OP seems to think that it might happen by accident and I just want someone to clarify that issue.

---

### Post by avtolle on 2008-07-09
No, that will not upgrade you to 8.10 unless you have enabled the 8.10 repositories in some way before executing the commands; and, as I understand it, without a sudo aptitude dist-upgrade command in there as well, the new kernel and associated files will not be downloaded, either.

---

