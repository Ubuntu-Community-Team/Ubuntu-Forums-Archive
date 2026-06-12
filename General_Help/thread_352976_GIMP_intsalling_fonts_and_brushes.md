---
title: "GIMP: intsalling fonts and brushes?"
date: 2007-02-04
forum: General Help
---

### Post by MSlaveubu on 2007-02-04
How is this accomplished in ubuntu?  I have good web sites to get brushes and fonts, but how do I install them?


thanks

---

### Post by closetpirate on 2007-02-04
1 download
2 drop brushes into the /home/<yourusername>/.gimp-2.2/brushes  directory
3 drop fonts into the /home/<yourusername>/.gimp-2.2/fonts   directory

reload gimp and voila!

and I am assuming (and a terrible assumption it is) that you are using gimp 2.2 otherwise substitute version as needed

---

### Post by MSlaveubu on 2007-02-04
How do I get to that directory?  shouldnt be hard, but its very hard for me.  :KS

---

### Post by closetpirate on 2007-02-04
the commands would be if you downloaded them to your desktop
for brushes:

sudo cp /home/<yourusername>/Desktop/<yournewbrushfiles> \ /home/<againyourusername>/.gimp-2.2/brushes

then type your password

for fonts

sudo cp /home/<yourusername>/Desktop/<yournewfontfiles> \
/home/<agaiiyourusername>/.gimp-2.2/fonts

if you feel more comfortable using a gui then I cannot help you without more info like::???: 
Do you use Gnome or KDE?
What file browser do you use?

here is a link that might help:
[http://gimp.org/tutorials/Custom_Brushes/](http://gimp.org/tutorials/Custom_Brushes/)

a ways down it shows you how to save the custom brushes but the example is gimp 2.0

---

### Post by closetpirate on 2007-02-04
ooopps.....

---

