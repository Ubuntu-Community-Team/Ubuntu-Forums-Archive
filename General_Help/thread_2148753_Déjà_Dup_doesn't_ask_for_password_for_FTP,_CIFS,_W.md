---
title: "Déjà Dup doesn't ask for password for FTP, CIFS, WebDAV or SSH backups"
date: 2013-05-26
forum: General Help
---

### Post by alex-s77 on 2013-05-26
Hello

I'd like to backup my laptop to my local NAS (a Synology DS212). The Syno supports FTP, WebDAV, CIFS or SSH. For backup, I'd like to use Déjà Dup.

In Deja Dup, I configured it to use FTP, like so: [ATTACH=CONFIG]243069[/ATTACH]

I also tried SSH, WebDAV and CIFS. The FTP target directory does exist: [ATTACH=CONFIG]243067[/ATTACH]

But when I then try to run a backup, it never passes beyond this screen: [ATTACH=CONFIG]243068[/ATTACH]

And it also never asked for a password. I guess, it should've, shouldn't it?

When I run "deja-dup --backup" from the command line, I don't see any error or so. Just that window shown in the 3rd screenshot pops up, and that's that.


Well - what did I do wrong and how do I use deja-dup to do backups to FTP/SSH/SFTP/CIFS/WebDAV?

Thanks,
Alexander

---

### Post by pedrobl on 2013-08-26
Same thing here, did you find any workaround?

---

### Post by pedrobl on 2013-08-26
I found a solution. deja actually works with sftp. You need to add sftp support to your ssh server by adding the following line to the sshd_config file:

```
Subsystem sftp /usr/libexec/openssh/sftp-server
```

And restart your sshd server.

HTH, cheers,

Pedro.

---

### Post by alexander-skwar on 2013-08-27
Well, if it were that easy… :o


I do have sftp enabled:

```
root@Speicher ~ # grep sftp /etc/ssh/sshd_config 
#Subsystem    sftp    /usr/libexec/sftp-server
#Subsystem       sftp    internal-sftp -f DAEMON -l VERBOSE -u 000
Subsystem       sftp    internal-sftp -f DAEMON -u 000
#Subsystem       sftp    /usr/syno/sbin/sftp-server -l DEBUG3

```
And sure enough, sftp works from the command line:

```

(1)9:52% sftp admin@disk
Connected to disk.
sftp> pwd
Remote working directory: /
sftp> cd home
sftp> mkdir Sicherung
sftp> cd Sicherung/
sftp> mkdir DejaDup
sftp> cd DejaDup
sftp> pwd
Remote working directory: /home/Sicherung/DejaDup
sftp> ^D


```




And it does not work.
[CENTER][IMG]http://alexs77.1st.ch/pics/01-DejaDup-Sicherung-Einstellungen.png[/IMG]

[IMG]http://alexs77.1st.ch/pics/02-DejaDup-Sichern.png[/IMG][/CENTER]

To be honest, I gave up on Deja Dup. I contacted the dev but didn't get a good, concrete answer. Seems nobody cares. Time to move on to something, which DOES work. Deja Dup obviously does not and nobody cares.

OTOH - if somebody knows how to make Deja Dup work with SSH, I'd be very happy to know! Simply enabling sftp is not the answer.

Cheers,
Alexander

---

