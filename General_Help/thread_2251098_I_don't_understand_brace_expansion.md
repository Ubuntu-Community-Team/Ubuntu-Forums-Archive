---
title: "I don't understand brace expansion"
date: 2014-11-02
forum: General Help
---

### Post by mageta2 on 2014-11-02
I'm learning about brace expansion, and I'm kind of confused about how the shell decides to do things. Example

[B]echo {1..3}-{1..3}
1-1 1-2 1-3 2-1 2-2 2-3 3-1 3-2 3-3

[/B]It looks like it does the first number of the first bracket, and then completes the entire second bracket before moving on to the next item in the first bracket again. Why does it do it this way? In my mind, it seems like it would just print 123-123, and if I put a space in there, that's exactly what it does.

[B]echo {1..3} - {a..c}
1 2 3 - a b c[/B]

Nested brackets are even stranger to me, but one step at a time. Why does this happen? I would like to understand the logic behind it.

---

### Post by sisco311 on 2014-11-02
In your first example you have a single word in which you use a brace expansion as preamble for another one. At the first step the first brace expansion is performed and you end up with 3 words: 1-{1..3} 2-{1..3} 3-{1..3}. In the next step expansion is performed on the 3 words.

In the second example you have 3 words. {1..3}, - and {a..c}. Brace expansion is performed on the 1st and 3rd one; the - has no special meaning, so no expansion is performed on it.

Please check out:  [http://wiki.bash-hackers.org/syntax/expansion/brace](http://wiki.bash-hackers.org/syntax/expansion/brace)

---

