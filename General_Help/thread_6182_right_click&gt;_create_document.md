---
title: "right click&gt; create document"
date: 2004-11-25
forum: General Help
---

### Post by tanari on 2004-11-25
right click> create document> **No templates installed** 

How and where can I install templates?

---

### Post by p!=f on 2004-11-25
[QUOTE=tanari]right click> create document> **No templates installed** 

How and where can I install templates?[/QUOTE]
Taken from Gnome User Guide:
> 
Templates and Documents

You can create templates from documents that you frequently create. For example, if you often create invoices, you can create an empty invoice document and save the document as invoice.doc in the $HOME/Templates folder.

You can also access the templates folder from a file browser window. Choose Go  &#8594; Templates .

The template name is displayed as a submenu item in the Create Document menu.

You can also create subfolders in the template folder. Subfolders display as submenus in the menu.

You can also share templates. Create a symbolic link from the template folder to the folder containing the shared templates. 


---

### Post by tanari on 2004-11-26
thank you

---

### Post by da Wookiee on 2008-01-08
Thanks this post was very informative.

---

### Post by PinkFloyd102489 on 2008-01-08
I didnt know you could do this. Nice!

---

### Post by antisocialist on 2008-02-02
sweet thanks

---

### Post by slayer04 on 2008-02-02
whats the point?? sorry to be blunt but I don't see a point in making a blanks document,

---

### Post by PinkFloyd102489 on 2008-02-03
> **slayer04 said:**
> whats the point?? sorry to be blunt but I don't see a point in making a blanks document,

It's a template so that Ubuntu doesnt create a blank, extension-less file. Ive got loads of files in my Templates, ranging from PHP to Oo Presentation.


Also, you need to change a file. Open up ~/.config/user-dirs.dirs and edit the following:


Change
```
XDG_TEMPLATES_DIR="$HOME/"
```

to

```
XDG_TEMPLATES_DIR="$HOME/Templates"
```



Then throw all of your template files into ~/Templates.

---

