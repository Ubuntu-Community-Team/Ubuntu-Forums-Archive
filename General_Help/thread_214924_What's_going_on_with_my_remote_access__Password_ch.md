---
title: "What's going on with my remote access?  Password changed?"
date: 2006-07-13
forum: General Help
---

### Post by Getwild2 on 2006-07-13
For some reason I receive an [COLOR="Navy"]"Access denied"[/COLOR] error when trying to connect to my Ubuntu box via putty but I have not changed my password!

I then try to connect via FreeNX and I receive this:
[COLOR="Navy"]NX> 203 NXSSH running with pid: 2736
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 200 Connected to address: XX.XXX.XXX.XX on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
NX> 204 Authentication failed.[/COLOR]

In both of the above examples I make a connection, its just not allowing me to authenticate.  I logged into my system last night with the account I am now trying to use and it worked just fine.  Why does it not work now?

Any suggestions? ](*,)

---

### Post by T700 on 2006-07-13
Is it possible your system rebooted (power failure?) and is not logged in?  Unlikely, but perhaps someone got in and changed it.

Paul

---

### Post by Getwild2 on 2006-07-13
> **T700 said:**
> Is it possible your system rebooted (power failure?) and is not logged in?  Unlikely, but perhaps someone got in and changed it.

Paul
My system has never needed to be logged in for me to access via putty or FreeNX.  If there was a power failure my system would be off and I wouldnt even be able to connect.  

I'm wondering if someone got in and changed it.  Strange though because I logged in last night just fine physically sitting in front of it and I keep it powered off at night.

My only thought is that we just hired this guy who is studying internet/LAN security and he saw me on my system the other day while at work.  Possibly he got my IP and hacked it somehow, I dont know.  I think that would be unlikely but possible I guess.  He was talking the other day about being a "hacker", I thought, "Great, what kind of idiot did we just hire".  

I wonder if it is more of an issue than hacking because I physically logged on last night just fine.  It's been days since I have been able to log on remotely.

---

