---
title: "Public one-time-password account"
date: 2014-02-19
forum: General Help
---

### Post by fra_87 on 2014-02-19
Hello everybody
I'm here to ask if you know if there is something suitable for me.
Here it is. I have a PC (debian is the OS, but this can also apply to a lubuntu-PC and a xubuntu-PC i have) and i am the administrator. I'd like to create a public user to share some functionalities (e.g. SFTP); this user, however, should have a one time password managed by me. This way, when i want to give access to someone, i login with my own account, create a password for the public user and give it to the one i want to grant access to, then when he logs in the password is destroyed (and, in order to gain access again, i have to generate another password).
What do you think? Is this feasible? How?
If there is no programs that can do this i think that the only alternative is to change the password twice (first to give it to the other one, then to "reset" using a random password just to prevent logins).

Bye and thanks a lot!

---

### Post by dragonfly41 on 2014-02-19
I would look to bouncycastle for ideas ...

[https://www.bouncycastle.org](https://www.bouncycastle.org)

e.g.

[http://stackoverflow.com/questions/2194222/java-me-md5-string-using-bouncy-castle-cannot-hash-multiple-times](http://stackoverflow.com/questions/2194222/java-me-md5-string-using-bouncy-castle-cannot-hash-multiple-times)

---

