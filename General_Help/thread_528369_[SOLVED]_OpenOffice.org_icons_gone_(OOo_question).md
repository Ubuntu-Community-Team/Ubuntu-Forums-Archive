---
title: "[SOLVED] OpenOffice.org icons gone (OOo question)"
date: 2007-08-17
forum: General Help
---

### Post by lyceum on 2007-08-17
I just opened Writer to find all of my icons gone, so the is not check mark, it just says "spell check", not **B** just the word bold, ext in the tool bar. I changed my icon set recently, but switch back to the old one did not fix the problem, and I have not idea what is going on. Can anyone help?

:confused:

-edit-
In case you were wondering, yes I did got to "tool/options/view" and yes, "use icons" is checked.

---

### Post by p_quarles on 2007-08-17
This happens when you change away from the default icon set for your desktop. You just need to get the other OOo icons, which are contained in the following packages:
```
openoffice.org-style-andromeda - Default symbol style for OpenOffice.org
openoffice.org-style-crystal - Crystal symbol style for OpenOffice.org
openoffice.org-style-default - Default symbol style for OpenOffice.org
openoffice.org-style-human - Human symbol style for OpenOffice.org
openoffice.org-style-industrial - Industrial symbol style for OpenOffice.org
openoffice.org-style-tango - Tango symbol style for OpenOffice.org
openoffice.org-style-hicontrast - Hicontrast symbol style for OpenOffice.org
```

---

### Post by lyceum on 2007-08-17
> **p_quarles said:**
> This happens when you change away from the default icon set for your desktop. You just need to get the other OOo icons, which are contained in the following packages:
```
openoffice.org-style-andromeda - Default symbol style for OpenOffice.org
openoffice.org-style-crystal - Crystal symbol style for OpenOffice.org
openoffice.org-style-default - Default symbol style for OpenOffice.org
openoffice.org-style-human - Human symbol style for OpenOffice.org
openoffice.org-style-industrial - Industrial symbol style for OpenOffice.org
openoffice.org-style-tango - Tango symbol style for OpenOffice.org
openoffice.org-style-hicontrast - Hicontrast symbol style for OpenOffice.org
```

Thanks, I tried the code in terminal, it did not work. How do I get past "command not found" ? I tried sudo.

---

### Post by p_quarles on 2007-08-17
Sorry, that's not code, it's just a list of packages (wrapped in the code tags for easier reading, but probably should have used quote tags instead). To install them, you need to use:
```
sudo apt-get install *packagenames*
```
where *packagenames* are all the packages you wish to install, separated by spaces.

---

### Post by lyceum on 2007-08-18
> **p_quarles said:**
> Sorry, that's not code, it's just a list of packages (wrapped in the code tags for easier reading, but probably should have used quote tags instead). To install them, you need to use:
```
sudo apt-get install *packagenames*
```
where *packagenames* are all the packages you wish to install, separated by spaces.

I was forgetting the word install. 

It worked, Thanks!

---

### Post by stchman on 2007-11-13
I know this thread is [SOLVED] and it worked for me as well.  I just have one other comment.

If you install OO2.3 from OO website then there is no issue with the icons no matter what icons you use.

Thanks.

---

### Post by cybergalvez on 2008-02-12
> **stchman said:**
> I know this thread is [SOLVED] and it worked for me as well.  I just have one other comment.

If you install OO2.3 from OO website then there is no issue with the icons no matter what icons you use.

Thanks.

so why aren't these packages installed by default?

---

### Post by lyceum on 2008-02-13
> **stchman said:**
> I know this thread is [SOLVED] and it worked for me as well.  I just have one other comment.

If you install OO2.3 from OO website then there is no issue with the icons no matter what icons you use.

Thanks.

That is good to know, thank you.

---

### Post by enchantedsky on 2008-03-11
Thanks, this post helped me. 

What I don't understand is why this problem happened to me in the first place. I did not mess around with the icons in my Ubuntu installation, yet reinstalling the icons brought it back in Open Office. Who knows eh?

---

### Post by amirman on 2008-06-14
i'm trying to delete this comment. but i dont see any delete option even though the mouseover for the edit button says edit/delete comment.

---

