---
title: "Can't see Samba share"
date: 2007-12-30
forum: General Help
---

### Post by methodical on 2007-12-30
I have samba running on my server and I'm trying to access it from my desktop (also on ubuntu). I can see the shared folders, but I cannot access them. I get the error "The folder contents cannot be displayed.".

Here is my smb.conf:

```
[global]
    ; General server settings
    netbios name = ARISE
    server string =
    workgroup = MSHOME
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    ;only users in local network have access to server
    interfaces = lo, eth0
    bind interfaces only = true

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

[storage1]
    path = /storage1
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = rswilley
    force group = rswilley

[storage2]
    path = /storage2
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = rswilley
    force group = rswilley

```

Is there someting wrong with my configuration or are my permissions not setup correctly?

---

### Post by gilf on 2007-12-30
I found two things solved all of my problems with Samba:

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

and installing the following GUI shares and users configuration program:

system-config-samba

it locates in your System>Administration dropdown menu as Samba

---

### Post by methodical on 2007-12-30
Yeah that is the guide I followed, but it doesn't work. I had it working before, but my hard drive crapped out on me so I had to restart from scratch. :confused:

---

### Post by skyjuice on 2007-12-31
same person over here looking for solution for this thing. T_T

---

### Post by methodical on 2007-12-31
Anyone?

---

### Post by skyjuice on 2008-01-01
anyone can assist us :D

---

### Post by santosh_gr on 2008-01-01
Does the locations /storage1 and /storage2 exist on the server?  You can check by typing.

ls -la /storage1

and 

ls -la /storage2

If it returns an error you either dont have the folder created or the pemissions or incorrect.

Try testing the samba config file by typing 

testparm

It will return a set of results about how the share is configured.

Try restarting samba service by typing.

/etc/init.d/samba restart

Test your samba connection locally by typing 

smbclient //host/share -U username

replace host, share and username with you settings.  This only works if you have created a user with smbpasswd command earlier.

---

### Post by methodical on 2008-01-01
Thanks...

Yes, /storage1 and /storage2 exist on the server.

Here is what I get when I run 'testparm':
```

rswilley@rswilley-desktop:~$ testparm
Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
ERROR: lock directory /var/run/samba does not exist
ERROR: pid directory /var/run/samba does not exist
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
        workgroup = MSHOME
        server string = %h server (Samba, Ubuntu)
        obey pam restrictions = Yes
        passdb backend = tdbsam
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *passwd:*password\supdated\ssuccessfully* .
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        panic action = /usr/share/samba/panic-action %d
        invalid users = root

[printers]
        comment = All Printers
        path = /var/spool/samba
        create mask = 0700
        printable = Yes
        browseable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers

```

Here is what I get when testing connection:
```

rswilley@rswilley-desktop:~$ smbclient //arise/storage1 -U rswilley
Password: 
Domain=[ARISE] OS=[Unix] Server=[Samba 3.0.26a]
tree connect failed: NT_STATUS_NO_SUCH_GROUP

```

> **santosh_gr said:**
> Does the locations /storage1 and /storage2 exist on the server?  You can check by typing.

ls -la /storage1

and 

ls -la /storage2

If it returns an error you either dont have the folder created or the pemissions or incorrect.

Try testing the samba config file by typing 

testparm

It will return a set of results about how the share is configured.

Try restarting samba service by typing.

/etc/init.d/samba restart

Test your samba connection locally by typing 

smbclient //host/share -U username

replace host, share and username with you settings.  This only works if you have created a user with smbpasswd command earlier.

---

### Post by santosh_gr on 2008-01-01
Looks like /storage1 and /storage2 do not show up with the testparm command.  The config file looks ok.  Did you reload the samba configuration once you have made changes to smb.conf?  Can you paste the output of the following commands.

sudo -la /storage1

sudo -la /storage2

sudo /etc/init.d/samba reload

sudo /etc/init.d/samba restart

sudo testparm

smbclient //arise/storage1 -U rswilley

---------------------------------------------------

In case it still does not work.  Try create a user id by name rswilley using the smbpasswd command given below

smbpasswd -a rswilley

It will prompt your for a new password.  Once you have set the new password try smbclient again (last step).

If a account already exists for samba then change the password using 

smbpasswd rswilley
Supply new passwd.

Last Step.  Try smbclient again.
smbclient //arise/storage1 -U rswilley

---

### Post by methodical on 2008-01-01
Ah I ended up just uninstalling samba and setting up NFS since it is two linux computers. No real need for samba anyway. NFS worked with no problem.

I used the guide here: [http://ubuntuforums.org/showthread.php?t=249889&highlight=nfs+server](http://ubuntuforums.org/showthread.php?t=249889&highlight=nfs+server)

Thanks a lot for your help though.

---

### Post by skyjuice on 2008-01-01
its abit weird T_T since i not very familiar with ubuntu environment 

i just installed pyNeighbourhood and follow this tutorial 
[http://ubuntuforums.org/showpost.php?p=3405430&postcount=2](http://ubuntuforums.org/showpost.php?p=3405430&postcount=2)

install smbfs 

after that i follow a tutorial over here 

[http://grumpymole.blogspot.com/2006/11/xubuntu-browsing-samba-shares-with.html](http://grumpymole.blogspot.com/2006/11/xubuntu-browsing-samba-shares-with.html)

and suddenly all work like a charm :D 

and santosh_gr 

thank you for your solutions also :)

---

