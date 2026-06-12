---
title: "SSH Public / Private Key How - To?"
date: 2008-03-10
forum: General Help
---

### Post by dacool25 on 2008-03-10
Hi Everyone!

I'm running server 7.10 and i'm thinking about enabling a key for my SSH.  I'm new to keys and have never worked with them.  If I understand this correct, I generate a key and then download it to my client pc in which i am connecting from ..Right?

If thats correct, Does anyone know of any how-to's or if its simple enough can someone post the commands?

Thanks

P.S. I'd like to do this through ssh, so locking myself out would be a bummer =P Is there a way to generate the key and put it in and everything without sitting in front of the box?

---

### Post by bodhi.zazen on 2008-03-10
This link review ssh keys :

[uwiki]AdvancedOpenSSH[/uwiki]

And some additional security options as well.

---

### Post by kevdog on 2008-03-10
Yes that link is very informative -- however I should not although the command:

ssh-keygen -t rsa

generates rsa keys (Type = rsa), I would recommend at least 2048 or 4096 bit keys over the default 1028 bit keys, unless you are using a smart card or portable device.  2048 will be the future default, but not currently.  In order to do this, you would:

ssh-keygen -t rsa -b 2048  or
ssh-keygent -t rsa -b 4096

This should be reflected in the manual but is not!!

---

### Post by dacool25 on 2008-03-10
Okay, I have read that website but am still very confused.  I have three computers that I usually connect from one PC and two Macs.  Once I generate the key where do I put them on the three computers I'm connecting from?

Thanks

---

### Post by Oldsoldier2003 on 2008-03-10
> **dacool25 said:**
> Okay, I have read that website but am still very confused.  I have three computers that I usually connect from one PC and two Macs.  Once I generate the key where do I put them on the three computers I'm connecting from?

Thanks
if the client machines are ubuntu, you can intsall seahorse and gpg... seahorse will set it up for you.

---

### Post by dacool25 on 2008-03-10
Aren't those gui's?  I'm running server 7.10  

Can I make the key from ubuntu and then find the file and download it onto my windows box and have putty use it to connect?

---

### Post by Oldsoldier2003 on 2008-03-10
> **dacool25 said:**
> Aren't those gui's?  I'm running server 7.10  

Can I make the key from ubuntu and then find the file and download it onto my windows box and have putty use it to connect?

the keys are made on the client end and uploaded to the server. though you could do it the other way its not really "secure" in that YOU would know their passphrases since you would be the one creating them.

---

### Post by dacool25 on 2008-03-10
Okay so,

I'm going to be making them with puttygen.exe.  I create them and then upload them to /home/whatever/.ssh and then edit the ssh config file to accept the keys?

---

### Post by dacool25 on 2008-03-10
I'm so confused :confused:

What is the difference between a public key and a private key and which one do I upload after creaing on my putty generator?

---

### Post by Oldsoldier2003 on 2008-03-10
> **dacool25 said:**
> I'm so confused :confused:

What is the difference between a public key and a private key and which one do I upload after creaing on my putty generator?
a key pair consists of two parts:

1 the public key- which people use to decrypt messages from you and also to encrpyt messages to you

2 the private key- which is your part of the key. never ever give out your private key, thats like hading the world the key to you house, and the deed too...

---

### Post by dacool25 on 2008-03-10
So which one do I upload? And where do I upload it to?

---

### Post by Oldsoldier2003 on 2008-03-10
> **dacool25 said:**
> Okay so,

I'm going to be making them with puttygen.exe.  I create them and then upload them to /home/whatever/.ssh and then edit the ssh config file to accept the keys?
[http://the.earth.li/~sgtatham/putty/0.58/htmldoc/Chapter8.html](http://the.earth.li/~sgtatham/putty/0.58/htmldoc/Chapter8.html) for puttygen
[http://tombuntu.com/index.php/2008/02/20/public-key-authentication-for-ssh-made-easy/](http://tombuntu.com/index.php/2008/02/20/public-key-authentication-for-ssh-made-easy/)  for seahorse

---

### Post by dacool25 on 2008-03-10
=(

Well i've uploaded the key, but now I can still login without it.  What did I do wrong?

---

### Post by dacool25 on 2008-03-10
I followed your PuTTY how to.  It only told me to put the text from the putty key generator into the known_hosts file there is nothing in .ssh but that.  Shouldn't there be a .pub key??

---

### Post by dacool25 on 2008-03-10
Figured it out..

You have to edit /etc/ssh/sshd_config and change the following:

```
#   PasswordAuthentication yes

Change to:
  
PasswordAuthentication no
UsePAM no
```

---

### Post by dacool25 on 2008-03-10
But one more question, how will i be using the key on a mac?

---

### Post by bodhi.zazen on 2008-03-10
> **kevdog said:**
> Yes that link is very informative -- however I should not although the command:

ssh-keygen -t rsa

generates rsa keys (Type = rsa), I would recommend at least 2048 or 4096 bit keys over the default 1028 bit keys, unless you are using a smart card or portable device.  2048 will be the future default, but not currently.  In order to do this, you would:

ssh-keygen -t rsa -b 2048  or
ssh-keygent -t rsa -b 4096

This should be reflected in the manual but is not!!

That is a good point. I updated the wiki page, but FYI you can add to the wiki if you have a launchpad account (Community = Community contributed).

---

### Post by kevdog on 2008-03-10
bodhi

I guess its time that I get a launchpad account!!  Thanks for the suggestion -- These recommendations were made from my discussions with the developers of gpg -- yes I know a different product -- but developers who have a constant eye on the cryptography community and goings-on!

---

### Post by kevdog on 2008-03-10
Ive never used a MAC past my MAC-SE, however I think the ssh client on a MAC should be built in -- at least on the command line.  Im sure they probably have a GUI frontend but I dont know what it is. 

Again if you plan to use putty, since the format of the key is different, generate the key using putty-keygen and then place the public key in (or copy it into this file -- which you might need to create if it doesn't exist) ~/.ssh/authorized_keys (on the server).  The private putty key will be in ~/.ssh/<key_name>  which will most likely be id.rsa

Summary

Client
~/.ssh/id_rsa  <---Private Key

Server
~/.ssh/authorized_keys (If file doesnt exits, create it by typing touch authorized_keys).  Inside the authorized_keys file, cut and paste the contents of the id_rsa.pub file -- it should be one line -- no Line Feeds or Carriage Returns, that screws things up!!)

---

### Post by dacool25 on 2008-03-10
Well everything works great with putty on windows, but on a mac it doesn't work at all.  I get a "Permission denied (publickey) error.

The command i am typing is sudo ssh myserver.com -i pathtoprivatekey

---

### Post by bodhi.zazen on 2008-03-10
My guess is that the putty key is NOT the same as an openssh key.

My advice is for you to make a new key and then import it to putty (I do not know how to export a key fro putty)

[http://linux-sxs.org/networking/openssh.putty.html](http://linux-sxs.org/networking/openssh.putty.html)

OR install putty on your MAC.

[http://putty.darwinports.com/](http://putty.darwinports.com/)

---

### Post by dacool25 on 2008-03-10
Hmm when i made the key in the Putty Gen i made a private key too (Not the .ppk one).  How do you make a key on a mac?

---

### Post by bodhi.zazen on 2008-03-10
I understand. The putty-gen key is not the same as an open-ssh key, they are not compatible (although you can import an open-ssh key and convert it to a putty key).

To make an open-ssh key on your MAC :


ssh-keygen -t rsa -b 2048

or

ssh-keygent -t rsa -b 4096

---

### Post by kevdog on 2008-03-10
I think bodhi hit it right on the head -- a conflict between the OpenSSH and putty keys.  Since MAC runs BSD down below which natively runs OpenSSH (not the portable variant as found on linux, cygwin, or others), I dont think that there should be a conflict with the OpenSSH keys between a linux and bsd or MAC system.  In fact you dont even need putty to do this.  Only when windows is involved do you need putty, or you need to run cygwin.  The beauty of putty compared to cygwin is that it makes a great portable app and can be run off a USB driver -- cygwin can be (kind of) but it is really a big pain to set this up and it takes up over 1GB in space).  putty is just a few Kb -- a great and well written app (along with WinSCP), but it does have its limitations that you must know about.

---

### Post by dacool25 on 2008-03-11
I completely agree, it should work but for some reason it isn't.  I'm going to try making the key on the Mac and the putting it onto the server and see if that works.  But before I do that is there any special name or file extension that it needs?

Thanks

---

### Post by bodhi.zazen on 2008-03-11
Nope, you can name it what you will.

See this link :

[http://alblue.blogspot.com/2005/08/howto-ssh-logins-using-keys.html](http://alblue.blogspot.com/2005/08/howto-ssh-logins-using-keys.html)

specifically scroll down to the multiple keys section ...

---

### Post by dacool25 on 2008-03-11
=( For some reason it still isn't working.  Here is exactly what i did:

ssh-keygen -t rsa -b 4096

It prompted me for all of that good stuff, filed it in and it seemed to have worked.

I then enabled hidden files on a mac so that i could see the id_rsa.pub so that I can go on a windows box to paste it onto the server under authorized_keys.

Then I just restarted the ssh service

After all that I tried it out and still get:

Permission denied (publickey).



P.S. And just to make sure I did a chmod 644 for the authorized_keys file

---

### Post by dacool25 on 2008-03-11
I think that it might be the config file.  Can someone post a default config file that will work with key authentication?

Thanks

---

### Post by dacool25 on 2008-03-11
Well I think I am making progress, But for some reason now the error that I am getting is ```
Permission denied (publickey,keyboard-interactive).

```

Can anyone help?  I made the key from the Mac and put it onto the ubuntu server but still no luck =(

---

### Post by dacool25 on 2008-03-11
This is a print out of ssh hostname -v

```
debug1: Host 'hostname' is known and matches the RSA host key.
debug1: Found key in /Users/myusername/.ssh/known_hosts:2
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,keyboard-interactive
debug1: Next authentication method: publickey
debug1: Trying private key: /Users/myusername/.ssh/identity
debug1: Offering public key: /Users/myusername/.ssh/id_rsa
debug1: Authentications that can continue: publickey,keyboard-interactive
debug1: Trying private key: /Users/myusername/.ssh/id_dsa
debug1: Next authentication method: keyboard-interactive
debug1: Authentications that can continue: publickey,keyboard-interactive
debug1: No more authentication methods to try.
Permission denied (publickey,keyboard-interactive).

```

Can anyone help??

---

### Post by bodhi.zazen on 2008-03-11
There are a number of potential variables, so lets try to isolate them.

First, use the key you made on your MAC and import that to putty.

Then, on the server, you need the public MAC key. Delete the others for now.

Then re-enable password log-ins.

Then connect, from the windows box with Putty.

Then the MAC. When you connect from the MAC use -vv for verbose.

[indent]ssh -vv use@ip [/indent]

Post the MAC terminal output (assuming putty works from Windows).

---

### Post by dacool25 on 2008-03-11
Alright, It works on PuTTY.  Here is the output of it with passwords re-enabled:

```
ssh myserver.com -l administrator -vv
OpenSSH_4.5p1, OpenSSL 0.9.7l 28 Sep 2006
debug1: Reading configuration data /etc/ssh_config
debug2: ssh_connect: needpriv 0
debug1: Connecting to myserver.com [xxx.xxx.xxx.xxx] port 22.
debug1: Connection established.
debug1: identity file /Users/myusername/.ssh/identity type -1
debug2: key_type_from_name: unknown key type '-----BEGIN'
debug2: key_type_from_name: unknown key type 'Proc-Type:'
debug2: key_type_from_name: unknown key type 'DEK-Info:'
debug2: key_type_from_name: unknown key type '-----END'
debug1: identity file /Users/myusername/.ssh/id_rsa type 1
debug1: identity file /Users/myusername/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.6p1 Debian-5ubuntu0.1
debug1: match: OpenSSH_4.6p1 Debian-5ubuntu0.1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.5
debug2: fd 3 setting O_NONBLOCK
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: mac_init: found hmac-md5
debug1: kex: server->client aes128-cbc hmac-md5 none
debug2: mac_init: found hmac-md5
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug2: dh_gen_key: priv key bits set: 135/256
debug2: bits set: 507/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'myserver.com' is known and matches the RSA host key.
debug1: Found key in /Users/myusername/.ssh/known_hosts:2
debug2: bits set: 492/1024
debug1: ssh_rsa_verify: signature correct
debug2: kex_derive_keys
debug2: set_newkeys: mode 1
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug2: set_newkeys: mode 0
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug2: key: /Users/myusername/.ssh/identity (0x0)
debug2: key: /Users/myusername/.ssh/id_rsa (0x1019d0)
debug2: key: /Users/myusername/.ssh/id_dsa (0x0)
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /Users/myusername/.ssh/identity
debug1: Offering public key: /Users/myusername/.ssh/id_rsa
debug2: we sent a publickey packet, wait for reply
debug1: Server accepts key: pkalg ssh-rsa blen 277
debug2: input_userauth_pk_ok: fp eb:7f:e3:22:97:ec:2e:81:3e:c5:bc:03:dd:03:83:3c
debug1: PEM_read_PrivateKey failed
debug1: read PEM private key done: type <unknown>
debug1: read PEM private key done: type RSA
debug1: Authentication succeeded (publickey).
debug1: channel 0: new [client-session]
debug2: channel 0: send open
debug1: Entering interactive session.
debug2: callback start
debug2: client_session2_setup: id 0
debug2: channel 0: request pty-req confirm 0
debug2: channel 0: request shell confirm 0
debug2: fd 3 setting TCP_NODELAY
debug2: callback done
debug2: channel 0: open confirm rwindow 0 rmax 32768
debug2: channel 0: rcvd adjust 131072
Linux myserver.myserver.com 2.6.22-14-server #1 SMP Tue Feb 12 08:27:05 UTC 2008 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
Last login: Tue Mar 11 20:36:45 2008 from 69.0.49.245
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

administrator@myserver:/$ 

```

So after going though that, It looks like I'm not doing all that I should to stop it from checking for passwords.  In the config file I am doing the following:

ChallengeResponseAuthentication yes
PasswordAuthentication no
UsePAM no

---

### Post by bodhi.zazen on 2008-03-11
Correct me if I am reading that wrong, but it looks like the ssh log in with the keys was successful, no ?

---

### Post by dacool25 on 2008-03-11
Yes, that is correct however that is with passwords enabled.  I do not want to be able to log in with anything but the key. (Sorry if i didn't make that clear earlier.)

---

### Post by kevdog on 2008-03-11
Yes,  just disable password authentication in the /config file and restart the sshd daemon

---

### Post by dacool25 on 2008-03-11
=) Yes that is how it was before, then I was asked to > ...Then, on the server, you need the public MAC key. Delete the others for now.

**Then re-enable password log-ins.**

Then connect, from the windows box with Putty...

As soon as i disable password authentication I get Permission denied (publickey).

---

### Post by kevdog on 2008-03-11
can you ssh with the -vvv option and then post the relevant output related to the key being denied??

Can you summarize your clients (os) and the server os?

---

### Post by dacool25 on 2008-03-11
Sure,

My client (the computer i'm connecting from) is a macbook pro running 10.5.  The server that I am trying to connect to is ubuntu server 7.10.

Here is the output with password authentiaction turned off:

```
 ssh mysite.com -vvv
OpenSSH_4.5p1, OpenSSL 0.9.7l 28 Sep 2006
debug1: Reading configuration data /etc/ssh_config
debug2: ssh_connect: needpriv 0
debug1: Connecting to mysite.com [xxx.xxx.xxx.xxx] port 22.
debug1: Connection established.
debug1: identity file /Users/myusername/.ssh/identity type -1
debug3: Not a RSA1 key file /Users/myusername/.ssh/id_rsa.
debug2: key_type_from_name: unknown key type '-----BEGIN'
debug3: key_read: missing keytype
debug2: key_type_from_name: unknown key type 'Proc-Type:'
debug3: key_read: missing keytype
debug2: key_type_from_name: unknown key type 'DEK-Info:'
debug3: key_read: missing keytype
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug2: key_type_from_name: unknown key type '-----END'
debug3: key_read: missing keytype
debug1: identity file /Users/myusername/.ssh/id_rsa type 1
debug1: identity file /Users/myusername/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.6p1 Debian-5ubuntu0.1
debug1: match: OpenSSH_4.6p1 Debian-5ubuntu0.1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.5
debug2: fd 3 setting O_NONBLOCK
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: mac_init: found hmac-md5
debug1: kex: server->client aes128-cbc hmac-md5 none
debug2: mac_init: found hmac-md5
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug2: dh_gen_key: priv key bits set: 111/256
debug2: bits set: 497/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug3: check_host_in_hostfile: filename /Users/myusername/.ssh/known_hosts
debug3: check_host_in_hostfile: match line 2
debug3: check_host_in_hostfile: filename /Users/myusername/.ssh/known_hosts
debug3: check_host_in_hostfile: match line 2
debug1: Host 'mysite.com' is known and matches the RSA host key.
debug1: Found key in /Users/myusername/.ssh/known_hosts:2
debug2: bits set: 504/1024
debug1: ssh_rsa_verify: signature correct
debug2: kex_derive_keys
debug2: set_newkeys: mode 1
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug2: set_newkeys: mode 0
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug2: key: /Users/myusername/.ssh/identity (0x0)
debug2: key: /Users/myusername/.ssh/id_rsa (0x101990)
debug2: key: /Users/myusername/.ssh/id_dsa (0x0)
debug1: Authentications that can continue: publickey
debug3: start over, passed a different list publickey
debug3: preferred publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /Users/myusername/.ssh/identity
debug3: no such identity: /Users/myusername/.ssh/identity
debug1: Offering public key: /Users/myusername/.ssh/id_rsa
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey
debug1: Trying private key: /Users/myusername/.ssh/id_dsa
debug3: no such identity: /Users/myusername/.ssh/id_dsa
debug2: we did not send a packet, disable method
debug1: No more authentication methods to try.
Permission denied (publickey).

```

---

### Post by kevdog on 2008-03-11
Ok, so if what Im looking at is correct, it seems to be a key format problem.  

Is it possible to take putty out of the loop for now??

Is this accurate or did you just edit these lines?
/Users/myusername

I see this:
ssh myserver.com -l administrator -vv

So on the server (ubuntu) you have a user named administrator?  I just want to confirm a few things -- want to cover all basis.

Usually I do the following:

ssh [email]adminstrator@myserver.com[/email]

Although I dont have an administrator user on the ubuntu machine.

Again just want to know if these usernames were edited for posting sake?

---

### Post by dacool25 on 2008-03-11
Yes, my apologies i should have said something.  Anything that shows personal information i altered for posting sake, this includes ip address, hostname and my username.

And yes it is possible to take PuTTY out of the loop.  However I made the file FROM the mac and then used the putty key generator to make one for putty's sake.

---

### Post by dacool25 on 2008-03-11
Here is what my Private key looks like (I just changed all of the randomized data to blahblahblah)

```
-----BEGIN RSA PRIVATE KEY-----
Proc-Type: 4,ENCRYPTED
DEK-Info: DES-EDE3-CBC,blahblahblah

somemoreblahblahblah
-----END RSA PRIVATE KEY-----

```

---

### Post by kevdog on 2008-03-11
Ok for now I would create the keys on the MAC or ubuntu at the command line -- leave putty alone for right now -- lets just get the basics hacked out.

Confirm key was created with
ssh-keygen -t rsa -b 2048 (or 4096)

The id_rsa key stays on the client.  Copy the id_rsa.pub key to the server in the appropriate user_directory/.ssh.

Create the authorized_keys file (on the server):
touch authorized_keys

Im not sure what the right permissions on the file are supposed to be but for now lets do the following on the server
chmod 644 authorized_keys

Then
cat id_rsa.pub > authorized_keys

Ok, seems like the server and client are working since we've verified password authentication, so that's out of the way.

Try to connect from the command line of the client to the server.

ssh <user>@<server>

Again can't be a port problem, firewall problem, etc since password authentication works!

---

### Post by dacool25 on 2008-03-11
:guitar:

That worked! I think that my problem was that i didn't have the .pub file i just had all of the stuff thats supposed to be in there in the authorized_keys file

I am so sorry, I should have payed more attention.  Thank you thank you thank you!

But just one more question =) I created the key on my mac, if i log onto another computer and try to use that key, will it work?

---

### Post by dacool25 on 2008-03-11
Wait i'm sorry, that may have been part of the problem but i had to do the [email]username@hostname.com[/email] just ssh hostname.com doesn't work.

So will this key work on other computers besides the one i made it on?

---

### Post by kevdog on 2008-03-11
You actually dont need the pub key on the server.  Once its contents are in the authorized_keys file, you can delete it.  Just to trust what I say is true, rename the file on the server and see if you can connect.  The way you copy the keys into the file is loaded with problems -- one extra space, and the entire authentication process fails.

Will the keys you made work on other computers??  Yes if they use OpenSSH.  If they use putty, then you have to convert the key to putty format.  You import  the private key, it should ask you to do a conversion, then save the private key in putty format.  Note that if you change the file name you either need to include a -i <filename> on the command line if its not the default, or make a ssh_config file and create a profile that you can then reference.  With putty, it saves its own profiles, so if you only change the name from id_rsa to id_rsa_putty, then it will store this within its own profile.

Hopefully that made sense??

---

### Post by dacool25 on 2008-03-11
That made perfect sense =)  Thank you for all of your help

---

### Post by bodhi.zazen on 2008-03-11
Thank you kevdog for your assistance.

@dacool25: glad it makes sense now. I gave you a link on how to import an open ssh key, one that you made from the command line, to Putty. If you need it again I can re-post it.

If you like you can make a putty key, with a different name, and import it to the server, but I do not want to confuse the matter :)

---

### Post by kevdog on 2008-03-12
bodhi

Sorry for the thread hijack -- I was really bored that's all.  I'll keep away next time.

---

### Post by bodhi.zazen on 2008-03-12
> **kevdog said:**
> bodhi

Sorry for the thread hijack -- I was really bored that's all.  I'll keep away next time.

LOL, please don't (keep away). Your input was invaluable, it was a team effort and you added more then I (in fact I think I was the original hijacker here).

---

### Post by dacool25 on 2008-03-12
And I was the idiot =) haha

---

