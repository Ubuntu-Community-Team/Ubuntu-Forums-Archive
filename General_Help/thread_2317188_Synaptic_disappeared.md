---
title: "Synaptic disappeared"
date: 2016-03-14
forum: General Help
---

### Post by Lloydb39 on 2016-03-14
I got the Dropbox deb file and wanted to install it with Synaptic. Unity can't find Synaptic, but Software Center says it is installed. I tried to remove it, thinking I would re-install and it told me it would have to remove Software Center as well, which I declined. What do I do now?
Update: Worst than I thought. Unity can't find ANY of my apps -- Libre, Gimp, etc. What's up with that?

---

### Post by howefield on 2016-03-14
Do you get any output from the terminal command...

```
which synaptic
```

If not, what does

```
sudo apt-get install synaptic
```

give you ?

---

### Post by Lloydb39 on 2016-03-14
I get this for which:
/usr/sbin/synaptic

---

### Post by howefield on 2016-03-14
So, try..

```
synaptic-pkexec
```

---

### Post by Lloydb39 on 2016-03-14
Thanks. That started Synaptic. What about the broader problem? Do I have to use the terminal to run all my apps that aren't on the desktop, since I can't find them with the dash?

---

### Post by howefield on 2016-03-14
> **Lloydb39 said:**
> What about the broader problem? Do I have to use the terminal to run all my apps that aren't on the desktop, since I can't find them with the dash?

No you shouldn't, you might find a logout/log back in will show your apps, not sure what you have done. I only wanted to ascertain as a first step that you had synaptic installed.

Does

```
Super + a
```

allow you to search and find your apps in the Dash ?

In any event, as far as I know you can't install local deb packages with synaptic, What is wrong with simply double clicking the deb package, that will launch whatever your system is defaulted to open and install deb files. Probably Software Centre.

---

### Post by Lloydb39 on 2016-03-14
Apparently, I didn't have "super." 
Installed and got this:
Reading state information... Done
The following packages were automatically installed and are no longer required:
  account-plugin-windows-live libmpdec2 winff-doc
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  super
0 upgraded, 1 newly installed, 0 to remove and 14 not upgraded.
Need to get 102 kB of archives.
After this operation, 835 kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates/universe super amd64 3.30.0-6+deb7u1build0.14.04.1 [102 kB]
Fetched 102 kB in 0s (236 kB/s)
Selecting previously unselected package super.
(Reading database ... 1043100 files and directories currently installed.)
Preparing to unpack .../super_3.30.0-6+deb7u1build0.14.04.1_amd64.deb ...
Unpacking super (3.30.0-6+deb7u1build0.14.04.1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Setting up super (3.30.0-6+deb7u1build0.14.04.1) ...
Clicking on the deb package problem would work, if I had sense enough to do it. I was distracted by the problem with the dash. That still exists: typing the name of any of my installed apps in the dash shows only files associated with them but not the application itself. Is there a fix for that?
By the way, tried "super + a" and super told me there was no "+" option.

---

### Post by LukeMorrison on 2016-03-14
In regards to your second question, regarding only seeing the files, I am not a computer with Ubuntu / Unity, but I believe at the bottom of the dash, there are different scopes that will filter what type of files it shows.  I would select different options at the bottom to see if you can get your applications "back."  I think the first one on the left relates to All.

---

### Post by howefield on 2016-03-14
> **Lloydb39 said:**
> Apparently, I didn't have "super." 

Apologies, my mistake for not being clearer, I meant the key combination, Super + a (Super being the key with the windows flag on it, usually to the left of the Alt key)

Sorry.

> Clicking on the deb package problem would work, if I had sense enough to do it.

Cool..

> I was distracted by the problem with the dash. That still exists: typing the name of any of my installed apps in the dash shows only files associated with them but not the application itself. Is there a fix for that?

Assuming a logout/back in doesn't solve it, you could try..

```
sudo apt-get purge unity-lens-applications    
sudo apt-get install unity-lens-applications
```

Then reboot.

---

### Post by Lloydb39 on 2016-03-14
Argggh. Had tried logout, no change. Tried it again, apps are back, problem solved. One last question. Since I installed "super" do I really need it, or should I uninstall?

---

### Post by howefield on 2016-03-14
> **Lloydb39 said:**
> Argggh. Had tried logout, no change. Tried it again, apps are back, problem solved. One last question. Since I installed "super" do I really need it, or should I uninstall?

If you didn't have it before, you probably don't need it now.. feel free to uninstall (or leave).

> Super allows specified users to execute scripts (or other commands)
as if they were root; or it can set the uid and/or gid on a
per-command basis before executing the command.  It is intended to be
a secure alternative to making scripts setuid root.



---

