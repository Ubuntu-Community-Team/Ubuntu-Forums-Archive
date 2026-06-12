---
title: "SSH Keys login"
date: 2016-08-31
forum: General Help
---

### Post by ELMIT on 2016-08-31
I got one desktop and several remote servers.

I followed [https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys) to get the keys and can log in perfectly at one remote server, for which I have created the key pair.

The other sites are not prepared for that now. How can I mix that, or gradually move to use Keys?

---

### Post by TheFu on 2016-08-31
**ssh-copy-id** - it doesn't have to be hard.

You can use the same key on all the remote machines. Many people do.  There are also those who choose to make a new key for each client-group or even each server.  The using the ~/.ssh/config file to manage these different identities is really important on the client.

---

### Post by cmcanulty on 2016-08-31
I am also interested in this. Can you explain more for a beginner at ssh, thank you

---

### Post by Rocket2DMn on 2016-08-31
When you generate keys, you're actually creating a pair - a private key and a public key.  The private key is exactly that - a secret key that you keep locally on your client.  You can share your public key with anybody (presumably others that you trust and want to communicate with).  You can add your public key to the trusted list on servers that you access, so that when you login to them, a protocol is initiated between your client and the server that verifies that you (the client) have the private key, thus authenticating you to the server.

If your private key is ever compromised, it's no longer useful and anybody who has your public key (like your servers) needs to remove it since it can no longer be trusted.  Somebody else who has compromised your private key could pretend to be you by using it.

Some people will generate a different private/public key pair for EVERY system they connect to, so that it if a single private key becomes compromised, they only have to make a change for one server, and the potential for damage is limited.  Using a single private key is more convenient, but if it becomes compromised, everybody who has your public key needs to be updated, and until that happens, they are all vulnerable to somebody pretending to be you.

I generally think that one private key is sufficient in most cases, because if somebody can compromise that key, they can probably compromise the rest of them stored on that single client.  It is possible, though computationally extremely difficult, to recreate somebody's private key without actually compromising the client's system (you need massive computing resources and lots of time to do so, e.g. resources like the NSA or other government agency might have).

Different clients should generate their own keys though.  So if you have 2 clients (e.g. a desktop and a laptop), they should probably create their own public/private key pairs so that if one becomes compromised, the other may still be secure.  Additionally, some people generated different key pairs for different purposes, like one for remote connecting to their servers, another for email encryption, and more for different SSL tasks like using GitHub or something like that.

---

### Post by ELMIT on 2016-08-31
To create different keys isn't the problem, but I have created that pair for ONE server. On the other servers I cannot login anymore, because now it requires me:

Enter passphrase for key '/home/ronald/.ssh/id_rsa': 

which does not exist on that other server.

Is there a way to use id_rsa on one server and normal password on another server?

---

### Post by TheFu on 2016-08-31
I've never seen that issue.  Nothing should be necessary on the client-side to support both keys and passwords.  Of course, if the server admin has forced all key-based authentication and prevented passwords, then that could be an issue. Talk to the admin.  This **is** a best practice for ssh - force all remote logins to use keys.

Could someone else have put their keys onto the server and that is why things are failing?  Shared account? If so, check the ssh manpage for how to specify a password be used.

OTOH, if you setup a ~/.ssh/config file, you can setup different identy files (id_rsa.pub/priv) to be used.

My goal in life is to use ssh-keys for all logins. It is the 2nd thing I do on a new server (1st thing is to purge nano).

---

### Post by ELMIT on 2016-09-02
I found out that it is working, however, not as I expected.

1. I used a pass phrase. 

2. I was confused when I got the prompt 
Enter passphrase for key '/home/ronald/.ssh/id_rsa': 
Since that server should not even ask for that. However, just hit Enter brings me to the normal password request. That works!


How can I improve that?
E.g. Filezilla complaint two things: Format of the id_rsa is not correct and Currently keys with password cannot be used.
Can I have two keys for one user? One with password, one without password?
Or should I just replace the key with password, with a key without password?

---

### Post by TheFu on 2016-09-03
**ssh-agent** is what you want.
I've never used filezilla, don't know anything about it.
You can have as many keys per user as you like. Just specify the key file-pair or rename previously made files.
Having ssh-keys without a password for end-users is a really bad idea from a security perspective. Of course, this is Unix, so you can decide to ignore it and do whatever you like.

There are lots of ssh how-tos out there for all sorts of things.  ssh is the swiss-army-knife of Unix connectivity. There isn't much in the way of connectivity that ssh cannot do.  The ssh manpage is a thing of beauty.

---

