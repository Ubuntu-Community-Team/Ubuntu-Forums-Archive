---
title: "replaced motherboard, cant boot"
date: 2007-11-13
forum: General Help
---

### Post by kc0eks on 2007-11-13
Hello all,

I have just replaced a motherboard on my ubuntu system with the same model board (old board was having issues). Now I know the new board likely has some minor differences, but it is the same model and all. 

Asus m2n32 SLI Deluxe
Running Gutsy
and a NVidia graphics card.

Problem is now I cant boot to anything graphical, recovery mode boots ok. Regular boot gives me so many errors (sometimes) I would need a book to list them all out.

Letting it boot normally I do get a graphical log in screen, trying to login just leaves me with a cursor and a black screen.

If I switch to a different console sometimes I can log in, other times I get errors just typing a username.

So do I need to reinstall completely or is their some magical command to fix all this?

Thanks all!

---

### Post by adityakavoor on 2007-11-13
```

sudo dpkg-reconfigure xserver-xorg

```

---

### Post by kc0eks on 2007-11-13
> **adityakavoor said:**
> ```

sudo dpkg-reconfigure xserver-xorg

```

just so happens I just did that...and well it didnt help anything.

---

### Post by adityakavoor on 2007-11-13
sorry, i don kno , try in IRC

---

### Post by gmaniac on 2007-11-13
posting the output of **dmesg** could be useful

---

