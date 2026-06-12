---
title: "kex error"
date: 2015-09-30
forum: General Help
---

### Post by pcjunki on 2015-09-30
I'm brand new to Linux, and installed Ubuntu, I've been using for about a couple weeks now, and love it!
I've set up open ssh on it, so I can ssh into it with no problem at all.

I recently found on google about a program called x2go, so I have it installed on my Ubuntu, but on my win7 computer I get this error message from the x2go client

---------------------------
Can not connect to mywanip:22
---------------------------
kex error : did not find one of algos diffie-hellman-group1-sha1 in list [EMAIL="curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group14-sha1"]curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group14-sha1[/EMAIL] for kex algos
---------------------------
OK   
---------------------------

what do I need to do?
please be easy with me, this is my first posting, and I have somewhat knowledge of Linux commands, but will need babysteps

---

### Post by Lars Noodén on 2015-10-01
Welcome.

It sounds like you need a newer version of X2go for your legacy OS as it looks like it is trying to use a Key EXchange algorithm that is no longer allowed.  If you log in via SSH and then run the following, it should tell you which algorithms are currently used on the server:

```

ssh -Q kex

```

It will probably show something including [email]curve25519-sha256@libssh.org[/email],ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,or diffie-hellman-group14-sha1.

Any tool that operates over SSH will need to support one of those.

Which version of OpenSSH server are you running on Ubuntu?

---

### Post by pcjunki on 2015-10-01
I ran this command and this is the out come.

> pcjunki[EMAIL="pcjunki@homepc:~$"]@homepc:~$[/EMAIL] ssh -Q kex
diffie-hellman-group1-sha1
diffie-hellman-group14-sha1
diffie-hellman-group-exchange-sha1
diffie-hellman-group-exchange-sha256
ecdh-sha2-nistp256
ecdh-sha2-nistp384
ecdh-sha2-nistp521
diffie-hellman-group1-sha1
[EMAIL="curve25519-sha256@libssh.org"]curve25519-sha256@libssh.org[/EMAIL]


---

### Post by Lars Noodén on 2015-10-01
Ok.  And on the server, check what SSH server is configured to look for.

```

/usr/sbin/sshd -T | sort | less

```

(The output of [sshd's extended test](http://manpages.ubuntu.com/manpages/trusty/en/man8/sshd.8.html) is [sort](http://manpages.ubuntu.com/manpages/trusty/en/man1/sort.1.html)ed by line alphabetically and then paged using [less](http://manpages.ubuntu.com/manpages/trusty/en/man1/less.1.html). )

There should be a line starting with "kexalgorithms" that will show what the server accepts.

---

### Post by pcjunki on 2015-10-01
this is my output, and thank you for helping me, this is the first time I've dealt with setting up a ssh server, and I'm learning about keys also



> [EMAIL="pcjunki@homepc:~$"]pcjunki@homepc:~$[/EMAIL] /usr/sbin/sshd -T | sort | less
Could not load host key: /etc/ssh/ssh_host_rsa_key
Could not load host key: /etc/ssh/ssh_host_dsa_key
Could not load host key: /etc/ssh/ssh_host_ecdsa_key
Could not load host key: /etc/ssh/ssh_host_ed25519_key
acceptenv LANG
acceptenv LC_*
addressfamily any
allowstreamlocalforwarding yes
allowtcpforwarding yes
authenticationmethods
authorizedkeysfile .ssh/authorized_keys .ssh/authorized_keys2
challengeresponseauthentication no
ciphers 3des-cbc,blowfish-cbc,cast128-cbc,arcfour,arcfour128,arcfour256,aes128-cbc,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com,chacha20-poly1305@openssh.com
clientalivecountmax 3
clientaliveinterval 0
compression delayed
gatewayports no
gssapiauthentication no
gssapicleanupcredentials yes
gssapikeyexchange no
gssapistorecredentialsonrekey no
gssapistrictacceptorcheck yes
hostbasedauthentication no
hostbasedusesnamefrompacketonly no
hostkey /etc/ssh/ssh_host_dsa_key
hostkey /etc/ssh/ssh_host_ecdsa_key
hostkey /etc/ssh/ssh_host_ed25519_key
hostkey /etc/ssh/ssh_host_rsa_key
ignorerhosts yes
ignoreuserknownhosts no
ipqos lowdelay throughput
kbdinteractiveauthentication no
kerberosauthentication no
kerberosorlocalpasswd yes
kerberosticketcleanup yes
kexalgorithms diffie-hellman-group1-sha1,diffie-hellman-group14-sha1,diffie-hellman-group-exchange-sha1,diffie-hellman-group-exchange-sha256,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group1-sha1,curve25519-sha256@libssh.org
keyregenerationinterval 3600
listenaddress 0.0.0.0:22
listenaddress [::]:22
logingracetime 120
loglevel INFO
macs hmac-sha1,hmac-sha1-96,hmac-sha2-256,hmac-sha2-512,hmac-md5,hmac-md5-96,hmac-ripemd160,hmac-ripemd160@openssh.com,umac-64@openssh.com,umac-128@openssh.com,hmac-sha1-etm@openssh.com,hmac-sha1-96-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-md5-etm@openssh.com,hmac-md5-96-etm@openssh.com,hmac-ripemd160-etm@openssh.com,umac-64-etm@openssh.com,umac-128-etm@openssh.com
maxauthtries 6
maxsessions 10
maxstartups 10:30:100
passwordauthentication yes
permitemptypasswords no
permitopen any
permitrootlogin without-password
:

---

### Post by Lars Noodén on 2015-10-01
Thanks.  Those look ok.  Which version(s) of x2go are you running?

---

### Post by pcjunki on 2015-10-01
4.0.2.0

---

### Post by Lars Noodén on 2015-10-01
It looks like version [4.0.2.0 is too old](http://bugs.x2go.org/cgi-bin/bugreport.cgi?bug=472) to work with the safe Key EXchange algorithms.  Can you get a more recent version of the X2go client?

---

### Post by pcjunki on 2015-10-01
installed latest client
now on the client, it's asking for a passphrase to decrypt a key

---

### Post by pcjunki on 2015-10-02
I got it to work, I didn't have the x2go server installed, I thought it just worked via ssh
anyway...I'm able to view my desktop, and apps via a remote location

---

