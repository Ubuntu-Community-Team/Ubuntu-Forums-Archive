---
title: "Good Latex Editor"
date: 2006-08-05
forum: General Help
---

### Post by calvinthomas on 2006-08-05
Can anyone tell me a good latex editor for Ubuntu 6.06? Preferably i'd like it to display the formula as I type rather than having to save it and then open it to see it in Latex format, it seems Texmacs would do this but it seems to have unconventional notation!

Calv

---

### Post by jordilin on 2006-08-05
In my opinion, Kile is one of the best latex editors out there, although emacs is always around :D

---

### Post by calvinthomas on 2006-08-05
Can I make Kile WYSIWYG?

Calv

---

### Post by jordilin on 2006-08-05
No, kile is just a powerful latex editor. If you want a latex WYSIWYG editor then try **lyx**. It's in the repos, so you know, apt-get :D

---

### Post by buttari on 2006-08-05
My choice is emacs + auctex + reftex. If you want wysiwyg then you can add to emacs another package that is called preview-latex. Here's how it looks like:

[http://www.gnu.org/software/auctex/img/preview-screenshot.png]("http://www.gnu.org/software/auctex/img/preview-screenshot.png")

regards

alfredo

---

### Post by calvinthomas on 2006-08-05
Thats great, I now have a powerful editor and a WYSIWYG editor aswell, even better! Thankyou!

Calv

---

### Post by calvinthomas on 2006-08-05
> **buttari said:**
> My choice is emacs + auctex + reftex. If you want wysiwyg then you can add to emacs another package that is called preview-latex. Here's how it looks like:

[http://www.gnu.org/software/auctex/img/preview-screenshot.png]("http://www.gnu.org/software/auctex/img/preview-screenshot.png")

regards

alfredo

This sounds really good but how would I actually use it within emacs, I open emacs and how do I then tell it I want to do Latex input? also how do I then get it into WYSIWYG?

Sorry to be a pain!

Calv

---

### Post by der_joachim on 2006-08-06
How about [LyX]("http://www.lyx.org/")? AFAIK you can either export to LaTeX, or just print directly. It is in the repos.

---

### Post by MarinaraOfDeath on 2006-08-06
I really like LyX, but it's really unstable, so you have to decide how much you want to fight with a software package. When it works it's just beautiful.

---

### Post by mamato on 2006-08-06
You can also try GNU TeXMac, it uses WYSIWYG for LaTeX 

~hope that helps

---

### Post by buttari on 2006-08-06
> **calvinthomas said:**
> This sounds really good but how would I actually use it within emacs, I open emacs and how do I then tell it I want to do Latex input? also how do I then get it into WYSIWYG?

Sorry to be a pain!

Calv

Once you have all this stuff installed when you open a .tex file emacs automatically goes into latex mode. Then you have a new menu in the top bar where you can control everything. 

alfredo

---

