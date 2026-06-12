---
title: "Coffee + laptop = ^[[19"
date: 2008-03-13
forum: General Help
---

### Post by letired on 2008-03-13
soup, post-spilling of coffee boot today was very much slower than usual. After loading GRUB, selecting Ubuntu etc I was brought to the usual "Failed to allocate memory" which I have yet to solve, but after this there was suddenly something like
^[[19[~^ .
This string of chars appeared everywhere, as Ubuntu continued to load - I got "the stuff" that is hidden behind the Ubuntu + loading bar loader so for example:
^[[19[~^^[[19[~^Mapping^[[19[~^ keymap ^[[19[~^^[[19[~^^[[19[~^
^[[19[~^^[[19[~^^[[19[~^Loading^[[19[~^ whatever^[[19[~^

etc. Since Google doesn't feature special chars, there is no known way for me to search for a solution to this problem and I must ask, what the hell is it? Could it be permanent, along with the 50% speed boot?

I appreciate any help here.
/örk

---

### Post by kuja on 2008-03-13
Probably could be permanent - Fluids and laptops don't get along well.

---

### Post by ibuclaw on 2008-03-13
^[[19 = the F8 key :KS

I thought I recognised it, so I wrote a program.

```

#include <stdio.h>
int main()
{
        int ch;
        while (ch != 65)
        { ch = getchar(); }
        return 0;
}

```

Started hitting the F Keys, and, its F8...

But as to what is wrong, and how this could do with the effect its having on your laptop, its probably not related.
Though just to be sure, check that F8 isn't stuck down.

Iain

---

### Post by kuja on 2008-03-13
A to exit? Odd choice.

---

### Post by ibuclaw on 2008-03-13
65 was the first ASCII number that came to mind that I know. (Blame College).

As for testing, holding down the Key at first appeared to slow down my booting time, I almost thought it froze at one point.

But I consider it inconclusive as one of my hard-drives went through a maintenaince checkdisk routine.

[[IMG]http://img525.imageshack.us/img525/6862/dsc00062so1.th.jpg[/IMG]](http://img525.imageshack.us/my.php?image=dsc00062so1.jpg)

took a snapshot though, is this the effect that you are seeing?

Iain

---

### Post by MindFlayer on 2008-03-13
That's Ubuntu's fault for making you a coffee-addict :) This is a known problem but no one on the open-source scene wants to take responsibility for it.:lolflag:

To be more serious, I'd take the computer to the nearest repair shop.

---

### Post by letired on 2008-03-13
> **tinivole said:**
> ^[[19 = the F8 key :KS

I thought I recognised it, so I wrote a program.

```

#include <stdio.h>
int main()
{
        int ch;
        while (ch != 65)
        { ch = getchar(); }
        return 0;
}

```

Started hitting the F Keys, and, its F8...

But as to what is wrong, and how this could do with the effect its having on your laptop, its probably not related.
Though just to be sure, check that F8 isn't stuck down.

Iain

Ah, yes - this exact same thing happened with my old computer except it was the down arrow that was permanently stuck. It would seem that fluids that leave any residue when they dry (the first time it was lemonade - sugar, and this time coffee - coffee residue?) could make keys rust or stick or whatever. I pulled out a couple of keys, the f5-b row and cleaned it, as well as the f8 key, and the problem seems solved for now. I am, however, still experiencing a longer boot time, but since I've never actually measured the time it takes to boot, it might as well be placebo.

@ tinivole: Yes, that's it.

Fanx for now, everyone. ^_-

---

