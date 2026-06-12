---
title: "Getting this site to work..."
date: 2008-06-28
forum: General Help
---

### Post by AdrianStrays on 2008-06-28
All right, this is a tad silly.  My mother likes to do puzzles, and she is flipping out about Ubuntu's inability to run these puzzles.  I've tried on both our computers, and the puzzles do not work.  It just says loading. Works on Vista, works through Firefox using Vista, but Ubuntu it does not.  Help?

[http://www.jigzone.com/](http://www.jigzone.com/)

---

### Post by avtolle on 2008-06-28
Two thoughts; just went to the link, and got the same result. My first thought is that this may be a Flash issue; have you installed flashplugin-nonfree from the repositories, and removed gnash (if it is installed) including its plugin to avoid conflicts: or

It is a java problem, and if you don't have the sun java installed and selected as the default, the open source java, f/k/a iced tea java, doesn't work. So, install the sun java (again from the repositories), select it as the one to use, and see if that helps.

EDIT: [https://help.ubuntu.com/community/Java#Choosing%20the%20default%20Java%20to%20use](https://help.ubuntu.com/community/Java#Choosing%20the%20default%20Java%20to%20use) will give you some helpful information, I believe, if it is indeed a java problem.

---

### Post by p_quarles on 2008-06-28
Yep, it's a Java application. It didn't work for me in Konqueror (my usual browser), but it worked fine in Opera. If it doesn't work in Firefox, it may be a quirk in how the Java plugin interacts with the browser.

---

