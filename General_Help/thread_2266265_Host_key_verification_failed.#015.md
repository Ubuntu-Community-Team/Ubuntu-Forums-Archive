---
title: "Host key verification failed.#015"
date: 2015-02-21
forum: General Help
---

### Post by ylafont on 2015-02-21
[COLOR=#333333][FONT=Helvetica Neue]I am trying to execute a script on a remote computer. Lets call this (Secondary), the script is as follows, for simplicity porposes,
#!/bin/bash

```
echo "This is the Remote Machine (Secondary)" > /tmp/test.txt
echo "---------------------------------------------------" >> /tmp/test.txt
echo "Test.sh scandir = $scandir" >> /tmp/test.txt
echo "Test.sh tmpdir = $tmpdir" >> /tmp/test.txt
echo "Test.sh CurrentDir = $CurrentDir" >> /tmp/test.txt
echo "---------------------------------------------------" >> /tmp/test.txt
```[/FONT][/COLOR][COLOR=#333333][FONT=Helvetica Neue]


I can execute the remotely from the primary machine with the following command.

```
ssh <username>@192.168.1.20 'screen -S TestProcess -d -m ./test.sh'
```

and the script runs as expected.

However when the script with the same command is executed automatically from a system process i get the following error.

**Feb 21 06:20:23 Primary test.sh: Host key verification failed.#015**

I have generated ssh keys and copied them.

```
ssh-keygen -R 192.168.1.20
ssh-copy-id <username>@192.168.1.20
```

What can be the cause of the  problem?
[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica Neue][ssh]("http://unix.stackexchange.com/questions/tagged/ssh") [verification]("http://unix.stackexchange.com/questions/tagged/verification")[/FONT][/COLOR]

---

### Post by Lars Noodén on 2015-02-21
When you are executing the script as a system process are you doing so as the same user or a different one?  I'm guessing the latter, in which case you need to have the correct public key from the remote host stored in that user's ~/.ssh/known_hosts  

How are you trying to launch the script as a system process?

---

### Post by ylafont on 2015-02-21
I have installed Scanbd and SANE, which is launched on start-up and monitors the scanner. This process owner is the user "saned"

```
saned     2163  0.6  0.5  29428  2464 ?        Sl   Feb20   8:23 /usr/local/sbin/scanbd -c /usr/local/etc/scanbd/scanbd.conf
```

Each each time a scanner action occurs, it runs scan.sh - which in turn executes 

```
[COLOR=#333333][FONT=Ubuntu Mono]ssh <username>@192.168.1.20 'screen -S TestProcess -d -m ./test.sh' with[/FONT][/COLOR]
```[COLOR=#333333][FONT=Ubuntu Mono]

The user I have tested the script on the primary machines is called "scanner". There is no home directory for this users, but that is easily solved.
The user on the secondary machine is called "ylafont"   

The users are already different and the script executes fine. I am under the impression that the keys are needed for the user one is using to login with SSH. 

I do not believe i am trying to run the script as a system process.[/FONT][/COLOR]

---

### Post by Lars Noodén on 2015-02-21
```
ssh -i /some/path/to/a/key_rsa <username>@192.168.1.20 'screen -S TestProcess -d -m ./test.sh' with
```

What happens when you use -i in your script to explicitly identify the private key to be used in authentication?

---

### Post by ylafont on 2015-02-21
Mounted the remote  drive and modified command as follows.


```
ssh  -i /mnt/CleanVM/home/ylafont/.ssh/authorized_keys  ylafont@192.168.1.20 'screen -S ScanProcess -d -m ./test.sh'

```


same results 

```
Feb 21 17:55:13 PiScanner scan.sh: Scanning page 2
Feb 21 17:55:13 PiScanner scan.sh: Scanned page 2. (scanner status = 5)
Feb 21 17:55:13 PiScanner scan.sh: Scanning page 3
Feb 21 17:55:13 PiScanner scan.sh: scanimage: sane_start: Document feeder out of documents
Feb 21 17:55:13 PiScanner scanbd: /usr/local/etc/scanbd/scan.sh: ************* Scanning ended on device fujitsu:fi-4220C2dj:100742 ***************
Feb 21 17:55:14 PiScanner scanbd: /usr/local/sbin/scanbd: Iteration on dbus call
**Feb 21 17:55:14 PiScanner scan.sh: Host key verification failed.#015**
Feb 21 17:55:14 PiScanner scanbd: /usr/local/etc/scanbd/scan.sh: This this End  ***********  of paperload for device fujitsu:fi-4220C2dj:100742
Feb 21 17:55:14 PiScanner scanbd: /usr/local/sbin/scanbd: child /usr/local/etc/scanbd/scan.sh exited with status: 0
Feb 21 17:55:15 PiScanner scanbd: /usr/local/sbin/scanbd: Iteration on dbus call
Feb 21 17:55:15 PiScanner scanbd: /usr/local/sbin/scanbd: append string fujitsu:fi-4220C2dj:100742 to signal scan_end

```

---

### Post by Lars Noodén on 2015-02-21
-i should point at the private key of the key pair you generated on the client, instead of the file [authorized_keys](http://manpages.ubuntu.com/manpages/trusty/en/man1/ssh.1.html).  Over there on the server, however, the file authorized_keys should contain the public key from the key pair you generated on the client, but if you used ssh-copy-id that should be set.  I think it is only a matter of finding your private key.  Normally they are kept in ~/.ssh/

---

### Post by ylafont on 2015-02-21
I had also used

```
ssh  -i /mnt/CleanVM/home/ylafont/.ssh  ylafont@192.168.1.20 'screen -S ScanProcess -d -m ./test.sh'
```
i used 

```
ssh-keygen -R 192.168.1.20
ssh-copy-id <username>@192.168.1.20
```

which should have copied the keys and did. 

Prior to generating the keys,  i had to manually enter the ssh password.   

let see if re-doing everything helps.

---

### Post by Lars Noodén on 2015-02-21
You're missing the key name for the -i option when you try to connect.  How did you generate the key pair?  You can give it a name with the -f option:

```

cd ~/.ssh/
ssh-keygen -t rsa -b 4096 -C "For 192.168.1.20" -f id_20_rsa
ssh-copy-id -i id_20_rsa user2@192.168.1.20
cd
ssh -i ~/.ssh/id_20_rsa user2@192.168.1.20 'screen -S TestProcess -d -m ./test.sh'

```

Or if you don't it wil default to id_rsa or something like that.

---

### Post by ylafont on 2015-02-21
Somethings is up. This requires further investigation

```
pi@PiScanner ~/.ssh $ ssh-keygen -t rsa -b 4096 -C "For 192.168.1.20" -f id_20_rs           a
Generating public/private rsa key pair.
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in id_20_rsa.
Your public key has been saved in id_20_rsa.pub.
The key fingerprint is:
8b:1a:b7:93:99:a4:e5:8e:3c:93:42:0d:cb:de:0a:4a For 192.168.1.20
The key's randomart image is:
+--[ RSA 4096]----+
|                 |
|                 |
|                 |
|  .              |
| . +    S        |
|  + . o. .       |
|.E ..*o+.        |
|o.o.*=*.         |
|. .o++o.         |
+-----------------+
pi@PiScanner ~/.ssh $ ssh-copy-id -i id_20_rsa user2@192.168.1.20
Host key verification failed.
```


```
pi@PiScanner ~/.ssh $ ssh -v ylafont@192.168.1.20OpenSSH_6.0p1 Debian-4+deb7u2, OpenSSL 1.0.1e 11 Feb 2013
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug1: Connecting to 192.168.1.20 [192.168.1.20] port 22.
debug1: Connection established.
debug1: identity file /home/pi/.ssh/id_rsa type -1
debug1: identity file /home/pi/.ssh/id_rsa-cert type -1
debug1: identity file /home/pi/.ssh/id_dsa type -1
debug1: identity file /home/pi/.ssh/id_dsa-cert type -1
debug1: identity file /home/pi/.ssh/id_ecdsa type -1
debug1: identity file /home/pi/.ssh/id_ecdsa-cert type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_6.6.1p1 Ubuntu-2ubuntu2
debug1: match: OpenSSH_6.6.1p1 Ubuntu-2ubuntu2 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_6.0p1 Debian-4+deb7u2
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-ctr hmac-md5 none
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: sending SSH2_MSG_KEX_ECDH_INIT
debug1: expecting SSH2_MSG_KEX_ECDH_REPLY
debug1: Server host key: ECDSA 86:4c:40:4f:5b:19:64:45:6d:6d:a8:b3:61:1d:bd:df
Host key verification failed.

```

---

### Post by ylafont on 2015-02-22
ok -  there mus have been something corrupted - I am now back to a point where i can see something that will point me in the right direction.  

Again everything is working from the command line. but i can't seem to get permission via script.   I am know able to see the ssh log.

Feb 22 20:27:55 PiScanner scanbd: /usr/local/etc/scanbd/scan.sh:  -------------------------    Starting ssh connection  -------------------------
Feb 22 20:27:55 PiScanner scan.sh: OpenSSH_6.0p1 Debian-4+deb7u2, OpenSSL 1.0.1e 11 Feb 2013
Feb 22 20:27:55 PiScanner scan.sh: Warning: Identity file /home/ylafont/.ssh/id_rsa.pub not accessible: No such file or directory.
Feb 22 20:27:55 PiScanner scan.sh: debug1: Reading configuration data /etc/ssh/ssh_config#015
Feb 22 20:27:55 PiScanner scan.sh: debug1: /etc/ssh/ssh_config line 19: Applying options for *#015
Feb 22 20:27:55 PiScanner scan.sh: debug2: ssh_connect: needpriv 0#015
Feb 22 20:27:55 PiScanner scan.sh: debug1: Connecting to 192.168.1.20 [192.168.1.20] port 22.#015
Feb 22 20:27:55 PiScanner scan.sh: debug1: Connection established.#015
Feb 22 20:27:55 PiScanner scan.sh: debug1: permanently_set_uid: 0/0#015
Feb 22 20:27:55 PiScanner scan.sh: debug1: identity file /root/.ssh/id_rsa type 1#015
Feb 22 20:27:55 PiScanner scan.sh: debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048#015
Feb 22 20:27:55 PiScanner scan.sh: debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048#015
Feb 22 20:27:55 PiScanner scan.sh: debug1: identity file /root/.ssh/id_rsa-cert type -1#015
Feb 22 20:27:55 PiScanner scan.sh: debug1: identity file /root/.ssh/id_dsa type -1#015
Feb 22 20:27:55 PiScanner scan.sh: debug1: identity file /root/.ssh/id_dsa-cert type -1#015
Feb 22 20:27:55 PiScanner scan.sh: debug1: identity file /root/.ssh/id_ecdsa type -1#015
Feb 22 20:27:55 PiScanner scan.sh: debug1: identity file /root/.ssh/id_ecdsa-cert type -1#015
Feb 22 20:27:55 PiScanner scan.sh: debug1: Remote protocol version 2.0, remote software version OpenSSH_6.6.1p1 Ubuntu-2ubuntu2#015
Feb 22 20:27:55 PiScanner scan.sh: debug1: match: OpenSSH_6.6.1p1 Ubuntu-2ubuntu2 pat OpenSSH*#015
Feb 22 20:27:55 PiScanner scan.sh: debug1: Enabling compatibility mode for protocol 2.0#015
Feb 22 20:27:55 PiScanner scan.sh: debug1: Local version string SSH-2.0-OpenSSH_6.0p1 Debian-4+deb7u2#015
Feb 22 20:27:55 PiScanner scan.sh: debug2: fd 3 setting O_NONBLOCK#015
Feb 22 20:27:55 PiScanner scan.sh: debug1: SSH2_MSG_KEXINIT sent#015
Feb 22 20:27:55 PiScanner scan.sh: debug1: SSH2_MSG_KEXINIT received#015
Feb 22 20:27:55 PiScanner scan.sh: debug2: kex_parse_kexinit: ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1#015
Feb 22 20:27:55 PiScanner scan.sh: debug2: kex_parse_kexinit: [email]ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521,ssh-rsa-cert-v01@openssh.com,ssh-dss-cert-v01@openssh.com,ssh-rsa-cert-v00@openssh.com,ssh-dss-cert-v00@openssh.com[/email],ssh-rsa,ssh-dss#015
Feb 22 20:27:55 PiScanner scan.sh: debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se#015
Feb 22 20:27:55 PiScanner scan.sh: debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se#015
Feb 22 20:27:55 PiScanner scan.sh: debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-sha2-256,hmac-sha2-256-96,hmac-sha2-512,hmac-sha2-512-96,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96#015
Feb 22 20:27:55 PiScanner scan.sh: debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-sha2-256,hmac-sha2-256-96,hmac-sha2-512,hmac-sha2-512-96,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96#015
Feb 22 20:27:55 PiScanner scan.sh: debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib#015
Feb 22 20:27:55 PiScanner scan.sh: debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib#015
Feb 22 20:27:55 PiScanner scan.sh: debug2: kex_parse_kexinit: #015
Feb 22 20:27:55 PiScanner scan.sh: debug2: kex_parse_kexinit: #015
Feb 22 20:27:55 PiScanner scan.sh: debug2: kex_parse_kexinit: first_kex_follows 0 #015
Feb 22 20:27:55 PiScanner scan.sh: debug2: kex_parse_kexinit: reserved 0 #015
Feb 22 20:27:55 PiScanner scan.sh: debug2: kex_parse_kexinit: [EMAIL="curve25519-sha256@libssh.org"]curve25519-sha256@libssh.org[/EMAIL],ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1#015
Feb 22 20:27:55 PiScanner scan.sh: debug2: kex_parse_kexinit: ssh-rsa,ssh-dss,ecdsa-sha2-nistp256,ssh-ed25519#015
Feb 22 20:27:55 PiScanner scan.sh: debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-gcm@openssh.com,aes256-gcm@openssh.com,chacha20-poly1305@openssh.com,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se#015
Feb 22 20:27:55 PiScanner scan.sh: debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-gcm@openssh.com,aes256-gcm@openssh.com,chacha20-poly1305@openssh.com,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se#015
Feb 22 20:27:55 PiScanner scan.sh: debug2: kex_parse_kexinit: [email]hmac-md5-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-ripemd160-etm@openssh.com,hmac-sha1-96-etm@openssh.com,hmac-md5-96-etm@openssh.com,hmac-md5,hmac-sha1,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-ripemd160,hmac-ripemd160@openssh.com[/email],hmac-sha1-96,hmac-md5-96#015
Feb 22 20:27:55 PiScanner scan.sh: debug2: kex_parse_kexinit: [email]hmac-md5-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-ripemd160-etm@openssh.com,hmac-sha1-96-etm@openssh.com,hmac-md5-96-etm@openssh.com,hmac-md5,hmac-sha1,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-ripemd160,hmac-ripemd160@openssh.com[/email],hmac-sha1-96,hmac-md5-96#015
Feb 22 20:27:55 PiScanner scan.sh: debug2: kex_parse_kexinit: none,zlib@openssh.com#015
Feb 22 20:27:55 PiScanner scan.sh: debug2: kex_parse_kexinit: none,zlib@openssh.com#015
Feb 22 20:27:55 PiScanner scan.sh: debug2: kex_parse_kexinit: #015
Feb 22 20:27:55 PiScanner scan.sh: debug2: kex_parse_kexinit: #015
Feb 22 20:27:55 PiScanner scan.sh: debug2: kex_parse_kexinit: first_kex_follows 0 #015
Feb 22 20:27:55 PiScanner scan.sh: debug2: kex_parse_kexinit: reserved 0 #015
Feb 22 20:27:55 PiScanner scan.sh: debug2: mac_setup: found hmac-md5#015
Feb 22 20:27:55 PiScanner scan.sh: debug1: kex: server->client aes128-ctr hmac-md5 none#015
Feb 22 20:27:55 PiScanner scan.sh: debug2: mac_setup: found hmac-md5#015
Feb 22 20:27:55 PiScanner scan.sh: debug1: kex: client->server aes128-ctr hmac-md5 none#015
Feb 22 20:27:55 PiScanner scan.sh: debug1: sending SSH2_MSG_KEX_ECDH_INIT#015
Feb 22 20:27:55 PiScanner scan.sh: debug1: expecting SSH2_MSG_KEX_ECDH_REPLY#015
Feb 22 20:27:55 PiScanner scan.sh: debug1: Server host key: ECDSA 86:4c:40:4f:5b:19:64:45:6d:6d:a8:b3:61:1d:bd:df#015
Feb 22 20:27:55 PiScanner scan.sh: debug1: Host '192.168.1.20' is known and matches the ECDSA host key.#015
Feb 22 20:27:55 PiScanner scan.sh: debug1: Found key in /root/.ssh/known_hosts:1#015
Feb 22 20:27:55 PiScanner scan.sh: debug1: ssh_ecdsa_verify: signature correct#015
Feb 22 20:27:55 PiScanner scan.sh: debug2: kex_derive_keys#015
Feb 22 20:27:55 PiScanner scan.sh: debug2: set_newkeys: mode 1#015
Feb 22 20:27:55 PiScanner scan.sh: debug1: SSH2_MSG_NEWKEYS sent#015
Feb 22 20:27:55 PiScanner scan.sh: debug1: expecting SSH2_MSG_NEWKEYS#015
Feb 22 20:27:55 PiScanner scan.sh: debug2: set_newkeys: mode 0#015
Feb 22 20:27:55 PiScanner scan.sh: debug1: SSH2_MSG_NEWKEYS received#015
Feb 22 20:27:55 PiScanner scan.sh: debug1: Roaming not allowed by server#015
Feb 22 20:27:55 PiScanner scan.sh: debug1: SSH2_MSG_SERVICE_REQUEST sent#015
Feb 22 20:27:55 PiScanner scan.sh: debug2: service_accept: ssh-userauth#015
Feb 22 20:27:55 PiScanner scan.sh: debug1: SSH2_MSG_SERVICE_ACCEPT received#015
Feb 22 20:27:55 PiScanner scan.sh: debug2: key: /root/.ssh/id_rsa (0xb7542560)#015
Feb 22 20:27:55 PiScanner scan.sh: debug2: key: /root/.ssh/id_dsa ((nil))#015
Feb 22 20:27:55 PiScanner scan.sh: debug2: key: /root/.ssh/id_ecdsa ((nil))#015
Feb 22 20:27:55 PiScanner scan.sh: debug1: Authentications that can continue: publickey,password#015
Feb 22 20:27:55 PiScanner scan.sh: debug1: Next authentication method: publickey#015
Feb 22 20:27:55 PiScanner scan.sh: debug1: Offering RSA public key: /root/.ssh/id_rsa#015
Feb 22 20:27:55 PiScanner scan.sh: debug2: we sent a publickey packet, wait for reply#015
Feb 22 20:27:55 PiScanner scan.sh: debug1: Authentications that can continue: publickey,password#015
Feb 22 20:27:55 PiScanner scan.sh: debug1: Trying private key: /root/.ssh/id_dsa#015
Feb 22 20:27:55 PiScanner scan.sh: debug1: Trying private key: /root/.ssh/id_ecdsa#015
Feb 22 20:27:55 PiScanner scan.sh: debug2: we did not send a packet, disable method#015
Feb 22 20:27:55 PiScanner scan.sh: debug1: Next authentication method: password#015
Feb 22 20:27:55 PiScanner scan.sh: debug1: read_passphrase: can't open /dev/tty: No such device or address#015
Feb 22 20:27:55 PiScanner scan.sh: debug2: we sent a password packet, wait for reply#015
Feb 22 20:27:55 PiScanner scan.sh: debug1: Authentications that can continue: publickey,password#015
Feb 22 20:27:55 PiScanner scan.sh: Permission denied, please try again.#015
Feb 22 20:27:55 PiScanner scan.sh: debug1: read_passphrase: can't open /dev/tty: No such device or address#015
Feb 22 20:27:55 PiScanner scan.sh: debug2: we sent a password packet, wait for reply#015
Feb 22 20:27:55 PiScanner scan.sh: debug1: Authentications that can continue: publickey,password#015
Feb 22 20:27:55 PiScanner scan.sh: Permission denied, please try again.#015
Feb 22 20:27:55 PiScanner scan.sh: debug1: read_passphrase: can't open /dev/tty: No such device or address#015
Feb 22 20:27:55 PiScanner scan.sh: debug2: we sent a password packet, wait for reply#015
Feb 22 20:27:55 PiScanner scan.sh: debug1: Authentications that can continue: publickey,password#015
Feb 22 20:27:55 PiScanner scan.sh: debug2: we did not send a packet, disable method#015
Feb 22 20:27:55 PiScanner scan.sh: debug1: No more authentication methods to try.#015
Feb 22 20:27:55 PiScanner scan.sh: Permission denied (publickey,password).#015
Feb 22 20:27:55 PiScanner scanbd: /usr/local/etc/scanbd/scan.sh:  -------------------------    Ending  ssh connection  -------------------------
Feb 22 20:27:55 PiScanner scanbd: /usr/local/etc/scanbd/scan.sh: This is the End  ***********  of paperload for device fujitsu:fi-4220C2dj:100742 ***********************


Further assistance is greatly appreciated. thank you.

---

### Post by Lars Noodén on 2015-02-23
Well, things are good for the beginning:

```

Feb 22 20:27:55 PiScanner scan.sh: debug1: Server host key: ECDSA 86:4c:40:4f:5b:19:64:45:6d:6d:a8:b3:61:1d:bd:df#01 5
Feb 22 20:27:55 PiScanner scan.sh: debug1: Host '192.168.1.20' is known and matches the ECDSA host key.#015
Feb 22 20:27:55 PiScanner scan.sh: debug1: Found key in **/root/.ssh/**known_hosts:1#015
Feb 22 20:27:55 PiScanner scan.sh: debug1: ssh_ecdsa_verify: signature correct#015

```

That part shows that the initial connection is ok.  However, it also shows that the script is being run as root.

```

Feb 22 20:27:55 PiScanner scan.sh: debug1: Next authentication method: publickey#015
Feb 22 20:27:55 PiScanner scan.sh: debug1: Offering RSA public key: **/root/.ssh/**id_rsa#015
Feb 22 20:27:55 PiScanner scan.sh: debug2: we sent a publickey packet, wait for reply#015
Feb 22 20:27:55 PiScanner scan.sh: debug1: Authentications that can continue: publickey,password#015
Feb 22 20:27:55 PiScanner scan.sh: debug1: Trying private key: **/root/.ssh/**id_dsa#015
Feb 22 20:27:55 PiScanner scan.sh: debug1: Trying private key: **/root/.ssh/**id_ecdsa#015
Feb 22 20:27:55 PiScanner scan.sh: debug2: we did not send a packet, disable method#015
Feb 22 20:27:55 PiScanner scan.sh: debug1: Next authentication method: password#015

```

ssh tries to use the keys found in */root/.ssh/* and none of them work.  So there are several ways out.  One would be to find a way have the script run as a regular user, not as root, particularly for the part(s) involving the ssh client.  Maybe there is a rogue instance of 'sudo' in there?  Another would be to put the right private keys in */root/.ssh*.  A third way would be to put root's public keys on the server in *authorized_keys* for the relevant account, but that is probably the least desirable.  Or a fourth way would be to specify the full path to the keys, using the -i option, on the line in the script using the ssh client, like in #4 above.

---

