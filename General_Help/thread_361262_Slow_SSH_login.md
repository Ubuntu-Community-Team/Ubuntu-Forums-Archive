---
title: "Slow SSH login"
date: 2007-02-14
forum: General Help
---

### Post by DiGiTY on 2007-02-14
Whenever I enter a username when SSH'n into my Ubuntu (6.06) box I get a long pause before it asks for the password. This happens with any user account and any SSH client.

How do I fix this so it prompts for password right after i put in the username???

TIA

---

### Post by LotsOfPhil on 2007-02-14
I don't know if SSH is 'voluntarily' being slow. You might try configuring passwordless login, [http://www.fastechlc.com/tricks/unix/0002.php](http://www.fastechlc.com/tricks/unix/0002.php)

---

### Post by beerorkid on 2007-02-14
has it been faster in the past?
do you have anything mounted like a samba share?

Many times I have run into problems when a samba share is mounted and then the samba mount goes down it will make it slow.

---

### Post by Keith Hedger on 2007-02-14
I found ssh slow when asking for passwords too and also a pain so i switched to RSA authentication and it seems to connect faster and no annoying asking for passwords, and probably more secure than using password

---

### Post by buttari on 2007-05-03
> **Keith Hedger said:**
> I found ssh slow when asking for passwords too and also a pain so i switched to RSA authentication and it seems to connect faster and no annoying asking for passwords, and probably more secure than using password

Hi,
I solved the problem commenting these lines in /etc/ssh/ssh_config

#    SendEnv LANG LC_*
#    HashKnownHosts yes
#   GSSAPIAuthentication yes
#   GSSAPIDelegateCredentials no


Alfredo

---

### Post by zasf on 2007-05-07
worked for me also

btw ssh_config to be modified is client's one

Matteo

---

### Post by BigDaddyEBK on 2007-06-17
No luck for me. :-({|=

---

### Post by azc on 2007-06-17
Not sure if this is related, but I was getting slow SSH logins on my LAN, but normal logins on my public server, and saw this suggestion on another thread here.

System > Administration > Network > Network Settings > General tab > uncheck 'Automatic service discovery'

Anyway, that cleared things up for me, and I didn't need to edit any files.

Using Ubuntu 7.04

---

### Post by meatpan on 2007-06-17
Rather than immediately jumping to the editing of config options, try to pinpoint the exact bottleneck in the ssh login process.  Adding '-vv' to the command options will print extra verbose messaging to stdout.  You will be able to see which portion of the authentication handshake is blocking or taking an exceptionally long time.  It is much easier to diagnose a specific stage of the login process in this manner.

SSH is intended to be safe and secure from the get-go, so try to be as deliberate as you can when you change the server/client behavior.

---

### Post by nekoyokoshima on 2007-06-28
The problem lies with the GSSAPIAuthentication. Apparently this is a new implementation on the whole SSH client/server suite. Predictibly most servers do not use it, while the ssh clients are being updated on desktops. So the client will try to connect with GSSAPI to a server which does'nt know what it is.

There are two solutions:-
1. Update the openssh server package
2. edit /etc/ssh/ssh_config with your fav editor and remark
> GSSAPIAuthentication yes

Thanks to [ Invert Your Mind » Blog Archive » SSH login problems]("http://brian.pontarelli.com/2007/05/11/ssh-login-problems/") and [Experiencing weblogging]("http://www.rolfs.no/2007/05/24/ssh-debug1-an-invalid-name-was-supplied-configuration-file-does-not-specify-default-realm/") for the info

---

### Post by trtech on 2007-12-04
Interesting that there are so many possible solutions to this. I had this problem w/ client and server running 7.04, and fixed it. Then when I upgraded the desktop to 7.10, the problem reappeared. None of the suggestions above worked for me, but then I found this:

[http://m0n0.ch/wall/list/showmsg.php?id=134/67](http://m0n0.ch/wall/list/showmsg.php?id=134/67)

I fixed it by adding the following line to /etc/ssh/sshd_config :
UseDNS no

Cheers,
Chris

---

### Post by ABX on 2007-12-10
Thanks.

I had the same issue.

---

