---
title: "network drive mounts through Nautilus, but not mount cifs"
date: 2014-01-31
forum: General Help
---

### Post by thefatmoop on 2014-01-31
I've been banging my head on this for a bit and none of the online solutions have worked so far. I have a network drive that i'm trying to mount permanently and everything works great if I open a nautilus window and go to file -> Connect to Server... -> select windows share and type in my server, user name, password. 

ctrl+l while in nautilus gives smb://ipAddress/media

Everything's good right? I go to edit the /etc/ftab and it won't mount. Here are some of the entries i've tried 

```

#//ipAddress/media/shared /home/bo/shares cifs username=myUsername,password=Password123 0 0
#//ipAddress/media/shared /home/bo/shares cifs ro,auto,username=myUsername,password=Password123 0 0
#//ipAddress/media/shared /home/bo/shares cifs defualts,uid=1000,username=myUsername,password=Password123 0 0
//hostname/media/shared /home/bo/shares cifs username=myUsername,password=Password123,iocharset=utf8,sec=ntlm 0 0
#//ipAddress/media/shared /home/bo/shares cifs username=myUsername,password=Password123,iocharset=utf8,sec=ntlm 0 0
```
when I tell mount to mount them i get the error
```

mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
```

i'm using ubuntu 12.04 and apt-get update/upgraded the system. I just need to mount this network share and have it accessible from the terminal. 

any ideas?

---

### Post by TheFu on 2014-01-31
I would test with a tiny script first. Get that working, then convert to either autofs or use the CIFS options in /etc/fstab.

A few questions to get started .... 
Which exact version of Windows is the shared?
How must it be authenticated?  
Local user account, 2008 Active Directory or something newer?

Did you read the mount.cifs page?

Have you turned up the verbosity for all commands?

What does the log file say on the server AND the client?

Here's a script that works to mount a Win7 Ultimate box here:```

sudo mount -t cifs "$RMT_MNT"  $MNT_PNT -o username=$RMT_USER,password=$RMT_PSWD,iocharset=utf8,rw,uid=$LOCAL_USER
```

I believe some authentication setting down-grade was needed on the Win7 box for this to work. I could be confused about remote desktop stuff tho.

On other machines with multiple users, I use a credentials file to prevent passwords from being stored in plain text files accessible to all user ... like the fstab is.

---

### Post by bab1 on 2014-01-31
> **thefatmoop said:**
> I've been banging my head on this for a bit and none of the online solutions have worked so far. I have a network drive that i'm trying to mount permanently and everything works great if I open a nautilus window and go to file -> Connect to Server... -> select windows share and type in my server, user name, password. 

ctrl+l while in nautilus gives smb://ipAddress/media

Everything's good right? I go to edit the /etc/ftab and it won't mount. Here are some of the entries i've tried 

```

#//ipAddress/media/shared /home/bo/shares cifs username=myUsername,password=Password123 0 0
#//ipAddress/media/shared /home/bo/shares cifs ro,auto,username=myUsername,password=Password123 0 0
#//ipAddress/media/shared /home/bo/shares cifs defualts,uid=1000,username=myUsername,password=Password123 0 0
//hostname/media/shared /home/bo/shares cifs username=myUsername,password=Password123,iocharset=utf8,sec=ntlm 0 0
#//ipAddress/media/shared /home/bo/shares cifs username=myUsername,password=Password123,iocharset=utf8,sec=ntlm 0 0
```
when I tell mount to mount them i get the error
```

mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
```

i'm using ubuntu 12.04 and apt-get update/upgraded the system. I just need to mount this network share and have it accessible from the terminal. 

any ideas?

These```
//ipAddress/media/shared
```...need to be in the form of ```
//ipAddress/[COLOR="#FF0000"]<share_name>[/COLOR]
```
Where [COLOR="#FF0000"]<share_name>[/COLOR] is the name of the share.  You shouldn't use the path to the share directory.

---

### Post by thefatmoop on 2014-02-02
thanks I'll look into it. I managed to get it working with a virtual windows 7 and virtual ubuntu 12.04 both under bridged and NAT ethernet. I need to get it working on the windows 2008 server. 

As for the 
> //ipAddress/<share_name>
Yeah i've done that. I checked to make sure I had everything exactly right by pressing ctrl+L when I was connected via nautilus...

---

### Post by bab1 on 2014-02-02
> **thefatmoop said:**
> Yeah i've done that. I checked to make sure I had everything exactly right by pressing ctrl+L when I was connected via nautilus...

Not according to this```

#[COLOR="#FF0000"]//ipAddress/media/shared [/COLOR]/home/bo/shares cifs username=myUsername,password=Password123 0 0
#[COLOR="#FF0000"]//ipAddress/media/shared[/COLOR] /home/bo/shares cifs ro,auto,username=myUsername,password=Password123 0 0
#[COLOR="#FF0000"]//ipAddress/media/shared[/COLOR] /home/bo/shares cifs defualts,uid=1000,username=myUsername,password=Password123 0 0
[COLOR="#FF0000"]//hostname/media/shared [/COLOR]/home/bo/shares cifs username=myUsername,password=Password123,iocharset=utf8,sec=ntlm 0 0
#/[COLOR="#FF0000"]/ipAddress/media/shared[/COLOR] /home/bo/shares cifs username=myUsername,password=Password123,iocharset=utf8,sec=ntlm 0 0

```
None of the items in red are in the form of either //SRVER_NAME/SHARE or //ip_address/share.  The SERVER_NAME should be the the NETBIOS name rather than the hostname and the share should be expressed as the **share_name ** rather than the path to the share.

---

### Post by Morbius1 on 2014-02-03
> **bab1 said:**
> Not according to this```

#[COLOR=#FF0000]//ipAddress/media/shared [/COLOR]/home/bo/shares cifs username=myUsername,password=Password123 0 0
#[COLOR=#FF0000]//ipAddress/media/shared[/COLOR] /home/bo/shares cifs ro,auto,username=myUsername,password=Password123 0 0
#[COLOR=#FF0000]//ipAddress/media/shared[/COLOR] /home/bo/shares cifs defualts,uid=1000,username=myUsername,password=Password123 0 0
[COLOR=#FF0000]//hostname/media/shared [/COLOR]/home/bo/shares cifs username=myUsername,password=Password123,iocharset=utf8,sec=ntlm 0 0
#/[COLOR=#FF0000]/ipAddress/media/shared[/COLOR] /home/bo/shares cifs username=myUsername,password=Password123,iocharset=utf8,sec=ntlm 0 0

```
None of the items in red are in the form of either //SRVER_NAME/SHARE or //ip_address/share. 
I've seen that format work successfully so many times in this forum that I had to investigate this for myself since it doesn't make any sense to me either.

Here's what I think the issue is here: It's not "shared" that's shared ( in the Samba sense ) it's "media". I think the "shared" refers to a filesystem permissions sharing such that only one user or group has access.

For example, If I have shared /home/morbius/Public and have a subfolder named "Tools" I can mount just the "Tools" subfolder specifying just that folder with a:
```
//ipAddress/public/Tools
```
It's not an absolute path on the server - it's a path within the share.

---

### Post by bab1 on 2014-02-03
> **Morbius1 said:**
> I've seen that format work successfully so many times in this forum that I had to investigate this for myself since it doesn't make any sense to me either.

Here's what I think the issue is here: It's not "shared" that's shared ( in the Samba sense ) it's "media". I think the "shared" refers to a filesystem permissions sharing such that only one user or group has access.

For example, If I have shared /home/morbius/Public and have a subfolder named "Tools" I can mount just the "Tools" subfolder specifying just that folder with a:
```
//ipAddress/public/Tools
```
It's not an absolute path on the server - it's a path within the share.
I agree.  Sometimes it will work from the command line an sometimes it won't.  It sure creates inconsistencies.

---

### Post by thefatmoop on 2014-02-04
Sorry to not clarify, but yeah Bab1 i've tried every way that was mentioned including not going into sub-directories when connecting to the share like you brought up. So in the case you mentioned the 
> //ipAddress/<share_name>
Lets Say I shared the folder "media" with a user, then i'd do this for the server
> //ipAddress/media

And oddly here's what happens when I put the server's name -- even though it works in nautilus  
mount error: could not resolve address for serverName: Unknown error
mount error(13): Permission denied

I've followed every guide I can find online and none have solved the problem. The server i'm trying to connect to is an unpatched version of windows server 2008 (How unpatched I don't know). The server is a virtual machine cloned off another virtual machine server being used for the same application in a different location -- the fstab method has no problem connecting to the original virtual machine, so I eventually just cloned the ubuntu machine that works with the original windows server and still no go. The new clones and original vms are in different subnets. 

I'm really at a loss here... I've checked the windows side and see nothing wrong with user/permissions. I'm in the process of getting another windows server up to see if I can connect to it and whatnot. 

I've come to the conclusion that there's some bad joo joo on that network ;P

---

### Post by bab1 on 2014-02-04
> **thefatmoop said:**
> Sorry to not clarify, but yeah Bab1 i've tried every way that was mentioned including not going into sub-directories when connecting to the share like you brought up. So in the case you mentioned the 

Lets Say I shared the folder "media" with a user, then i'd do this for the server


And oddly here's what happens when I put the server's name -- even though it works in nautilus  
mount error: could not resolve address for serverName: Unknown error
mount error(13): Permission denied

The **share name** is NOT the directory name.  Let's say I have a share at *_/srv/samba/bab_* with the **share name** of [COLOR="#FF0000"]sysadmin[/COLOR].  The proper way to state the resource is //ipaddress/[COLOR="#FF0000"]sysadmin[/COLOR].  In fact if I were to move the share to /mnt/junk (by changing the path parameter) the share would still be located by  //ipaddress/[COLOR="#FF0000"]sysadmin[/COLOR].

> 
I've followed every guide I can find online and none have solved the problem. The server i'm trying to connect to is an unpatched version of windows server 2008 (How unpatched I don't know). The server is a virtual machine cloned off another virtual machine server being used for the same application in a different location -- the fstab method has no problem connecting to the original virtual machine, so I eventually just cloned the ubuntu machine that works with the original windows server and still no go. The new clones and original vms are in different subnets.

Regardless of all of this you still need to follow the basics.  Can you communicate with the server via PING?
>  

I've come to the conclusion that there's some bad joo joo on that network ;P

Hmmm. I don't have a cure for that.  ;-)

---

### Post by thefatmoop on 2014-02-04
Well as an update smbclient works, so i'll probably go with this program -- still need to write a script to use it.

---

### Post by steeldriver on 2014-02-04
Did you see this --> [http://askubuntu.com/a/404907/178692](http://askubuntu.com/a/404907/178692)

... seems to indicate a possible change in default SNB protocol version for 13.10 (and consequent need for an explicit vers= option)?

---

