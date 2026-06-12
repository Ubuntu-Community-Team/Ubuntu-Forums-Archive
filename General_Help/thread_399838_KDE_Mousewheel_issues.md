---
title: "KDE Mousewheel issues"
date: 2007-04-02
forum: General Help
---

### Post by kc0eks on 2007-04-02
Hello again everyone...
:)

here goes. In gnome my mouse works properly, as far as scrolling goes and such. I have my xorg.conf file set up to work with it and all.

In KDE the wheel acts as forward/back in firefox. 
in Konqueror it will scroll up and down but ONLY if the pointer is over the scroll bar..

so how do I go about getting KDE to like my mouse a bit better? 

I have searched around a bit on here and google but really didnt find much in the way of how to fix this. 

I greatly appreciate your help!

---

### Post by kc0eks on 2007-04-03
pretty please does anyone know how to fix this? Even searching google hasnt gotten me very far. I have seen mention of editing an xf86 file but the posts are quite old, so im not sure this applies anymore...

EDIT: Ignore this thread I got it working. Just incase anyone has this issue I needed to run this to make it work:

xmodmap -e "pointer = 1 2 3 6 7 4 5 8 9 10 11"

---

