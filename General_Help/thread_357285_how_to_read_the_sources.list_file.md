---
title: "how to read the sources.list file?"
date: 2007-02-09
forum: General Help
---

### Post by zhouray on 2007-02-09
Hi everyone,

I am a Linux newbie just started using Ubuntu a month ago. I would like to know about the sources.list file, but couldn't find what I was looking for in here or Google. So I shall ask my first question in this forum:

say, for this line
```

deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse

```

When I go to [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu), I have to go to the "dist" folder before I can reach the "edgy-security" directory. How does apt knows to find the "edgy-security" directory under the "dist" directory?

And, why are the directory named main, restricted, universe and multiverse? What do they mean?

```

deb http://some.repo.somewhere word1 word2 word3 word4 
```

How does apt parse the file? are ** word2, word3, word4** always a subdirectory of **word1** ? What if I want to include only some, not all,  files in directory **word2**, How do I do it?

I am not sure if anyone understand my questions. I am just so confused every time I encounter the sources.list file and I wanted to know what exactly I am doing when I modify the file. Any help would be appreciated. Thanks.

Ray

---

### Post by fenian on 2007-02-09
double post sorry.

---

### Post by fenian on 2007-02-09
This link has some good info for you...

[https://help.ubuntu.com/community/Repositories](https://help.ubuntu.com/community/Repositories)

Read the sections on managing repositories and all the further reading links.

---

### Post by zhouray on 2007-02-09
Thanks for the great link (still reading). It is exactly what I am looking for. Thanks.

---

