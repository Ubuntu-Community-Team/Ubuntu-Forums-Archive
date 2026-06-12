---
title: "chown recursion question"
date: 2005-05-13
forum: General Help
---

### Post by limewolf on 2005-05-13
I'm just trying to change permissions for some user directories on a system I have recently changed over to ubuntu. I need to recurse all the hidden directories so I do the following (as root):

chown -R bob /home/bob/.*  

...trouble is this seems to cause it to recurse the "../" directory and so it appears to recurse the other user directories - this seems a bit odd to me, but I guess it is behaving as it should?

I have verified that the permissions get changed on the other users home directories (i.e. they all end up owned bu "bob" in the case above). 

This is probably a silly quesion but can anyone explain what I should be doing to just change the permissions for each users home directory (including hidden firles/directories)?

Thanks!

---

### Post by Sam on 2005-05-13
It this what you need ?
Execute 'chown -R bob' on every directory (recursive) from your current directory:
```
$ find . -type d -exec chown -R bob {} \;
```

These commands are helpful:

List every directory from your current directory in the terminal:
```
$ find . -type d
```
List every file from your current directory:
```
$ find . -type f
```
List every hidden directory (non recursive) from your current directory:
```
$ find . -maxdepth 1 -type d -name '.*'
```

Hope this helps ?

---

### Post by limewolf on 2005-05-14
Many thanks, those are a lot of help. Problem solved.

---

