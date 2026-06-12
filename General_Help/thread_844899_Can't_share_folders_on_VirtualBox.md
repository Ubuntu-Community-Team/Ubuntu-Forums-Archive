---
title: "Can't share folders on VirtualBox"
date: 2008-06-30
forum: General Help
---

### Post by PauGNU on 2008-06-30
Hi

Two weeks ago I was able to enable shared folders on VirtalBox. I added these folders just by the "Shared folders" dialog on the specific Virtual Machine.

I dind't do anything else, and it worked well. Then I reinstalled Ubuntu (reasons unknown, hehe) and when I try to share folders, Windows is not able to detect them. 

What I do is:

1. Virtual Machine is off. I go to the preferences dialog, Shared Folders and add the folder I want to share.

2. Start the VM, “My Networking Places” -> “Entire Network” -> “VirtualBox Shared Folders”.

3. And it is supposed that Windows should detect the virtualbox shared folder, but... it just shows "VirtualBox Shared Folder" like if it wasn't anything inside (mean not shared folders).

I'm using VirtualBox 1.6.2 on Ubuntu 8.04.


Any ideas?

Thanks!

---

### Post by northwestuntu on 2008-06-30
same here :confused:

---

### Post by mempman on 2008-06-30
After you start up your virutal machine, you have to go into devices--> "Install Guest Additions."  After that you can mount your shared device using by going into Device->"Shared Folder."

After the above is completed, you can access your shared drive via windows with the following:


net use x: \\vboxsvr\share-name


This should get you on your way.

---

### Post by PauGNU on 2008-06-30
Still the same :(

There is something wrong here. Maybe it's the virtualbox version cause there are many 1.6.2 revisions...

I'll try downloading older versions.

Thanks :(

---

### Post by airflow on 2008-06-30
> **PauGNU said:**
> Still the same :(

There is something wrong here. Maybe it's the virtualbox version cause there are many 1.6.2 revisions...

I'll try downloading older versions.

Thanks :(

Havin' the same problem here. Did you find a solution yet?

Thanks,
airflow

---

### Post by marcv700 on 2008-06-30
Hi all,

Had to upgrade to 1.6 all works well, additions installed

Same problem with shared folders.

when I use the command net use e: \\vboxsvr\nameusedinadditions

The message I get is that it cannot find the name of the network (which I have defined as vboxsvr as per the documentation manual) (p 60 user manual)

So maybe we need to have or define another name for the server

BTW the VirtualBox Shared Folders on guest XP did not appear in 1.5

Marc

---

### Post by airflow on 2008-06-30
> **marcv700 said:**
> 
Had to upgrade to 1.6 all works well, additions installed


Hi,

I found the solution in the meantime. It's not about upgrading to 1.6, as I started already with 1.6.2 (I used the "commercial" version from the homepage of the developers, not the version in ubuntus repositories).

The problem seems to be a broken installation-routine for the additions. I installed the additions on two different virtual maschines (both Windows XP, but different flavours). On both machines I had the problem that after configuring the shared folders they did not appear in the network-neighbourhood of the maschines.

To fix the problem you just have to install the additions *again* (a second time) over the old installation, i.e. without de-installing the previous installation first. Then it works as it should. I could reproduce this with both my virtual-maschines. I got this hint from another forum, where others where having the same problem and solution.

regards,
airflow

---

### Post by marcv700 on 2008-07-01
Thank you Airflow.

Got the sharing to work. :D

Reinstallation solved the problem

Marc

---

### Post by MxGB on 2008-07-10
> **airflow said:**
> To fix the problem you just have to install the additions *again* (a second time) over the old installation, i.e. without de-installing the previous installation first. Then it works as it should. I could reproduce this with both my virtual-maschines. I got this hint from another forum, where others where having the same problem and solution.

regards,
airflow
Great, worked for me thanks.

---

### Post by Taxman415a on 2008-07-31
> **airflow said:**
> 
To fix the problem you just have to install the additions *again* (a second time) over the old installation, i.e. without de-installing the previous installation first. Then it works as it should. I could reproduce this with both my virtual-maschines. I got this hint from another forum, where others where having the same problem and solution.

regards,
airflow

I'm in the same situation, running 1.6.2 on Ubuntu 8.04 and unfortunately the above didn't work for me, but I found a thread that suggested removing the 1.6.2 guest additions and installing the 1.6.0 and that did work fine. 
[http://forums.virtualbox.org/viewtopic.php?t=7146&sid=99f6170bfb52316878b61aadad32fdd6](http://forums.virtualbox.org/viewtopic.php?t=7146&sid=99f6170bfb52316878b61aadad32fdd6)

Everything else seems to work fine too.

---

### Post by dimeotane on 2008-09-20
same problem here when I upgraded from gutsy to hardy and reinstalled virtualbox.  Now I can't access the shared folders.  Reinstalling guest additions v 1.6.6 doesn't seem to change anything.  downloading vbox 2.02 and installing that update including the virtualbox additions fixed the problem.

---

### Post by jdtfk on 2008-10-19
Just do what **mempman** said and you'll be ok.
thanks btw =D
Using Version 2.0.2

---

