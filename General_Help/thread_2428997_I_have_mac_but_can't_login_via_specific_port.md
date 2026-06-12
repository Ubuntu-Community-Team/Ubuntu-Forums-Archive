---
title: "I have mac but can't login via specific port"
date: 2019-10-12
forum: General Help
---

### Post by buyusardp on 2019-10-12
Hello,

Please guide me how to login from MAC to ubuntu server, I have set the port to xxxx

I type ping username@IP:1122 and it doesn't work for me.

Regards

---

### Post by TheFu on 2019-10-12
Ping isn't a remote login tool. It is a basic, IPv4 'are you alive' testing tool. That's all ping does.  There are thousands of different protocols. Each has a different purpose.

In general, unix systems all should use ssh for remote logins, remote file transfers, backups, and any sort of remote desktop.  [https://en.wikipedia.org/wiki/Secure_Shell](https://en.wikipedia.org/wiki/Secure_Shell) explains more about ssh.

Setup ssh on both systems.  There is a meta-package on Ubuntu, ssh, that includes both the client and the server. I have no clue what Apple calls ssh. They have a habit of renaming standard things to something Apple-funky.

Setup fail2ban to prevent brute force attacks on both - I don't know if OSX supports this or not.

I would do this on the ubuntu machine:
```
sudo apt install ssh fail2ban
```
After you get ssh installed on the OSX machine, use somethign like this in a Mac terminal:
```
ssh username@IP
```
When asked, enter your ubuntu password.

You should see the normal prompt with a *userid@hostname:current directory$ *. From there, you can run shell commands.  No GUI stuff.

If you want the connection to be more secure AND more convenient, then setup ssh-keys between the client and the server.  I don't know the specific details on OSX, but on all other Unix systems, we use these 2 commands:
```
ssh-keygen -t ed25519
ssh-copy-id -i ~/.ssh/id_ed25519.pub username@remote

```

If you want to be more convenient, you can setup a ~/.ssh/config file on the client and provide an alias for the remote system:
```
host brians
  user user8874    
  hostname thebrians.com
  port 63428 
```

The "hostname" entry can be an IP address or some funky DNS name (like all cloud providers give, but we always just type **ssh brians** to have the *user8874@thebrians.com* and non-standard port used for all ssh-based connections.  There are about 50 other tools which use ssh, so this is a huge time saver. They use of ssh-keys means it is both more secure AND more convenient.  That never happens.  ssh-keys are the only example I know in the world that works this way.

Clear as mud?  You'll need to get OSX specific instructions somewhere else.

Also, if you need to use a non-standard port and don't want to use the ~/.ssh/config file, then the ssh manpage explains that option.  Does OSX have manpages?

---

