---
title: "Default programs to open files?"
date: 2006-12-16
forum: General Help
---

### Post by JMO707 on 2006-12-16
Is there anyway to choose the default programs to open a file extension with Nautilus?

---

### Post by hikaricore on 2006-12-16
> **JMO707 said:**
> Is there anyway to choose the default programs to open a file extension with Nautilus?

Yes this is very simple :)

Right click on the type of file you would like to change the opener for, and chose properties.  There should be an "Open With" tab at the top of the properties window, click on this and you can choose on of the options in there or you can add your own with the button at the bottom.

My info here might be a little be off as I'm at the office and I have kubuntu installed here, so I'm going from memory, but this should get you on the right track.

--Aaron

---

### Post by JMO707 on 2006-12-16
Haha, silly me :p

Thanks!

---

### Post by JMO707 on 2006-12-19
Mmm, I got a situation here:

[[IMG]http://img82.imageshack.us/img82/8239/pantallazotr2.th.png[/IMG]](http://img82.imageshack.us/my.php?image=pantallazotr2.png)

I cant avoid that the .odt document keep being open with "Java" =(

---

### Post by hikaricore on 2006-12-19
Does that document have anything in it that is using java script?  It may be an issue with your mime types seeing the file header wrong.  I've had this happen with other files before, usually they were corrupt or the file header was bad.  Try resaving it after opening it up in Open Office from the File Open menu in the program.  Otherwise I'm a little stumped.

You may also want to see what mime type linux thinks file thinks the file is in the Basic (Basico) Tab.

---

### Post by JMO707 on 2006-12-19
I solved it re-saving them. The mime type were "x-java" or something like that =)

Thanks again.

---

### Post by hikaricore on 2006-12-19
No problem :)

---

