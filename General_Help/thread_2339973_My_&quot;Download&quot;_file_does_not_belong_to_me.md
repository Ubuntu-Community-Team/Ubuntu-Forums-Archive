---
title: "My &quot;Download&quot; file does not belong to me anymore"
date: 2016-10-14
forum: General Help
---

### Post by gourney on 2016-10-14
Hi everyone,
  
I had just noticed that my Download folder wasn't accessible anymore. When I try to get into the folder it returns me that I don't have the permissions of access.
In fact when I go to folder properties, I see that the file belong to "user #105757", I really don't see who is this user.

If I want to access the folder I can but only by typing ```
chmod o+rx Downloads
``` It looks that my user isn't responsible of this.

I'm a beginner and I do not know what's really happening, but when I list my users on a graphic interface I only see : My user, and Invitee.

Do you know what's happening ?

---

### Post by QIII on 2016-10-14
Hello!

Could you answer the following questions, please?  This should help with diagnosis.

Do you have desktop sharing enabled?  
Is your machine on a network others have access to?  
Do you have an active firewall?  
Have you recently connected to an unsecured WiFi, such as at a cafe?
Is your computer in a secure location where others do not have access?  
Do you use third party desktop sharing or meeting software?

---

### Post by gourney on 2016-10-14
Hello!

Desktop sharing isn't allowed in my cp.
My machine is on my neighbour's network which had kindly gave me his wpa key, however, I know it could be a problem.
I have Netfilter by default.
I had connected to the wifi of my university during the last days.
My computer is usually locked at my home, but others could have access to it during common works at the uni.
I do not use any third party desktop sharing or meeting software.

Thank you for the answer.

---

### Post by ajgreeny on 2016-10-14
It might help us if you can please show us the output of command ```
ls -la
``` in terminal.
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by yancek on 2016-10-14
If you get some unknown user "user #105757" as the owner of the Downloads directory in your user /home directory you need to change the owner.  Try this, changing 'gourney' to whatever the actual user name is. If you can access the Downloads directory by giving others rx permissions, this should work although you'll still have to watch to see how that changed to start with.

```
sudo chown -R gourney /home/gourney/Downloads
```

---

### Post by gourney on 2016-10-14
In **home **it gives :

```
total 468
drwxr-xr-x 33 quentin quentin   4096 Oct 14 22:01 .
drwxr-xr-x  4 root    root      4096 Oct 10 23:28 ..
drwx------  3 quentin quentin   4096 Sep 22 19:11 .adobe
-rw-------  1 quentin quentin   8830 Oct 14 22:02 .bash_history
-rw-r--r--  1 quentin quentin    220 Sep 22 01:30 .bash_logout
-rw-r--r--  1 quentin quentin   3771 Sep 22 01:30 .bashrc
drwxrwxr-- 11 quentin quentin   4096 Oct 10 22:25 .BitwigStudio
drwxrwxr-x  6 quentin quentin   4096 Sep 24 00:29 Bitwig Studio
drwxrwxr-x  2 quentin quentin   4096 Sep 28 00:29 BOOKS
-rw-rw-r--  1 quentin quentin   9133 Oct 10 23:06 Buddy.odt
drwx------ 32 quentin quentin   4096 Oct 11 00:10 .cache
drwxrwxr-x  3 quentin quentin   4096 Oct  8 09:03 Calibre Library
drwx------  3 quentin quentin   4096 Sep 22 23:50 .compiz
drwx------ 30 quentin quentin   4096 Oct  2 14:50 .config
drwxrwxr-x 15 quentin quentin   4096 Oct 13 22:00 Cours
drwx------  3 root    root      4096 Sep 24 17:40 .dbus
drwxr-xr-x  3 quentin quentin   4096 Oct 14 19:05 Desktop
-rw-r--r--  1 quentin quentin     25 Sep 22 01:37 .dmrc
drwxr-xr-x  4 quentin quentin   4096 Oct 10 23:04 Documents
dr-x---r-x 70  105757  100513  12288 Apr 21  2015 Downloads
-rw-r--r--  1 quentin quentin   8980 Sep 22 01:30 examples.desktop
drwx------  3 quentin quentin   4096 Oct 14 22:01 .gconf
-rw-r-----  1 quentin quentin      0 Oct 14 18:45 .gksu.lock
drwx------  3 quentin quentin   4096 Oct 14 22:01 .gnupg
-rw-------  1 quentin quentin  19034 Oct 14 22:01 .ICEauthority
-rw-rw-r--  1 quentin quentin 231859 Oct 14 18:46 Image.png
-rw-rw-r--  1 quentin quentin     53 Oct  4 17:53 .jackdrc
drwxrwxr-x  3 quentin quentin   4096 Sep 25 00:34 .java
drwx------  4 quentin quentin   4096 Sep 24 17:48 .local
drwx------  3 quentin quentin   4096 Sep 22 19:11 .macromedia
drwxrwxr-x  4 quentin quentin   4096 Oct  4 18:52 .mixxx
drwxr-xr-x  2 quentin quentin   4096 Sep 22 17:27 Movies
drwx------  4 quentin quentin   4096 Sep 22 01:38 .mozilla
drwxr-xr-x  5 quentin quentin   4096 Oct 10 20:53 Music
drwxrwxr-x  2 quentin quentin   4096 Sep 24 00:29 .oracle_jre_usage
drwxr-xr-x  2 quentin quentin   4096 Oct 13 17:37 Pictures
-rw-r--r--  1 quentin quentin    655 Sep 22 01:30 .profile
drwxr-xr-x  2 quentin quentin   4096 Sep 22 01:37 Public
drwxrwxr-x  2 quentin quentin   4096 Oct 14 17:35 rosegarden
drwxr-xr-x  2 root    root      4096 Sep 25 00:21 .rpmdb
-rw-rw-r--  1 quentin quentin   2713 Oct  4 18:52 .rubberband.wisdom.d
drwx------  6 quentin quentin   4096 Oct 14 20:56 .Skype
-rw-r--r--  1 quentin quentin      0 Sep 22 15:15 .sudo_as_admin_successful
drwx------  2 quentin quentin   4096 Oct 11 00:39 .synaptic
drwxr-xr-x  2 quentin quentin   4096 Sep 22 01:37 Templates
-rw-rw-r--  1 quentin quentin   2557 Oct  8 10:11 .terminatorXrc
drwx------  4 quentin quentin   4096 Sep 24 17:58 .thunderbird
-rw-------  1 quentin quentin     55 Oct 14 22:01 .Xauthority
-rw-------  1 quentin quentin     82 Oct 14 22:01 .xsession-errors
-rw-------  1 quentin quentin   1331 Oct 14 21:54 .xsession-errors.old


```

---

### Post by gourney on 2016-10-14
Ok thank you *yancek* I didn't know this command. It was useful.

---

### Post by QIII on 2016-10-14
> **yancek said:**
> ....you'll still have to watch to see how that changed to start with.

That is the $64,000 question ...

From the information presented, it is my opinion that this represents an intrusion and compromise.  That, also in my opinion, can only be greeted with a full overwrite and reinstall.

---

### Post by gourney on 2016-10-14
Erg, I hope it worth the price.

---

### Post by deadflowr on 2016-10-14
See what the oddball user is:
```
getent passwd | grep 105757
```
and see what groups they belong to:
```
id 105757
```
fwiw

---

### Post by gourney on 2016-10-14
Thx, there's nothing in both entries, looks like the smart guy left the field properly.

Do you know if any logs on my system would allow us to retrieve an imprint on what he did before erasing all this ?

It may be too difficult to do that but I'll be happy to know if, and how we can do this.
As well as know how to protect my computer for the next time, so do you think that the default Netfilter is a sufficient firewall for an everywhere internet use ?
Do you think that installing an antivirus in the future can protect me from those attacks ?
Do we can protect ourserlves properly without having an antivirus ?

---

### Post by ajgreeny on 2016-10-15
I also see that the .dbus  and .rpmdb folders in your /home are owned by root.

The .dbus folder should not be owned by root but by you as user, and probably the same applies to the .rpmdb folder, though I do not know what that is for; I do not have such a folder in my home.

I certainly recommend you run the command ```
sudo chown -R quentin /home/quentin
``` to make sure all your home folders are owned by you, but like yancek and QIII I also wonder how this incorrect ownership occurred in the first place.

---

### Post by gourney on 2016-10-16
Thank you ajgreeny, I did this but I formated my computer securely in order to prevent others aspects of what's an attack, in my opinion.
Still, I'm asking me about if my neighbor hacked me or something because he is the owner of the network I use. And I don't have the money to afford me internet.
Do you think that it is possible to block all connections coming from other machines of the local network I use with a firewall ?

---

