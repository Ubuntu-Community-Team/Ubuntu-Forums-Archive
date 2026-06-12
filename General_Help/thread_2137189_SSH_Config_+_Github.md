---
title: "SSH Config + Github"
date: 2013-04-20
forum: General Help
---

### Post by ricomoss on 2013-04-20
I'm trying to create a ~/.ssh/config file to handle multiple ssh users and seem to be doing it wrong.

For my specific problem I'm trying to get a Github account to work correctly.

I have a github account with ```
git@github.com:username/my_project.git
```.

I created a ```
id_rsa_git
``` file (with .pub file).  I uploaded my .pub file to github.

I created a config file with:
```

# github account
Host github.com-test
        HostName github.com
        User git 
        IdentifyFile ~/.ssh/id_rsa_git.pub

```

...and...
```

# github account
Host github.com-test
        HostName github.com
        User git 
        IdentifyFile ~/.ssh/id_rsa_git

```

I try to clone/push with the following command:

```

git clone git@github-test:username/my_project.git

```
or
```

git push

```

and I always get the following error:

```

/home/username/.ssh/config: line 5: Bad configuration option: IdentifyFile
/home/username/.ssh/config: terminating, 1 bad configuration options
fatal: The remote end hung up unexpectedly

```

Any suggestions?

---

### Post by ricomoss on 2013-04-20
I figured it out.  So, it helps when you spell correctly.  ```
IdentityFile
``` not ```
IdentifyFile
```.

---

