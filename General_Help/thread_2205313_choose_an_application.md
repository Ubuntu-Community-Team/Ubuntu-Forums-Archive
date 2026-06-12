---
title: "choose an application"
date: 2014-02-13
forum: General Help
---

### Post by Brotell1950 on 2014-02-13
I have some pdf's waiting but all I get when I try is a box containing choose an application what is my way around this.

Regards

Terry

---

### Post by PotatoHead007 on 2014-02-13
Hey :) First check that your PDF documents actually have a .pdf extension.
If they do and you still get the error, try this:
```
sudo apt-get install evince 
```
This will install a program that can view PDF files, and it comes pre-installed with Ubuntu, maybe not with Kubuntu(?)

---

### Post by ajgreeny on 2014-02-13
If you want to stay more with the qt/kde style, install **okular**; evince will pull in several gtk/gnome dependencies, I think.

---

### Post by mastablasta on 2014-02-13
> **Brotell1950 said:**
> I have some pdf's waiting but all I get when I try is a box containing choose an application what is my way around this.

Regards

Terry

chose the propper applicaiton (okular). if Okular is not installed install it and then try to open it again.

---

### Post by Brotell1950 on 2014-02-15
Already have okular but unable to choose it as an application

Terry

---

### Post by SeijiSensei on 2014-02-16
If you right-click on a file with a .pdf extension, it should offer you the "Open With" option.  Okular should be one of the entries there on any recent Kubuntu system.  If not, choose "Other" in that menu, select Okular, and check the box to make it the default application for PDF files.

You can manage all default applications by using System Settings > File Associations.  This associates applications with "mime types" like "application/pdf".  You don't need to know the full mime type; searching for "pdf" brings up the appropriate dialog box as well.  You can add or remove applications associated with a mime type or reorder the list to make sure your preferred application is at the top.

---

