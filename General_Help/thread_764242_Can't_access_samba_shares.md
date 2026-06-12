---
title: "Can't access samba shares"
date: 2008-04-23
forum: General Help
---

### Post by Mateo on 2008-04-23
Ok, so I have several shares in my samba network.  I can't access any of them.  It asks for a user name and password.  First, only 1 of my computers is linux.  this one i created a username and password using:

smbpasswd -a username

But I can't even access THOSE shares in nautilus.  it doesn't except the password.

Weird thing is that this was working perfectly fine yesterday.  as far as I know, i haven't changed anything.  Problem is that I dont' even know where to begin to look to solve this problem.

---

### Post by Mateo on 2008-04-23
now i restarted my computer and it's not even showing any computers on the network at all!!

I **hate** stuff that works one day and then not the next. that's why i absolutely hate networking stuff.  there's never any consistency.

---

### Post by Mateo on 2008-04-23
ok, so now they have mysteriously showed up again.  nevertheless, the samba password is not letting me in. 

CAN ANYONE OFFER ADVICE?

---

### Post by upthelum on 2008-04-23
You could try this. Change your password using 
smbpasswd username
then try logging in again. 
Do 
/etc/init.d/smb start
 to make sure it's running, then 
/sbin/chkconfig smb 
to start it every time you boot.

---

### Post by Mateo on 2008-04-23
lol, it gets better.  now i'm not able to create new users with smbpassword.

---

### Post by upthelum on 2008-04-23
Are you root? sudo smbpasswd username

---

### Post by Mateo on 2008-04-23
yep.  


matthew@matthew-desktop:~$ sudo smbpasswd -a newuser
New SMB password:
Retype new SMB password:
Failed to modify password entry for user newuser
matthew@matthew-desktop:~$

---

### Post by Mateo on 2008-04-23
haha, restarted my computer and now my shares don't even show up in nautilus **period**.  Just says Windows Network, with nothing in it.

---

### Post by upthelum on 2008-04-23
Does it work with -m instead of -a?

---

### Post by Mateo on 2008-04-23
it must have fallen asleep.  now it's showing up.

---

### Post by Mateo on 2008-04-23
uh.  any time you change a share it takes FOREVER for it to show up on the network.

---

### Post by upthelum on 2008-04-23
Glad you got it...

---

### Post by Mateo on 2008-04-23
i didn't get it.  my shares aren't even showing up on the network.  i restarted my computer again.  the shares aren't showing up.

---

### Post by Mateo on 2008-04-23
that's it.  i'm fed up.  switching to nfs.

---

### Post by upthelum on 2008-04-23
Thats about as much as i can help you with.

---

### Post by bodhi.zazen on 2008-04-23
You might want lo look at this :

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by Mateo on 2008-04-24
> **upthelum said:**
> Thats about as much as i can help you with.

thank you for your help, but i got completely fed up with samba and switched to nfs.  so far so good.

---

