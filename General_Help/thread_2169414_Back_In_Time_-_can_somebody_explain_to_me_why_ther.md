---
title: "Back In Time - can somebody explain to me why there is a root version?"
date: 2013-08-22
forum: General Help
---

### Post by Roasted on 2013-08-22
Tonight I installed Back In Time. I must say, this backup program is very, very nice. It's kind of like Deja Dup but with more control without being crazy overbearing with obnoxious features. Very satisfied with it so far. I ended up setting up a profile to rsync my data over SSH to my server from my laptop. So far, it's worked great. I went into the scheduling feature, which I thought for SURE would be why you'd need the root version. I set backups to run every 5 minutes. Then, I rebooted, and came up to a fresh instance on my laptop. I did not launch Back In Time. Instead, I just opened YouTube and killed 5 minutes while I was waiting for the Back In Time instance to supposedly run another snapshot. Meanwhile, I was in a terminal window SSH'd into my server. To my surprise, I saw another entry come up after 5 minutes as Back In Time had ran another backup. I did not have Back In Time open and there are no crontab entries for it.

So I got to wondering, what's the point of the root version? What does it do that I'm seemingly unaware of?

---

### Post by stinkeye on 2013-08-22
Haven't used, but I believe it would be
to retain file permissions when backing up files not owned by you?
eg back up and restore another users files or files owned by root.

---

### Post by Roasted on 2013-08-22
> **stinkeye said:**
> Haven't used, but I believe it would be
to retain file permissions when backing up files not owned by you?
eg back up and restore another users files or files owned by root.

What bothers me about the root version of B.I.T. is the fact that I cannot get a profile set up for SSH under the root side. Even if I choose my user (jason) as the SSH user, it errors out saying my.server.ip.address is not in ssh_known_hosts. But in order to do that, I would have to run ssh-keygen, then ssh-copy-id [email]user@my.server.ip.addres[/email]s.... which I did under jason, but I cannot do this under root due to the nature in which the root user is handled in Ubuntu.

Does anybody have B.I.T. Root working over SSH? I'd love to hear if you ran into this issue, and if you did, how you worked around it.

In other news, the non-root version with syncing my data as jason (my user) is working great. Extremely solid backup application thus far.

---

### Post by Germar on 2013-09-07
For SSH in BackInTime running as root you need to create a public-private key pair for root, too. At the moment you only have a key pair for you local 'jason' user. And also only your 'jason' user knows the remote ssh-server. The ssh keys for root will be stored in /root/.ssh/

```

sudo -s
ssh-keygen -t dsa
ssh-copy-id -i /root/.ssh/id-dsa.pub REMOTE-USER@HOST
exit

```

Regards,
Germar

---

### Post by publicface on 2014-06-26
I have followed this advice (although substituting rsa for dsa).  I'm getting "111.111.111.111 not found in ssh_known_hosts." (I'm using an IP address not a host name).

Any thoughts on this?  

Thank you


> **Germar said:**
> For SSH in BackInTime running as root you need to create a public-private key pair for root, too. At the moment you only have a key pair for you local 'jason' user. And also only your 'jason' user knows the remote ssh-server. The ssh keys for root will be stored in /root/.ssh/

```

sudo -s
ssh-keygen -t dsa
ssh-copy-id -i /root/.ssh/id-dsa.pub REMOTE-USER@HOST
exit

```

Regards,
Germar

---

### Post by publicface on 2014-06-26
It turns out that because I followed someone's advice on another post elsewhere, I created a /etc/ssh/ssh_known_hosts file.  That was enough to prevent my ~/.ssh/known_hosts file from being generated.  Deleting the system file allowed the one I needed to be generated properly by running ssh [FONT=verdana]REMOTE-USER@HOST

[/FONT]Perhaps someone else will find this info. helpful.

> **publicface said:**
> I have followed this advice (although substituting rsa for dsa).  I'm getting "111.111.111.111 not found in ssh_known_hosts." (I'm using an IP address not a host name).

Any thoughts on this?  

Thank you

---

