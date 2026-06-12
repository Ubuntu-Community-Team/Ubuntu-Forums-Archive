---
title: "Yet another SAMBA question..."
date: 2007-09-10
forum: General Help
---

### Post by Akula on 2007-09-10
Hello,

I have been roaming around this forum for some time now trying to find a solution for my problem with sharing files on UBUNTU server with WinXP computer. So far I have tried this method:

[http://ubuntuforums.org/showthread.php?t=202605&highlight=howto+setup+samba+peer-to-peer](http://ubuntuforums.org/showthread.php?t=202605&highlight=howto+setup+samba+peer-to-peer)

And my smb.conf looks like this:

```
[global]
    ; General server settings
    netbios name = Ace
    server string =
    workgroup = MSHOME
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = no

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[MyFiles]
    path = /home/akula/Jako/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = akula
    force group = akula
```

So I haven't yet succesfully mapped network drive from UBUNTU MyFiles as instructed, windows just keeps asking username and password (they are same in ubuntu and windows, username and password). I had to change my accountname in XP because the first one had scandic letters on it and I don't think UBUNTU or SMB did like that much. As I changed to akula in XP machine, I don't think it is changed properly...? Just changed the account name from windows user management.

So. As I can't map my Ubuntu shares as network drive it seems I need to use different way to approach the problem.

WHAT I REALLY WANT IS to have this directory /home/akula/Jako to become shared and to be shown in windows network environment as a folder like it would be shared folder from another windows system on same LAN. That would be ideal solution. I don't really need to WRITE files from WinXP TO UBUNTU, but rather only COPY files FROM this UBUNTU share folder TO WinXP system. 

AND finally. I don't think I need any user/password stuff to protect my files on UBUNTU share folder, because all I need to have acces to it ONLY from my LAN (I have adsl modem/router between lan and wan, and my ubuntu server is used same time as web server and lan fileshare (described here) ).

So. As I have posted my smb.conf file above, could someone instruct me how to make changes to make my 'dream' come true. 

Thank you.

PS. sorry for being a part of flood of same old questions but I really didn't find solution from other threads :-/

---

### Post by lintoolman on 2007-09-10
A couple of things to check...

Are there any Samba errors in the Syslog?

Did you set a Username and password for samba?   You mention Ubuntu and windows, but not Samba.

Make sure "akula" is the owner of the directory "/home/akula/Jako/."  I know it seems obvious, but sometimes I forget and create a directory as root.

Is your XP box is in the same Workgroup (this may not matter, I'm not sure).

I don't see any obvious errors in your smb.conf file.  Does "testparm" report any errors?  Maybe there is a typo I don't see.

---

### Post by Akula on 2007-09-10
Some errors I found in SYSLOG:

Sep 10 18:47:33 Ace NXSERVER-3.0.0-63[8757]: ERROR: nxssh process exited with '255' 'NXNodeExec::exec'
Sep 10 18:47:35 Ace NXSERVER-3.0.0-63[8757]: ERROR: run command: no child process with pid 8768 Logger::log nxserver 3061

Similar error 'pairs' seem to come about for 3 times. Could it have effect on this as I am using my UBUNTU server from my WinXP computer with nomachine NX remote desktop session?

* I did set same username and password for samba as I did for ubuntu and winxp accounts.
* Both computers (UBUNTU and WinXP use same workgroup MSHOME)
* testparm does not give any errors.
* akula is owner of directory /home/akula/Jako

CURRENTLY I can see my UBUNTU box in my network area in winXP box, but can't access it (forgot to mention earlier). I get error translated as:  "\\Ace is not available[or usable]. You may not have permissions to use network resource. Contact Server administrator to check your permissions. Valid network path not found."

IN ADDITION when trying to get properties of my UBUNTU BOX in WinXP network screen (I see my own WinXP box and UBUNTU Box) I get error "Server Ace was not found in network."

---

### Post by lintoolman on 2007-09-10
You got me on this one.  

You are essentially attempting to access your home directory, but 1 level down.  So something I might try would be to un-comment the [homes] sections and restart samba.  This should allow access to /home/akula and accomplish what you are trying to do (assuming your XP box is logged on as akula).

---

### Post by Akula on 2007-09-10
Ok, uncommented. 

Now as I try to map network drive from \\ubuntu-box-ip\akula winXP mapper connects (?) and starts asking for username and password, I try with the ones I created (and ones I have on UBUNTU box and XP), but no, it just keeps asking again and again (and after first time fills user account as ubuntu-box-ip\akula ). Trying to map network drive from \\ubuntu-box-ip\MyFiles does exactly same (also fills user account as ip\akula after first username/password attempt)

Also same old error exists when I try to connect to UBUNTU Box from network workgroup in windows explorer.

EDIT: 

ANOTHER thing worth mentioning might be that when I explore into my /home/akula dir in graphical interface in my UBUNTU BOX I can see some kind of LOCK icon on Jako directory's icon. Also, when I examine the properties of folder, I can see all permissions (owner, group, others) folder access set to List Files Only, and --- on File access

AND I also modified my smb.conf file so that in [MyFiles] section I changed the path to shared folder from /home/akula/Jako/ to /home/akula/Jako removing last slash. Did not make any difference.

---

### Post by bmorency on 2007-09-10
when it asks you for a username and password to connect to the share,when you type the username in the box do you only type the username or do you type something like this in?

```
 UbuntuHostName\username
```


when I setup samba on my system it wouldn't work when i only typed in the username.

---

### Post by Akula on 2007-09-11
I have been trying to give username and password with host and without it (in form you explained it). It just does not work at all.

---

### Post by Akula on 2007-09-12
-bump-

---

### Post by lintoolman on 2007-09-12
Have you looked through the official howtos?

Check out this link:  [http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/index.html]("http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/index.html")

This is what I use.  

Something to try:  create a public share not in /home.  When it works, lock it down.  When that works, configure /home/akula/Jako/ to match.  

If you were setting up a Samba Domain, you would need to have a machine account for your XP box in /etc/passwd.  I don't think this is case for your setup.

---

### Post by Akula on 2007-09-22
Thanks for the link, but I don't think I'm understanding everything I need to to allow my winXP machine to browse my ubuntuserver's shares. Tried some configurations as in examples, but without success.

---

### Post by Akula on 2007-09-24
Finally! Fixed it. It was just firewall problem. Sorry to bother you with such simple problem. Just had to add local IP addresses I wanted to allow access into server into firestarter. =)

---

### Post by cjdaweasel on 2007-12-13
I had the same issue as the previous poster, firestarter was part of it. Later I realized that I hadn't set an SMB password. It gives the same error (constant requests for password). 

```

sudo smbpasswd -a jackb
New SMB password: m0r3pa1n
Retype new SMB password: m0r3pa1n
Added user jackb.

```

Just in case anyone else has the same issue.

---

