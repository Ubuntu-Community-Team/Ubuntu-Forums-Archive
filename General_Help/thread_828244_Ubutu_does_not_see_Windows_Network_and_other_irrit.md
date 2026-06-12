---
title: "Ubutu does not see Windows Network and other irritants"
date: 2008-06-13
forum: General Help
---

### Post by kriemer on 2008-06-13
Two installations of Ubuntu v8.04 on two nearly identical computers (difference only in graphic card and Ram); one in my house the other my friends.  Both of these machines are connected to other computers (same type Ethernet card and router) with WinXP installed.

My friend can connect to his Windows machines and I can not.  Here too there is a minor difference as his Windows computers do not have AV software installed and mine do (though I have turned off AV protection, firewall and rebooted all computers to try and get this working).  Going to "Places" > "Network" I see a "Windows Network".  Clicking on that I see "Workgroup".  Clicking on that... nothing.  I have reinstalled Ubuntu several times in an attempt to fix this.

As a secondary and less important issue; any attempts I make to set Visual Effects to “Extra” fail.  My graphics card is a Sapphire ATI Radeon HD2400 Pro.  Whatever new settings I add cause the screen to either jumble or go black.  My only solution is to reinstall Ubuntu (not the optimum solution).  Any way to recover without reinstalling, so I can continue to play around?

As you can see from above, my solution for problems is reinstalling the OS.  My premise is that I have caused the problems in the first place, though I am being dissuaded of this idea over a large number if reinstallations that have not gotten rid of my problems.

Any and all suggestions are welcome.

Thanks

K

---

### Post by Gannon8 on 2008-06-13
Is SAMBA installed?
```
sudo apt-get install samba
```

Why do you have to reinstall after clicking on the workgroup button?

---

### Post by kriemer on 2008-06-13
Yes neglected to mention this.

Once I installed Samba I was able to "see" the drive on the Linux machine from my Windows machines.  So I know that there is a connection of sorts.

Thanks

k

---

### Post by cariboo on 2008-06-13
Is your Windows computer setup with the standard workgroup eg: MSHOME

If so just change it to WORKGROUP and you should be OK.

Jim

---

### Post by eriqjaffe on 2008-06-13
> **kriemer said:**
> Once I installed Samba I was able to "see" the drive on the Linux machine from my Windows machines.  So I know that there is a connection of sorts.samba is for sharing Linux to Windows.  You'll need to install (at least) smbfs and smbfs-common to see Windows shares.

---

### Post by kriemer on 2008-06-13
Windows workgroup is indeed "workgroup".

k

---

### Post by kriemer on 2008-06-13
Install smbfs and smbfs-common, still nothing.

I also neglected to say my friends setup worked "out of the box". in that he jumped through no installation hoops to get the networking working.

---

### Post by kriemer on 2008-06-13
eriqjaffe (and anyone else)

You said I needed to install "(at least) smbfs and smbfs-common to see Windows shares".  What else should I try adding?

Thanks in advance

k

---

### Post by plucky on 2008-06-14
>  What else should I try adding?

Have you tried adding a share on your Ubuntu computer and seeing if you can see it from windows?

To add a share,open your home folder in Nautilus,select the folder to share(say Documents) right click on folder,scroll to **sharing options**,select **Share Folder**. In share folder tick all the boxes and then see if you can see it from windows.

Another thing is after you install samba etc. have you rebooted? I think I read somewhere that to enable permissions with sharing,you have to reboot after samba installation.


Good Luck

---

### Post by kriemer on 2008-06-14
Plucky,

My problem is the other way about.  I CAN see the Ubuntu machine's hard drives and folders from my Windows machine, but I can not see the Windows machines from Ubuntu.

Thanks for you suggestion.

k

---

### Post by joshsmith on 2008-06-14
hey
if you can, forget browsing through workgroups

just type in the address bar
smb://X

where X is either the ip adress of the computer
or the  name of the computer (ie for an ubuntu computer username-desktop or something similar, windows can find the name in control panel > system)

---

### Post by EmanresuusernamE on 2008-06-14
If you have ZoneAlarm installed, you'll also need to either lower the settings in the trusted zone, or shut it down.  It blocks pings and file sharing requests by default.  :D It's not always the virus scanner's fault, unless of course it is Norton.

---

### Post by kriemer on 2008-06-14
Nope again (!@#$$%#@ frustrating)

I have Kaspersky AV/Firewall, all turned off.  Rebooted Windows and Ubuntu machines.  Still nothing.

I feel like the south end of a horse facing north.

k

---

### Post by kriemer on 2008-06-14
I did try the smb://X "trick" and I can connect Ubuntu to the Windows machine; so there is communications, just not the normal way.

---

### Post by lisati on 2008-06-14
There's a "How to" at [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605) which might provide a few extra ideas on finessing the connection.

---

### Post by aldeby on 2008-06-15
I have the same exact problem: windows sees samba shares, however linux cannot access to windows shared folders (it can only see the windows machine).

With the help of smbtree I managed to figure out that one problem was that I had configured my router and box to resolve host names through OpenDNS. 

However despite reverting to my ISP dns I still can access only to standard **print$** and public. 

Using smb://IPaddress/ShareName works.

I wonder why Hardy has all this samba problems Gutsy didn't. 

I read that these samba problems would have been fixed for 8.04.1 update... I wonder why Ubuntu developers are taking all that time to fix those issues!

---

### Post by kriemer on 2008-06-15
As I noted, the part I find most confusing is that my friends hardware is essentially identical to mine and he does not have this problem, even the routers are the same.  I have not made any changes to router setting though I can not be sure for the next few days if this is true for my friends setup.  

Through all this I have become suspicious/convinced this is a routers setting  problem as my friend 2 Windows machines can both be "seen" from Ubuntu.  

Now not so sure of the Router as being the problem as I ran 7.04 live and could see the Win machines.  DAMN!

Far more difficult than it should be.


Thanks for all comments/suggestions... hoping for more.

k

---

### Post by EmanresuusernamE on 2008-08-25
Quick question, is File and Printer sharing enabled and allowed on your Windows machines?  I know that XP usually won't even show up in My Network if it's not enabled and has something shared on it.

---

### Post by kriemer on 2008-08-25
Yes F&P sharing is set.  As I noted I can connect to the Windows network by manually entering smb://ShareName/.
   
More than just a little strange.

Thanks for getting back to me.

k

---

### Post by pie[3.14] on 2008-09-18
ok i went to network then I clicked workgroup then i replaced workgroup with mshome. I was then sent to the mshome workgroup then when I went back to SMB:/// MSHOME was there. im not sure if this is a temp fix or if it'll stick but hey it works.:):D

---

