---
title: "zsh will not run scripts as /bin/bash"
date: 2012-11-24
forum: General Help
---

### Post by graysky on 2012-11-24
Been using zsh for a while now and loving it.  I ran into a problem today.  The following script errors out if run with zsh as my default shell:

```
#!/bin/bash

v_build() {
	echo "The file is $1"
}

export -f v_build
find . -maxdepth 1 -type f | parallel v_build
```

Output:
```
% ./test 
zsh:1: command not found: v_build
zsh:1: command not found: v_build
zsh:1: command not found: v_build
zsh:1: command not found: v_build
```

If I switch to a user who has bash as its default shell, the same script runs just fine:

```
$ ./test
The file is ./test
The file is ./01.jpg
The file is ./02.jpg
The file is ./03.jpg
```

Love to understand what I have incorrectly configured.  It seems like zsh is ignoring the shebang telling it to use /bin/bash as the shell to run the script.

---

### Post by dcstar on 2012-11-24
> **graysky said:**
> .........
Love to understand what I have incorrectly configured.  It seems like zsh is ignoring the shebang telling it to use /bin/bash as the shell to run the script.

The paths are probably different.

---

### Post by codemaniac on 2012-11-26
Have you tried giving the full path of zsh to shabang instead of (#!/bin/bash).
you can determine the full path name by using 
```
which zsh
```

---

### Post by haziz on 2013-04-07
> **graysky said:**
> Been using zsh for a while now and loving it.  I ran into a problem today.  The following script errors out if run with zsh as my default shell:

```

#!/bin/bash


```

.....
 
Love to understand what I have incorrectly configured.  It seems like zsh is ignoring the shebang telling it to use /bin/bash as the shell to run the script.

Try setting the "#!" shebang to point to zsh instead:

```
#!/bin/zsh
```

Do you actually have bash installed? I presume yes unless you have deliberately uninstalled it.

---

