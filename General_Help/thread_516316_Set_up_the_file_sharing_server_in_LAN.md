---
title: "Set up the file sharing server in LAN"
date: 2007-08-03
forum: General Help
---

### Post by rockymaxsource on 2007-08-03
Hey,

We have about 10 computers in my LAN. The computer I'm using is Ubuntu 7.0.4. I want to share my documents with my co-workers who are using Windows XP.  Therefore I installed samba and smbfs. and in the /etc/samba/smb.conf I add the following
   > [MyFiles]
    path = /home/lover/samba/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0766
    directory mask = 0766
    force user = nobody
        force group = nogroup
I did smbpasswd -a lover as well.

In the Windows XP workstation I browse to \\my.ip.address.is prompt me to input the user name and password. I input the lover as user name and the password I inputed the same as the one I gave with the smbpasswd command. But the system hangs there with the log in interface.

Can any of you help me please?

Blessings,
Rocky

---

### Post by DrSpirograph on 2007-08-04
What do you mean it hangs? It asks you for your password again? Or it just sits there trying to log in forever?

You could check out the logs in
/var/log/samba
to see whats going on.

Also if it's a problem with things taking a long time, it might be a name resolution issue, check that your computers are able to resolve each others names.

---

### Post by rockymaxsource on 2007-08-06
Hey DrSpirograph,

Thank you very much for your reply! I mean it just sits there trying to log in forever. I have attached a screen shot show exactly what I mean.

Since I'm using the private static IP to log in, I think name resolution is not the problem. Do I have to make some changes to the windows system?

Thanks a lot!
Blessings,
Rocky

---

### Post by freebeer on 2007-08-06
did you try dropping the machine name and just log in with "lover"  (ie NOT LAPTOP/lover)

---

### Post by rockymaxsource on 2007-08-06
Hey freebeer,

Thanks very much for your input! Yes I tried to do that but I can not get rid of that. The machine name is prefixed automatically. I try to eliminate that by comment out   "name resolve order = hosts wins bcast" in /etc/samba/smb.conf file. But no success.

The problem still hold me up. Can any of you help me please?

Blessings,
Rocky

---

### Post by freebeer on 2007-08-06
hmm... instead of adding it in "Network Places" in XP, have you tried just mapping the drive directly?  (I used Windows Explorer to do this.)

Another thing you might want to look into: adding the machine (not just the user) to the Samba configuration.  Seem to me I did that on my 6.06 box.  (I was following a HOWTO without understanding much of it - and it's been quite a while since I did that.)  This may be a blind alley, but I thought I'd mention it just in case.

---

### Post by rockymaxsource on 2007-08-07
Hey freebeer,

Thank you very much for your reply! Yes I tried your proposals, but still got the same problem. Can any of you help me please?

Blessings,
Rocky

---

