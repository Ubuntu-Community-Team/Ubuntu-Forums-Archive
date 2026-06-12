---
title: "SSH Requires Two Passwords? Local and Server?"
date: 2014-03-12
forum: General Help
---

### Post by orangeman555 on 2014-03-12
SSH requires me to enter my local user password (the sudo) and then the server password. 

So its like this:

>> ssh [email]user@somewebsite.com[/email]

>> Enter passphrase for key '/home/user/.ssh/id_rsa':

bla bla bla

>> [email]user@somewebsite.com[/email]'s password: 

I'd like to eliminate the first (local) password request. How is this done?

---

### Post by Lars Noodén on 2014-03-13
What version of sshd are you running on the server?   It looks like it is configured to require both a key and a remote password.  That your key's passphrase has been set to the same as your local password is probably a mistake.  That can be corrected.

```

ssh-keygen -p -f /home/user/.ssh/id_rsa

```

But if you want to avoid typing the key's passphrase repeatedly, the best way is to load the key in to the ssh-agent that Ubuntu has running in the background.

```

ssh-add /home/user/.ssh/id_rsa

```

That will put the key id_rsa into the agent and then ssh will try using the agent when connecting.  If the key is there, you don't have to do anything more.  

You can keep up to six keys that way and they are good until you cancel them or log out of your graphical session.

---

### Post by tfrue on 2014-03-13
Generate a new key and leave the pass phrase empty. When you generated the keys on the local side, you told it to have a pass phrase hence the password. To generate new keys, type:
```

ssh-keygen -t rsa

```
That will create a 2048 bit rsa key, and when it ask for a passphrase, leave it blank by hitting enter.

So when you try to connect the next time, you shouldn't be prompted at the local level.

*NOTE*
You can actually set up the server to use the generated key to authenticate so you will just have to issue the "ssh username@server" command and it will automatically connect. The downfall, is you will have to set up each computer before you can use ssh  to your server on that computer. Which isn't an issue for me, so I went ahead and use key based authentication, since it's more safe and easier to use.

Here is a link to the OpenSSH website that does a better job at explaining all of this better than I:
[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

If the site isn't clear enough, I will help you set up key based authentication.

---

### Post by efflandt on 2014-03-14
Just curious if you have your ~/.ssh/authorized_keys properly set up on the server, because if that is not quite right or has excessive permissions, the key might either be not trusted or not working and that may be why the server is then requesting a password (possibly instead of key rather than in addition to it). Typically ~/.ssh should have 700 permission and any files in it should have 600 permission (only your user should have read or write permission to those files on client or server). Public keys go into authorized_keys 1 key per line (wordwrap would break them).

Usually once I have my key on a computer that I control, I configure sshd to not accept passwords at all (makes password crack attempts futile).

---

