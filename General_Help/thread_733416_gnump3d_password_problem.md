---
title: "gnump3d password problem"
date: 2008-03-23
forum: General Help
---

### Post by Sjovan on 2008-03-23
okay, for some strange reason i can't get the password protection to work.

here is some info:
```
sjovan@analplugg:~$ ls -ali /media/Music/
   49154 -rwxrwxr-x  1 sjovan root    15 2007-10-23 19:56 .password
sjovan@analplugg:~$ 

```
as you can see, there is nothing wrong with the .per. on the password file

from the config file:
```
# a password file in the MP3 directory called '.password'.
#
#  (To disable this uncomment the 'enable_password_protection' line).
#
#   The password file should be of the following format:
#
#  username:password
#  username2:password2
#  ...:....
#  usernameN:passwordN
#
#
#  NOTE
#  ----
#
#  The password file must be readable to the user the server is running
# as.
#
###
 enable_password_protection = 0
###

```

```
#  SECURITY OPTIONS.
####

#
#  If there is a user value setup below then the server will become that
# user, after creating the listening socket and after opening the logfiles
# for writing.
#
#  If you want to run this server via init.d, (which has the effect of
# starting the daemon as root), you should make sure you have this set
# to an appropriate value.
#  Otherwise you will have the server running as root, which is clearly
# not a good idea - even in the unlikely event that this application is
# 100% bug free.
#
#  You may comment the line out if you are running the daemon from your home
# directory, and you are the only user with read access to the server root.
# Although this is not recommended way of running the server.
#
#  For the benefit of fellow computer users is recommended that you run the
# server as a user such as 'nobody', and allow people read-only access to
# your audio files.
#
user = gnump3d

```


sooo... any one got a ide?

---

### Post by Biochem on 2008-04-04
I Was asking myself the same question. Here is the answer.

[http://www.gnu.org/software/gnump3d/attacks.html](http://www.gnu.org/software/gnump3d/attacks.html)
> Note: Password protection was removed in 3.0 as being too weak to be useful.

IMHO better weak protection than none.

---

