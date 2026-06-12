---
title: "ASCII chars in terminal / C program"
date: 2006-08-08
forum: General Help
---

### Post by immesys on 2006-08-08
This is also a bit of a programming question. I am using the normal terminal on ubuntu (not in X... the traditional one). I can use aptitude and other curses apps fine. But when I try use the ascii box drawing characters like (&#9580;&#9578;&#9576;&#9560;&#9560;) then nothing comes out.

for instance, this C snippet prints nothing but the normal alphabet and some punctuatuon:

```
int i;
for (i=0;i<255;i++){
    printf("%i: %c",i,i);
}
```

Do you know how I can get it to work? Thanks!

---

### Post by immesys on 2006-08-08
The very rudimentary ones are available as macro's in curses.h.. they start with ACS_ , for instance ACS_ULCORNER is the upper left corner character.

I have found this out so far... but while some of those characters work on my pc when I access it from windows using putty, they don't work on the actual terminal.

Is there any way I can change the terminal so that it supports a wider character set? Like maybe changing the font?

---

