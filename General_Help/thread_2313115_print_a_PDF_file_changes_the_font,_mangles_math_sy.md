---
title: "print a PDF file changes the font, mangles math symbols"
date: 2016-02-09
forum: General Help
---

### Post by michael-h-williamson on 2016-02-09
Printing a PDF changes the font and mangles the math symbols. The document is displayed correctly in the Firefox web browser, or in evince after downloading the document. Printing to a file instead of to a printer also exhibits the problem. The converted PDF file is roughly ten times bigger too. The first line of the converted PDF file is %PDF-1.5.
The problem is verified for source PDF versions 1.4 and 1.5. I suspect that CUPS is doing some conversion (pdftopdf?) that is the cause. How do I fix it?   

I am using Ubuntu 12.04.

I am replying to my own thread with new information.
I did 
 # sudo apt-get install cups-pdf
and that appeared(!) to fix it, but after printing one page correctly, the problem returned. 
Then I did '... remove cups-pdf' and '...install cups-pdf, but that was unsuccessful.

---

### Post by michael-h-williamson on 2016-02-10
I found a work around. I can print correctly from evince as a regular user (not superuser). 
I normally do everything as superuser (root). I suspect that is somehow causing the problem.

---

### Post by vasa1 on 2016-02-10
> **michael-h-williamson said:**
> ...
I normally do everything as superuser (root). I suspect that is somehow causing the problem.
+1.

And more to come. Why not be like the rest of us and avoid being "superuser"?

---

### Post by michael-h-williamson on 2016-02-10
Superpowers do not usually cause a problem.

---

### Post by pauljw on 2016-02-10
> **michael-h-williamson said:**
> Superpowers do not usually cause a problem.

Heh, that's not even true for Superman.  I don't understand why you would want to circumvent what is arguably the biggest safety feature of the *nix family of OSes, the isolation of the user from the core of the system.  The entire underlying structure and philosophy of linux, and unix before it, is based on the ability for the user to make a mess of things while the core system happily continues unaffected.

However, as always, the choice is yours.  As for why the root account is printing weirdly, I have no answer, and since I won't play around in that account to test it, I can only wish you good luck in finding a solution.

---

### Post by michael-h-williamson on 2016-02-10
I am inclined to believe that for computers that are actually used as PCs (e.g. personal computers, not multi-user), the distinction between ordinary users and the super-user is not very useful.

---

### Post by QIII on 2016-02-10
I'm inclined to believe that in Linux, as in Windows, running always as root is a risky game to play.  There is likely a good reason or two why professionals in each world strongly recommend against it, as I have for going on four decades.

One "Ooops!" destroys a hundred "Attaboys".

But in any case, are you satisfied with the solution you found?  If so, please mark the thread as solved.

Cheers.

---

