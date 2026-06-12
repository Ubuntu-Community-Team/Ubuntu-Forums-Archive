---
title: "Samba Network File Share Connection Refused"
date: 2023-01-11
forum: General Help
---

### Post by goodstuff9 on 2023-01-11
I have two computers, both running Ubuntu 22.04 (wayland).  One, system19, acts as a server/host, and the other, system1, acts as the client.  


I set up the standard samba configuration file to serve some directories from system19.  In addition, for some directories on system19 I selected guest access for Local Network Share/Folder Sharing.  


For the directories I set up via the samba configuration file to share from system19, I can access them just fine from system1.  But, on system1, in Nautilus, if I go to “Other Locations”, I see other entries for system19 besides the samba shares I consciously created.  It appears to be samba sharing directories not from system19, but from something called “system19.local.”  


Strangely, sometimes from system1 I’m able to click on the entry in Nautilus’ Other Locations for the system19.local samba shares and I am able to access those directories; but, at other times – with no changes I’m aware of on either system – I get this error message in a popup window:  “Unable to access location / Failed to retrieve share list from server:  Connection refused.”  


Questions:  


What is “system19.local”, and how is it different from “system19”?  


How did system19.local get created?  And, How did the samba sharing from system19.local get created?  By virtue of me choosing Local Network Share/Folder Sharing for some directories on system19?  


Why is it that sometimes from system1 I can open up the system19.local samba shared directories in Nautilus’ Other Locations, and other times I get the error message described above?

---

### Post by Morbius1 on 2023-01-11
You might want to post the output of the following commands so the folks here can see how your server is set up:
```
testparm -s
```
```
net usershare info --long
```

As for the system19 / system19.local phenomenon:

A samba server can broadcast it's presence to the network two different ways: NetBIOS and mDNS

THe NetBIOS method ( system19 ) was the standard way of doing things in times past but most current systems ( Windows 10 / 11 and Linux ) pretty much disable it by default since none of them enable SMB1 by default any longer and NetBIOS will not work without it. It will still broadcast itself that way but the client can't access it that way.  Everyone ( in the technical community ) now knows that with the exception of the Gnome developers.

mDNS ( system19.local ) is the other standard way Samba will announce itself and is dependent on having avahi-daemon running on both server and Linux client ( Windows 10/11 and MacOS have their own mDNS client mechanisms ).

These parameters - with their defaults - in the samba configuration ( don't look at your smb.conf - they are not there ) control them:
```
disable netbios = No
multicast dns register = Yes
```

You can disable either ( or both ) by adding then setting the netbios parameter to Yes and the multicast parameter to No in your smb.conf file.

I don't know why system19.local works one minute and not the next. Perhaps something in how you configured the server or some network issue?

---

### Post by goodstuff9 on 2023-01-11
I didn't know the stuff about the NetBios and the mDNS or the SMB1 thingy (not a tech person).  So, does that mean that system19 is "broadcasting" the samba shared directories two ways:  NetBios method, and mDNS method?  And that is why in Nautilus I see them as two samba entries (system19 and system19.local)?  

Below is the output of the two commands, in case you notice something odd or outdated in them.....  I can't explain it, this is just the configuration file that someone provided me about ten (?) years ago, and I've always just tweaked the share definitions section.  


```
main19@system19:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
lpcfg_do_global_parameter: WARNING: The "client lanman auth" option is deprecated
lpcfg_do_global_parameter: WARNING: The "client ntlmv2 auth" option is deprecated
Loaded services file OK.
Weak crypto is allowed


Server role: ROLE_STANDALONE


# Global parameters
[global]
    client lanman auth = Yes
    client max protocol = SMB3
    client min protocol = NT1
    client NTLMv2 auth = No
    dns proxy = No
    domain master = Yes
    guest account = main19
    log file = /var/log/samba/log.%m
    logging = file
    map to guest = Bad User
    max log size = 1000
    name resolve order = bcast host lmhosts wins
    ntlm auth = ntlmv1-permitted
    obey pam restrictions = Yes
    pam password change = Yes
    panic action = /usr/share/samba/panic-action %d
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    passwd program = /usr/bin/passwd %u
    preferred master = Yes
    security = USER
    server min protocol = NT1
    server role = standalone server
    server string = %h server (Samba, Ubuntu)
    unix password sync = Yes
    username map = /etc/samba/smbusers
    usershare allow guests = Yes
    idmap config * : backend = tdb
    guest ok = Yes




[printers]
    browseable = No
    comment = All Printers
    create mask = 0700
    guest ok = No
    path = /var/spool/samba
    printable = Yes




[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers




[shared_stuff]
    path = /home/main19/shared_stuff
    read only = No




[ubuntu2]
    path = /media/main19/ubuntu2/
    read only = No




[Toshiba]
    path = /media/main19/Toshiba/
    read only = No




[Public]
    path = /home/main19/Public
    read only = No
main19@system19:~$

```



```
main19@system19:~$ net usershare info --long
[Public]
path=/home/main19/Public
comment=
usershare_acl=Everyone:F,
guest_ok=y


[ubuntu2]
path=/media/main19/ubuntu2
comment=
usershare_acl=Everyone:F,
guest_ok=y


[Toshiba]
path=/media/main19/Toshiba
comment=
usershare_acl=Everyone:F,
guest_ok=y


[shared_stuff]
path=/home/main19/shared_stuff
comment=
usershare_acl=Everyone:F,
guest_ok=y


[multimedia]
path=/media/main19/Toshiba/multimedia
comment=
usershare_acl=Everyone:F,
guest_ok=y


[router]
path=/media/router
comment=
usershare_acl=Everyone:F,
guest_ok=y


main19@system19:~$

```

---

### Post by Morbius1 on 2023-01-11
It's generally not a good idea to create a samba share ( like [Public] for example ) using both the classic method ( in smb.conf ) and the Usershsare method ( using Nautilus ) since they may end up conflicting one another and I don't know which one Samba will honor at any given moment.

You do have some settings that do reflect how samba was configured 10 years ago but I don't think they are the case of the problem.

I'm surprised that all the shares pointing to folders under /home/main19 work at all. Ubuntu 22.04 changed the default permissions on /home/username to 750 meaning they are only accessible to - in this case - main19. But all your shares allow guest access.

Did you change the permissions on /home/main19 itself?

**[COLOR="#FF0000"]EDIT: Ah, never mind - I found it:[/COLOR]**
> guest account = main19
Your guests become main19 which will make the guest shares work.

---

### Post by goodstuff9 on 2023-01-11
Ok, so if I understand....

Your advice is to choose either the "classic" (smb.conf) method, or the "usershare" method (via Nautilus) - correct?  

If I decide to try going with the usershare method, what do I do with my existing smb.conf file?  I assume I should replace it with a more modern, "generic" config file?  If so, where would I find that, and what modifications might I need to make to it?

---

### Post by Morbius1 on 2023-01-11
Before you reset everything when you get the "failed to retrieve share list ... " error access the server directly:

Open up Nautilus on the client machine and enter it's network path. For example:
```
smb://system19.local/public
```

You cannot enter just the host name. You have to enter the host name and share name. It's a bug in the gnome backend to nautilus. And it's best to use system19.local rather than system19. 

Does that not resolve the situation?

Anyway, there is a copy of the default smb.conf Ubuntu ships with at **/usr/share/samba/smb.conf**

Make a backup copy of your current smb.conf and then copy the /usr/share ... version to the /etc/samba location. 

You can make minimal changes to it like:
```
 server min protocol = NT1
 guest account = main19
```
Then restart smbd: 
```
sudo service smbd restart
```

My personal preference is to do everything in smb.conf rather than Nautilus' usershare but that's up to you.

---

### Post by goodstuff9 on 2023-01-11
I tried what you suggested, still had problems.  Gave a lot of thought to what you said, did a lot of reading.  I'm no expert, so I could be completely wrong, but from my reading I got the impression that nautilus-share is no longer consistently maintained, a lot of people basically reporting that it is flaky and unreliable and a source of problems.  

So, I backed up my smb.conf file, uninstalled both samba and nautilus-share, and started fresh by installing only samba and related, did not install nautilus-share.  Now everything is working as I would expect.  

Thanks for your help.

---

