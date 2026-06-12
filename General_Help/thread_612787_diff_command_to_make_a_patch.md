---
title: "diff command to make a patch"
date: 2007-11-14
forum: General Help
---

### Post by Tex-Twil on 2007-11-14
Hello,
I would like to know how I can specifiy the file **types** which are affected by the diff command. I would also like to know is it's possible to exclude some **specific** files from the from the diff command.

The idea is that I'm working on a C project which is a extension for openssl. I have imported the whole openssl sources directory as a project. Now I want to make the diff between my project directory and a "fresh" extracted openssl sources.  Therefore, I'd like that diff reads only .h and .c files.

I tried the command with the following params:
```

diff -rBNu openssl-0.9.8c MYopenssl098c > my.patch

```

The problem is that the patch includes also  some "new" files witch I don't want such as .bak files The specific files I want to exclude are files like config.h which are generated froö the ./configure command.

Thanks for your help.

regards,
Tex

---

### Post by Tex-Twil on 2007-11-14
Ok, I think I've found a nice guide to use the diff command :
[http://www.network-theory.co.uk/docs/diff/Comparing_Directories.html](http://www.network-theory.co.uk/docs/diff/Comparing_Directories.html)

In my case, the -x options does perfectly what I want !
;)

---

### Post by Tex-Twil on 2007-11-14
Ok, everything is not solved yet. The -x parameter allows to exclude files that match the pattern. The problem is that I have some files with the same filename and I want to apply diff only to one of them.

For example, I have several MakeFile files in defferent directories and I want diff to look only at one of those (orexclude all the other). Any ideas ?

Thanks,
Tex.

---

