---
title: "MPlayer Chapter Select?"
date: 2007-02-20
forum: General Help
---

### Post by ~LoKe on 2007-02-20
I'm trying to watch a DVD through MPlayer, but the main movie is on Chapter 2, but only Chapter one is selectable.  How can I access chapter 2 through MPlayer?

---

### Post by renzokuken on 2007-02-21
mplayer isnt great for chapter selection.

i think if you use the arrow keys (up and down = big jump)(left and right = little jump) you can just skip chapters quickly to get the next one. ignore the progress bar. it starts fresh for each chapter.

---

### Post by ~LoKe on 2007-02-21
That's not the problem I'm having, though. :(

For me, some of my DVD's are split into two chapters.

Chapter 1 will have all the previews and advertisements, and it will contain 14 titles (one for each).
The movie is **not** on this chapter, in any of the titles.

The movie is actually on Chapter 2, which MPlayer doesn't seem to recognize (on any of my DVD's mastered this way).  Using the up/down left/right keys skip through the title, but don't let me skip through the chapter.

:(

---

### Post by artships on 2007-02-21
You might try from a command line:

mplayer dvd://2

---

### Post by ~LoKe on 2007-02-21
> **artships said:**
> You might try from a command line:

mplayer dvd://2

dvd://2 would be title 2, if memory serves.

---

### Post by artships on 2007-02-22
> **~LoKe said:**
> dvd://2 would be title 2, if memory serves.

Memory serves correctly.  In my vast experience (all this month!) I've never known a film to start on **chapter** 2, so I assumed you'd meant **title** 2.  How about:

mplayer dvd://1 -chapter 2-100

---

