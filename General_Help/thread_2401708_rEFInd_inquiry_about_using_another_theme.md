---
title: "rEFInd inquiry about using another theme"
date: 2018-09-21
forum: General Help
---

### Post by drpeppercan on 2018-09-21
So in the refind.conf file there are these default flags/entries:

#icons_dir myicons
#icons_dir icons/snowy

First question is: 
Why these default directory/subdirectory names do not match the actual files layout?
I mean, if you see the attachment img file, you'll see that the icons directory is simply called "icons" (not myicons). And, inside the icons dir there's no subdir called "snowy", in fact, there's no file starting with an "s".
So, if indeed the above entries serve to tell rEFInd where to find the icons, then I do not get it!


Second question:
If there's only one icons directory, then why to have 2 entries?
Perhaps we can have more than one icons dir available?

Thanks guys!

---

### Post by oldfred on 2018-09-21
Those look like they are just alternative examples of places you put your icons if desire.


> # an icon can't be found in the specified directory, an attempt is made
# to load it from the default directory; thus, you can replace just some
# icons in your own directory and rely on the default for others.

---

### Post by drpeppercan on 2018-09-21
I see!
Thank you oldfred!! :)

---

