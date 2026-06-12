---
title: "files display question"
date: 2014-12-05
forum: General Help
---

### Post by jgw on 2014-12-05
I have noticed that the file columns display cannot be expanded and compressed as they can be in ms windows.  For instance, if I am looking at the home directory, and the display has room one can goto the top, find the divider, and move the sizes around.  On the other hand, if I am looking at a folder that fills up the available space one cannot change the column width.   This means that if one column has compressed its contents I cannot expand that column to see the actual contents of that column.   I have attached a screenshot of a folder that I cannot change column width when displayed.

I am wondering if I have set something up wrong which is causing this.

Thank you..............

---

### Post by ian-weisser on 2014-12-07
You have described the normal behavior for constrained spaces. You didn't set something up wrong.

Instead, for constrained spaces, try Edit --> Preferences --> List Columns, and change the list to a format you find more useful in that small space.

---

### Post by jgw on 2014-12-07
Thanks for the reply - I will give it try!!

---

### Post by mcduck on 2014-12-07
THe way how resizing the columns in Nautilus works can be a bit unintuitive, but based on your screenshot you should be able to resize them, as long as you do it in correct order. Most likely you'll need to grab the divider between "Modified" and "Location" first and shring the "Location" column, and that should give you enough space to stretch the "Name" wider.

Also you can always disable the "Lcoation" column completely, after all all the files/directories you are looking at will be in the same location, the folder you are currently viewing, and the location for that is already visible in the breadcrumns navigation buttons in the toolbar... That should give you plenty of sppace for file names and other information...

---

### Post by mc4man on 2014-12-07
*Some* of this behavior has been addressed in newer nautilus, currently seen in 15.04's version I believe, screens are 14.04
Pretty hard to show in a couple of static screens but anyway
scr 1 - fairly long path, decent amount of other info inc. file name
scr 2 shrunk window horizontally, location gets truncated,  not the file name.

On some rarer combo's the file name can get .. but in most cases not, there is a min to that column 
Maybe the patch will show in 14.04, otherwise a couple of ppa's have.

---

### Post by jgw on 2014-12-08
Thank you for all the replies!

I found that just getting rid of the location does the trick and, as pointed out, I already know what the location is.  thanks again!

---

