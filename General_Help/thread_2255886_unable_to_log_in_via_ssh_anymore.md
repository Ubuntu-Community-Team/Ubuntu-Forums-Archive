---
title: "unable to log in via ssh anymore"
date: 2014-12-08
forum: General Help
---

### Post by andrew-miller57 on 2014-12-08
I recently have been unable to log in to my server via ssh anymore.  I purged it from the server and reinstalled and have temporarily turned on password authentication to yes.  I even purged the openssh-client from the client machine and reinstalled but am still being denied access when typing in my password.  Any ideas??  

Here is ssh -v andrew@192.168.1.70

```
andrew@andrew-desktop ~ $ ssh -v andrew@192.168.1.70OpenSSH_6.6.1, OpenSSL 1.0.1f 6 Jan 2014
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug1: Connecting to 192.168.1.70 [192.168.1.70] port 22.
debug1: Connection established.
debug1: identity file /home/andrew/.ssh/id_rsa type -1
debug1: identity file /home/andrew/.ssh/id_rsa-cert type -1
debug1: identity file /home/andrew/.ssh/id_dsa type -1
debug1: identity file /home/andrew/.ssh/id_dsa-cert type -1
debug1: identity file /home/andrew/.ssh/id_ecdsa type -1
debug1: identity file /home/andrew/.ssh/id_ecdsa-cert type -1
debug1: identity file /home/andrew/.ssh/id_ed25519 type -1
debug1: identity file /home/andrew/.ssh/id_ed25519-cert type -1
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_6.6.1p1 Ubuntu-2ubuntu2
debug1: Remote protocol version 2.0, remote software version OpenSSH_6.0p1 Debian-4+deb7u2
debug1: match: OpenSSH_6.0p1 Debian-4+deb7u2 pat OpenSSH* compat 0x04000000
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-ctr hmac-md5 none
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: sending SSH2_MSG_KEX_ECDH_INIT
debug1: expecting SSH2_MSG_KEX_ECDH_REPLY
debug1: Server host key: ECDSA 4a:30:07:f0:5c:56:c8:52:95:63:b7:b0:70:dd:46:37
debug1: Host '192.168.1.70' is known and matches the ECDSA host key.
debug1: Found key in /home/andrew/.ssh/known_hosts:1
debug1: ssh_ecdsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: Roaming not allowed by server
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /home/andrew/.ssh/id_rsa
debug1: Trying private key: /home/andrew/.ssh/id_dsa
debug1: Trying private key: /home/andrew/.ssh/id_ecdsa
debug1: Trying private key: /home/andrew/.ssh/id_ed25519
debug1: Next authentication method: password
andrew@192.168.1.70's password: 
debug1: Authentications that can continue: publickey,password
Permission denied, please try again.
andrew@192.168.1.70's password: 



```

---

### Post by TheFu on 2014-12-08
What are the permissions on the ~/.ssh/ directory and files?  That is usually the issue for stuff like this.

The directory needs to be 700.
The private key needs to be 600
The public key can be anything, 644 is fine.
known_hosts and authorized_leys - 600.
When in doubt - 600. I use that for the ~/.ssh/config file too.

---

### Post by andrew-miller57 on 2014-12-08
Are you talking about the permissions on the server or client?

---

### Post by TheFu on 2014-12-08
both.  Basically, if the files are auto-created by tools, they will be correct.
For example, use **ssh-copy-id** to push the keys over ... don't manually do it.
If there is a duplicate known-host, use the command provided in the error message to fix it.

I avoid using any GUI tools in these directories. GUI tools seem to do extra things whenever I use them - more than I want.

---

### Post by andrew-miller57 on 2014-12-08
I'll need to check them...Worst case, is there a way for me to just remove all traces of SSH on my clients and servers and start from scratch?  I'm talking like all config files and everything. As is SSH didnt exist there before so that I can reinstall...

---

### Post by TheFu on 2014-12-08
Are you serious?  That is like nuking all of the western hemisphere over a mosquito bite in Florida.
ssh just isn't that complicated.

If you don't understand what I'm saying to do, ASK. This is a 15 sec thing on each box, assuming this is the root cause (I believe it is 95% likely).

You didn't touch any ssh files in /etc/ssh/    correct?

---

### Post by andrew-miller57 on 2014-12-08
haha a bit of an over reaction i guess.  all I did was clear out all keys and regenerate them.  How would I check for the permissions on the files your mentioning?

---

### Post by TheFu on 2014-12-08
> **andrew-miller57 said:**
> haha a bit of an over reaction i guess.  all I did was clear out all keys and regenerate them.  How would I check for the permissions on the files your mentioning?

Ok - so file and directory permissions are the CORE of every UNIX OS. It controls access to everything - files, devices, disks, networking, drivers, everything. You need to learn this stuff to be effective.  My best recommendation is for you to **read** the 1st 100 pgs of this book ([http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) - easy free PDF download) and skim the rest just to see what other things are possible. Doing this will save you hours, days, weeks, months of frustration with all UNIX/Linux systems. Trust me.

OTOH, your life is probably busy and you don't have the time to do that, use the **ls -l** command to see file/directory permissions. Seeing them doesn't mean that understanding them will happen.  Google will find tutorials on file/directory permissions. help.ubuntu.com has one too.

Grab that book, read the first part, skim the rest and be happy - seriously. That homework will save you time and much frustration overall.  BTW, there is a section in the book on ssh. ;)

I'm sorta surprised that other people with slightly different opinions haven't chimed in yet. Sometimes reading someone elses version is very helpful.

---

### Post by Lars Noodén on 2014-12-09
> **andrew-miller57 said:**
> haha a bit of an over reaction i guess.  all I did was clear out all keys and regenerate them.  How would I check for the permissions on the files your mentioning?

TheFu has covered it all 

But one fine point that can help is to give the keys unique names, so that you can keep using the old  keys while testing the new keys.  Sadly few tutorials and howtos show how to use either [-f or -C](http://manpages.ubuntu.com/manpages/trusty/en/man1/ssh-keygen.1.html).  -f will set the file name.  That will help when tidying up or moving things around.  -C will add a comment to the key.  The comment will be used by programs like Seahorse so, like with the file name, use something that will identify the key itself.  

That way you can keep the old keys around on the client and still use the new keys.  And you can keep the old public key around on the server until you are sure that you can log in with the new keys.  The *~/.ssh/authorized_keys* file on the server can hold many public keys at the same time.  ssh-copy-id will put your new key there but you'll have to pull the old one from it manually.

---

### Post by TheFu on 2014-12-09
Yeah - if you don't have console access to the machine, having a way to install newer keys later is important.  If you do have console access, like I do for all my systems, it hasn't been necessary to use different keys.  When a key needs to be replaced ... like when a laptop is out of my control on travel for a few hours, I need to create new keys and push those to all the systems desired.

Thanks Lars. Excellent points, as usual.

---

