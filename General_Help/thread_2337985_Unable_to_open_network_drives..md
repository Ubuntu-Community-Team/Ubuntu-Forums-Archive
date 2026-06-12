---
title: "Unable to open network drives."
date: 2016-09-23
forum: General Help
---

### Post by uRock on 2016-09-23
Hi all!

I've noticed that I am unable to mount network drives in Nautilus for the past few days. [s]Could it be because I've enabled UFW?[/s] I turned off UFW and same thing.

Here's a quick screen record, [https://youtu.be/aB6MTFQhi7o](https://youtu.be/aB6MTFQhi7o)

Thanks for your input!

Cheers & Beers,
uRock

---

### Post by SeijiSensei on 2016-09-23
Can you connect with "smbclient -U username \\\\server\\share"?

---

### Post by uRock on 2016-09-23
> **SeijiSensei said:**
> Can you connect with "smbclient -U username \\\\server\\share"?

No, but I am probably getting the syntax wrong. I can connect using the "Connect to server" option in Nautilus, just can't click on Network and browser the network shares like I used to.

---

### Post by bab1 on 2016-09-23
> **uRock said:**
> No, but I am probably getting the syntax wrong. I can connect using the "Connect to server" option in Nautilus, just can't click on Network and browser the network shares like I used to.
Do some debug then. Post the output of this terminal command```

smbclient d-3 -U <yourusername> ////server//share
```
The syntax is exactly as you see it. The only variables are <yoursername> and ////servername//share

---

### Post by uRock on 2016-09-24
I get ```
Connection to DriveAway failed (Error NT_STATUS_HOST_UNREACHABLE)
``` when I run the original command. I get the following with your command, ```
d-: Not enough '\' characters in service
```Possible local DNS issue?

---

### Post by bab1 on 2016-09-24
> **uRock said:**
> I get ```
Connection to DriveAway failed (Error NT_STATUS_HOST_UNREACHABLE)
``` when I run the original command. I get the following with your command, ```
d-: Not enough '\' characters in service
```Possible local DNS issue?Sorry that is my fault.  The / should be \  or you can just use this for the debug```
smbtree -d3
```
Host unreachable can be many things, but I doubt it is dns.  It seems that the host is known but unavailable.

---

### Post by SeijiSensei on 2016-09-24
You can use either "//server/share" or "\\\\server\\share" with modern versions of smbclient.  Originally you could only use the backslashes the same way Windows does.  However since \ operates as the "escape" character in the shell, you need to use "\\" to enter the literal "\".  I've tried to break myself of the habit of using \\\\, but I've been using Samba for so long that I forget!

So try
```
smbclient -U username //server/share
```

---

### Post by uRock on 2016-09-25
```
ronnie@5FDP:~$ smbclient -U mcadmin //192.168.1.62/Videos
WARNING: The "syslog" option is deprecated
Enter mcadmin's password: 
Domain=[WORKGROUP] OS=[Windows 6.1] Server=[Samba 4.3.9-Ubuntu]
tree connect failed: NT_STATUS_BAD_NETWORK_NAME
```Oddly enough, when I use the Connect to Server in Nautilus it connects with no problems.

---

### Post by SeijiSensei on 2016-09-25
You have to use a hostname.  You can tell smbclient what the IP address of the host is with
```
smbclient -I 192.168.1.62 //server/Videos
```
or you can just create an entry in /etc/hosts for the server's name assuming you're not running a local DNS server.  See "man smbclient" for details.

---

