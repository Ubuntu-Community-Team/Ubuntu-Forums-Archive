---
title: "Problem with SSH key auth"
date: 2018-05-31
forum: General Help
---

### Post by clodiw on 2018-05-31
Hello, I've got some troubles understanding SSH key authentication.

So here's my problem :

I've got a client machine (RPI) and a remote server (NAS). 

I'm logged in as user "ALICE" on (RPI). There is also an user "ALICE" on the (NAS). After basic configuring password-less auth, I manage to connect with user "ALICE" from (RPI) to (NAS) with key auth.

Now, I'd like to create a user "RSYNC" on (NAS). I do exactly the same configuration than for "ALICE", except than when I do ssh-copy-id I use "RSYNC" user to copy the pub key.

But I'm not able to key auth with "RSYNC" user. I tried creating the "RSYNC" user on my (RPI), generating a new key pair etc... But that doesn't work neither.

I already searched through the Internet, read the manpages, tried creating a "config" file in .ssh directory, nothing worked. Maybe, I'm miss-understanding something.

Note that, all the configuration are OK (dir permissions, NAS config, NAS permissions etc...). It must have something to do with SSH, maybe a config that is missing. 

Thanks for help,

clodiw

EDIT : Here's the output when I try to connect from (RPI) to (NAS) with SSH and user (RSYNC). I can understand that ssh looks up for a public key, finds it, and then looks up for the private key, but it seems like he's not finding the id_rsa.

[[IMG]https://nsa39.casimages.com/img/2018/05/31/180531010723316785.png[/IMG]]("https://www.casimages.com/i/180531010723316785.png.html")

---

### Post by TheFu on 2018-05-31
usernames need to be all lowercase. Mixing case can cause issues. Avoid those.

ssh requires specific file and directory permissions to work.  Check that those are correct on both the client and server.

[http://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections](http://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections)

NAS implementations for many tools are stripped down and often old versions.  Does the NAS support the methods being used?  

BTW, please copy/paste TEXT, not images. Some people pay by the byte for data.

---

### Post by clodiw on 2018-05-31
Well, my users are actually all lowercase, this was just to illustrate my problem. As I said, I have configured everything, permissions on auth_keys, on .ssh directory and on home profiles. Again, as I said, it is working fine for the user that is the same on the client and on the remote system. But when I try to SSH with "ALICE" (on local system) to "RSYNC" (on distant machine), I'm not able to auth with keys.

Thanks anyway.

Maybe this is more understandable : 

ssh 10.10.10.10 -l alice -p 1232 --> works with keys (=does not prompt for password)
ssh 10.10.10.10 -l rsync -p 1232 --> doesn't work with keys (=prompts for password)

---

### Post by anspectrum on 2018-05-31
If your private key is not being found. Try running this command:

> ssh-add

I've encountered this kind of probelms and although private keys are automatically added to ssh agent, sometimes we have to add them manually.

---

### Post by TheFu on 2018-05-31
I tend to assume things that aren't said, but accept exactly those things said, unless there is a clear conflict.  So, I fell into the trap of thinking uppercase was used, because that was the example provided.

Always best to show the exact commands. Thanks.
Being explicit is good. I'd normally put the alternate userid and port into the ~/.ssh/config under an alias for the connection.

Permissions on the ~/.ssh/ on both sides please?  **ls -al **preferred to prevent confusion.

Anything in the ~/.ssh/config that would override defaults for either connection?  Looks like RSA keys aren't being tried.

Always best to show the setup with facts and less description.

Initially, I looked for an rsync userid on my boxes.  I know some people run an rsyncd and perhaps the NAS does?

Did the troubleshooting link help?

---

### Post by clodiw on 2018-05-31
Sure, you're right.

Okey, I managed to workaround the problem. I missed something.

That's the situation right now : I've got 2 users on both local and distant machine. I can now connect without a password from both users (on the local machine). So, I'm currently logged in as user "alice" on local system, I can connect to the remote system with that command : "ssh 10.10.10.10 -p 1232". I do not have to enter the -l argument, because by default, I guess, SSH uses the local user as a distant user.

So, my question right now is, what if the local user is called "alice" and the distant user is called "rsync" ? Can I do : "alice@RPI : ssh 10.10.10.10 -p 1232 -l rsync" in order to connect to the distant "rsync" user ?

Here's a sample of ls -la showing the permissions. 
> 
-rw------- 1 rsync rsync 1679 mai   31 14:55 id_rsa
-rw-r--r-- 1 rsync rsync  394 mai   31 14:55 id_rsa.pub

Thanks.

Edit : I could not open the link you gave me.

---

### Post by TheFu on 2018-05-31
Did anspectrum's idea work?  Seems plausible, though I've never run into it.  Try logging out and back in. That should also reset the ssh-agent session info. Might be the issue.

Ah the URL ... govt internet filters on your side or the subnet in use has been a source of attacks. The waybackmachine or google cache will have a copy or a VPN can be used. A 403 error will happen if it isn't govt filter and it is blocked.

BTW, the **ls -al** isn't complete.  Wanted to see the directory permissions too. And on all 3 directories.  client & server for all the userids.

Specific permissions requirements. ssh-copy-id doesn't break them, so if you generated the key(s), used ssh-copy-id to push them, and never did a chmod on any system, it should be correct. Can't hurt to show the permissions.

"alice@RPI : ssh 10.10.10.10 -p 1232 -l rsync"
Huh?  you lost me.  Is the first part a prompt?  User prompts have a $.  root prompts have #. This is the normal way to differentiate which sort of account is being used.

I'd do **ssh rsync@10.10.10.10 -p 1232** as the alice userid, provided the alice public key has been installed on the rpi system into the ~rsync/.ssh/ directory.

I use **ssh userid@10.10.10.10 -p 1232** form of the command if the usernames don't match on both sides. It shouldn't matter, but who knows what a NAS implementation might or might not support?  This format works for almost all ssh-based commands, including rsync.  The default PROMPT for bash usually shows the correct format for scp, sftp, and rsync URLs.

I alluded to the config file. An example. 
```
host pi3
  user steve
  hostname pi3
  port 63022
```
Multiple 'host' stanzas allowed.  I have 50+ in my main desktop.

So **ssh pi3** would be used by any ssh-using tool as *ssh steve@pi3 -p 63022*.  I use different aliases (the host line) depending on which different settings I want. It also means never having to remember IPs or those terrible cloudy hostnames or ports.  rsync and every librsync-based tool I've ever used honor the config file.

The config file is a convenience.  Command line options override it and explicit options are good for testing.

In the troubleshooting link, it explains how to turn up the verbosity and about the server-side logs.  Always good to check those.

There's also an IPv6 issue in recent sshd implementations.  If you don't allow IPv6, some setups fail. 1 of my 20 servers had this issue, which makes no sense to me. I disable IPv6 across all the systems using automation, but only 1 system was impacted?  Since 1 ssh login is working, this isn't the issue for you.

---

### Post by clodiw on 2018-05-31
Yes, sorry, I wrote it myself and missed the "$".

> rsync@NAS:~/.ssh$ 

Thanks for the explanations.

Well, correct me if I'm wrong, using the config file, makes > ssh pi3 execute > ssh steve@pi3 -p 63022 ?

The question I had in fact, was, can I log in from the same local user to multiple remote users ? I think I found an answer, but again, correct me if I'm wrong please.

I generate a pair of keys from my unique user "alice" on (RPI). I copy the public key to both users on remote system.

Now I can login from the local "alice" on (RPI) to both distant users ? Am I right ?

Thanks a lot.

---

### Post by TheFu on 2018-05-31
Yes, you can use ssh to ssh into different (or the same) systems (local or remote) under different (or the same) userids.

This is commonly used by admins for all sorts of needs.

But on specialized, minimal equipment, sometimes they don't use the full tools due to storage or RAM limitations.

---

### Post by clodiw on 2018-05-31
Well, thank you

---

### Post by TheFu on 2018-05-31
> **clodiw said:**
> Well, thank you

What was the issue?  Might help the next person to post it here.

BTW, you can use the same or different keys for authentication to other userids/systems. That's where the ~/.ssh/config file really becomes helpful, but command line options work to specify the key to be used too.

---

