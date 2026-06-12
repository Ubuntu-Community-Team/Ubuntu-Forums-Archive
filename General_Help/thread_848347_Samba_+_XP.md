---
title: "Samba + XP"
date: 2008-07-03
forum: General Help
---

### Post by chrislynch8 on 2008-07-03
Hi,

I have a Ubuntu server running samba.

When I connect to my Samba share in XP it asks for the username and password. I enter this and it all works. My issue is that when I close out of my share and try to go back in again XP has retained my username and password.

I the Ubuntu desktop if you access the samba share it asks for Username and Password and when I exit and try to go in again it will ask for the username and password again. This is what I want to happen when I have XP client connecting to there shares..

In XP there is an option to save the password when you connect but I do not check this.

Is this a setting that must be changed on Samba or is there something in XP that I can say never remember usernames and passwords for this connection/network etc.


Any help would be greatly appreciated and if this is in the incorrect forum sorry.

Chris

---

### Post by rbc on 2008-07-03
I wanted to have the same setup as you, to force the Windows user to enter user and password in order to access the shared folder on Ubuntu. What I was told was that the problem actually lies with Windows, as it caches that login information. Keep in mind I was using the Desktop version, not Ubuntu Server edition, so things may be different

---

### Post by marshal on 2008-07-03
hi i think you are looking for something like this

[http://support.microsoft.com/?scid=kb%3Ben-us%3B281660&x=7&y=9]("http://support.microsoft.com/?scid=kb%3Ben-us%3B281660&x=7&y=9")

i dont think this is a nice solution, but it windows:confused:

---

### Post by chrislynch8 on 2008-07-04
Hi Marshal,

Thanks for the response but I found this already and it does not contain my information.

I log into XP using my username and password. I have approx 20 samba users setup and I'm trying to test there security settings. So if I connect to \\192.168.1.250 and give the username johnwall and his password its fine. If the shares then and type \\192.168.1.250 it is logging back into john walls account.

His username and password does not appear in the Stored Usernames and Passwords. 

I'm thinking maybe a cookie or something gets created and this is the reason as if I restart XP I will have to enter the password again.


Chris

---

### Post by marshal on 2008-07-04
hi,

i took another look.

before connecting to a samba share with windows open a cmd in windows. here you type:

```
net use
```

this will give you a list of netlogons windows is currently connected. i think the list will be empty =)
```

Status   Lokal    Remote       Network
--------------------------------------

```

now connect to the samba share as usual

after connection run
```
net use
```
again

now there should be a line like:
```

Status   Lokal    Remote                Network
-----------------------------------------------
OK                \\"samba-server"\     Micorsoft Windows-Network

```

so win created a new netlogon. to stop the logon and delete the connection informations u can use this command
```
net use /delete \\"samba-server"\
```
command: net use /delete +remote-address.
i think you can't use wildcards, so writing a batch is not that easy

---

### Post by chrislynch8 on 2008-07-04
Hi,

Thanks for that it worked a charm.

Now I have to figure out how to make this automatic.

I will post it here I get get a batch script to work.

Rgds
Chris

---

### Post by marshal on 2008-07-04
you could use 

net use /delete * /y

this will stop every share you have connected

---

### Post by chrislynch8 on 2008-07-04
HI so this little script is what I'll be using.

```

@ECHO OFF
ECHO.
ECHO Removing all open network connections
ECHO Please wait........
ECHO.
net use /delete * /Y
#PAUSE
CLS
EXIT

```

This works fine for what I require which may or maynot be correct for anyone else.

Rgds
Chris

---

### Post by KennedyM on 2008-08-25
Chris,

I tried to cover that issue in a HOWTO at: [http://ubuntuforums.org/showthread.php?t=720889](http://ubuntuforums.org/showthread.php?t=720889)

  - Mike

---

