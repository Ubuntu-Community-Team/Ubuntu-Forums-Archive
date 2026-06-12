---
title: "vi error"
date: 2004-12-16
forum: General Help
---

### Post by jaybee99 on 2004-12-16
on a new install of ubuntu 1.0 launching vi gives me this error:
```

Error detected while processing /usr/share/vim/vimrc:
line   58:
E91: 'shell' option is empty
E484: Can't open file /tmp/v246343/0
Hit ENTER or type command to continue

```
after typing enter it seems to work fine altho' there is no syntax highlighting...?

---

### Post by jdong on 2004-12-16
something is corrupted. Can you open /usr/share/vim/vimrc with another text editor and see if something's weird around line 58?

---

### Post by jaybee99 on 2004-12-16
the if statement on 3rd line of this block is line 58:

```

" Set paper size from /etc/papersize if available (Debian-specific)
try
  if filereadable('/etc/papersize')
    let s:papersize = matchstr(system('/bin/cat /etc/papersize'), '\p*')
    if strlen(s:papersize)
      let &printoptions = "paper:" . s:papersize
    endif
    unlet! s:papersize
  endif
catch /E145/
endtry

```
the file /etc/papersize exists, is owned by root and is just the one line 'a4'

---

### Post by Yani on 2005-01-26
[QUOTE=jaybee99]on a new install of ubuntu 1.0 launching vi gives me this error:
```

Error detected while processing /usr/share/vim/vimrc:
line   58:
E91: 'shell' option is empty
E484: Can't open file /tmp/v246343/0
Hit ENTER or type command to continue

```
after typing enter it seems to work fine altho' there is no syntax highlighting...?[/QUOTE]
 I was getting something amazingly similar.  The part about the 'shell' being empty made me check my /etc/passwd, and sure enough, my useraccount's line did not have the last field specifing a shell in it.  (One wonders why I was able to log in all these weeks...) 

I added /bin/bash to the line, 
su - (myself)
and I no longer get the wierd errors when I launch vi.

(I'm actually on Debian sarge, not ubuntu, but I figured I should post this here 'cause this was all I found when googling my error message)

I think what happened is that I added my user account via `adduser` without first configuring defaults for it.

Yani

---

### Post by jaybee99 on 2005-01-27
thanks a lot Yani, that's the fix :)

---

### Post by Muravei5238 on 2007-05-15
Spam.

---

