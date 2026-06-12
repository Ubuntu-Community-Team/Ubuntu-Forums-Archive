---
title: "Program changes in edgy"
date: 2006-12-15
forum: General Help
---

### Post by jdavis72 on 2006-12-15
I have noticed that two separate programs are behaving differently from dapper to edgy. In Edgy, in vi (link to vim.tiny), when in insert mode, the backspace key on my keyboard only moves the cursor left, not deleting the characters, using the arrow keys inserts capital letters instead of moving the cursor (up inserts "A", down inserts "B", right arrow inserts "C", and left arrow inserts "D", you have to escape from insert mode for the arrow keys to move the cursor), the delete key only deletes the character the cursor is on, not removing all characters to the right of the cursor. Instead, using vim (still a link to vim.tiny) these problems go away. Why? Both vi and vim link to vim.tiny.

Also, the find command is acting a little weird. When I search the directory I'm currently in, I sometimes (not always) get the error "find: paths must precede expression". For example, I have some file names in my home directory that start with "tr". Now, entering the command "find ~ -iname tr*" gives me that error. However, adding letters to the argument (thereby narrowing the search field) finally prints out the list like normal. Also, moving out and up the directory tree seems to fix it.

Are these broken binaries, some config file I'm missing, or what? Thanks in advance!

Jeremy

---

### Post by taurus on 2006-12-15
1.  
```
sudp aptitude update
sudo aptitude install vim-full
```

2.  
```
find ~/ -iname tr*
```

---

### Post by Lord Illidan on 2007-01-04
> **taurus said:**
> 1.  
```
sudp aptitude update
sudo aptitude install vim-full
```


Hey thanks, taurus, I was searching for this too. Why can't this be added by default? I was wondering whether vi was broken in Ubuntu.

You have a mistake there, though..

it should be sudo aptitude update

---

