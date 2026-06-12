---
title: "Beginner Guide for RSA SSH Authentication"
date: 2016-04-28
forum: General Help
---

### Post by ulrichkenneth on 2016-04-28
Hello All, 

I am trying to setup RSA SSH Authentication on my Ubuntu 16 Server. 

On the server, I've ran the following commands
--ssh-keygen
--cp .ssh/* /home/<sshuser>/.ssh
--cp .ssh/id_rsa.pub /home/<sshuser>/.ssh/authorized_keys
--service ssh restart

I'm using a mix of Chrome App MOSH and Secure Shell, yet I'm having difficutly. When I use MOSH and insert the Public Key in the "Add Key" area, It will prompt for the passphrase, yet when I type it in, It will not work and goes to Password Authentication(which I have enable until I can get the RSA SSH Key working properly).

I'm on a Windows 10 Computer using the Chrome App MOSH and Secure Shell

I cannot find a beginner guide for this, and the ones I did find, I am having difficulty understanding, thus why I came here.

Any help on finding a document that a beginner can understand would be great!

---

### Post by deadflowr on 2016-04-28
Seems backwards.
Normally you want to generate the keys on the client, then upload the public key to the server.
rsa auth is enabled on Ubuntu's ssh-server setups by default, if I remember correctly.
So you shouldn't need to do anything more to get that up and running.

On the client when generating the key use the -t rsa option to make sure it doesn't generate a key with some other auth-level, or what not.
(I think it, too, defaults to rsa, but again, not really sure if I remember that correctly)

I think Ubuntu's wiki is as good as you might find on ssh and keys:
[https://help.ubuntu.com/community/SSH/OpenSSH/Keys]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys")

---

### Post by ulrichkenneth on 2016-04-28
> **deadflowr said:**
> Seems backwards.
Normally you want to generate the keys on the client, then upload the public key to the server.
rsa auth is enabled on Ubuntu's ssh-server setups by default, if I remember correctly.
So you shouldn't need to do anything more to get that up and running.

On the client when generating the key use the -t rsa option to make sure it doesn't generate a key with some other auth-level, or what not.
(I think it, too, defaults to rsa, but again, not really sure if I remember that correctly)

I think Ubuntu's wiki is as good as you might find on ssh and keys:
[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

Thank you for that information. My "Client" is Windows 10, and I'm kind of restricted with what I can do(Non Admin). As far as I am aware of, Windows doesn't have a built in way to generate an RSA Key for this, and my understanding of all the "tutorials" may have been wrong as well.

I did see something about using Putty to generate a key, but I can't find a place that goes into each step.

I have an Old Windows 7 computer, but it's not powerful enough to run a VM for me to generate the keys, and with it being my fiancé, I can't reinstall Linux on it.

Would you happen to know any work around on this?

---

### Post by nerdtron on 2016-04-28
Hello, 

you can try this link for generating keys from you Windows machine: [https://support.rackspace.com/how-to/generating-rsa-keys-with-ssh-puttygen/](https://support.rackspace.com/how-to/generating-rsa-keys-with-ssh-puttygen/)

---

### Post by ulrichkenneth on 2016-04-28
> **nerdtron said:**
> Hello, 

you can try this link for generating keys from you Windows machine: [https://support.rackspace.com/how-to/generating-rsa-keys-with-ssh-puttygen/](https://support.rackspace.com/how-to/generating-rsa-keys-with-ssh-puttygen/)

When I follow the directions on that article, I get the error "Disconnected: No supported authentication methods available(server sent: pubkey)".

I've attempted to Google the heck out of this error and can't seem to get it working.

---

### Post by ulrichkenneth on 2016-04-28
> **ulrichkenneth said:**
> When I follow the directions on that article, I get the error "Disconnected: No supported authentication methods available(server sent: pubkey)".

I've attempted to Google the heck out of this error and can't seem to get it working.


I'm not sure what I did, but now I'm getting a "Server refused our key" error on top of the Disconnected: No supported authentication methods available(server sent: pubkey)

I did some modifying in the /etc/ssh/sshd_config file.
ie 
--StrictMode No(was yes)
--Authentication keys directory changed from %h/.ssh/authorized_keys to /etc/ssh/authorized_keys 
--Also changed the Authentication Key directory to /home/<user>/.ssh/authorized_keys

I think the %h/ isn't working right, It's not making the sshd_config look in the home directory of whatever user. I've also tried replacing the %h with %u but same error prior to the "Server refused our key" based error.

---

### Post by ulrichkenneth on 2016-05-09
All, 

I was able to get it working. It appears that I didn't have the username in the "AddUsers" section. It was a noob mistake on my part.

---

### Post by alberttackie on 2016-06-28
> **ulrichkenneth said:**
> All, 

I was able to get it working. It appears that I didn't have the username in the "AddUsers" section. It was a noob mistake on my part.

I can totally out-noob that :KS can you elaborate on what you mean by AddUsers? is this part of a command, to add the user for whom the certificate is created to a particular group? I'm brand new to 16.04/installing a key on it, and have no idea why I am getting that [HTML]disconnected: no supported authentication methods available (server sent: publickey)[/HTML] but no matter what I do, the server is pretty insistent I not be able to ssh in haha. I don't know what on earth I'm still doing wrong.

---

