---
title: "sudo chmod -x .* // nothing is working anymore"
date: 2015-03-31
forum: General Help
---

### Post by jix2 on 2015-03-31
Hi,

I have written this command to remove the +x on hidden files, and now nothing is working, I cannot execute simple commands.

Here is some exaples :

```
sudo chmod +x *
chmod: cannot access &#8216;*&#8217;: No such file or directory
```

> ls
ls: cannot open directory .: Permission denied

I cannot connect by ftp either now

Does somebody has a solution for this ?

Thank you very much !

---

### Post by jix2 on 2015-03-31
Problem resolved with sudo chmod +x .*
Sorry :)

---

### Post by Holger_Gehrke on 2015-03-31
The wildcard '.*' also covers '.' - the current directory. If that was your home directory you've just taken away your permission to change to your own $HOME - you're $HOME-less (sorry, couldn't resist ...). 
```

sudo chmod u+x /home/"your_username"

```
should fix this (replace the obvious...). After this you should give yourself the x-permission for the hidden directories, otherwise a lot of programs might have problems reading their configuration ...

---

### Post by Impavidus on 2015-03-31
.* also covers .. - the parent directory. Removing execute permissions on the directories made it impossible to access the files and directories inside. I don't know of any case in which you want read permission on a directory, but no execute permission.

Now try removing the execute permission from your non-executable files again.

You can mark your thread as solved by clicking "thread tools" &#8594; "mark as solved".

---

