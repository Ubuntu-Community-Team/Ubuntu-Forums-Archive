---
title: "opening text files"
date: 2008-02-13
forum: General Help
---

### Post by theovn on 2008-02-13
Hello there,

When I double click a .txt file, I get the message: Do you want to run <file name>, or display its contents?
When I right click on the file, I see under menu: "Properties > Open With" that "Text Editor" is the standard choice.
However, it stays coming back with the first question.

How can I get Ubuntu to start Gedit directly, when double clicking a *.txt file?

Regards and thank you,
Theo

---

### Post by joeashcraft on 2008-02-13
Maybe the text file you're trying to edit is an executable script.
To test this theory, **create a new empty file. Then double-click to open the file**. It should not give you Run as an option because an empty file can't be executed

---

### Post by kpkeerthi on 2008-02-13
> How can I get Ubuntu to start Gedit directly, when double clicking a *.txt file?

Open nautilus (double-click on Home icon on your desktop)
Edit->Preferences -> Behavior tab -> Select "*View executable text files when they are clicked*"

---

### Post by theovn on 2008-02-13
> **kpkeerthi said:**
> Open nautilus (double-click on Home icon on your desktop)
Edit->Preferences -> Behavior tab -> Select "*View executable text files when they are clicked*"
I am using Gnome and don't have a "Nautilus" icon on my desktop.
How should I activate it otherwise?

---

### Post by theovn on 2008-02-13
In my home directory, I do see the nautilus-debug-log.txt, which opens directly when I double click it. But I don't see any difference with other .txt files.

---

### Post by kpkeerthi on 2008-02-13
> 
I am using Gnome and don't have a "Nautilus" icon on my desktop.
How should I activate it otherwise?

> 
Open nautilus (double-click on **[COLOR="Red"]Home icon[/COLOR]** on your desktop)
Edit->Preferences -> Behavior tab -> Select "View executable text files when they are clicked"


Click on Places -> Home. The window that appears is called nautilus which is the File Manager for Ubuntu/GNOME

Open a terminal and type **nautilus** and press <enter>

[More about nautilus]("http://www.google.com/search?q=nautilus+gnome")

---

### Post by theovn on 2008-02-14
Thank you Kpkeerthi,
It works fine now.
Regards,
Theo

---

