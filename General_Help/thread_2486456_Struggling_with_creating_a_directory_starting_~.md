---
title: "Struggling with creating a directory starting ~"
date: 2023-05-01
forum: General Help
---

### Post by grl570810 on 2023-05-01
Not exactly a newbie, but returning to *nix after a thirty plus year absence so my skills are rusty.
Simple question. Possibly not simple answer?
I need to create a directory inside a website (under /var/www) named precisely ~f.  (A long story, don't ask, I know it's a bloody stupid name for the directory but it's out of my control).
All attempts so far have failed, I've tried escaping it (\~f), quoting it "~f" and '~f', or just typing ~f. No luck it either creates the directory with the name showing in ls -lasi as just f  or as '~f' and neither work when trying to open an html file in the folder (I get a 403 forbidden back from the nginx service).
Please can some one advise a) IF this can be done and b) if so HOW (please provide explicit command syntax)?
I know this is very basic but it's doing my head in. I'll be eternally grateful if someone can fix this for me.
Environment is Ubuntu Server 22.04 LTS, using bash shell.

---

### Post by The Cog on 2023-05-01
> or as '~f'  is correct if you're doing ls. This is because ls knows that you're in a command shell, and helpfully adds the quotes (or backslashes) if they are needed to re-enter the filename. If you were to use a file browser then you will see the filname correctly in the GUI.

Having created the directory, you will need to pay attention to the ownership and permissions of the directory and the files inside it. I have a feeling that they must be owned by user enginx for the web server to be able to read them. Look at the other files inside /var/www to see what is normal. Additionally, they should be read-only so that it's harder for any exploit of enginx to modify the content being served.

---

### Post by TheFu on 2023-05-01
mkdir /path/to/~f

If it doesn't work, then I suspect it is a permissions issue or you are using a relative path and there's a username "f" on the system.  
$HOME == ~
$HOME == ~/
/home/john == ~john (usually)
For many shells, the "~" character says to perform a "getent passwd" command for the following username and return the HOME directory entry from the password DB.  On single user user systems, that can be the same as looking in /etc/passwd, but some people use LDAP for their user/group databases, so 'getent' is safer.

This works:
```
:~$ cd /tmp/
:/tmp$ mkdir ~f
:/tmp$ cd ~f
:/tmp/~f$ ls
:/tmp/~f$
```

---

### Post by grl570810 on 2023-05-02
Thanks for the replies guys. I think the trick was to create it using  the full path as the name rather than just trying to create it from the  parent directory.  I was trying just mkdir '~f'  and failing, but mkdir  '/var/www/domain.tld/htdocs/~f' worked just fine. One to file away in  the memory banks.....

---

### Post by TheFu on 2023-05-02
Please mark this thread as **SOLVED** using the "Thread Tools" button to help others in the community save time.

---

