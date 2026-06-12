---
title: "auto-login on ftp with ~/.netrc file"
date: 2005-09-26
forum: General Help
---

### Post by bernardfrancois on 2005-09-26
I wanted to be able to use the **ftp** command, so I checked the man pages.
There, I read this:

> 
     -n 

           Restrains ftp from attempting auto-login upon initial connection.
           If auto-login is enabled, ftp will check the .netrc (see netrc(5))
           file in the user's home directory for an entry describing an
           account on the remote machine.  If no entry exists, ftp will prompt
           for the remote machine login name (default is the user identity on
           the local machine), and, if necessary, prompt for a password and an
           account with which to login.

I would have liked to do this, so I checked the netrc man page, where I found:
in netrc man page:

> 
default   

               This is the same as machine name except that default matches
               any name.  There can be only one default token, and it must be
               after all machine tokens.  This is normally used as:

                     **default login anonymous password user@site**

               thereby giving the user automatic anonymous ftp login to
               machines not specified in .netrc.  This can be overridden by
               using the -n flag to disable auto-login.


So I created such such file, and I changed the permissions (ftp doesn't accept the file if other users can read the password).

> 
ber@ubuntu:~$ ls -l ~/.netrc ; cat ~/.netrc
-rw-------  1 ber users 51 2005-09-26 17:25 /home/ber/.netrc
default login bfran password **** [email]bfran@ftp.evonet.be[/email]

(the I replaced the real password with ****) 

When I start ftp, nothing happens, and an **ls** returns **Not connected.**.

After some googling, I also tried other lines, like 
**machine ftp.evonet.be login bfran password **** [email]bfran@ftp.evonet.be[/email]**
and
**machine ftp.evonet.be password **** [email]bfran@ftp.evonet.be[/email]**

But none of them worked.
Can anyone help me with this? And does anyone know how I can see if the program **ftp** actually accesses the **.netrc** file?

---

### Post by bernardfrancois on 2005-09-26
Ok, I just noticed I get connected when I type **open** and **ftp.evonet.be** after starting ftp (in that case, my login and password is automatically entered). However, I want to get connected to my ftp account right after entering the **ftp** command. Is this possible?

[edit] I think I made a mistake. It doens't work. [/edit]

---

### Post by SL666 on 2008-05-25
Doubtful this will help you, but this was the first hit i got when i googled, and i eventually found this link that worked.

[http://www.cyberciti.biz/tips/increase-productivity-with-ftp-autologin-and-macros.html](http://www.cyberciti.biz/tips/increase-productivity-with-ftp-autologin-and-macros.html)

---

