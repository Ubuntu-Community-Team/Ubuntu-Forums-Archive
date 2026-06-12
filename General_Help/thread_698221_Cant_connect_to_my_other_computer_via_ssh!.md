---
title: "Cant connect to my other computer via ssh!"
date: 2008-02-16
forum: General Help
---

### Post by CameronCalver on 2008-02-16
Hey iv done this for years just with terminal 
```
ssh -X calver@192.168.0.2
``` and things like that but i reinstalled the  192......0.2 and now i canot unless under root this is the error
```
cameron@ubuntu:~$ ssh -X calver@192.168.0.2
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
90:aa:39:2d:ce:06:c3:e6:4c:e0:0b:55:44:91:78:64.
Please contact your system administrator.
Add correct host key in /home/cameron/.ssh/known_hosts to get rid of this message.
Offending key in /home/cameron/.ssh/known_hosts:1
RSA host key for 192.168.0.2 has changed and you have requested strict checking.
Host key verification failed.
cameron@ubuntu:~$ 


```

---

### Post by kesman on 2008-02-16
your host information has changed. Go to ~/.ssh/ and open the file in there that contains the RSA keys and remove all of them. Then try again and answer yes to the question about the host being trusted.

---

### Post by Herman on 2008-02-16
SSH remembers the ID of other computers you connect to and it has detected that something has changed. This message is to protect you from an imposter pretending to be a computer you normally connect to. That wouldn't happen in a home LAN, but SSH was designed to be used in an untrusted network, so it's just being extra careful.

You can safely delete the file SSH uses to record the IDs of other computers,
```
rm .ssh/known_hosts
```Now make the connection again,```
ssh -X calver@192.168.0.2
```Once you have deleted the file called 'known_hosts', SSH will connect no worries. It will automatically regenerate a new 'known_hosts' file right away.

Regards, Herman :)

---

### Post by Whiffle on 2008-02-16
What its telling you is that the host you're trying to connect to has a different key than it had earlier, which could be a sign of a big security issue, hence the big warning.  But since you reinstalled on the host machine its safe, as that would change the key.

---

### Post by CameronCalver on 2008-02-16
I tryed that and it still doesnt work?

---

### Post by CameronCalver on 2008-02-17
anyone

---

### Post by Herman on 2008-02-17
```
sudo rm -rf .ssh
```
:) Try that then, that command should be a bit more potent.

Regards, Herman :)

---

### Post by CameronCalver on 2008-02-17
AHHH still not working wat the?

---

### Post by aBitLater on 2008-02-26
I had the same problem as you, followed the advice here, and deleted the known_hosts from my regular user home directory.  Didn't work for because I was using a root terminal for ssh, so  if you're trying to connect via .ssh in a root terminal, you need to delete /root/.ssh/known_hosts. 

I suppose the same would apply for any user (and there respective /.ssh/known_hosts files) on your machine.

---

### Post by CameronCalver on 2008-03-13
nope still not working ahhh this is getting annoying  i can only connect using root terminal i need this fixed

---

