---
title: "Ubuntu machine on Windows network"
date: 2007-12-21
forum: General Help
---

### Post by mjpatey on 2007-12-21
Hi,

I haven't done this in so long I forget how to set it up, and can't seem to find a description of it anywhere in the forums...

My Ubuntu (Gutsy) computer can see the 2 Windows machines on my home network, but the 2 Windows machines can't see the Ubuntu computer.  How do I set the Ubuntu computer to be able to be seen by its Windows brethren?  I just want to be able to access the Ubuntu computer's shared directories/files from the Windows machines, including being able to save to them where appropriate.

Thanks for any insight you may have!

-Mark

---

### Post by TeaSwigger on 2007-12-21
Mark, little wonder you forgot. Networking and WINE were my two biggest griefs getting things going. Anyhow, two guides I found invaluable that I refer folks to:

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)
and also
[https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently)

Luck!

---

### Post by kaervos1024 on 2007-12-21
Yeah, I would just check out Winbind to see if that solves your woes. Its a great package. It will allow you to refer to windows machine shares on the network by smb://windowsmachinename/sharename and much more. You can find it in the standard repositories. In my case it improved Windows interoperability by many magnitudes.

---

### Post by mjpatey on 2007-12-21
kaervos, I'm tempted to try your suggestion, if you could clarify... does Winbind also work in tho other direction (i.e., Win machines can see my Ubuntu shares)?  I've already got the ability to access Windows' shared directories from Ubuntu.

TeaSwigger... thanks for the links!  I worked through the howto in the first one, and encountered little resistance; it went very smoothly.  But when I got to the end, I was still unable to access my Ubuntu shared directory (as specified in smb.conf as /home/samba) from Windows machines.

In Windows, I got to the next-to-last step:

> With WINS enabled:
- Click "START"
- Right-click "My Computer"
- Select "Map network drive"
- Choose the drive letter
- Type \\DAPPER\MyFiles
NOTE: Adjust this to the hostname and sharename you chose above!
- Click "Finish"

...and it asked me for a username and password.  I typed the usernames and passwords I'd created in previous steps, and none worked.

Here's the optput of my smb.conf:

```
[global]
    ; General server settings
    netbios name = Shekkster
    server string =
    workgroup = MSHOME
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

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
    path = /home/samba/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = mjpatey
    force group = mjpatey
```

Sorry for the long dump... I'm trying to get to the bottom of this, and don't know which way is up at this point.  Thanks for any help!

-M.

---

### Post by kaervos1024 on 2007-12-25
Hey. Well, windbind does a whole lot of stuff, but its main purpose is to automate the correlations between windows and linux users. If you've already gone through other procedures, and aren't too concerned with having to maintain windows and linux users independently, you might just want to continue down your current road. 

As for your error with the username, try running the following:

```
sudo smbpasswd <username>
```

and replace <username> with the username you plan to use. Samba and actual Linux passwords are maintained independently... this is often the last step I have to take to get access to my protected shares from a windows machine.

---

