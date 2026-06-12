---
title: "Encoding for Bluefish 1.0.7 ?"
date: 2008-04-04
forum: General Help
---

### Post by amelie on 2008-04-04
Hello, there!
I'm very new in Ubuntu =) I've just installed the Bluefish HTML editor but unfortunately it doesn't support Bulgarian, so I have unknown symbols in my pages... I thought I need an encoding but Google didn't help me :confused: 
Thanks in advance if someone knows how to fix this...

---

### Post by Peter76 on 2008-04-04
What I understand of it, try UTF-8. And set your encoding to utf-8  in your source as well

---

### Post by amelie on 2008-04-05
Hello, Peter =) 
thank you very much for the answer.
I saved it in UTF-8 - is that what I am supposed to do? Because that's the problem itself - when I save it in UTF-8 everything written with my language (Bulgarian) is hieroglyphs...

---

### Post by Peter76 on 2008-04-05
Under edit -> preferences -> files, set default character set to UTF-8.
Just to be sure start bluefish again and make a new document. Start with the HTML mentioned here:

[http://www.w3.org/QA/2002/04/valid-dtd-list.html](http://www.w3.org/QA/2002/04/valid-dtd-list.html)

This will trigger your ( or ) any browser in using UTF-8.
You can also do this in Bluefish under Dialogs -> general -> quickstart.
In this part of the html : 

<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">

set the xml:lang= and the lang= value to your language. 
Hope this helps, because this is as much as what I understand from character encoding I guess...

---

### Post by amelie on 2008-04-05
Thank you very very very much - I think I've fixed it after these explanations =)

---

### Post by Peter76 on 2008-04-05
:-)

---

