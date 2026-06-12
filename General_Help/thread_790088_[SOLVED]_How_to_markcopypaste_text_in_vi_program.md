---
title: "[SOLVED] How to mark/copy/paste text in vi program"
date: 2008-05-11
forum: General Help
---

### Post by abcuser on 2008-05-11
Hi,
I have read excellent tutorial about vim program:
[https://engineering.purdue.edu/ECN/Support/KB/Docs/ViTextEditorTutorial/9.rearrange.dup.text](https://engineering.purdue.edu/ECN/Support/KB/Docs/ViTextEditorTutorial/9.rearrange.dup.text)

But I can' fine any option just to mark some text, copy it and paste it at some other position.

I am very used to: <Shift>+right or <Shift>+<Control>+right to mark and then <Ctrl>+c to copy and <Ctrl>+p to paste.

It looks like there is just 'y' and 'p' options to copy/paste, is it?

Is there any similar mark/copy/paste way in vim program?
Thanks,
Abcuser

---

### Post by nirkir on 2008-05-11
Hi,

You can enter "visual" mode using 'v'. This enables you to visually select text. 

Then you can use standard movement command to select text (e.g. 3w will select the following 3 words).

Once you've got your selection right, press 'y' to copy (or 'd' to delete/cut) and press 'p' (or 'P') to paste at the desired location

---

### Post by sdennie on 2008-05-11
If you are just talking about marking text in vim and then copy/cut/paste within vim.  If you hit 'v' it will put you into visual mode and then you can use normal movement commands to select stuff.  After that,  'y' or 'd' will copy or cut it and 'p' will paste it.

---

### Post by tbfr on 2008-05-11
It's actually quite easy. Just press v and mark the selection by using the cursor keys, then press y to copy it. Move the cursor to where you want to put the text and press p

[http://www.vim.org/htmldoc/visual.html](http://www.vim.org/htmldoc/visual.html)

---

### Post by kerry_s on 2008-05-11
you might also want to try the tutor program in your free time.
just open a terminal and type> vimtutor
it teaches by doing, not memorizing.

i tend to use y or #y or yy or yw or y#w aka:yank, p to paste

---

### Post by abcuser on 2008-05-12
Hi,
It is very easy: v-mark, y-copy, p-paste.
Thanks a lot,
Abcuser

---

