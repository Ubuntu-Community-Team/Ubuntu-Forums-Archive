---
title: "SSH fails on multiple accounts"
date: 2015-07-18
forum: General Help
---

### Post by prongs95 on 2015-07-18
UPDATE: I'm an idiot and i missed a few steps.

Upon typing this command:

```
ssh -v 127.0.0.1
```
i get this output:
i have an OpenSSH server running on ubuntu 14.04 LTS.


```
debug1: Authentications that can continue: publickey
debug1: Next authentication method: publickey
debug1: Offering RSA public key: /home/steven/.ssh/id_rsa
debug1: Authentications that can continue: publickey
debug1: Trying private key: /home/steven/.ssh/id_dsa
debug1: key_parse_private2: missing begin marker
debug1: read PEM private key done: type RSA
debug1: Authentications that can continue: publickey
debug1: Trying private key: /home/steven/.ssh/id_ecdsa
debug1: Trying private key: /home/steven/.ssh/id_ed25519
debug1: No more authentication methods to try.
Permission denied (publickey).


```
any help appreciated.

---

### Post by Keith_Helms on 2015-07-19
Why are you trying to ssh to the local box you're already signed on to???

---

### Post by Lars Noodén on 2015-07-19
Welcome.

If you haven't yet put the right public key on the server in ~/.ssh/authorized_keys then that needs to be done.  

If you have put the right public key on the server in ~/.ssh/authorized_keys then try explicitly naming the key when you try to connect. e.g.

```

ssh -v -i ~/.ssh/some_key_rsa 127.0.0.1

```

---

### Post by prongs95 on 2015-07-19
to test the server.

---

### Post by prongs95 on 2015-07-19
thanks for the advice. your command yielded this output:

```
debug1: Authentications that can continue: publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /home/steven/.ssh/id_dsa
debug1: key_parse_private2: missing begin marker
debug1: read PEM private key done: type RSA
debug1: Authentications that can continue: publickey
debug1: No more authentication methods to try.
Permission denied (publickey).
```
 when i tried linking to the privatekey,
and this:
```
debug1: Authentications that can continue: publickey
debug1: Next authentication method: publickey
debug1: Offering RSA public key: /home/steven/.ssh/id_rsa.pub
debug1: Authentications that can continue: publickey
debug1: No more authentication methods to try.
Permission denied (publickey).
```
upon linking to the publickey.

---

### Post by Lars Noodén on 2015-07-20
The client needs to be pointed at the private key.  The public key is the one that goes on to the server but is not otherwise used.  

How did you generate the key pair?

---

### Post by prongs95 on 2015-07-30
> **Lars Noodén said:**
> The client needs to be pointed at the private key.  The public key is the one that goes on to the server but is not otherwise used.  

How did you generate the key pair?

with the method shown here: [https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)
Sorry. I'm sort of an ubuntu n00b, so i just did everything by the tutorial.

---

### Post by Lars Noodén on 2015-07-30
The tutorial is good, it just probably that a step went missing or a typo was made somewhere.  

If you followed the tutorial, you should have two files in ~/.ssh, one called id_rsa and the other id_rsa.pub
Are they there?  You can find them with [ls](http://manpages.ubuntu.com/manpages/trusty/en/man1/ls.1.html) or your favorite file manager.  

If they are both there, then we can verify them with [file](http://manpages.ubuntu.com/manpages/trusty/en/man1/file.1.html) to check the file types.
```

cd ~/.ssh/
file id_rsa*

```

It should say one is a private key and that the other is a public key.  

```

id_rsa:     PEM RSA private key
id_rsa.pub: OpenSSH RSA public key

```

If that is ok then we can check the ~/.ssh/authorized_keys file next.

---

