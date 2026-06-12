---
title: "How do i open .rar files?"
date: 2007-02-10
forum: General Help
---

### Post by mikeaguilar1 on 2007-02-10
Guys I just got Unbuntu like  2 days ago. I like it and all but need some help, I got a file that i would normally (on windows) use winrar to open... How do i open it using linux?

---

### Post by Maestro23 on 2007-02-10
[http://www.ubuntuforums.org/showthread.php?t=356828&highlight=unrar](http://www.ubuntuforums.org/showthread.php?t=356828&highlight=unrar)

Might need to enable extra repositories: [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by ~LoKe on 2007-02-10
In the Terminal:
```
sudo apt-get install unrar
```
```
unrar x file.rar
```

Assuming you have the multiverse repository enabled (uncommented).  I think that's where it is.

---

### Post by maddog39 on 2007-02-10
Well this is a very simple and easy problem to fix, just run:
```

sudo apt-get install unrar

```Then do; Right Click > Extract Here and it should extract. If that doesnt work then just run:
```

unrar x /path/to/file.rar

```In terminal and it should do the same thing.
[Edit]
lol, 3 people responded when I was typing this post, oh well...

---

### Post by mikeaguilar1 on 2007-02-10
Thankx guys but i am very new to this. I still cannot even figure how to install it.

alrite i downloaded 'unrar" 

then it downloaded to my desktop i right clicked on it and selected "extract here" 

then it gave me a folder, I opend it and now have no idea how to install it. please help.

---

### Post by mikeaguilar1 on 2007-02-10
fellas this is are far as i can get please help

> mike@mike-desktop:~$ sudo apt-get install unrar
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package unrar is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package unrar has no installation candidate
mike@mike-desktop:~$ sudo apt-get install unrar
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package unrar is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package unrar has no installation candidate
mike@mike-desktop:~$ 



---

### Post by Maestro23 on 2007-02-10
> **mikeaguilar1 said:**
> fellas this is are far as i can get please help

Have you enabled extra repositories like I posted earlier?

What does your /etc/apt/sources.list look like?

> #cat /etc/apt/sources.list

Past the output here.

---

