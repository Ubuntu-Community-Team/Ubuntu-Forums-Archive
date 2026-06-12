---
title: "gksudo nautilus error"
date: 2008-04-25
forum: General Help
---

### Post by bossa on 2008-04-25
Hi All
Installed Hardy and all seems well the only problem I have encountered is changing permissions.I can change the owner but not the file access(read/write) using gksudo nautilus. I get this message in terminal :

steve@steve-desktop:~$ gksudo nautilus
Initializing nautilus-share extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


** (nautilus:7075): WARNING **: Unable to add monitor: Not supported
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


--- Hash table keys for warning below:
--> computer:///
--> file:///

(nautilus:7075): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 2 elements at quit time (keys above)

(nautilus:7075): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 2 elements at quit time
seahorse nautilus module shutdown
steve@steve-desktop:~$ 

Can someone please advise me how to correct this 
Thanks

---

### Post by Naatan on 2008-04-25
does "/var/lib/samba/usershares" exist? Try creating it if not, hopefully nautilus will be confident enough to launch.

Otherwise try doing what the error message suggest: enable file sharing. If it's already enabled; disable and enable again.

---

### Post by bossa on 2008-04-25
Hi Naatan

I created folders using what you said and I got this massage in terminal :

steve@steve-desktop:~$ gksudo nautilus
Initializing nautilus-share extension

--- Hash table keys for warning below:
--> computer:///
--> file:///
steve@steve-desktop:~$ 

Still cant change the file access "read/write"
How do you enable file sharing?

---

### Post by Naatan on 2008-04-25
I reckon by going to System > Administration > Samba

I'm unable to verify though; it's crashing for me *sigh* - cba to look into it now.

try executing this in console:

$ sudo aptitude reinstall nautilus-share

---

### Post by bossa on 2008-04-25
Samba is not in system>administrtion ? I tried sudo aptitude reinstall nautilus-share ,but I still cant change read/write and get this message in terminal :

Initializing nautilus-share extension

--- Hash table keys for warning below:
--> computer:///
--> file:///
steve@steve-desktop:~$

:confused:

---

### Post by Naatan on 2008-04-25
Sorry, I think the samba menu is there for me since I've specifically installed samba for my work.

The error only occurs when you try to run nautilus as root right?

try;

$ sudo rm /root/.nautilus

---

### Post by bossa on 2008-04-25
> **Naatan said:**
> Sorry, I think the samba menu is there for me since I've specifically installed samba for my work.

The error only occurs when you try to run nautilus as root right?

try;

$ sudo rm /root/.nautilus

No worries naatan
I get this :
steve@steve-desktop:~$ sudo rm /root/.nautilus
[sudo] password for steve: 
rm: cannot remove `/root/.nautilus': Is a directory
steve@steve-desktop:~$

---

### Post by Naatan on 2008-04-25
*sigh* sorry it's getting late :)

$ sudo rm -R /root/.nautilus

for directories you have to add -R (means recursive)

---

### Post by bossa on 2008-04-25
not getting any messages in terminal anymore after doing " $ sudo rm -R /root/.nautilus" but still cannot get the "read/write access"

---

### Post by Naatan on 2008-04-25
Sorry I think I was confusing your thread with another; where are you trying to change file permissions?

Can you do a "ls -ahl /path/to/dir" from the directory the file is in and post the results? I don't need to know the file names.

---

### Post by bossa on 2008-04-25
naatan sorry man I should of said from the start . I was trying to change permissions in usr/share/icons ,but it looks like I cant change permissions (read/write) anywhere

Sorry again because I don't know how to "ls -ahl /path/to/dir" Can you enlighten me?

---

### Post by Naatan on 2008-04-25
You can type that in a console, but nevermind that now.

I'm guessing you are trying to install some icons to use; point your nautilus file manager to ~/.icons and copy the icon pack your trying to install there.

It's never a good idea to play with permissions on files outside your home directory unless you know what your doing.

---

### Post by bossa on 2008-04-25
> **Naatan said:**
> You can type that in a console, but nevermind that now.

I'm guessing you are trying to install some icons to use; point your nautilus file manager to ~/.icons and copy the icon pack your trying to install there.

It's never a good idea to play with permissions on files outside your home directory unless you know what your doing.

Yeah I have done that but I still cant change the "read/write" I thought there may be a problem as all the Icons I installed work except the folder icons have stayed as stock Gnome folder icons.Just thought it might be because of that :confused:

---

### Post by Naatan on 2008-04-25
Are you referring to the folder icons? I have noticed that some older icon packs don't function properly in Ubuntu 8.04, there's not much you can do about that other than renaming the icons to their proper names.. but I can't help you there.

---

### Post by bossa on 2008-04-25
> **Naatan said:**
> Are you referring to the folder icons? I have noticed that some older icon packs don't function properly in Ubuntu 8.04, there's not much you can do about that other than renaming the icons to their proper names.. but I can't help you there.

Yes ,I guess its an older icon pack "Mac_OS_X_Leopard_for_Ubuntu_v1.0" worked well in Gutsy. Thanks for helping

---

