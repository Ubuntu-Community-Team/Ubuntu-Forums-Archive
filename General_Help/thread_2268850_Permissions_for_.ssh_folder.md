---
title: "Permissions for .ssh folder?"
date: 2015-03-11
forum: General Help
---

### Post by michael260 on 2015-03-11
Hello all.
I was attempting to configure openssh-server to work with RSA keys, but by following a tutorial, I changed the permission for the .ssh folder to 700, I alos executed the command chmod go-w ~/, so can someone please explain what this does, and if it coauses any problems with sshing, how would I fix it? Also, I have uninstalled openssh-server as of now. I am running Ubuntu 14.04.
Thanks.

---

### Post by CaptainMark on 2015-03-12
chmod 700 will mean for that folder you have permissions to read write and execute whilst no one else has any of those permissions.
chmod go-w ~/ will remove write permissions to your home folder for everyone but you (This one is a bit pointless, they shouldn't have write permissions to start unless you've made things that way intentionally)

I don't think any of these commands are causing your issues.

Do you get any error messages? You'll need to reinstall openssh-server for us to help you further, then try using ```
ssh localhost
```to confirm your server is running. If its running okay, you'll be asked for your password and just see another command prompt, if its not running you'll get connection refused errors or no route to host errors

---

### Post by efflandt on 2015-03-12
The 700 permission for ~/.ssh is so that only you can do a directory listing (ls) on it, and any files in it should have 600 permission so only you can even read-write files (in other words: **chmod -R go-rw ~/.ssh**). Note that sshd running as root can still read that to log you into that computer. For security reasons you might not be able to log in if sshd thinks anyone other than you can read or change any files in your ~/.ssh (on ssh client or ssh server). So you need same permissions for ~/.ssh and anything in it including your private key on the client and your public key on the server.

Note that if **StrictHostKeysChecking** is **yes** (instead of ask or no) in your client /etc/ssh/ssh_config or ~/.ssh/config, a new host you try to connect to will not connect and will not be added to ~/.ssh/known_hosts. If StrictHostKeysChecking is ask, it should first ask if you want to connect to the host if its host key is new or changed.

Running ssh with -v option may tell you more about what is failing.

---

