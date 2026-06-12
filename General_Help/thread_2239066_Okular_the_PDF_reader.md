---
title: "Okular the PDF reader"
date: 2014-08-11
forum: General Help
---

### Post by Robbyx on 2014-08-11
In ubuntu Okular opens when clicked on, but not in Lubuntu. It is in the application manager of Lubuntu but nothing happens when I click on it. If I go to the terminal and type okular then it does open. 

I tried reinstalling Okular but it made no difference. 

What should I do to make sure that Okular works properly.

R

---

### Post by nerdtron on 2014-08-11
Any output/error message from the terminal when you launch okular from there?

---

### Post by vasa1 on 2014-08-11
Look in /usr/share/applications for .desktop files relating to **okular**. There maybe more than one. See which works for you.

---

### Post by Robbyx on 2014-08-12
> **vasa1 said:**
> Look in /usr/share/applications for .desktop files relating to **okular**. There maybe more than one. See which works for you.

Are you sure that is the correct location? My /usr/share/applications  one has no hidden files in it. Just a load of icons and Okular is not among them.

R

---

### Post by Robbyx on 2014-08-12
> **nerdtron said:**
> Any output/error message from the terminal when you launch okular from there?

Nothing. It just does not open. 

 I tried to look in the var/log and did not know which to use. Could you suggest a command line to give the hidden error message?

R

---

### Post by SeijiSensei on 2014-08-12
Look at the properties sheet for Okular in the application menu.  (Right-clicking the entry usually enables this.)  What is the path to the program file?  It should be /usr/bin/okular.

---

### Post by Robbyx on 2014-08-12
> **vasa1 said:**
> Look in /usr/share/applications for .desktop files relating to **okular**. There maybe more than one. See which works for you.

The properties of Okular in the application menu points to 

/home/robins/.local/share/applications

Okular.desktop is in there. I can click on it and okular runs and opens, but it does not open from the application menu entry which is pointing to it! 


According to whereis Okular
okular: /usr/bin/okular /usr/bin/X11/okular /usr/share/man/man1/okular.1.gz


So I changed Okular's desktop type file  properties (/home/robins/.local/share/applications/Okular) to:
/usr/bin/okular %U %i -caption %c

and still it does not open from the application menu. I noted the differences in Caps but I think that is correct as the files referred to have different capitalisations.

R




R

---

### Post by Robbyx on 2014-08-12
I have just clicked on the option to copy the okular's  application menu entry onto to the desktop. From there the okular icon  opens Okular, but still it does not work from the application menu.

Where is the contents of the application menu stored?

R

---

