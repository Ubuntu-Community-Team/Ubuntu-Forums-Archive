---
title: "SSH - confusion with passphrase using two different key pairs (for Mac &amp; Windows)"
date: 2021-05-25
forum: General Help
---

### Post by freeflyjohn on 2021-05-25
I had been using Ubuntu server 16.04 but just performed a fresh install of 20.04 and in the process of configuring ssh.

I had ssh working on 16.04 with my Mac laptop (using terminal, Putty, Filezilla and X2go) as well as a Windows laptop (using Putty, Filezilla and X2go).

This time, instead of having a single pair of keys I have created two pairs of keys - one pair for the Windows laptop and another pair for the Mac laptop.

Both keys have been added to the authorized_keys file on the server.

On the Windows laptop, Putty and Filezilla work correctly and ask for the key passphrase when connecting.

However, on the Mac laptop laptop its only half working.

- With Filezilla I can connect, but it doesn't ask me for the passphrase (when I was running Ubuntu 16.04 Filezilla always asked for a passphrase)
- With terminal I can connect, but it doesn't ask me for the passphrase (when I was running Ubuntu 16.04 terminal always asked for a passphrase)
- With X2go it asks me for the passphrase but rejects it and fails after 3 attempts (X2go points to the same ppk key file that Filezilla points to)

How do I force ssh connections from the Mac laptop to always request the key passphrase ?

And why does X2go ask for the passphrase (when Filezilla & terminal doesnt) and then reject it, even though it points to the same key used by Filezilla ?

Also, when using terminal on the Mac (i.e. ssh user@mydomain -p xxxxx) how does terminal know which key pair to use ?  By default key pairs have the name id_rsa, which is what I've stuck with on the Mac but used a different name on Windows.  If I were to use a different name for the key pair on the Mac, then how would terminal know which key pair to use or does it just try all key pairs in the .ssh folder until its successful ?

---

### Post by ActionParsnip on 2021-05-25
```

ssh -i /path/to/private.key user@server

```
If you want to specify the private key. I believe by default it will use ~/.ssh/id_rsa

---

### Post by CharlesA on 2021-05-25
> **ActionParsnip said:**
> ```

ssh -i /path/to/private.key user@server

```
If you want to specify the private key. I believe by default it will use ~/.ssh/id_rsa

In addition to this, if you don't want to have to specify the key each time, you can look into creating a config file.

I use this on my ansible box to tell it which key to use for my ansible users.

See here for more info:
[https://linuxize.com/post/using-the-ssh-config-file/](https://linuxize.com/post/using-the-ssh-config-file/)

---

### Post by freeflyjohn on 2021-05-26
Thanks ActionParsnip and CharlesA

I have tired X2go on the Windows laptop which uses different keys to that of the Mac laptop, but it still doesnt accept the passphrase so I don't know why this isn't working on both the Mac and Windows laptop ?

Also I still don't understand why the Mac laptop does not request the passphrase for terminal and Filezilla (it used to when I was running Uuntu 16.04 and it does on the Windows laptop).

Is there a setting or config somewhere that bypasses the request for the passphrase on the Mac (I guess it would have to have stored the passphrase in a keychain or something) ?

---

### Post by TheFu on 2021-05-26
x2go from Windows requires that the key be created by the ssh-keygen included with x2go.  I worked through this about 1-2 months ago.
Every client should be using a different ssh key. They shouldn't be shared.

I don't use filezilla, so cannot help with that.  I use WinSCP from Windows and between Linux systems, I tend to use NFS or rsync or scp from a shell. If I already have a file manager running, using the sftp://xxxxxxxxxxx/ in the URL location textentry works, at least on all Linux file managers.  Some may need ssh:// - but the keys will be honored based on the ~/.ssh/config settings.  The manpage for this file is **ssh_config** if you want more details.
[https://blog.jdpfu.com/2011/07/14/easy-key-based-ssh-authentication](https://blog.jdpfu.com/2011/07/14/easy-key-based-ssh-authentication) explains how to setup ssh-keys and the ~/.ssh/config file.

Now that Windows supports ssh, it works about the same, just with Windows-paths instead of Unix paths.  OTOH, all Windows programs understand using /, rather than \ characters.  c:/users/thefu/.ssh/config  ... would be where the ~/.ssh/config would be on Windows for "thefu" userid.  Unfortunately, Windows does not have **ssh-copy-id**.

putty has been around a very long time, so their method is different from the expected. That's good and bad.

---

### Post by ActionParsnip on 2021-05-26
Is it a known issue in Mac? I'm not a Mac guy in any way, so can't really comment. Could try:
```

ssh -vvvvvvvvv -i /path/to/private.key user@server

```
On the Mac, then read the output. See what's going on. May help

---

### Post by CharlesA on 2021-05-26
> **freeflyjohn said:**
> 
Also I still don't understand why the Mac laptop does not request the passphrase for terminal and Filezilla (it used to when I was running Uuntu 16.04 and it does on the Windows laptop).

Is there a setting or config somewhere that bypasses the request for the passphrase on the Mac (I guess it would have to have stored the passphrase in a keychain or something) ?

I don't know the answer to that question. I use WinSCP if I want to use scp of sftp rather than Filezilla (on windows at least) and it piggy backs on putty, so it uses the ppk format for the private keys.

With that said, I usually only use putty at home due to inertia. I use Windows Subsystem for Linux (WSL) on my work box to ssh in if I need to. This has the added bonus of being a linux system rather than running on windows.

---

### Post by freeflyjohn on 2021-05-26
Thanks TheFu, ActionParsnip and CharlesA

The thing is, ssh is working on the Mac and I can connect to the server.

My concern is the fact it does not ask for the key passphrase, which it used to do when I was running Ubuntu 16.04 and on the Windows laptop it always asks for the passphrase.

So its not the fact ssh and the keys are not working (except for X2go and I've now resorted to using Nomachine), its the fact that the Mac laptop does not ask me for a passphrase which is a security concern

I don't understand why its not asking for the passphrase on the Mac ?

---

### Post by freeflyjohn on 2021-05-26
Maybe the question is.... if you generate an ssh key with a passphrase, what would cause the situation where the key works but without asking for that passphrase ?

---

### Post by TheFu on 2021-05-26
Setup ssh-agent?  Is that the answer?  Then unlocking the ssh-key only need happen once every "configured period" of ssh-agent time.

```
     -t life
             Set a default value for the maximum lifetime of identities added
             to the agent.  The lifetime may be specified in seconds or in a
             time format specified in sshd_config(5).  A lifetime specified
             for an identity with ssh-add(1) overrides this value.  Without
             this option the default maximum lifetime is forever.
```

So, basically once per login, if you run ssh-agent automatically.

---

### Post by freeflyjohn on 2021-06-01
I've managed to fix this by generating a new pair of keys on the Mac

But this time I only copied the public key (id_rsa.pub) to the folder ~/.ssh on the Ubuntu server, where as before I had copied both the public key and the private key.

So I wonder if having the private key in the folder ~/.ssh on Ubuntu server was the issue ?

---

### Post by TheFu on 2021-06-01
Private keys should not be moved off the system where they are built and must be 0600 permissions.
If you've solved this, please help the community save time - "Thread Tools" button near the top of the page, "SOLVED" - Please and thank you.

---

