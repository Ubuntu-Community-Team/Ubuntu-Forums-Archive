---
title: "Where is  form.css for Firefox 3 beta 5 on Hardy"
date: 2008-06-03
forum: General Help
---

### Post by dangodango on 2008-06-03
I've looked in the usual places like:

**/urs/lib/firefox/res/** and **/opt/mozilla/lib/firefox/res**

but it is not in these locations could it be in a different location for x64 users or because it's firefox 3 beta 5?

---

### Post by crossedout on 2008-06-03
Check out /usr/share/firefox/res/samples.  The exact 'form.css' folder is not listed, however, a.b.cform.css could be what you are looking for.

-Xout

---

### Post by dangodango on 2008-06-03
> **crossedout said:**
> Check out /usr/share/firefox/res/samples.  The exact 'form.css' folder is not listed, however, a.b.cform.css could be what you are looking for.

-Xout

the res folder is not there there is only a defaults folder. I'm trying to change the form.css file because the gtk theme i'm using makes input boxes and other controls too dark but can't find the file :-(

---

### Post by dangodango on 2008-06-04
^bump

---

### Post by crossedout on 2008-06-04
> I'm trying to change the form.css file because the gtk theme i'm using makes input boxes and other controls too dark but can't find the file.

Sounds like a darker theme issue.  For the record, some darker themes will work right off the bat with FF, its the ones that don't that need to be tweaked.
There are a couple things you can try:
1. Goto System>Preferences>Appearance, select the theme you want, click customize>colors and adjust the input boxes colors (and whatever else you need) to your liking.

If that doesn't work:
2. Edit the theme colors itself by opening the gtkrc file.  It will take some trial and error to determine what works since the font color will likely need be changed as well.  I believe base[NORMAL] will change your input fields.  You'll need the color code(s).  You can use the GIMP eyedropper for that.

3. FF and theme color are a common question, search around and you'll see many posts on the subject.  You might find that one of those other suggestions works as a solution for you.

EDIT:
I found this solution doing a search, it sounds like what you need.
4. [http://ubuntuforums.org/showthread.php?t=424511]("http://ubuntuforums.org/showthread.php?t=424511")
5th post.

Good Luck.
-Xout

---

