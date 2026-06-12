---
title: "Samba not working?"
date: 2007-02-02
forum: General Help
---

### Post by Dr Small on 2007-02-02
Hello, I just noticed that my Samba is not working for other people on other computers (they are on Windows), yet I can access their computer (local network). I have internet and can access my own IP (of which I have my localhost, using XAMPP [lampp] ).

So, is there some way to restart Samba or something?
Because samba WAS working, and then it quit for some reason and is no one can access MY IP (where my localhost is) or my shared folder (my home folder that I shared.)

So, if anyone could possibly help me, I would greatly appreciate it. :)

Dr Small

---

### Post by Paerez on 2007-02-02
look in the file:
/etc/samba/smb.conf

and make sure that this line says "NO":
wins server = no

EDIT: to restart, type "sudo /etc/init.d/samba restart"

---

### Post by Dr Small on 2007-02-02
Check it, and it already said "no":

> 
# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
;   wins support = no

And I tried restarting Samba and it still didn't work....


Dr Small

---

### Post by Paerez on 2007-02-02
can they see it but not access it? Or can they just not see it?

If they can't see it you can type in "\\ip\" (for instance "\\192.168.0.100\" in their Windows Explorer bar to force windows to look.

---

### Post by Dr Small on 2007-02-02
I just went to my Windows XP laptop, and tried:
> \\192.168.0.103\
(that's my network IP)
That didn't work, so I tried:
> \\drsmall\
(my system name, that used to prompt me with a username/password {samba} and I could then access my PC)
And that didn't work.

I have EasyPhp running on the laptop, (which is basically a webserver over the network) and went to it's IP via my Ubuntu box, and I could access it. If I'm on the laptop, and type my IP for the Ubuntu box, it times out...

The thing is, all of this used to work, and then it quit working! :S

Dr Small

---

### Post by Paerez on 2007-02-02
try to do a reinstall:

```
sudo aptitude reinstall samba
```

**if that doesn't work**, copy your /etc/samba/smb.conf to your desktop as a backup, then run this:
```
sudo aptitude purge samba samba-common
sudo aptitude install samba samba-common
```
then restore your smb.conf.

---

### Post by Dr Small on 2007-02-02
hmmm.
I just tried everything you just told me, in that order, I tried reinstalling Samba, that didn't work, and then tried the other aptitude cmds and restored the smb.conf (after I had saved it to my desktop), went to my sister's computer, and went to My IP (192.168.0.103) and it didn't do anything.

As a matter of fact, I timed out.

I'm stumped.

Dr Small

---

### Post by Paerez on 2007-02-02
OK a couple of "duh" things:

Reboot?

All the computers involved can access the internet?

---

### Post by Dr Small on 2007-02-02
ok. duh. I'll be the idiot.
And yes, all computers have internet access.

Lemme reboot.
I've been gimping and doing this the entire time, so my brain wss somewhat cluttered. :P

Dr Small

---

### Post by Paerez on 2007-02-02
Hey you never know. Even in linux a reboot helps. Good luck.

Can you post "/var/log/samba/log.drsmall"?

---

### Post by Dr Small on 2007-02-02
Reboot didn't work. Still can't access it....
And my /var/log/samba/log.drsmall file is empty !? Strange... Maybe because I just reinstalled samba? I dunno.

Dr Small

---

### Post by Paerez on 2007-02-02
what files are in the /var/log/samba folder?

---

### Post by Dr Small on 2007-02-02
log.nmbd and log.smbd

[quote=log.nmbd][2007/02/02 21:14:46, 0] nmbd/nmbd.c:main(727)
  Netbios nameserver version 3.0.22 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2006
[2007/02/02 21:19:06, 0] nmbd/nmbd.c:terminate(58)
  Got SIGTERM: going down...
[2007/02/02 21:20:42, 0] nmbd/nmbd.c:main(727)
  Netbios nameserver version 3.0.22 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2006
[2007/02/02 21:26:31, 0] nmbd/nmbd_become_lmb.c:become_local_master_stage2(396)
  *****
  
  Samba name server DRSMALL is now a local master browser for workgroup MSHOME on subnet 192.168.0.103
  
  *****
[2007/02/02 21:32:24, 0] nmbd/nmbd.c:terminate(58)
  Got SIGTERM: going down...
[2007/02/02 21:32:28, 0] nmbd/nmbd.c:main(727)
  Netbios nameserver version 3.0.22 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2006
[2007/02/02 21:38:17, 0] nmbd/nmbd_become_lmb.c:become_local_master_stage2(396)
  *****
  
  Samba name server DRSMALL is now a local master browser for workgroup MSHOME on subnet 192.168.0.103
  
  *****
[/quote]

[quote=log.smbd][2007/02/02 21:14:46, 0] smbd/server.c:main(805)
  smbd version 3.0.22 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2006
[2007/02/02 21:20:42, 0] smbd/server.c:main(805)
  smbd version 3.0.22 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2006
[2007/02/02 21:32:28, 0] smbd/server.c:main(805)
  smbd version 3.0.22 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2006
[/quote]

---

### Post by Paerez on 2007-02-02
hmm. I am tapped out of suggestions.

Maybe try making a backup of smb.conf and then running:
```
sudo dpkg-reconfigure samba
sudo /etc/init.d/samba restart

```

That will put in a default samba file. Then add a share.

Then see if someone can connect.

---

### Post by Dr Small on 2007-02-03
Hmm. I just tried what you said. and still didn't work.
I checked the /etc/samba/smb.conf file. and it still had the previous settings at the bottom.
Went to System -> Administration -> Shared Folders and it still had my shared folder in there.  :S
(And this was after I ran BOTH commands. The reconfigure and the restart on samba, and then I rebooted)

Maybe it has something to do with Xampp (Lamp Server) or something. I'm bumfuzzled.
Because I have Lamp to autostart at reboot, so my "localhost webserver" will always be avalible to the network. But even after I stop Xampp, the problem still persists....

Dr Small

---

### Post by Paerez on 2007-02-03
Under General Properties in the Shared Folders program is WINS Server unchecked?

---

### Post by Dr Small on 2007-02-03
Basically, yes.
I'm on Dapper Drake, so it may appear a little different. Mine is checked as, "Do not use WINS server"

Screenshot:
[http://ubuntuforums.org/attachment.php?attachmentid=24492&stc=1&d=1170546054](http://ubuntuforums.org/attachment.php?attachmentid=24492&stc=1&d=1170546054)


Dr Small

---

### Post by Dr Small on 2007-02-26
Geesh. It's been 3 weeks, and I finally found out what my problem was.

Apparently I had installed Firestarter (Firewall) on Ubuntu before all my problems started, and it was blocking incoming requests to my computer (that just shows you the power of linux!)
Anyhow, I had to add the other network IP addresses into my allow policy, and now they can access my computer! yay!

Sincerely,
Dr Small

---

