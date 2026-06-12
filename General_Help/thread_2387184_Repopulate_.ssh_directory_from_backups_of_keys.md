---
title: "Repopulate .ssh directory from backups of keys"
date: 2018-03-15
forum: General Help
---

### Post by Sam_Williams on 2018-03-15
** Update - I've solved the issue below before I got round to posting... but I thought I would post anyway with the answers in case it helps someone else in the future ** 

Hello,

I normally do passwordless ssh into a server, but have had to do an unexpected reinstall on my laptop following a h/w failure. Whilst I had a fairly recent tarball of my home directory, for some reason it didn't include my .ssh directory (or any other hidden items).
Thankfully, I've got the content of my private and public keys saved somewhere else (plus fingerprint and randomart image), and would like to recreate the files that were in my .ssh directory using these, but don't know quite how to do this.
So, my questions are:
1) Does the .ssh directory has any other directory structures below it? 
**** No, the keys just go in the top level of the .ssh directory ****
2) When creating files from the keys, do I include the header lines like "-----BEGIN RSA PRIVATE KEY----" or just go straight to the block of characters?
**** Yes, this seems to work with the header line included ****
3) What are the files containing the private and public keys named, and is there some way of registering them with ssh (or will it just look for a key named username@machine when I try to connect)?  
**** 'id_rsa' for the private key, 'id_rsa.pub' for the public key - and you will be asked for the private key passphrase when trying to log into the server for the first time using these keys ****

Cheers,

Sam

---

### Post by TheFu on 2018-03-16
Those are good starts, but not 100% accurate.
1) The location of config files and other files is completely up to you. Using the default ~/.ssh/ might not be what you want, especially if you are security conscious.
2) The ssh-keygen tool will create the files you request.  Do not edit those files.  Changing the files periodically is a good security practice.
3) There is a xxx.pub and xxx - sans extension file created by ssh-keygen.  These can be named anything you like.  Using different key files for different server connections **is** a best practice.  Also, rsa-based keys might not be secure enough for all purposes.  Might want to use ed25519 instead.

Using a personal config file makes handling connections easier. The config file is honored by every ssh-using tool that I know. sftp,scp, sshfs, rsync, rdiff-backup ... I've never had to do anything special to get it honored.  

ssh is crazy-flexible for all sorts of needs.  The manpage for it and each of the config files are pretty detailed and amazing. Highly recommended reading.  I learn something new with each re-re-re-read.  Today I learned about the ~/.ssh/rc capability. Nice.

Defaults are usually good for a working system, but might not be the best from a security standpoint.  That applies with almost all services. Just look at what the defaults for memcache have done the last 2 weeks.

---

### Post by Habitual on 2018-03-16
Not every private key has a password.

---

