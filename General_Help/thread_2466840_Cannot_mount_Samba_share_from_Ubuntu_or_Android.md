---
title: "Cannot mount Samba share from Ubuntu or Android"
date: 2021-09-07
forum: General Help
---

### Post by evinrude on 2021-09-07
I cant find anywhere else to ask this so if anyone knows of a more appropriate forum please let me know .(I was unable to find a 'Samba User Forum') .

My environment

KDE NEON 5.22 User Edition
CIFS Version 2.23
samba/focal-updates,now 2:4.11.6+dfsg-0ubuntu1.10 amd64

All I am trying to do is share via Samba a single folder to a single user . 
Here is my smb.conf

[global]
netbios name = OLLIES
workgroup = OLLIE-SAMBA
security = user
passdb backend = tdbsam
server string = %h server (Samba, Ubuntu)
log file = /var/log/samba/log.%m
max log size = 1000
logging = file
panic action = /usr/share/samba/panic-action %d
log level = 3
server role = standalone server
obey pam restrictions = no
unix password sync = no
passwd program = /usr/bin/passwd %u
passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
pam password change = no
map to guest = bad user
usershare allow guests = no
usershare path =

[LinuxShare]
path = /Share
valid users = neon
guest ok = no
read only = no
available = yes
writable = yes
public =  no
printable = no
locking = yes
strict locking = no
create mask = 0644
directory mask = 0755

After starting Samba I seem my share


        Sharename       Type      Comment
        ---------       ----      -------
        LinuxShare      Disk      
        IPC$            IPC       IPC Service (linux-desktop server (Samba, Ubuntu))
        
So here is where the problem starts . First I attempt to access the share from an Android machine . Ii looks as though I am being authenticated  OK

 smbstatus

Samba version 4.11.6-Ubuntu
PID     Username     Group        Machine                                   Protocol Version  Encryption           Signing              
----------------------------------------------------------------------------------------------------------------------------------------
221522  neon         neon         10.10.10.221 (ipv4:10.10.10.221:36687)    SMB2_10           -                    partial(HMAC-SHA256) 

Service      pid     Machine       Connected at                     Encryption   Signing     
---------------------------------------------------------------------------------------------
IPC$         221522  10.10.10.221  Tue Sep  7 01:49:35 PM 2021 EDT  -            HMAC-SHA256

However when I attempt to browse into the share or create a file in it I get 

Error Invalid smb status:STATUS_ACCESS_DENIED

On the Android tab I am using the app "X-plore"

So if I go to the Linux host and attempt to do this

mount -t cifs -o vers=3.0,username=neon //localhost/LinuxShare /mnt01
Password for neon@//localhost/LinuxShare:  *******

I get this 

mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs) and kernel log messages (dmesg)


dmesg -T shows me this

[Tue Sep  7 14:03:07 2021] CIFS: Attempting to mount //localhost/LinuxShare
[Tue Sep  7 14:03:07 2021] CIFS VFS: cifs_mount failed w/return code = -13

Here are the perms for the share and mount point

ls -ld /Share
drwxr-xr-x 1 neon neon 0 Sep  7 08:22 /Share

 ls -ld /mnt01
drwxr-xr-x 2 neon neon 4096 Mar 16 12:15 /mnt01

The other odd thing is I can enable my home directory in smb.conf and that works . I can connect , read and write files etc with no complaints .

If I su to 'neon' on the samba host I have full access to /Share and /mnt01


any help , ideas would be appreciated 

This has to be something easy that I just dont see

---

### Post by Morbius1 on 2021-09-07
It's going to take me a bit to go through all that but there is one thing missing from what it a fairly extensive set of detail and that is the samba password.

You never mentioned creating it. Did you set a samba password for neon:
```
sudo smbpasswd -a neon
```

That would explain at least this part of your description:
> mount -t cifs -o vers=3.0,username=neon //localhost/LinuxShare /mnt01
Password for neon@//localhost/LinuxShare:  *******

I get this 

mount error(13): Permission denied

THe samba password can be the same as your local login password but you must add it to the samba password database.

EDIT: Note that if successful you will not have write access to that mount but that can be fixed later.

---

### Post by evinrude on 2021-09-07
user 'neon' created with smbpasswd 

see

smbstatus

Samba version 4.11.6-Ubuntu
PID     Username     Group        Machine                                    Protocol Version  Encryption           Signing              
----------------------------------------------------------------------------------------------------------------------------------------
221522  neon         neon         10.10.10.221 (ipv4:10.10.10.221:36687)     SMB2_10           -                    partial(HMAC-SHA256)

---

### Post by HermanAB on 2021-09-07
In my experience, the best way to debug samba issues is from the command line with smbclient.  The error messages will tell you exactly what the matter is and if smbclient doesn’t work, any other method won’t either.

---

### Post by Morbius1 on 2021-09-07
Not doing very well here.

I made my smb.conf your smb.conf.
Changed neon to tester
Created the /Share directory w/tester as owner.
Mounted the share to my Test directory:
> tester@vxub2004:~$ sudo mount -t cifs -o vers=3.0,username=tester,uid=tester //localhost/LinuxShare /home/tester/Test
[sudo] password for tester: 
Password for tester@//localhost/LinuxShare:  *****     
Added a file:
> tester@vxub2004:~$ touch Test/forum-test.txt
Seems to work for me:
> tester@vxub2004:~$ ls -l /Share
total 0
-rw-r--r-- 1 tester tester 0 Sep  7 15:37 forum-test.txt

---

### Post by evinrude on 2021-09-07
I took the suggestion to  play with smbclient and this is what I got

```
root@linux-desktop:~# smbclient -d3 '\\linuxdesktop\LinuxShare' -U neon 
lp_load_ex: refreshing parameters 
Initialising global parameters 
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384) 
Processing section "[global]" 
added interface enp7s0 ip=fd05:92d7:663f::216 bcast= netmask=ffff:ffff:ffff:ffff:ffff:ffff:ffff:ffff 
added interface enp7s0 ip=fd05:92d7:663f:0:189:2c3d:bab3:1076 bcast= netmask=ffff:ffff:ffff:ffff:: 
added interface enp7s0 ip=fd05:92d7:663f:0:2154:7f9:f5e6:a9a1 bcast= netmask=ffff:ffff:ffff:ffff:: 
added interface enp7s0 ip=fd05:92d7:663f:0:a450:3284:e82b:7619 bcast= netmask=ffff:ffff:ffff:ffff:: 
added interface enp7s0 ip=10.10.10.249 bcast=10.10.10.255 netmask=255.255.255.0 
Client started (version 4.11.6-Ubuntu). 
resolve_lmhosts: Attempting lmhosts lookup for name linuxdesktop<0x20> 
resolve_wins: WINS server resolution selected and no WINS servers listed. 
resolve_hosts: Attempting host lookup for name linuxdesktop<0x20> 
Connecting to 10.10.10.249 at port 445 
Enter WORKGROUP\neon's password:  
Kinit for neon@WORKGROUP to access linuxdesktop failed: Cannot contact any KDC for requested realm 
GENSEC backend 'gssapi_spnego' registered 
GENSEC backend 'gssapi_krb5' registered 
GENSEC backend 'gssapi_krb5_sasl' registered 
GENSEC backend 'spnego' registered 
GENSEC backend 'schannel' registered 
GENSEC backend 'naclrpc_as_system' registered 
GENSEC backend 'sasl-EXTERNAL' registered 
GENSEC backend 'ntlmssp' registered 
GENSEC backend 'ntlmssp_resume_ccache' registered 
GENSEC backend 'http_basic' registered 
GENSEC backend 'http_ntlm' registered 
GENSEC backend 'http_negotiate' registered 
GENSEC backend 'krb5' registered 
GENSEC backend 'fake_gssapi_krb5' registered 
Got challenge flags: 
Got NTLMSSP neg_flags=0x628a8215 
NTLMSSP: Set final flags: 
Got NTLMSSP neg_flags=0x62088215 
NTLMSSP Sign/Seal - Initialising with flags: 
Got NTLMSSP neg_flags=0x62088215 
NTLMSSP Sign/Seal - Initialising with flags: 
Got NTLMSSP neg_flags=0x62088215 
tree connect failed: NT_STATUS_ACCESS_DENIED
```

I dont know if the kinit error means anything since kerb is not installed .
The 'NT_STATUS_ACCESS_DENIED' error is telling me I have authenticated but are not allowed to do what I am attempting .
That does not give me any more of a clue .

I deleted and re-created samba user 'neon' but it didnt help

---

### Post by dragonfly41 on 2021-09-08
I know very little about Samba management, but this idea might possibly help.

Recently I have revived an old tool which I have used in past local development.

Webmin

This can be found in Ubuntu Synaptic or follow the manual installation guide.

[https://www.digitalocean.com/community/tutorials/how-to-install-webmin-on-ubuntu-20-04](https://www.digitalocean.com/community/tutorials/how-to-install-webmin-on-ubuntu-20-04)

Now I know that the veterans in this forum frown on any GUI tool which does not follow the Unix way - and particularly so if it opens up a port 10000. But Webmin allows me to do keyhole surgery when my desktop is in a mess. Or just to fine tune performance.

Precautions I take are to limit use to my desktop, and to close down Webmin when not in use.

Now to Samba.

Assuming you decide to take the step of installing Webmin, then proceed to Servers > Samba Windows File Sharing.

There you will find a wealth of tools to troubleshoot your problems.

If you decide to retain Webmin there are steps to change its certificate to Let's Encrypt to avoid the warning note you see when starting Webmin with its default self signed certificate.

---

### Post by kevdog on 2021-09-08
Only one thing I can suggest since I've had all types of problems with my Samba mounts -- In your configuration:
workgroup = OLLIE-SAMBA

change that to
workgroup = WORKGROUP

You can kind of see this in your other post:
Enter WORKGROUP\neon's password:
Kinit for neon@WORKGROUP to access linuxdesktop failed: Cannot contact any KDC for requested realm

---

### Post by evinrude on 2021-09-08
For 'fun' I installed webmin , deleted the share  , added it back and ended up with the same error . I think this issue is external to samba but I have no clue as to what it might be

---

### Post by Morbius1 on 2021-09-08
I don't want to waste your time but did you just not print the whole smb.conf or is this really in there:
> usershare path =

Samba defaults to /var/lib/samba/usershares and is usually not explicitly stated in smb.conf. Did you set the path to another location?

If you did you might want to see if you "double" shared the /Share folder:
```
net usershare info --long
```

You can share your home directory without issue but not this one folder and ... um ... I'm just trying to make sense of that.

---

### Post by HermanAB on 2021-09-09
"The 'NT_STATUS_ACCESS_DENIED' error is telling me I have authenticated but are not allowed to do what I am attempting ." - Yes, I also think that you have a permission problem.  The username and password authentication works, but Samba is not allowed to provide access to the working directory by the underlying filesystem.  You can try to make the directory and the files in it wide open to prove it with 'chmod 777 pathtodirectory'.  Note that the system can also be blocked by SELinux or AppArmor if you have one of those active.

---

### Post by evinrude on 2021-10-10
Good news I got it to work 
Bad news I have no idea what I'm doing differently .

---

### Post by evinrude on 2021-10-10
Someone please explain this .
If I name the share [linuxshare] or [share]  I cannot access it . If I name it [MyStuff] it works fine  .  

I'm not making this up .

---

### Post by TheFu on 2021-10-10
Last time I looked at using Android as a Samba client, it seemed that most of the non-paid Samba clients were using weak NT1 authentication.  These days, it is easier to crack that sort of authentication than it is to look up the credentials and type them in.  Of course, YMMV.

Glad you got something working.  Sad you don't know why.  When stuff like that happens to me - perhaps once a year - it drives me crazy.  Last week had it happen when trying to get NFS as a client working from inside a linux container.  It didn't work and I stepped away for some dinner, then came back and it was working.  No clue why.

---

### Post by evinrude on 2021-10-11
But I did figure it out , See my post from above .

---

### Post by Morbius1 on 2021-10-11
Since you introduced webmin into this I suggesting posting the output of the following commands so the folks here can see how you are currently set up:
```
testparm -s
```
```
net usershare info --long
```

---

### Post by ActionParsnip on 2021-10-11
If you SSH to the system to manage it then you can mount SFTP. AndFTP in Android can do this and it connects on port 22. Nice and easy. This will sidestep the issue.

---

### Post by evinrude on 2021-10-11
But I did figure it out , See my post from above .

---

### Post by evinrude on 2021-10-11
reproduced the issue from linux cli

with the share name set to [share] I get this

[FONT=monospace][COLOR=#54ff54]**neon@linux-desktop**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ smbclient '\\10.10.10.249\share' [/COLOR]
Enter OLLIE\neon's password:  
tree connect failed: NT_STATUS_ACCESS_DENIED

With the share name set to [MyStuff] it works

[/FONT]
[FONT=monospace][FONT=monospace][COLOR=#54ff54]**neon@linux-desktop**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ smbclient '\\10.10.10.249\MyStuff' [/COLOR]
Enter OLLIE\neon's password:  
Try "help" to get a list of possible commands. 
smb: \> l 
  .                                   D        0  Sun Oct 10 17:38:54 2021 
  ..                                  D        0  Wed Sep  8 11:19:03 2021 
  Screenshot_20211010-144209_X-plore.jpg      A   169689  Sun Oct 10 14:42:10 2021 
  Screenshot_20211010-144408_X-plore.jpg      A   250686  Sun Oct 10 14:44:08 2021 

                1114652760 blocks of size 1024. 521069640 blocks available 
smb: \>
[/FONT][/FONT]

---

### Post by Morbius1 on 2021-10-11
If that is supposed to be a response to my request I was referring to this post:
> Someone please explain this .
If I name the share [linuxshare] or [share]  I cannot access it . If I name it [MyStuff] it works fine  .  

I'm not making this up . 				

---

### Post by TheFu on 2021-10-11
> **evinrude said:**
> But I did figure it out , See my post from above .

To mark a thread as SOLVED, please use the Thread Tools button near the top-right of the page. Only the OP for each thread can do this.  What you learn is that people look for that and if they don't see it, they will read the first post and try to provide their insight towards a solution without carefully reading other replies. After all, the other replies didn't work, right?

Some threads will continue with deeper discussions even after SOLVED, to over other aspects for the other 1,000 people who come to this thread for help over the next few years.  Especially when the exact solution for the exact issue isn't 100% known.

Fortunately, there are lots of different ways to connect computers for file transfers, so if 1 method isn't working, there are a few others which might be slightly more overhead or not easily integrated or even better integrated, but with a different setup that is unfamiliar. Lots of possible answers.  Heck, if you just want to copy files in 1 direction, there are 1-line HTTP servers that make files in 1 directory available for any client to grab. 1-direction - download only, but there is use in that too for stuff that is needed once, for 5 minutes.

---

### Post by evinrude on 2021-10-11
Not exactly solved  , see # 19

---

### Post by TheFu on 2021-10-11
Use //, not \\.

Also, restarting smbd after each change?

I'm seeing smb.conf options that I've never seen before, ever, anywhere.  I'd say it would be best to start with a default conf file,and change the 2-3 global settings, then add a 5 line stanza for the share and be done. A few settings like conflict and the result is unknown by me, but I'm hardly an expert and we don't have win10.

Is "share" a reserved config setting?

---

### Post by Morbius1 on 2021-10-12
Whatever you do - and I cannot emphasize this enough - under no circumstances should you run and post the output of the following commands back to the forum:
```
testparm -s
```
```
net usershare info --long
```

---

### Post by TheFu on 2021-10-12
evinrude, Morbius1 is joking.  Those commands are normally the first steps in any samba troubleshooting. They would be very helpful.

---

