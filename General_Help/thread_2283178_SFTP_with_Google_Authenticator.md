---
title: "SFTP with Google Authenticator"
date: 2015-06-19
forum: General Help
---

### Post by Vaindil on 2015-06-19
I'm using Google Authenticator for additional security for SSH connections on my installation of Ubuntu 14.04, and I like the feature. However, the problem I've come across is that I have to re-enter an authentication code every single time I initiate a new file transfer over SFTP. I enter the code and my password once when I log in, which is how it should be, but when I actually transfer the file(s) over ten seconds later I'm prompted for another code and my password again. If I have to navigate to a different directory on my computer to grab a different file to upload, I'll be prompted *again* to enter a code and my password to upload it, even if it's the *same code I just entered*.


Did I possibly do something wrong when I set up Google Authenticator? I followed [these instructions](https://www.digitalocean.com/community/tutorials/how-to-protect-ssh-with-two-factor-authentication) and my server is completely up-to-date. I'm on Windows 8.1 using FileZilla 3.11.0.2 (the latest as of this post). FileZilla is set to Interactive authentication, as I understand it needs to be to work with 2FA (or is this incorrect?).


Is this intended behavior for 2FA with Google Authenticator on Ubuntu 14.04, or should I be able to enter my code once and have it remembered for the length of my session as with standard SSH (and with SFTP via FileZilla in the past)?

---

### Post by Elizine on 2015-06-19
Here's a guide to secure SSH connections with Google authenticators two factor authentication - [http://www.howtogeek.com/121650/how-to-secure-ssh-with-google-authenticators-two-factor-authentication/](http://www.howtogeek.com/121650/how-to-secure-ssh-with-google-authenticators-two-factor-authentication/)

---

### Post by CharlesA on 2015-06-25
> **Vaindil said:**
> I'm using Google Authenticator for additional security for SSH connections on my installation of Ubuntu 14.04, and I like the feature. However, the problem I've come across is that I have to re-enter an authentication code every single time I initiate a new file transfer over SFTP. I enter the code and my password once when I log in, which is how it should be, but when I actually transfer the file(s) over ten seconds later I'm prompted for another code and my password again. If I have to navigate to a different directory on my computer to grab a different file to upload, I'll be prompted *again* to enter a code and my password to upload it, even if it's the *same code I just entered*.

Which client are you using? FilaZilla, for example, initiates a new connection for each file it transfers.

It sounds like you set everything up correctly, but the sftp client you are using is probably the root of the problem.

Have you try using sftp from a terminal and seeing if it exhibits the same issues?

---

