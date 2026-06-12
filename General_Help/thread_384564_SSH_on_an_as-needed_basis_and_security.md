---
title: "SSH on an as-needed basis and security"
date: 2007-03-14
forum: General Help
---

### Post by DeathOnJuice on 2007-03-14
I'm trying to use SSH for brief periods of time to troubleshoot my friend's computer. He's leeching off my wireless so we're on the same network, but it's a bit of a hassle to walk over there every time I need to fix a problem. The trouble is that I would not feel safe for him with a SSH server running all the time his computer is on, which is what happens when one installs openssh-server. Is there any way to simply start the server when you need it and stop it right afterward?

Additionally, could someone give me a few pointers on security with SSH? We'll be on the same network so the router won't need port forwarding, but I'm sure there are still some security holes and I'd like to know how to keep it safe in the future if I do need to port forward.

---

### Post by LotsOfPhil on 2007-03-14
You could put 
sshd: ALL EXCEPT 192.168.
in /etc/hosts.deny

And that would only let people with an IP of 192.168.1.XXX.XXX (i.e., on your side of the router) log in.

---

### Post by peabody on 2007-03-14
Another more complicated mechanism involves connecting to a random port to have SSH briefly open to that particlur IP.  I think the technique was called "knocking" or some such.  If I find a link I'll post it.

Edit: [http://www.windley.com/archives/2004/04/knock_knock_its.shtml](http://www.windley.com/archives/2004/04/knock_knock_its.shtml)

There's something, I'll try and post more.

Edit2: [http://www.soloport.com/iptables.html](http://www.soloport.com/iptables.html)

That one doesn't use knockd, let me see if I can find anything on that...

Edit3: [http://www.ducea.com/2006/07/05/how-to-safely-connect-from-anywhere-to-your-closed-linux-firewall/](http://www.ducea.com/2006/07/05/how-to-safely-connect-from-anywhere-to-your-closed-linux-firewall/)

That one looks promising.

---

### Post by tribaal on 2007-03-14
Or alternatively you could set sshd to accept only ssh key authentification?

The host.deny trick works very well, but if someday for some reason you need to access his machine from another IP... :(

- trib'

---

### Post by bernied on 2007-03-14
If you want it so sshd (the server) doesn't start automatically at startup, you can change this in the Settings - System Services. You need to turn off ssh for all runlevels that you use and that it is set to start in - this is probably only runlevel 2, but I'm not sure about this. You can use the same GUI to start and stop the ssh server.

Or, in a terminal
```
/etc/init.d/sshd start
```or stop (or restart).

To control what does or doesn't start at startup, look in the /etc/rcX.d/ directories (where X is a number 0-6). The files in these directories are shortcuts to scripts in /etc/init.d/ so you can delete the shortcuts without too much harm (just make not of which ones you are changing). Another less destructive way is to change the first letter (S means start, K means stop [kill]) to lowercase. This will stop it from running.

Many people have their ssh servers open to the world - like me. I'm sure you'll be fine within your own firewall. 

Apparently the most secure security is public key authentication. That is where you have a pair of matching (not identical) keys, private and public. You keep your private key to yourself, and put your public key on any server that you want to be able to access. This method does not use passwords. If you don't have the correct key then the server drops the connection.

You can create a key-pair with the ssh-keygen command. Generally you need to keep your private key in ~/.ssh/id_rsa (this file must be readable only by you) and any public keys that have access to your login you keep in ~/.ssh/authorized_keys

---

### Post by DeathOnJuice on 2007-03-14
Thanks, everyone! I think I'll use bernied's method, since I've heard of this method of SSH security before. I have a question about generating the keys, though. What does the passphrase that you enter do, and how are the keys generated? Also, how would I configure SSH to use them?

Thanks again, everybody, especially for that bit about stopping it from running at bootup.

---

### Post by bernied on 2007-03-14
> **DeathOnJuice said:**
> What does the passphrase that you enter do,
I think the passphrase is used to encrypt the key.This can make the key a bit more secure, you can't use the key without the passphrase, so it's like having a password as well as the key. Useful if the key is going to be kept on a work machine, for instance. If you're going to be logging in and out all day, you can use an ssh authentication agent to hold your decrypted key. In linux ssh-agent, in windows (if you are using putty), pageant is the agent.
> ...and how are the keys generated?Hmmm, it's some randomness mumbo jumbo (magic to me), but I'm sure you'll find an explanation somewhere.
> Also, how would I configure SSH to use them?
Here's an example /etc/ssh/sshd.conf - I've bolded the important security features. Note that if you implement this before setting up your keys you will not be able to get in through ssh.
```
# What ports, IPs and protocols we listen for
Port 22

**Protocol 2**
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key

#Privilege Separation is turned on for security
UsePrivilegeSeparation yes

# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 768

# Logging
SyslogFacility AUTH
LogLevel INFO

# Authentication:
LoginGraceTime 120
**PermitRootLogin no**
StrictModes no

[B]RSAAuthentication yes
PubkeyAuthentication yes
AuthorizedKeysFile      %h/.ssh/authorized_keys
[/B]
# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hosts
**RhostsRSAAuthentication no**
# similar for protocol version 2
**HostbasedAuthentication no**
# Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
#IgnoreUserKnownHosts yes

# To enable empty passwords, change to yes (NOT RECOMMENDED)
PermitEmptyPasswords no

# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
**ChallengeResponseAuthentication no**

# Change to no to disable tunnelled clear text passwords
**PasswordAuthentication no**

X11Forwarding yes
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
#UseLogin no

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

UsePAM yes
```
I like to change my ssh settings while in a remote ssh session. When you restart the ssh server it does not disconnect existing sessions, so if you mess it up you can have another try or revert to your backup, something like this:
- make a backup 'cp /etc/ssh/sshd.conf /etc/ssh/sshd.conf.working'
- edit the file 'nano /etc/ssh/sshd.conf'
- restart ssh server '/etc/init.d/sshd restart'
- try to start another session (use 'ssh -v user@host' for more detail about the login process)
- does it start properly? if not, then try again, or revert 'cp /etc/ssh/sshd.conf.working /etc/ssh/sshd.conf'

So if your buddy has given you root access (foolish buddy) you can fix his security from your place.

---

### Post by DeathOnJuice on 2007-03-14
Cool. Thanks again!

---

