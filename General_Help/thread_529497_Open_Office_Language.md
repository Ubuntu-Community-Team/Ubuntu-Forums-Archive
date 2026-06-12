---
title: "Open Office Language"
date: 2007-08-19
forum: General Help
---

### Post by mikeylikesit on 2007-08-19
HI all, somehow the language in open office has changed on me and i have no idea how to change it. can someone please help me. all i really need is someone to tell me were i can locate the option to change the language on the menu bars. 

Thanks!

---

### Post by gobbles414 on 2007-08-19
HI mikeylikesit,

In OpenOffice, go tools --> options --> language settings --> languages. You can also tell OpenOffice to check documents in all available languages by going tools --> options --> language settings --> writing aids.

If the language you want is not available, you will need to add it. Do this in Ubuntu by going system --> administration --> language support. BTW, language support may need to install some files before you can access the list of languages.

---

### Post by mikeylikesit on 2007-08-19
hi and thanks the problem is the menus and all are in the differernt language so i guess i need some like (5 over, 3 down) that type of thing

Thanks again though for responding so quickly

---

### Post by gobbles414 on 2007-08-19
mikeylikesit,

Oh... It should still be easy to fix by going in OpenOffice:

tools (7th from left to right) --> options (last going from top to bottom) --> language settings (3rd category going from top to bottom) --> languages (1st sub-category going from top to bottom) --> user interface (first drop-down menu from top to bottom). OK is the first button from left to right.

Assuming that the rest of Ubuntu is in your preferred language, you should then be able to go back to the user interface drop-down menu and select default (same with locale setting).

---

### Post by mikeylikesit on 2007-08-19
well i found it okay, then i even went as far as installing open office on my windows box and cross referencing the best i could, but with no luck, so i unistalled open office, and reinstalled it, and it was still in the different language. Maybe im downloading the wrong package or something. 

thanks again though

---

### Post by mikeylikesit on 2007-08-19
Thanks all i got it working, turns out i had to sudo apt-get remove openoffice.org-core then reinstall thanks for all the help

---

### Post by gobbles414 on 2007-08-19
mikeylikesit,

Is the language you want in the user interface drop-down menu? If not, you need to install it in Ubuntu using language support. What language are you trying to use in OpenOffice?

---

### Post by Hagar Delest on 2007-08-20
Just for information, it happens sometimes. The quick fix is to go to the Gnome System>Preferences>Fonts and change the font used for applications. No link it seems but it works.

NB: never had this problem with the official version (not the OOo Ubuntu one).

---

### Post by timak on 2008-01-24
This problems was driving me crazy this morning...  Changing the Font fixed it.  


Thanks a bunch.


TIm

---

### Post by macaroo on 2008-01-26
I am experiencing the same problems... I have installed all the japanese language packages i can think of. 
I can use SCIM in text editor no problem. 
I instaned the scim bridge, Anthy, reinstalled the openoffice.org core. 

In my options > language settings 
i have enabled Japanese as my eastern language. I have checked to enable east asian language. 
I am so frustrated with this application right now. I know the japanese works as I can open my old MS Word docs that used MSMincho TTF and can read these docs no problem in Kanji. 

I don't seem to have a system > PReoferences > fonts .. 

My assumption is that I am actually missing the required fone. I have no idea how to go about finding this font however. 
ANY assitance is appreciated. 
Mac

---

