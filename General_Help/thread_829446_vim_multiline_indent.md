---
title: "vim multiline indent?"
date: 2008-06-14
forum: General Help
---

### Post by PGScooter on 2008-06-14
Hi, I am starting to like vim!

how can I indent the next, say, 7 lines one tab to the right (or one tab to the left)?

I want to
         change this


to this:

        I want to
                 change this

thanks!

---

### Post by Joeb454 on 2008-06-14
> **PGScooter said:**
> Hi, I am starting to like vim!

how can I indent the next, say, 7 lines one tab to the right (or one tab to the left)?

I want to
         change this


to this:

        I want to
                 change this

thanks!

Try using [noparse]```

```[/noparse] tags to show what you want - like so:

```
I want to
         change this


to this:

        I want to
                 change this
```

Though I'm not sure how you would do this. All I know is mine auto-indents for my C & C++ app's, that's all I care about :p

---

### Post by VMC on 2008-06-14
Yes, the code tags would help. I'm not sure I understand what your after, since it all appears the same. Something in the oder of 
```
:%s/^/^I
```   Subsitute all lines with a tab at the begininng
```
:5,9s/^/^I
``` Will do the same thing with lines 5 through 9

---

### Post by ibuclaw on 2008-06-14
Here is a small page about indents in Vim.

[http://www.vim.org/htmldoc/usr_25.html#25.3](http://www.vim.org/htmldoc/usr_25.html#25.3)

Hope its of use to you.

Regards
Iain

---

### Post by PGScooter on 2008-06-15
I will remember to use the code tags next time, thanks for the suggestion.
VMC, that's exactly what I was after, thanks!
good link tinivole, I'll check that out.

Thanks!

---

