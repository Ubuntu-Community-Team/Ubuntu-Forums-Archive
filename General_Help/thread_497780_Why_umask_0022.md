---
title: "Why umask 0022?"
date: 2007-07-10
forum: General Help
---

### Post by bmagyarkuti on 2007-07-10
Hi, I have just understood the umask + user rights system, and I just couldn't figure out why ubuntu sets umask to 0022 by default.

This way, the users on the same computer have read acces to the other user's files... isn't this EXTREMELY insecure? Why isn't umask set to something more secure, like 0027 by default, at least on the user level (~/.profile)?

I don't mean to be niggling,  it' just...  it would be great to know :). Any ideas on this?

---

### Post by bmorency on 2007-07-10
> **bmagyarkuti said:**
> Hi, I have just understood the umask + user rights system, and I just couldn't figure out why ubuntu sets umask to 0022 by default.

This way, the users on the same computer have read and execute acces to the other user's files... isn't this EXTREMELY insecure? Why isn't umask set to 0027, by default, at least on the user level (~/profile.conf)?

I don't mean to be pushy, it' just it would be great to know :). Any ideas on this?

i checked my home folder and I do not have profile.conf in there. did you make that file if not why would I be missing it?

when i make a file in my home folder the permissions are set to 644 which would mean the umask is different than yours.

---

### Post by bmagyarkuti on 2007-07-10
It's simply ".profile" - sorry for mistyping, I've corrected it in the original post.

644 means that your umask is set to 0022: the default setting (You can check your umask value by typing umask to the shell.).
Anyway, 644  is exactly my problem: the last "4" means read access for "others" - not exactly my idea of a home folder.

---

### Post by bmorency on 2007-07-10
what you want to do is try this:

sudo dpkg-reconfigure adduser

you can set it so home directories are not readable when a new user is added,

---

### Post by bmagyarkuti on 2007-07-11
I understand that I can set these settings, I know how to do so.

I was trying to figure out why the defaults were so insecure - I thought the developers were trying to help users with keeping their data safe.

---

### Post by jimbob on 2007-07-11
I think a umask of 022 results in 755 or rwxr-xr-x for files, not 644 which would be rw-r--r-- unless I am mistaken.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

---

### Post by bmagyarkuti on 2007-07-12
One is for directories, the other is for files...

I still don't really understand why the last digit is not set to "0" by default...

---

