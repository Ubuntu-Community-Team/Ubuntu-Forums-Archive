---
title: "Can't see windows network"
date: 2008-06-12
forum: General Help
---

### Post by miickEe on 2008-06-12
Sup chaps?

I've trawled the internet and tried a lot of things to get networking between the existing xp network in my house and my ubuntu machine.

Using older versions of ubuntu a few years ago I was able to view the whole network no problem, without any other tweaking/programs.

I've downloaded all the samba and affiliated programs (sudo apt-get install samba smbfs smbclient winbind).

I can ping the hosts on the network no problem. Just being able to find them under Places -> Network -> Windows Network. Once getting that far it doesn't show anything.

I made a rule on one of the xp machine's firewall to let all traffic in from my IP address but to no avail.

---

### Post by molotov00 on 2008-06-12
Ubuntu? Kubuntu? Xubuntu? They have different file managers. I'm on Xubuntu, for example, and I can't browse Windows network like I can in Windows Explorer. But that doesn't mean it isn't there. Try some of the following:

man smbclient (just give it a read...)
smbclient -L //<hostname or ip>/ (to display shared files on <hostname or ip>)

If that works then samba's working fine -- it's just the file manager that's acting up, and for that we need to know which one you're using.

If you only want to access a few shares then you can mount them, just like you would   any other drive:

```
sudo mount -t smbfs -o username=user,password=pass //server/folder /home/molotov/folder_on_server
```

Let us know how that goes. (If you can connect using smbclient then no need to try 'mount' -- I just wanted you to know that option's avaialble)

---

### Post by miickEe on 2008-06-13
Yeah, that smbclient -L //<ip or hostname> command worked, I saw the list of shares.

Now, accessing them is the problem. I'm using Ubuntu 7.10. How can I get the network manager window working?

The mounting business, with username and password.. username and password of the computer we're trying to access?

Thanks for the help mate, getting there.

---

### Post by miickEe on 2008-06-13
Nup I did it, mounted one of his drives haha. Hell yeah. Just had to revise uni notes.

Thanks for the nudge in the right direction mate.

---

### Post by miickEe on 2008-06-13
Ok I can mount his K drive and access it from the mount point:
```

sudo mount -t smbfs -o username=miickee,domain=WORKGROUP //<ip address>/K$ /mnt/seanspcK
```

But doing the same for C won't work

```

26083: tree connect failed: ERRDOS - ERRnoaccess (Access denied.)
SMB connection fail

```

---

### Post by FAJALOU on 2008-06-13
Had(Have) same problem.  What I really did was something like this;
smb://192.168.1.101/users/<username>
A little less convenient, but for me it works.  From there you can mount what you feel fit, just as long as you manually know the path to it in samba

---

### Post by miickEe on 2008-06-13
Hrm doesn't work for me.. might need another solution.

Also, to access my shares on ubuntu from one of the windows machines.. what syntax do we use to access it? I'm not familiar with it.

---

### Post by ddales on 2008-06-13
I struggled with this for a while until I found a posting that said you have to set the UID and GID, otherwise, Ubuntu/Samba will mount the drive without any write permissions.  I could mount the shares but couldn't write to them.

Make sure your user has permissions to the windows share that you want to mount.

In your home directory, create a file called .smbpasswd or whatever you like.  I named mine .smbpasswd.

The contents of the .smbpasswd will look like this:
username=[your samba user name]
password=[your samba password]

chmod on the .smbpassword to 600 so only your user can see it.  It's plain text and you don't want anyone snatching your password.

Edit your /etc/fstab to look something like the following:

//[IP of Windows box]/[share name] /[local directory on which to mount the share] smbfs credentials=/home/[your user]/.smbpasswd,uid=[your UID],gid=[your GID],file_mode=0755,dir_mode=0755 0 0

Now you can either use "sudo mount -a" or reboot to automagically mount the share after a reboot.  Add a similar fstab entry for each share that you would like to mount.

Required packages:  samba samba-client winbind smbfs

---

### Post by miickEe on 2008-06-13
I do not know my UID/GID..

Found it. Ok, that works well in mounting the shares that I could already mount, but permanently this time. However, I still need to be able to mount other shares, like the C drive. When I do the command

```
smbclient -L //<ip address>
```

I get this:
```

miickee@miickee-gutsy:~$ smbclient -L //<ip address>
Password: 
Domain=[WORKGROUP] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Sharename       Type      Comment
        ---------       ----      -------
        K               Disk      
        My Documents    Disk      
        IPC$            IPC       Remote IPC
        I$              Disk      Default share
        K$              Disk      Default share
        G$              Disk      Default share
        Music (G)       Disk      
        F$              Disk      Default share
        ADMIN$          Disk      Remote Admin
        C$              Disk      Default share
        I               Disk      
        J$              Disk      Default share
session request to <ip address> failed (Called name not present)
session request to 192 failed (Called name not present)
Domain=[WORKGROUP] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Server               Comment
        ---------            -------
        SEANSPC              

        Workgroup            Master
        ---------            -------
        MSHOME               NEIL-MUSIC
        WORKGROUP            SEANSPC


```

Ok.. I can mount K, but I cannot mount C. Also, do the drives need to be "shared" in windows (Properties, Sharing etc) to be able to access them via mount?

I get this:
```

miickee@miickee-gutsy:~$ sudo mount -a
[sudo] password for miickee:
6825: tree connect failed: ERRDOS - ERRnoaccess (Access denied.)
SMB connection failed

```
When this is in my fstab:
```

//<ip address>/C$ /mnt/seanspcC smbfs user,credentials=/home/miickee/.smbpasswd,uid=1000,gid=1000,file_mode=0755,dir_mode=0755 0 0

```

---

### Post by celem on 2008-06-18
The same issue troubles me, namely "Using older versions of ubuntu a few years ago I was able to view the whole network no problem, without any other tweaking/programs.". Now it is very, very slow and generally fails. I don't want to mount, I just want to access via the "Places" path. I get some odd results from the terminal.

ecomer@Dell-C400:~$ ping 192.168.0.104
PING 192.168.0.104 (192.168.0.104) 56(84) bytes of data.
64 bytes from 192.168.0.104: icmp_seq=1 ttl=64 time=5.06 ms
64 bytes from 192.168.0.104: icmp_seq=2 ttl=64 time=4.19 ms
64 bytes from 192.168.0.104: icmp_seq=3 ttl=64 time=3.41 ms
64 bytes from 192.168.0.104: icmp_seq=4 ttl=64 time=3.50 ms
64 bytes from 192.168.0.104: icmp_seq=5 ttl=64 time=1.89 ms
64 bytes from 192.168.0.104: icmp_seq=6 ttl=64 time=1.84 ms
64 bytes from 192.168.0.104: icmp_seq=7 ttl=64 time=1.82 ms

--- 192.168.0.104 ping statistics ---
7 packets transmitted, 7 received, 0% packet loss, time 5997ms
rtt min/avg/max/mdev = 1.828/3.105/5.060/1.194 ms
ecomer@Dell-C400:~$ smbclient -L //VERNA
timeout connecting to 208.69.32.132:445

ecomer@Dell-C400:~$ smbclient -L //192.168.0.104
session request to 192.168.0.104 failed (Called name not present)
session request to 192 failed (Called name not present)

It used to work under Dapper, but it hasn't really worked since then.

---

