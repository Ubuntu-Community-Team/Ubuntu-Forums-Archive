---
title: "My user is gone"
date: 2008-05-05
forum: General Help
---

### Post by Wulfish on 2008-05-05
So my user disappeared on my laptop. I left it running while i went to dinner and i came back and it was at the login screen without my user in the list. When I try to log in by typing it it says that my spelling is wrong :(, which its not. Seeing as thats my only user i can't go into my computer to fix the problem. :confused:

Any advice or thoughts would be readily welcomed.

---

### Post by tacutu on 2008-05-05
read carefully... it is asking for your username or your password? I think you got a locked screen, not a login screen

---

### Post by Zorael on 2008-05-05
If only the user disappeared and not your entire home directory, it's salvageable. If your home directory somehow got swiped, you'll have lost all settings, unless you've got a backup.

If you reboot the system, can you login?

---

### Post by Wulfish on 2008-05-05
I've rebooted several times and nothings different
I also tried cutting all power for awhile cause sometimes that helps but it didn't do anything

how would i salvage though?
If worst comes to worst i guess i'll just try to save my data and get a new computer
thanks for the fast response

---

### Post by Wulfish on 2008-05-05
I've rebooted several times and nothings different
I also tried cutting all power for awhile cause sometimes that helps but it didn't do anything

how would i salvage though?
If worst comes to worst i guess i'll just try to save my data and get a new computer
thanks for the fast response

---

### Post by spec-chum on 2008-05-05
You can use recovery mode to fix this.

Reboot the machine and press ESC when the GRUB prompt comes up to enter the menu.  Select the entry with (recovery mode) beside it.

Once that's booted you'll get a screen with three options on it.  If you select the option to drop to a root shell then you'll drop to the terminal logged in as root so you can make any changes to your system that you need to.  BE VERY CAREFUL.  You can easily trash your system when you're logged in as root.

Anyhow if you run
```

nano /etc/passwd

```
and go to the bottom of the file you'll see your username there so you can check what you should be typing in at the login screen.

If that is what you've been typing in then running
```

passwd myuser

```
(replacing myuser with your username) will allow you to set a new password for that user.  You won't see any characters appearing as you type the password.  That's a security feature.  Just type the correct password twice to set it.

Then enter
```

exit

```
and you should go back to the screen that you chose to drop to a root shell.  Just select the option to resume normal boot and your system should boot up and you can enter your username and new password.

---

### Post by Zorael on 2008-05-05
edit: Above poster's method seems better, ignore me. :>
[quote=me]I've never done this before, but this should work.

Boot up into recovery mode, pick 'root shell' if you get the menu with three options (among 'fix X').

Enter the following.
```
# adduser *<username>*
```
Obviously, replace *<username>* with your old login. It might ask you a few questions, notably what password you want.

The hard part would be to restore your group affiliations. For instance, my user (zorael) is part of these groups (which you can divine by entering **id *<username>*** as illustrated below.)
```
zorael@sunspire:~$ id zorael
uid=1000(zorael) gid=1000(zorael) groups=1000(zorael),4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),107(fuse),109(lpadmin),114(admin),120(sambashare),121(pulse),122(pulse-access),123(pulse-rt)
```
Whereas when I tried to create a guest account just now, it ended up with these groups.
```
zorael@sunspire:~$ id guest
uid=1001(guest) gid=1001(guest) groups=1001(guest)
```


So, if your group affiliations is very skeletal, you may need to manually affiliate yourself with groups via either the terminal or in some Gnome setting (users and groups? It's called User management in KDE). Use my group list as a guide.
```
# usermod -a -G *<group>* *<username>*
```
Notably, if you're not part of adm or admin, I'm not sure you can perform sudo commands.[/quote]

---

### Post by Wulfish on 2008-05-06
Thanks a bunch!!
Work great turned out my friend had changed my user name as a joke :(
aw well

---

