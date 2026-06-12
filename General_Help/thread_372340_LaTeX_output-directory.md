---
title: "LaTeX output-directory"
date: 2007-02-28
forum: General Help
---

### Post by Mitlik on 2007-02-28
I am trying to compile my LaTeX documents into a folder. To accomplish that I used the output-directory command with my favourite LaTeX backend. So I used:
latex -output-directory=foo bar.tex
And I get out:
! I can't write on file 'bar.log'

I have tried several combinations but without any luck.

Thanks in advance,

Ben

---

### Post by girishv on 2007-02-28
Works perfectly for me Ben. The problem might becos of two reasons. The directory might already have bar.log and no write permission and the directory itself might not have write permission.
Can you check out whether writing to /tmp works
latex -output-directory=/tmp bar.tex

Girish

---

### Post by Mitlik on 2007-03-01
Okay, that works, and taking it one step further writing to a relative directory in existence also works. It never occurred to me that it had to be a directory that already existed.  -- thanks for the idea, Girish.
I am trying to find a way to make a directory and compile to it from within my front-end (Kile). Not entirely sure how to go about that.

Ben

---

