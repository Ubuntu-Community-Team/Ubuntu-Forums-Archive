---
title: "Ubuntu help needed with Pipe."
date: 2013-11-26
forum: General Help
---

### Post by lucas12zarzur on 2013-11-26
O “pipe” é igual ao “>”? Justifique.  The "Pipe" is equal an ">"? Justified. HEELP me?

---

### Post by jdeca57 on 2013-11-26
It's about redirection of the output of a program in a terminal, like
ls > out.txt
and then
cat out.txt
gives you the output of the ls command.
But honesty, I don't read Spanish (?) that well...

---

### Post by germanix on 2013-11-26
The "pipe" =  | 
The "pipe" is the vertical bar on your keyboard. How you get to it depends on your keyboard configuration.
On my keyboard, a lenovo thinkpad, the pipe is above the Strg. button on the left bottom of the keyboard. On this same button I have ">", and "<" AND THE VERTICAL BAR CALLED THE PIPE.
To type it I have to press and hold the "shift button" together with the AltGr button, and then whilst holding those buttons press the pipe button.
On some keyboards you have to press the "shift" + / key which then turns the / into a  |
Not sure how your specific keyboard is configured.
I assume this is what you want to know, if not come back.

---

### Post by lucas12zarzur on 2013-11-26
No germanix, i want know the function...

---

### Post by philinux on 2013-11-26
Please use descriptive titles in future. Thanks.

---

### Post by Lars Noodén on 2013-11-26
> **lucas12zarzur said:**
> No germanix, i want know the function...


Compare this

```

ls /usr/bin | less

```

with this
```

ls /usr/bin > /tmp/foo
less /tmp/foo

```

The pipe sends output from one program into the next one as input.

---

### Post by germanix on 2013-11-26
"The pipe sends output from one program into the next one as input"
Thanks for that. Never thought about it makes wonderfully sense to me now. It is a conduit, it allows the flow from one point to another, just like water in a pipe. Live and learn!

---

### Post by philinux on 2013-11-26
Using a bit of google foo.

[http://www.linfo.org/pipes.html](http://www.linfo.org/pipes.html)

---

### Post by lucas12zarzur on 2013-11-26
> **Lars Noodén said:**
> Compare this

```

ls /usr/bin | less

```

with this
```

ls /usr/bin > /tmp/foo
less /tmp/foo

```

The pipe sends output from one program into the next one as input.

Thank u so very much.

---

