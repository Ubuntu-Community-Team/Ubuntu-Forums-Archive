---
title: "[SOLVED] cannot upadate"
date: 2008-05-05
forum: General Help
---

### Post by justborn on 2008-05-05
when i tried to update using synaptic and update manager i got this error

[COLOR="Red"]E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.[/COLOR]
and when i tried did command in the terminal i get this

[COLOR="Red"]sudo: unable to resolve host appy-desktop
[/COLOR]
help me !

---

### Post by kesman on 2008-05-05
Open terminal and run
```

sudo apt-get update
sudo dpkg --configure -a

```
and post the errormessages here. Also, is your hostname appy-desktop?

---

### Post by justborn on 2008-05-05
[COLOR="Red"]appy@appy-desktop:~$ sudo apt-get update
sudo: unable to resolve host appy-desktop
appy@appy-desktop:~$ sudo dpkg --confifure -a
sudo: unable to resolve host appy-desktop
appy@appy-desktop:~$ 
[/COLOR]
yes appy -desktop is my host name

---

### Post by forestpixie on 2008-05-05
Had this yesterday with someone else - can you open a terminal and run these commands, post the whole output here please

```
cat /etc/hosts
cat /etc/hostname
```

---

### Post by justborn on 2008-05-05
[COLOR="Red"]appy@appy-desktop:~$ cat /etc/hosts
127.0.0.1 localhost
127.0.1.1 appy-desktop.AIRTEL

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
appy@appy-desktop:~$ cat /etc/hostname
appy-desktop
[/COLOR]

---

### Post by forestpixie on 2008-05-05
Edit the first one - use nano, to save file Ctrl+O then enter, Ctrl+X to exit. Don't know if you'll need to reboot for it to take effect, but maybe.

```
sudo nano /etc/hosts
```

go to second line and remove .AIRTEL
then save and exit, check that change has taken effect with cat /etc/hosts

Try these again - if you get hosts error again reboot
```
sudo apt-get update
sudo dpkg --configure -a
```

---

### Post by chrisccoulson on 2008-05-05
As sudo doesn't work, you'll have to edit these files without sudo from recovery mode. To get to recovery mode, press [ESC] as GRUB loads, then use the arrow keys to select the recovery mode option from the GRUB menu.

---

### Post by forestpixie on 2008-05-05
:oops:

Forgot that - the other way would be to use gksudo and gedit

[http://ubuntuforums.org/showpost.php?p=4872544&postcount=4](http://ubuntuforums.org/showpost.php?p=4872544&postcount=4)

---

### Post by justborn on 2008-05-05
i cannnot get u ***_forestpixie_***

---

### Post by roderick on 2008-05-05
The entry in /etc/hosts is incorrect.

edit it with gedit or kwirte or something and make the appy-desktop line without the .AIRTEL (the .AIRTEL is what's breaking it).

sudo gedit /etc/hosts

Then make the change to remove .AIRTEL and exit/save the changes.

---

### Post by roderick on 2008-05-05
> **chrisccoulson said:**
> As sudo doesn't work, you'll have to edit these files without sudo from recovery mode. To get to recovery mode, press [ESC] as GRUB loads, then use the arrow keys to select the recovery mode option from the GRUB menu.

sudo works, it's the networking thats broke with the incorrect hostname.

should be no need to recover.

---

### Post by justborn on 2008-05-05
dude i completely get u but the thing is that no sudo command works
i am able to do i without sudo but then i cannot save/exit.

please help me

---

### Post by chrisccoulson on 2008-05-05
> **roderick said:**
> sudo works, it's the networking thats broke with the incorrect hostname.

should be no need to recover.

No, sudo ***doesn't*** work, as already pointed out. sudo tries to resolve the hostname, but fails in this case due to the broken networking

---

### Post by forestpixie on 2008-05-05
Either boot into recovery mode and use nano to edit the file - recovery has root rights. 
Or open a terminal and run gksudo as a command - it will give you a box to enter a command in - gedit /etc/hosts then edit the file.

---

### Post by roderick on 2008-05-05
I didn't get that from the post sorry.

Oh well, if 'sudo' doesn't work, then you are unfortunate enough to require (as suggested) booting into some recovery mode.

---

### Post by justborn on 2008-05-05
i was not able to do it using gedit 
because the sudo command itself doesnt work.
i tried it out without sudo and couldnt save.
i did it gui way ,editing network settings
and now i have left the [COLOR="Red"]DOMAIN NAME[/COLOR] blank&changed the host by deleting the old host and entering a new  one without AIRTEL,doing all this has corrected my problem,and i am able to update now.
but i am afraid that leaving the [COLOR="Red"]DOMAIN NAME[/COLOR] blank
will cause me net problems




will it?

---

### Post by forestpixie on 2008-05-05
I've no idea - but I wouldn't change soemthing unless I either knew what it was doing or was deliberately trying to break my system.

If it does cause a problem you have sudo back and can edit the file again and just make the changes that needed to be made.

---

### Post by roderick on 2008-05-05
Apparently there is a known bug about this DOMAIN NAME and sudo. Search for it in Launchpad and add your notes. 

This will help the team in resolving this going forward.

---

### Post by justborn on 2008-05-06
kk ,lets end it all .
 purpose of the thread met.
thank u all of u

---

### Post by justborn on 2008-05-06
hey, and i don't have the [COLOR="Red"]thread solved[/COLOR] option under [COLOR="Red"]thread tools[/COLOR] menu

---

### Post by chrisccoulson on 2008-05-06
> **roderick said:**
> Apparently there is a known bug about this DOMAIN NAME and sudo. Search for it in Launchpad and add your notes. 

This will help the team in resolving this going forward.

The bugs you're referring to are [bug 185209]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/185209") and [bug 32906]("https://bugs.edge.launchpad.net/ubuntu/+source/sudo/+bug/32906")

---

### Post by tipiglen on 2008-05-06
Similar problem.  Update just hung.  SOLVED by editing /etc/hosts as recommended.

I did it by going into su in a terminal. then gedit /etc/hosts...

For those who don't know how to set up this capability, check System/Administration/Users and Groups/

Unlock (normal password)
select 'root' and set a password you can remember

There's also the possibility of a 'root terminal' which you can get added to your Applications/Syatem menu.

The usual caution notice applies: DO NOT MAKE A HABIT OF WORKING AS ROOT - IT CAN CAUSE CONSIDERABLE GRIEF.

&#30693;&#13;&#32773;&#13;&#19981;&#13;&#35328;&#12290;&#13;&#35328;&#13;&#32773;&#13;&#19981;&#13;&#30693;&#12290;&#13;
(those who talk don't know; Those who know don't talk)
xx
ed

---

### Post by tipiglen on 2008-05-06
testing - update successful, Thanks for the help.
xx
ed

---

