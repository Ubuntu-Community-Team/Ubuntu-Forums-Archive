---
title: "Noob question: why so difficult to set up an encrypted server?"
date: 2014-08-09
forum: General Help
---

### Post by Cubytus on 2014-08-09
Hi there, 

I had a rather noob question about setting up a plain HTTP server, encrypted on the server. 

I already know it's good practice to secure the connection itself through HTTPS, but found next to no information about encrypting the server's content itself. I assume it doesn't do too much good securing doors and windows while the whole house could be lifted off, which is pretty much what happens when a server is hacked (including by NSA dragnets) or seized. Not that I have very sensitive content, but I do like the idea that my data be completely unreadable should anyone else lay its hands on it.

Now, I have a shared hostspace where I tried to set up an ownCloud install. It being so buggy, it would give mass of errors 500, and would refuse to enable the encryption plugin. But its mere existence led me to think that server-side encryption would be possible, without requiring root access to the server.

Am I missing something fundamental as to why server encryption (including MySQL databases) would be so rare? Are developers simply not worried enough to include such capability? Or is server encryption inherently weak?

---

### Post by TheFu on 2014-08-10
Anyone can encrypt any file at any time that they want, but it will probably be easily hacked.  It isn't that encryption is hard, it is that doing it well, so that it cannot be hacked is extremely difficult.

So - let's step back to your desire. You want to make files encrypted, but allow access to that data (unencrypted) to anyone.  That means that either the files are stored AND transferred encrypted (the client-side does the decryption) or the file storage is decrypted so the server process can transmit the files unencrypted.  That means when the server is powered on, the files are not encrypted, though they are when on disk. This last case means that only when the system is off will the files be inaccessible to the root user.

If the server is rebooted, should the encrypted storage be automatically mounted?  If yes, then whenever the server is running, all that effort to encrypt is useless.  Of no, then the server trying to access the encrypted storage will hang/or fail until someone provides the decryption key - and then it is available to anyone (root).

There are documented attacks against linux encryption when physical access to the system is provided. 

So ... what is the point?  Well, only client-side encryption can really be secure. The server doesn't need to store anything encrypted at all and that would also mean that the server doesn't need to be involved with storage encryption.

Oh ... and if you care about security, using any program written in php on the internet is probably not a good idea. The base language implementation has 2x more security issues than other popular languages and the core php development team has shipped a new release with known critical flaws more than once rather than delay for a week and fix them.  Php webapps should only be accessed through a proper VPN (IPSec or openvpn), IMHO.  

Encryption of an entire DB with 1 key isn't really all that useful for the same reasons that encrypting storage with 1 key isn't.  I don't think mysql does record level encryption, like the big DBs do - which is why reputable financial institutions don't use it.

There are many holes in my statements - hopefully smarter folks will reply and point out everything I got wrong. ;)

I didn't look into owncloud recently - did about 18 months ago.  However another tool, similar, [http://seafile.com/en/help/security/](http://seafile.com/en/help/security/) appears to support client-side encryption, doesn't use php, and might be helpful for your end goal?  I dunno.  [http://doc.owncloud.org/server/6.0/user_manual/files/encryption.html](http://doc.owncloud.org/server/6.0/user_manual/files/encryption.html) says that owncloud encryption module happens on the server side, which isn't what you really want, is it?

---

