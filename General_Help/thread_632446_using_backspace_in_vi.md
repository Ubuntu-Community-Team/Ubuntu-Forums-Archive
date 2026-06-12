---
title: "using backspace in vi?"
date: 2007-12-05
forum: General Help
---

### Post by sternkanz on 2007-12-05
Hi, I happened to have to do some quick perl editing in vi. I tried pressing backspace but instead of deleting a character it just moves the cursor one character to the left. Also when I press any of the arrow keys I get capital letters like A for the up arrow, B for the down arrow, C for the right arrow and D for the left arrow. Is there any way I can disable these? Has it something to do with my keyboard settings? 

My keyboard is a german laptop layout and when I installed ubuntu and did the testing to make sure the keys were all in the right places it seemed to work fine.

Thanks for any help!

---

### Post by metalheart on 2007-12-05
Run vim instead of vi.

---

### Post by sternkanz on 2007-12-05
Oh, thanks! I don't suppose you know how to switch on the syntax colouring for perl too? I know my uni has these all set by default but I have no idea if I can do this on my machine?

---

### Post by metalheart on 2007-12-05
Install vim-perl - enhanced vi editor - with Perl support
```
sudo apt-get install vim-perl
```
I don't know the perl file extension, but you may have to include it in the filename.

---

### Post by sternkanz on 2007-12-05
I've installed it, but how do I use it? Sorry but i'm still pretty new to linux in several aspects.

---

### Post by pointone on 2007-12-05
In normal mode, type:

```
:syntax on
```

---

