---
title: "Vim cursor movement"
date: 2005-05-03
forum: General Help
---

### Post by rosslaird on 2005-05-03
I'm just starting to use Vim in a fullscreen terminal that I'm switching to with ctl-alt-f1. It's a neat application: very minimalist, very Zen. And I know that there are quite a few uber-geeks on this forum who will know the answer to my question:

When I press the cursor movement keys (letters or arrows), my vertical movement does not happen one line at a time. The cursor jumps 9 lines with every press of the key. How do I fix this?

Update:

Aha! It's jumping paragraphs (the file I'm working on is a text file with long lines). So I think I'm getting closer here. But help would still be nice.

Thanks.

Ross

---

### Post by shakin on 2005-05-03
What it's actually doing is jumping lines. Push the Home and End keys goes to the beginning and ending of that line, respectively. It's a handy feature when editing configuration files, but not so good for story writing or anything else with paragraphs.

Sorry, I don't know how to navigate within the current line, but I'm sure Google can find a lot of vi tutorials.

---

### Post by rosslaird on 2005-05-03
Thanks for the input. I've been googling for a while without any tangible result. I did eventually figure out that it's jumping "lines" -- but what I want is for it to jump a single line on screen rather than a single line as defined by carriage returns.

I have discoverd how to move by sentences, which is an improvement:

(     back
)     forward

Update:

OK, got it:

Use "g" before the letter movement keys (hjkl). But you have to press "g" every time.

---

### Post by rosslaird on 2005-05-03
And an ultimate solution:

:noremap <Up> gk
:noremap! <Up> <C-O>gk
:noremap <Down> gj
:noremap! <Down> <C-O>gj
" the following are optional, to move by file lines using Alt-arrows
:noremap! <M-Up> <Up>
:noremap! <M-Down> <Down>
:noremap <M-Up> k
:noremap <M-Down> j 

The above goes in the .vimrc file. Makes the arrow keys work perfectly (one screen line at a time).

---

