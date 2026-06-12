---
title: "how do you not get prompted for ssh passphrase?"
date: 2008-05-02
forum: General Help
---

### Post by chris.olsen on 2008-05-02
I have copied my id_rsa.pub key to the server and put it in it's authorized_keys file. After logging in one the server's key is saved into the local machine's known_hosts file. Unfortunately, I still get prompted for the local passphrase when logging in via ssh to the server.

What am I missing to get around having to type the passphrase all the time? The local machine is really a backup server and to allow the backups be automated I can't have the passphrase prompt popping up all the time.

Thanks for the help.

---

### Post by p_quarles on 2008-05-03
First things first: there is a difference between a password and a passphrase. In the case of SSH, a password would be asked for by the server to which you are connecting, while the passphrase would be requested by the RSA authentication agent.

If it's asking for the RSA passphrase, that means that you configured the key to require a passphrase, and you'll need to create a new one if you don't want that. 

If it's really asking for the user account password, then the problem is most likely either 1) The server-side sshd_config file is configured incorrectly, or 2) Your private key is not in the right place on the client machine.

---

### Post by Slim Odds on 2008-05-03
> **p_quarles said:**
> If it's really asking for the user account password, then the problem is most likely either 1) The server-side sshd_config file is configured incorrectly, or 2) Your private key is not in the right place on the client machine.

Also, make sure the ssh dir has the proper access rights.

I.E. not world readable ( 0700 I think )

---

### Post by chris.olsen on 2008-05-03
> **p_quarles said:**
> 
If it's asking for the RSA passphrase, that means that you configured the key to require a passphrase, and you'll need to create a new one if you don't want that. 
.

That was it.  I could have sworn I always entered a passphrase when prompted for one on other machines where I didn't have this problem.  Is this not less secure?

Thanks for the help

---

### Post by p_quarles on 2008-05-03
> **chris.olsen said:**
> That was it.  I could have sworn I always entered a passphrase when prompted for one on other machines where I didn't have this problem.  Is this not less secure?

Thanks for the help
What the passphrase does is this: it verifies that it is you attempting to access the private RSA key on your machine. If you believe your RSA is at a high risk of being stolen, then passphrase protecting it might be a good idea. If you are confident you can keep it private, and are in a position to deactivate it if something happens (i.e., you have physical access to the server with public key), then it's okay to leave it open.

---

