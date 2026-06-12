---
title: "Gimp and Gimpshop"
date: 2008-07-05
forum: General Help
---

### Post by geovino on 2008-07-05
I have used Gimp for a few things, but have always had trouble manipulating text, not as easy as Fireworks. 

I've heard of Gimpshop, which is a more PhotoShop looking version of Gimp. Will installing Gimpshop override Gimp? or can they both be used separately?

Just trying to find a Linux Graphics program that I can learn to be proficient at.

---

### Post by L337_K3y5 on 2008-07-05
> **geovino said:**
> I have used Gimp for a few things, but have always had trouble manipulating text, not as easy as Fireworks. 

I've heard of Gimpshop, which is a more PhotoShop looking version of Gimp. Will installing Gimpshop override Gimp? or can they both be used separately?

Just trying to find a Linux Graphics program that I can learn to be proficient at.

Separate I believe in Linux...I could be wrong, I used it once, but it didn't work in Vi$ta.  Haven't needed nothin' but GIMP 2 here.  I'll do it now, and tell you if it does overwrite.

---

### Post by eriqjaffe on 2008-07-05
Also, be aware that GIMPshop is out-of-date now.

---

### Post by L337_K3y5 on 2008-07-05
> **eriqjaffe said:**
> Also, be aware that GIMPshop is out-of-date now.

True, its like 2 or 3 WHOLE releases behind.

---

### Post by L337_K3y5 on 2008-07-06
I can't seem to build it from the source...I go into the extracted folder using terminal, then use ./configure, then it gives me no target identified markers.  The way its labeled though, I think it does overwrite.:confused:

---

### Post by geovino on 2008-07-06
That's good to know. I'll stick with Gimp and go to the Gimp forum and find some tutorials. Just want to be able to handle text better.

---

### Post by fragos on 2008-07-06
The Gimp team has been focusing on UI of late. I recommend you go to [http://getdeb.net/search.php?keywords=gimp](http://getdeb.net/search.php?keywords=gimp) and install the latest version 2.4.6.

---

### Post by wrtpeeps on 2008-07-06
gimpshop eliminates the most annoying thing ever about gimp - its all contained within 1 window.

None of this 3 seperate windows rubbish! :)

---

### Post by geovino on 2008-07-08
> **fragos said:**
> The Gimp team has been focusing on UI of late. I recommend you go to [http://getdeb.net/search.php?keywords=gimp](http://getdeb.net/search.php?keywords=gimp) and install the latest version 2.4.6.

tried to installed, but it won't work. now Gimp is removed and I get this message when I try to reinstall it:

gimp:
  Depends: gimp-data (<2.4.5-z) but 2.4.6-1~getdeb1 is to be installed

I was able to remove the new gimp data and then reinstall Gimp. 
How do I get the other windows to open with Gimp. I only get the one main panel? 

I look forward to a redesigned Gimp. I still have to use Fireworks in Windows to manipulate fonts, since the Gimp text and fonts are very hard to use. Any tutorials for using text and fonts?

---

### Post by fragos on 2008-07-08
Download all the getdeb Gimp packages into an empty folder. Open a terminal and cd to that folder. last run "sudo dpkg -i *" and all packages will be installed in the correct order to avoid the dependency problem you had.

---

