---
title: "Samba not working... HELP!!!!!"
date: 2006-10-25
forum: General Help
---

### Post by mrcdan on 2006-10-25
Im on ubuntu edgy and when i try to view my windows network it doesnt work. I ve tried unblocking the ports in firestarter for smb but still no go. When I had 6.06 it worked fine. Can some1 please help me?

---

### Post by TigerWolf on 2006-10-25
Found here: [http://ubuntuforums.org/showthread.php?t=2389](http://ubuntuforums.org/showthread.php?t=2389)

> **FLeiXiuS said:**
> 
**Configuring /etc/smb.conf**
We will be creating a whole new samba config because we are the guru's and it improves validity. :-P. 

[I]1. Rename /etc/smb.conf to /etc/smb.conf.old
2. Open /etc/smb.conf with your favorite text editor![/I]

```

; /etc/smb.conf
;
; Make sure and restart the server after making changes to this file, ex:
; /etc/rc.d/init.d/smb stop
; /etc/rc.d/init.d/smb start

[global]
; Uncomment this if you want a guest account
; guest account = nobody
   log file = /var/log/samba-log.%m
   lock directory = /var/lock/samba
   share modes = yes

[homes]
   comment = Home Directories
   browseable = no
   read only = no
   create mode = 0750

[tmp]
   comment = Temporary file space
   path = /tmp
   read only = no
   public = yes

```

NOTE: If your Samba server has more than one ethernet interface, the smbd may bind to the wrong one. If so, you can force it to bind to the intended one by adding a line that looks like this to the [global] section of /etc/smb.conf:

```
"interfaces = 192.168.1.1/24" 
```
Replace the IP above with the interfaces IP address.  Notice the /24 at the end.  This is the subnet default for a CLASS-C network.  It may vary depending on your network.

To share a directory with the public, create a clone of the [tmp] section above by adding something like this to smb.conf:

```

[public]
   comment = Public Stuff
   path = /home/public
   public = yes
   writable = yes
   printable = no

```

To make the above directory readable by the public, but only writable by people in group ubuntu, modify the entry like this:

```

[public]
   comment = Public Stuff
   path = /home/public
   public = yes
   writable = yes
   printable = no
   write list = @ubuntu

```

After this I would reccommend setting up samba for encrypted passwords.
In the [global] section of /etc/smb.conf, add the following lines:
```

encrypt passwords = yes
smb passwd file = /etc/smbpasswd

```
NOTE: If your clients and server are using encrypted passwords, you will not be able to browse the available shares on the server until an initial connection has been made with the appropriate authentication.

This should be all, save and exit.

**Starting SMB Daemons**
```
sudo /usr/sbin/smbd -D && /usr/sbin/nmbd -D
```

**Accessing Shared Folder on Another Linux Box**
To see which shares are available on a given host, run:
```

/usr/bin/smbclient -L host

Example:
/usr/bin/smbclient -L fleixius

```

Where 'host' is replaced with the hostname of the samba server on the network.  Unless the SMB server has no security configured, it will ask you for a password.  This should print back a service page.  Where services are what the host can share to you.

To view the shared folder 'public' on machine 'fleixius' (//fleixius/public) you will need to:
```

/usr/bin/smbclient service <password>

Example:
/usr/bin/smbclient ////fleixius/public  mypwd

```
Because of shell restrictions you have to escape the backslashes.

Now once your in the 'smb: \' console.   You can type 'h' for a help menu.

**Mounting a Shared Drive**
Using the examples above, lets say we want to mount a folder called "Ubuntu" shared on "fleixius" to a directory of "/home/Ubuntu" on the local box.  The typical mount command would be as following:

```

smbmount "\\\\fleixius\\Ubuntu" -U rtg2t -c 'mount /home/Ubuntu -u 1000 -g 1000'

```

Notice -u and -g.  UID and GID.  Replace those with your values also.

I hope this helps and solves the problems with samba.  Please send feedback!

---

### Post by mrcdan on 2006-10-25
Hmm that solution didnt completly solve my problem, i can access those shares from the command line but i still cant see anything in nautilus.

---

