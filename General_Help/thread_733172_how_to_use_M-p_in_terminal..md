---
title: "how to use M-p in terminal."
date: 2008-03-23
forum: General Help
---

### Post by qns8dn3 on 2008-03-23
Manpage for bash states:

       non-incremental-reverse-search-history (M-p)
              Search backward through the history starting at the current line
              using a non-incremental search for  a  string  supplied  by  the
              user.
       non-incremental-forward-search-history (M-n)
              Search  forward  through  the  history  using  a non-incremental
              search for a string supplied by the user.

When I press Esc-p (or Alt-p), it just replaces my command with a colon, how do i supposed to use this non-incremental-reverse-search-history thing?

---

### Post by bapoumba on 2008-03-23
<ctrl><p>, <ctrl><n>.

<ctrl><r> will also search commands with particular letters:
```
isabella@yeti:~ $ 
(reverse-i-search)`ful': sudo aptitude full-upgrade
```

---

### Post by qns8dn3 on 2008-03-24
I figured out how to use M-p. Press M-p (i.e. Esc and p) and type a word and press Enter, then it goes to the most recent item in history containing the word. Press M-p again and press Enter, it goes to the next recent item containing the word. It is like / and n in "less".

---

