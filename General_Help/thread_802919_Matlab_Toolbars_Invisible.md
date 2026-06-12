---
title: "Matlab Toolbars Invisible"
date: 2008-05-21
forum: General Help
---

### Post by Iteria on 2008-05-21
So, I installed Matlab using a CD. it installed correctly and boots beautifully, except... Well the toolbars/menus are invisible! when I right-click I can toggle the invisible bars on and off, but I cannot actually see them. Has anyone else had this problem and is there a fix for it?

Update: I fixed it. The problem is caused by compiz/beryl. To fixed it all you have to do is add "export AWT_TOOLKIT=MToolkit" to MatlabDirectory/bin/matlab I made mine the first uncommented line, but I'm not sure if just having it in the file will make it run fine.

---

### Post by arpitubun on 2008-09-20
> **Iteria said:**
> So, I installed Matlab using a CD. it installed correctly and boots beautifully, except... Well the toolbars/menus are invisible! when I right-click I can toggle the invisible bars on and off, but I cannot actually see them. Has anyone else had this problem and is there a fix for it?

Update: I fixed it. The problem is caused by compiz/beryl. To fixed it all you have to do is add "export AWT_TOOLKIT=MToolkit" to MatlabDirectory/bin/matlab I made mine the first uncommented line, but I'm not sure if just having it in the file will make it run fine.


Great , Extremely perfect!
It worked for me! The problem was too irritating.
Thanks!

---

### Post by Jacob Collstrup on 2008-10-16
Man, I've been having that problem for weeks now!! This worked like a charm!!=D>

Jacob

---

### Post by toolisima on 2008-10-17
Thanks a lot!!:biggrin: I had the same problem and this fixes it!

---

### Post by PreDa on 2008-11-18
thanks a lot beautiful job!!!!

---

### Post by jeneverboy on 2009-09-10
Still working for matlabR2007b. Thanks.

---

### Post by yoldas ataseven on 2010-02-14
Well, I had the same issue. With a karmic and R2007a, the menu was invisible. Besides, I wasn't able to resize the windows. To be precise, when i resized the matlab window, the sub-windows (editor, command line etc.) were not following it. Instead, they were acting as if they were confined to a pre-defined window size. When I tried to separate one of the sub-windows (e.g. editor) from the main window, it used to separate, but got blank. I searched through the forum and got some tricks, tried two of them and the second solved the problem.

First, I tried the method mentioned above: I added this before the first un-commented line of $MATLAB_DIR$/bin/matlab :

```
export AWT_TOOLKIT=MToolkit
```

and it didn't change anything. Then I erased it and tried this one (at the same place):

```
export MATLAB_JAVA=/usr/lib/jvm/java-6-sun-1.6.0.15/jre/
```

1.6.0.15 is my version, of course, you should use your own version name. 

This worked for me. Hope it helps.

---

### Post by Rezzz on 2011-01-22
That works perfectly except that I found that the window background become grayish. Is it possible for me to change the background color back to white? Thanks.

---

