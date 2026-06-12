---
title: "SFTP, chroot and file permission problem!"
date: 2015-12-17
forum: General Help
---

### Post by kevin195 on 2015-12-17
Hi all,

I found this [thread]("http://ubuntuforums.org/showthread.php?t=1107974") which is related to my problem. I followed the instructions there but it does not work for me for some reason.

I have 2 users, both in the same group. I restricted access for user B to a specific directory.

This is the part from my ssdh config file:

Subsystem sftp internal-sftp
UsePAM yes
Match Group sftponly
        ChrootDirectory /home/%u
        ForceCommand internal-sftp
        X11Forwarding no
        AllowTcpForwarding no

The user is jailed to the directory just like I want it to be. Only problem is with uploaded files (using WINSCP for this). I am not able to overwrite files because of denied permission. I guess owner / file rights are not correct. See screenshot:

[IMG]http://i74.photobucket.com/albums/i263/myspaceye/2015-12-17_12-24-32.png[/IMG]

umask should solve this issue, but for some reason I can not get it to work. What am I doing wrong?

---

### Post by btindie on 2015-12-17
To create a shared directory.
1) Make sure all users are members of the same group
2) Set the group owner of that directory to the shared group name
3) Set permissions on the root shared directory to 2775 (g+w,g+s). That makes all newly created files use the same group and gives group members write access to the directory.
4) Set the umask for sftp to 0007 to allow group members to write to the same file
```
Subsystem sftp internal-sftp -f AUTH -l INFO -u 0007
```

Note: some clients may change the umask.

With the ChrootDirectory command it first does a chroot() to the specified directory and then cd's to the users home directory as specified in /etc/passwd, if that exists.
So with your above ChrootDirectory statement you'd really want the following directories
/home/UserA/home/UserA
/home/UserB/home/UserA
Though that may not be what you'r trying to achieve?

---

### Post by kevin195 on 2015-12-17
Thanks for your reply.

First, I am not a linux pro, so I wonder if you could explain more detailed (with examples).

I need this stuff for my minecraft server that I am running (it's hosted on a dedicated server).

[SIZE=4]So this is the **current situation**:[/SIZE]

I have 2 users...

Username: mc1 (Group: mc1)
Username: mc2 (Group: sftponly)

User mc1's home: /home/mc1/
User mc2's home: /home/mc2/

I achieved restricting mc2 to only access his home directory (he can not login via ssh nor leave his home directory).
Then I mounted a directory which belongs to mc1 so that mc2 can access it (read, upload etc.)


[SIZE=4][B]part of my sshd.conf:
[/B][/SIZE]
```
Subsystem sftp internal-sftp
UsePAM yes
Match Group sftponly
        ChrootDirectory /home/%u
        ForceCommand internal-sftp
        X11Forwarding no
        AllowTcpForwarding no
```

[SIZE=4]
What I want to achieve:
[/SIZE]
Both, mc1 & mc2 should be able to upload, download, edit and overwrite files in the directory "/home/mc1/minecraft/plugins/betonquest". While user mc1 can browse anywhere without restrictions, user mc2 should only be able to see this specific directory and be able to upload, download and overwrite files in it.

What will I have to do?

---

### Post by btindie on 2015-12-17
That's a good explanation and should make it easier to come up with a working solution

Firstly, the way ChrootDirectory works is that it expands the variables which would result in /home/mc2. It then changes the root to that directory. It then does a CD to place the user in their home directory by doing the equivalent of
```
$ getent passwd mc2 | cut -d: -f6
/home/mc2
```
That means that you'd need the directory /home/mc2/home/mc2 to exist on your system. If you decide to add additional users that'll result in multiple chroot() directories which isn't really necessary.

In the below example I'll be using /home/sftponly as the chroot().

So edit your sshd_config to match the below
```
Match Group sftponly        ChrootDirectory /home/sftponly
        ForceCommand internal-sftp -u 0002
        X11Forwarding no
        AllowTcpForwarding no
```
Adding '-u 0002' to the internal-sftp command will set the umask so it allows group writeable files.

Directory structure we're aiming for along with permissions+user+group ownership
```

/home
|-- [drwxr-xr-x mc1      mc1     ]  mc1/
|   +-- [drwxr-xr-x mc1      mc1     ]  minecraft/
|       +-- [drwxr-xr-x mc1      mc1     ]  plugins/
|           +-- [drwxrwsr-x mc1      mc1     ]  betonquest/
|               +-- [-rw-rw-r-- mc2      mc1     ]  example.txt
+-- [drwxr-xr-x root     root    ]  sftponly/
    +-- [drwxr-xr-x root     root    ]  home/
        +-- [drwxr-x--- mc2      mc2     ]  mc2/
            +-- [drwxrwsr-x mc1      mc1     ]  betonquest/

```


Assuming two user accounts mc1 & mc2 where the default group is mc1 & mc2 respectively add user mc2 to the mc1 group
```
adduser mc2 mc1
```
either run that command as *root* or prefix it with 'sudo'.
And also the *sftponly *group
```
adduser mc2 sftponly
```
Which will result in the following memberships (numeric values are irrelevant) 
```
$ id mc1
uid=1000(mc1) gid=1000(mc1) groups=1000(mc1)
$ id mc2
uid=1001(mc2) gid=1001(mc2) groups=1001(mc2),1000(mc1),999(sftponly)

```

When user mc2 logins via SFTP the actual directory they'll be placed in is /home/sftponly/home/mc2, we'll also need a directory for the bind mount.
```
mkdir -p /home/sftponly/home/mc2/betonquest
chown -R mc2:mc2 /home/sftponly/home/mc2
chmod o-rx /home/sftponly/home/mc2
```

That sets up users mc2's access.

Now for mc1. We need to set the group 'sticky' bit on the directory to be shared so all new files/directories created will have that group ownership so both users have access to the files.
```
chmod 2775 /home/mc1/minecraft/plugins/betonquest
```
Again, run that command as root or with sudo.

Now just to 'bind mount' the directory. Add the below to your /etc/fstab file
```
/home/mc1/minecraft/plugins/betonquest /home/sftponly/home/mc2/betonquest none bind 0 0
```
and mount it with
```
mount /home/sftponly/home/mc2/betonquest
```

Now both directories contain the same files
```
$ ls /home/mc1/minecraft/plugins/betonquest/example.txt
$ ls /home/sftponly/home/mc2/betonquest/
example.txt

```

Don't forget to reload sshd once you've made the changes. Otherwise that should be it.

---

### Post by kevin195 on 2015-12-17
I followed these steps carefully but it does not work.

Here the id part:

[IMG]http://i74.photobucket.com/albums/i263/myspaceye/2015-12-17_20-27-40.png[/IMG]

This is the error when mc2 tries to upload any file into the "betonquest" directory:

[IMG]http://i74.photobucket.com/albums/i263/myspaceye/2015-12-17_20-29-12.png[/IMG]

mc2 can only upload into "/home/mc2" without any problems:

[IMG]http://i74.photobucket.com/albums/i263/myspaceye/2015-12-17_20-30-34.png[/IMG]

This is my current fstab:

```

proc  /proc       proc    defaults    0    0
none  /dev/pts    devpts  rw,gid=5,mode=620    0    0
none  /run/shm    tmpfs   defaults    0    0
/home/mc1/minecraft/plugins/betonquest /home/sftponly/home/mc2/betonquest none bind 0 0

```

And here is the part from the sshd conf file:

```

Match Group sftponly        
        ChrootDirectory /home/sftponly
        ForceCommand internal-sftp -u 0002
        X11Forwarding no
        AllowTcpForwarding no

```

I restarted the service, of course.

Can you tell me what I am droing wrong?

---

### Post by kevin195 on 2015-12-22
Ok somehow got it working with this, I found somewhere else:

useradd someuser
mkdir -p /home/someuser/www
mount --bind /var/www /home/someuser/www
chmod g+s /home/someuser/www
chown -R someuser:www-data /home/someuser/www
setfacl -d -m g::rwx /home/someuser/www


But every new folder a user creates there gets CHMOD 777 ... why is that? How to change to default (755) ? And files we upload get CHMOD 666 instead of 644 ??

---

