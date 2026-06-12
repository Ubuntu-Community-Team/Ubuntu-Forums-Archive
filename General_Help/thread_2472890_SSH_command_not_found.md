---
title: "SSH: command not found"
date: 2022-03-15
forum: General Help
---

### Post by kiddalpha on 2022-03-15
Trying to SSH into an AWS instance with user@ and getting command not found.  When I just enter SSH it does return the usage options.  Any ideas?

---

### Post by TheFu on 2022-03-16
Please post your exact command and the client/workstation OS details.

---

### Post by kiddalpha on 2022-03-16
It's on Ubuntu 18.04 LTS
The command being run

SSH -i "~/file-KP.pem" ubuntu@address and it returns SSH: command not found

---

### Post by TheFu on 2022-03-16
Unix systems are case sensitive.  SSH is _NOT_ correct.  ssh is.  Same for all filenames and all directories. 
BTW, I don't think a .pem is allowed as a proper ssh-key file either.

To create an ssh key, [Https://ubuntuforums.org/showthread.php?t=2433034&p=13916386#post13916386](Https://ubuntuforums.org/showthread.php?t=2433034&p=13916386#post13916386)
```
   $ ssh-keygen -t ed25519
   $ ssh-copy-id -i ~/.ssh/id_ed25519.pub username@remote

```Change the username and remote to the correct settings for your remote login.
The ssh-keygen works on Windows, but Windows lacks the ssh-copy-id command for some reason. All Unixen OS have it.

---

### Post by kiddalpha on 2022-03-16
I cannot believe I kept just copy pasting that command in with SSH instead of ssh.  The command ran but now I'm getting Permission denied (publickey) when trying to connect.  The .pem file matches the key name listed on the AWS instance.  Do you still think I should generate the key?

---

### Post by TheFu on 2022-03-16
Did you create a new key on the client and push it over to the remote box using ssh-copy-id?
Without that, you'll be stuck using crappy password-based logins, which should never be used over the internet.

If you have connection issues, try increasing the verbosity of ssh.  **ssh -vvvv <normal other stuff here>** In the verbose output is usually a clear reason for what is failing.

Any my ssh troubleshooting page is here: [https://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections](https://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections)
It isn't for amazon. I've never setup an EC2 install myself, so there could be some differences, but once installed, it is Ubuntu and works like Ubuntu works everywhere ... except I think EC2 enables root, which normal Ubuntu doesn't.

Bed time here. Good luck.

---

### Post by kiddalpha on 2022-03-17
Thanks for your help on this.  I'll continue to work on it.

---

