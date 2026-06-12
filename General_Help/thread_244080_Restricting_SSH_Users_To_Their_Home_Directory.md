---
title: "Restricting SSH Users To Their Home Directory?"
date: 2006-08-25
forum: General Help
---

### Post by sddfdds on 2006-08-25
Is there a way to restrict SSH users to their home directory, so they can do whatever they want inside there, but not browse around the rest of the system?

Also, does the SSH server log all commands users execute, or only login attempts?

Thanks

---

### Post by peabody on 2006-08-25
You're going to need to look into setting up a chroot (change root) jail.  I haven't setup one myself, so unfortunately I don't have much advice, perhaps someone else, or googling could turn up a howto.  I do know that you will probably want to move the home folders of these particular users to a different area, and you are also going to need to copy a lot of stuff from /bin /usr /lib and /usr/lib to that folder.

---

### Post by ruudiculus on 2006-08-26
Hey, I have the same question. I found an article [here]("http://www.securityfocus.com/infocus/1404") and tried it, but still my chrooted user(s) can walk around everywhere!

I found a Debian howto as well ([here]("http://www.debian.org/doc/manuals/securing-debian-howto/ap-chroot-ssh-env.en.html"))

but I haven't yet tried it since it seemed a bit more difficult than the other method.

---

### Post by ruudiculus on 2006-08-26
Well, it seems like the first article is OK if you use SSH2 instead of SSH1 (Ubuntu Server uses SSH1).

I think I'll try the second (Debian) method in some days...

---

### Post by kaamos on 2006-08-26
> Well, it seems like the first article is OK if you use SSH2 instead of SSH1 (Ubuntu Server uses SSH1).

Ssh-servers by default use both protocols. You can change this by setting with the option "Protocol" in /etc/ssh/sshd_config

I used this howto: [http://www.howtoforge.com/chrooted_ssh_howto_debian](http://www.howtoforge.com/chrooted_ssh_howto_debian) except that [jailkit](http://olivier.sessink.nl/jailkit/) makes adding programs to the jail much simpler.

---

### Post by sddfdds on 2006-08-29
What about logging?  How can I log, for example, which files a user puts/gets?

---

### Post by peabody on 2006-08-29
> **sddfdds said:**
> What about logging?  How can I log, for example, which files a user puts/gets?

What service?  SCP?  FTP?  HTTP Post?

---

### Post by sddfdds on 2006-08-30
ssh/scp/sftp

puts and gets mostly, mvs, cps, mkdirs too

---

### Post by peabody on 2006-08-30
> **sddfdds said:**
> ssh/scp/sftp

puts and gets mostly, mvs, cps, mkdirs too


ssh/scp/sftp have their own logging in /var/log/secure I believe (I'm fuzzy on this, someone please correcty me).  As for their command history, I'm not sure if there's a package that does this.  If there is, I'm not familiar with it.  You can try to lockdown their history file by trying something like this in the chroot jail home folder of each user:

```

chown root.username .bash_history
chmod 660 .bash_history
cd ..
chown root.username username
chmod 1775 username

```

That locks them out of ownership of both their home folder and .bash_history file while allowing the user to write to them, yet not delete them.

---

### Post by thk on 2006-08-30
You might try rbash, although I suspect that would be too restrictive.

---

### Post by sddfdds on 2006-09-01
They log to /var/log/auth.log, there is no /secure.  I tried the various debug settings of sshd_config to see if any of them produced command logs, but to no avail.  I thought there might be a simple way, similiar to apaches logging which has GETs for each web page served.  The bash_history only works for ssh sessions, but not sftp.

---

