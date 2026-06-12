---
title: "Where to put aliases"
date: 2016-07-22
forum: General Help
---

### Post by 4kh3RAm on 2016-07-22
Usually I put aliases in .bashrc.

Would I put this in bash.bashrc ?

```
clear;alias full='ls -l -a -t --color=never  | more'
```

---

### Post by papibe on 2016-07-22
Hi 4kh3RAm.

Yes. That's a good place.

If you want your 'full' alias to clear the screen before the ls command, you need this instead:
```
alias full='clear; ls -l -a -t --color=never  | more'
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by 4kh3RAm on 2016-07-22
Thanks it works. 

But it also gives this

> [3;J
ls: cannot access '.gvfs': Permission denied

---

### Post by papibe on 2016-07-22
Could you run this command, and paste back the result?
```
grep full ~/.bashrc
```

---

### Post by 4kh3RAm on 2016-07-22
andy@7:~$ grep full ~/.bashrc
alias full='clear; ls -l -a -t | more'

---

### Post by papibe on 2016-07-22
Thanks. It looks OK.

Now, the next time you open a terminal, the alias will be valid.

As for the current terminal, you may still have a previous version of the alias. You can test it by running:
```
alias | grep full
```
In order to get the one on the file, you can either close the terminal, and open another; or you can 'source it':
```
source ~/.bashrc 
```
Hope it helps. Let us know how it goes.
Regards.

P.S.: the error seems to be coming from the ls command itself, not the alias. Let us know if you want to tackle that.

---

### Post by 4kh3RAm on 2016-07-22
Neither made any difference.

The extra stuff on top is no big deal.

Before I put the alias in .bashrc in my home directory,
I put it in another .bashrc.XXX file.

But I can not find it.

---

### Post by deadflowr on 2016-07-22
For what it's worth, you can make a file for just the aliases called ~/.bash_aliases.

I find it easier to manage them that way.

---

### Post by 4kh3RAm on 2016-07-22
Something for me to consider.

---

