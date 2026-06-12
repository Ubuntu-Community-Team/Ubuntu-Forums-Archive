---
title: "VIM and FTP Question"
date: 2007-02-23
forum: General Help
---

### Post by Mars8082686 on 2007-02-23
Hi, recently I've been trying to get more familiar with *nix and therefore have started doing most of my web development via the terminal. Anyways I find my self doing the same repetitive tasks and I know there must be a more effiecent way. I start by opening an FTP connection, then I "!" out and start editing my php file. Once I'm done I exit the shell to go back into FTP, however by that time my connection has expired and I have to start another one. I was wondering if there was a way I could save my username/password, and just be able to do a simple " : put" from vim or something and put my file on the server. Or if there is any other way to do this repetitive task more efficiently.
Any Advice?

---

### Post by Mars8082686 on 2007-02-24
I tried
ftp open hostname.com /user:Myusrname /password:Mypassword
and I got this error message:
usage: ftp host-name [port]

---

