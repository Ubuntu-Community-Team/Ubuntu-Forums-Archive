---
title: "Logging as root via ssh using public keys"
date: 2005-08-15
forum: General Help
---

### Post by igb on 2005-08-15
I want to back up some things from my Ubuntu box using rsync via ssh. In order to do this I need to run rsync as root, so I need to create a public key with no password to let rsync run.

I have done this several times before on computers running other flavours of Linux with no problem. Here's a brief run down of what I do:

Create key pair on mirror computer (banter) using ssh-keygen -t rsa, logged in as root.

Copy the public portion of the key to authorized_keys2 on the primary computer (firewall running Ubuntu).

Chmod authorized_keys2 to 600.

Test it using: ssh -v -i /root/.ssh/id_rsa firewall.banter.local

If I do this using any account other than root, it all works as expected and I can login without being asked for a password.

When I try it using the root account the public key authentication always fails:

debug1: Found key in /root/.ssh/known_hosts:1
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,keyboard-interactive
debug1: Next authentication method: publickey
debug1: Offering public key: id_rsa
debug1: Authentications that can continue: publickey,keyboard-interactive
debug1: Next authentication method: keyboard-interactive

Any ideas why this is happening?

Ian.

---

