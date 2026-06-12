---
title: "umask Modification Misbehaving"
date: 2014-08-19
forum: General Help
---

### Post by clalian on 2014-08-19
Hello everyone,
I have a user I want to modify the umask for him.
Lets call this user user3.

I modified /home/user3/.bashrc
At the very end of the file, I added the line:
umask 0002

I then did a fresh login as user3.
Once logged in, in the command line, I typed:
umask

And it came back:
0022

Any idea what could be going on?
I don't understand what is going on.

Am I missing something?
Do "group permissions" supersede user permissions?

Looking forward to your suggestions and help!
:)

---

### Post by clalian on 2014-08-19
Issue has been solved.

For the benefit of others:
The user was loggin in via ftp. 
Well, I am running vsftp on my server.

So vsftp has its own umask setting at /etc/vsftpd.conf
Go in there, modify the file (look for the line umask).
Change it to what you want. 
Restart vsftp with  service vsftpd restart
And you are done.

Hope this helps someone.
:)

---

