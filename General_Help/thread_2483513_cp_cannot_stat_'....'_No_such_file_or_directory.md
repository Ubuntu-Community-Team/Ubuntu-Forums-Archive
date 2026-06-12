---
title: "cp: cannot stat '....': No such file or directory"
date: 2023-02-01
forum: General Help
---

### Post by exeo on 2023-02-01
When I try to copy a folder from one user to another user on the same machine:

```
sudo cp /home/user/desktop/tranfer /home/user2/desktop/transfer && sudo chown user2:user2 /home/user2/desktop/transfer
```

I get error:

```
cp: cannot stat '/home/user/tranfer': No such file or directory
```


Hope someone can help here. Thanks

---

### Post by QIII on 2023-02-01
Check the simplest thing first:  case.  Are any of the directories below /home capitalized?  For instance, user should be "Tom" but you are using "tom".  How about sub-directories.

I'm not trying to impugn your expertise.  I do stuff like that all the time.

Also, note "tranfer" in one spot in your command and "transfer" in another.  I also misspell things a lot.

---

### Post by exeo on 2023-02-01
Thanks. I corrected the spelling and the capitalizations where needed and now it says:
```
 cp: omitting directory '/home/user/transfer' 
```

---

### Post by exeo on 2023-02-01
Okay. I found the solution here.  [URL="https://askubuntu.com/questions/484707/what-does-omitting-directory-mean-and-how-do-i-make-it-cp-the-directory-rather"]https://askubuntu.com/questions/484707/what-does-omitting-directory-mean-and-how-do-i-make-it-cp-the-directory-rather


[/URL]I needed to add -r after cp

Thanks for your help

---

