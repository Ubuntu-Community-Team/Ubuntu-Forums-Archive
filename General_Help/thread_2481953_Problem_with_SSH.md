---
title: "Problem with SSH"
date: 2022-12-14
forum: General Help
---

### Post by bill-lancaster on 2022-12-14
Can no longer copy files from wifi device.
This command in Terminal produces an error.
```
sshpass -p 'xxxx' scp root@192.168.1.138:/mnt/sda1/meter_E.txt /home/bill/Downloads/yundata.txt
```

The error is:-
```
sshpass -p 'alex23' scp root@192.168.1.138:/mnt/sda1/meter_E.txt /home/bill/Downloads/yundata.txt
```

The device is an Arduino Yun

I've spent hours on thos problem so any help would be appreciated.

---

### Post by TheFu on 2022-12-14
Did you try increasing the verbosity and simplifying the command?  All ssh tools support adding -vvv to show more details.

---

### Post by bill-lancaster on 2022-12-14
Thanks for the prompt response.
No but I have now and get the same result.
Also tried a simpler command:-
```
ssh root@192.168.1.138
```
and get the same error.
I read somewhere that the Arduino Yun device has 'heritage ssh', does that mean anything?

---

### Post by HermanAB on 2022-12-14
Well SSH won’t work if your network isn’t.  So first check your net with pings, then try ssh locally on the server with vvv.

---

### Post by bill-lancaster on 2022-12-14
ping 192.168.1.138 works fine.

"then try ssh locally on the server with vvv", if by 'server' you my PC then I don't know how to do that.

BTW I tried PUTTY and could access the Yun device but couldn't get much further.

---

### Post by bill-lancaster on 2022-12-15
The Arduino Yun device is on my local network (wi fi) so I guess I'm running SSH locally anyway.

Here is the result of using the verbose option:-
```
:~$ ssh -vvv LongMeadow@192.168.1.138
OpenSSH_8.9p1 Ubuntu-3, OpenSSL 3.0.2 15 Mar 2022
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: include /etc/ssh/ssh_config.d/*.conf matched no files
debug1: /etc/ssh/ssh_config line 21: Applying options for *
debug3: kex names ok: [diffie-hellman-group1-sha1]
debug2: resolve_canonicalize: hostname 192.168.1.138 is address
debug3: expanded UserKnownHostsFile '~/.ssh/known_hosts' -> '/home/bill/.ssh/known_hosts'
debug3: expanded UserKnownHostsFile '~/.ssh/known_hosts2' -> '/home/bill/.ssh/known_hosts2'
debug3: ssh_connect_direct: entering
debug1: Connecting to 192.168.1.138 [192.168.1.138] port 22.
debug3: set_sock_tos: set socket 3 IP_TOS 0x10
debug1: Connection established.
debug1: identity file /home/bill/.ssh/id_rsa type 0
debug1: identity file /home/bill/.ssh/id_rsa-cert type -1
debug1: identity file /home/bill/.ssh/id_ecdsa type -1
debug1: identity file /home/bill/.ssh/id_ecdsa-cert type -1
debug1: identity file /home/bill/.ssh/id_ecdsa_sk type -1
debug1: identity file /home/bill/.ssh/id_ecdsa_sk-cert type -1
debug1: identity file /home/bill/.ssh/id_ed25519 type -1
debug1: identity file /home/bill/.ssh/id_ed25519-cert type -1
debug1: identity file /home/bill/.ssh/id_ed25519_sk type -1
debug1: identity file /home/bill/.ssh/id_ed25519_sk-cert type -1
debug1: identity file /home/bill/.ssh/id_xmss type -1
debug1: identity file /home/bill/.ssh/id_xmss-cert type -1
debug1: identity file /home/bill/.ssh/id_dsa type -1
debug1: identity file /home/bill/.ssh/id_dsa-cert type -1
debug1: Local version string SSH-2.0-OpenSSH_8.9p1 Ubuntu-3
debug1: Remote protocol version 2.0, remote software version dropbear_2012.55
debug1: compat_banner: no match: dropbear_2012.55
debug2: fd 3 setting O_NONBLOCK
debug1: Authenticating to 192.168.1.138:22 as 'LongMeadow'
debug3: record_hostkey: found key type RSA in file /home/bill/.ssh/known_hosts:1
debug3: load_hostkeys_file: loaded 1 keys from 192.168.1.138
debug1: load_hostkeys: fopen /home/bill/.ssh/known_hosts2: No such file or directory
debug1: load_hostkeys: fopen /etc/ssh/ssh_known_hosts: No such file or directory
debug1: load_hostkeys: fopen /etc/ssh/ssh_known_hosts2: No such file or directory
debug3: order_hostkeyalgs: prefer hostkeyalgs: rsa-sha2-512-cert-v01@openssh.com,rsa-sha2-256-cert-v01@openssh.com,rsa-sha2-512,rsa-sha2-256
debug3: send packet: type 20
debug1: SSH2_MSG_KEXINIT sent
debug3: receive packet: type 20
debug1: SSH2_MSG_KEXINIT received
debug2: local client KEXINIT proposal
debug2: KEX algorithms: curve25519-sha256,curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,sntrup761x25519-sha512@openssh.com,diffie-hellman-group-exchange-sha256,diffie-hellman-group16-sha512,diffie-hellman-group18-sha512,diffie-hellman-group14-sha256,diffie-hellman-group1-sha1,ext-info-c
debug2: host key algorithms: rsa-sha2-512-cert-v01@openssh.com,rsa-sha2-256-cert-v01@openssh.com,rsa-sha2-512,rsa-sha2-256,ssh-ed25519-cert-v01@openssh.com,ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com,sk-ssh-ed25519-cert-v01@openssh.com,sk-ecdsa-sha2-nistp256-cert-v01@openssh.com,ssh-ed25519,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521,sk-ssh-ed25519@openssh.com,sk-ecdsa-sha2-nistp256@openssh.com
debug2: ciphers ctos: chacha20-poly1305@openssh.com,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com,aes128-cbc
debug2: ciphers stoc: chacha20-poly1305@openssh.com,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com,aes128-cbc
debug2: MACs ctos: umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-sha1
debug2: MACs stoc: umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-sha1
debug2: compression ctos: none,zlib@openssh.com,zlib
debug2: compression stoc: none,zlib@openssh.com,zlib
debug2: languages ctos: 
debug2: languages stoc: 
debug2: first_kex_follows 0 
debug2: reserved 0 
debug2: peer server KEXINIT proposal
debug2: KEX algorithms: diffie-hellman-group1-sha1,diffie-hellman-group14-sha1
debug2: host key algorithms: ssh-rsa,ssh-dss
debug2: ciphers ctos: aes128-ctr,3des-ctr,aes256-ctr,aes128-cbc,3des-cbc,aes256-cbc
debug2: ciphers stoc: aes128-ctr,3des-ctr,aes256-ctr,aes128-cbc,3des-cbc,aes256-cbc
debug2: MACs ctos: hmac-sha1,hmac-md5
debug2: MACs stoc: hmac-sha1,hmac-md5
debug2: compression ctos: none
debug2: compression stoc: none
debug2: languages ctos: 
debug2: languages stoc: 
debug2: first_kex_follows 0 
debug2: reserved 0 
debug1: kex: algorithm: diffie-hellman-group1-sha1
debug1: kex: host key algorithm: (no match)
Unable to negotiate with 192.168.1.138 port 22: no matching host key type found. Their offer: ssh-rsa,ssh-dss
b
```

It looks like there's a lot wrong!

---

### Post by bill-lancaster on 2022-12-15
I have read that because the Arduino device has 'heritage' ssh the use of "-oHostKeyAlgorithms=+ssh-dss" may help.

Here is the result:-

```
:~$ ssh -oHostKeyAlgorithms=+ssh-dss root@192.168.1.138
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that a host key has just been changed.
The fingerprint for the DSA key sent by the remote host is
SHA256:anvks1b5n9P7yZoXdg1GH9Y8wSZGzCouEoIylkdN3Hw.
Please contact your system administrator.
Add correct host key in /home/bill/.ssh/known_hosts to get rid of this message.
Offending RSA key in /home/bill/.ssh/known_hosts:1
  remove with:
  ssh-keygen -f "/home/bill/.ssh/known_hosts" -R "192.168.1.138"
Host key for 192.168.1.138 has changed and you have requested strict checking.
Host key verification failed.
bill@bill-Vostro-3470:~$ ssh -oHostKeyAlgorithms=+ssh-dss root@192.168.1.138
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that a host key has just been changed.
The fingerprint for the DSA key sent by the remote host is
SHA256:anvks1b5n9P7yZoXdg1GH9Y8wSZGzCouEoIylkdN3Hw.
Please contact your system administrator.
Add correct host key in /home/bill/.ssh/known_hosts to get rid of this message.
Offending RSA key in /home/bill/.ssh/known_hosts:1
  remove with:
  ssh-keygen -f "/home/bill/.ssh/known_hosts" -R "192.168.1.138"
Host key for 192.168.1.138 has changed and you have requested strict checking.
Host key verification failed.
```

Is the correct key SHA256:anvks1b5n9P7yZoXdg1GH9Y8wSZGzCouEoIylkdN3Hw ?

Tried adding it to /home/bill/.ssh/known_hosts  but it still fails

---

### Post by btindie on 2022-12-15
It's because your device is using legacy hostkeys which have been disabled by the default SSH install on your client.

Additionally, you've already got the RSA hostkey stored in your known_hosts file which is why it's displaying that last message.

You can see the hostkeys your client supports in the output
```
debug3: order_hostkeyalgs: prefer hostkeyalgs: rsa-sha2-512-cert-v01@openssh.com,rsa-sha2-256-cert-v01@openssh.com,rsa-sha2-512,rsa-sha2-256
```

But you weren't far off with [COLOR=#000000][FONT=&amp]-oHostKeyAlgorithms=+ssh-dss[/FONT][/COLOR] if you change that to [COLOR=#000000][FONT=&amp]-oHostKeyAlgorithms=+ssh-rsa[/FONT][/COLOR] it should then work.

To save yourself some typing in future, when you find out what works, you can add an entry to your ~/.ssh/config file for that, e.g.
```

Host arduino
  User root
  Hostname 192.168.1.138
  HostKeyAlgorithms +ssh-rsa

```
you can then just type "ssh arduino" to connect.

Also try using SSH Public/Private keys if your device supports them, it'll save messing around with a password.

---

### Post by bill-lancaster on 2022-12-15
Thank you so much btindie
ssh -oHostKeyAlgorithms=+ssh-rsa root@192.168.1.138 takes me straight into ssh panel.

Now I need to copy /mnt/sda1/meter_E.txt to my pc

:~$: ssh -oHostKeyAlgorithms=+ssh-rsa [email]root@192.168.1.138:/mnt/sda1/meter_E.txt[/email] /home/bill/Downloads/yundata.txt

gives error:-

ssh: Could not resolve hostname 192.168.1.138:/mnt/sda1/meter_E.txt: Name or service not known

Until recently this was working fine:-

sshpass -p 'alex2304' scp [email]root@192.168.1.138:/mnt/sda1/meter_E.txt[/email] /home/bill/Downloads/yundata.txt

it had been run every 20 minutes for many months!.

---

### Post by TheFu on 2022-12-15
Is /mnt/sda1 mounted on the remote device?  That's an odd name and place for storage that isn't temporary.
BTW, using remote root is a bad idea too. Ubuntu disables that. Could the other OS do the same for security reasons?

Is there a reason you don't use ssh-keys rather than sshpass?  Don't care about security?  If that's the situation, maybe running a tiny 1-line web server would be sufficient instead?  Then you can pull the file using curl or wget without any authentication.

---

### Post by bill-lancaster on 2022-12-15
Thanks, yes, /mnt/sda1 is a micro sd card on the remote device, it's part of a Linux system on the Yun.

I'll have a look at  ssh-keys.

---

### Post by btindie on 2022-12-16
You're using [FONT=system]ssh[/FONT] and not [FONT=system]scp[/FONT]
```

:~$: ssh -oHostKeyAlgorithms=+ssh-rsa root@192.168.1.138:/mnt/sda1/meter_E.txt /home/bill/Downloads/yundata.txt

```
which is why it doesn't work.

if you're logged in as user 'bill', you can simply us ~/Downloads/yundata.txt for the destination path.

Combined with the .ssh/config entry I provided above that would become
```

$ scp arduino:/mnt/sda1/meter_E.txt ~/Downloads/yundata.txt

```

---

### Post by ActionParsnip on 2022-12-16
> **btindie said:**
> You're using [FONT=system]ssh[/FONT] and not [FONT=system]scp[/FONT]
```

:~$: ssh -oHostKeyAlgorithms=+ssh-rsa root@192.168.1.138:/mnt/sda1/meter_E.txt /home/bill/Downloads/yundata.txt

```
which is why it doesn't work.

if you're logged in as user 'bill', you can simply us ~/Downloads/yundata.txt for the destination path.

Combined with the .ssh/config entry I provided above that would become
```

$ scp arduino:/mnt/sda1/meter_E.txt ~/Downloads/yundata.txt

```

Yeah I was confused by the ssh instead of scp bit...... very strange

---

### Post by bill-lancaster on 2022-12-16
Thank you btindie

```
scp arduino:/mnt/sda1/meter_E.txt ~/Downloads/yundata.txt
```
Produces this error #:-
```
sh: Could not resolve hostname root: Temporary failure in name resolution
```

```
scp 191.168.1.138:/mnt/sda1/meter_E.txt ~/Downloads/yundata.txt
```

No messages and just a new blank line in terminal

---

### Post by TheFu on 2022-12-16
> **bill-lancaster said:**
> Thank you btindie

```
scp arduino:/mnt/sda1/meter_E.txt ~/Downloads/yundata.txt
```
Produces this error #:-
```
sh: Could not resolve hostname root: Temporary failure in name resolution
```

```
scp 191.168.1.138:/mnt/sda1/meter_E.txt ~/Downloads/yundata.txt
```

No messages and just a new blank line in terminal

If you don't setup the ~/.ssh/config file as shown above, then using the name won't work.
The last scp command probably worked. Check that the file is there.  The Unix philosophy is not to say anything when stuff works and to complain loudly when it doesn't.

---

### Post by bill-lancaster on 2022-12-16
No file was created but have now created the config file as suggested and after a prompt srduino password the file was transferred.
:~$ scp arduino:/mnt/sda1/meter_E.txt ~/Downloads/yundata.txt
Hooray & thanks.
Now, is there a way to avoid having to enter the password?

---

### Post by bill-lancaster on 2022-12-16
OK, just added shpass -p "password"  ans that's it.
Thanks for all the help

---

### Post by TheFu on 2022-12-16
> **bill-lancaster said:**
> No file was created but have now created the config file as suggested and after a prompt srduino password the file was transferred.
:~$ scp arduino:/mnt/sda1/meter_E.txt ~/Downloads/yundata.txt
Hooray & thanks.
Now, is there a way to avoid having to enter the password?

Yes, use ssh-keys.  I can give the commands I use, but since I use eliptical keys, they won't work with yoru setup.  OTOH, the manpages for the commands will say how to use different style keys, so you can look that up.
   
Step 1:  Run on the client as the normal user:
```
   $ ssh-keygen -t ed25519
```

Step 2:  Run from the client to the server:
```
   $ ssh-copy-id -i ~/.ssh/id_ed25519.pub username@remote
```

The "username" is optional and not needed if the same between the client machine and remote server. This can be in the ~/.ssh/config file if you don't want to enter it.

 "remote" can be a DNS name, IP address, some manually setup lookup  inside the /etc/hosts or configured in the ~/.ssh/config file.

So, basically 10 seconds of your time.  If you enter a password for the ssh-key, it will need to be unlocked once per login on the client system, assuming ssh-agent is configured and running. Generally, this is already there. The public key can be pushed to more than 1 system. I tend to have a different key for different customers, but use the same one within the same LAN.

All this stuff is in the manpages and has been posted about in these forums multiple times. You just need to look.

---

