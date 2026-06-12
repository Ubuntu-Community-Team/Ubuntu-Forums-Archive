---
title: "Update"
date: 2013-04-20
forum: General Help
---

### Post by vlgngl on 2013-04-20
Hi friends the command when &#305; tried to run the command "sudo apt-get update" the message in below was seen in terminal shell ;

~$ sudo apt-get update
E: Malformed line 56 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.

 what is the problem and what can i do anyone help me .?

---

### Post by grahammechanical on 2013-04-20
The problem? > [COLOR=#000000]E: Malformed line 56 in source list /etc/apt/sources.list (dist parse)[/COLOR]

You can access sources.list in a text editor. You cannot edit it without opening the editor with administrator privileges. This is what line 56 in my sources.list says

> deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) raring main

I am using Raring. What are you using? 12.10 (quantal)? 12.04 (precise)? The line will change accordingly. But more importantly what does line 56 of your sources.list say? This is line 56 in my 12.10 installation.

> deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) quantal main

Open your file manager and browse to file system (computer in 13.04) open the etc folder. Then the apt folder and right click sources.list and open with text editor. Show us what is there, please. Oh, once the text editor is open go to Edit>Preferences and you can set line numbering in the editor. That would be useful in this case.

Regards.

---

### Post by btindie on 2013-04-20
What's the output of
```
sed -n 56p /etc/apt/sources.list
```

---

### Post by vlgngl on 2013-04-20
the 56. row is "sed -n 56p /etc/apt/sources.list
deb [http://archive.canonical.com/](http://archive.canonical.com/) quantalpartner"

---

### Post by mörgæs on 2013-04-20
There should be a space between quantal and partner.

---

### Post by vlgngl on 2013-04-20
I am using ubuntu 12.10 32 bit
I don't exactly understand what will I do at [About problems due to upgrading]("http://ubuntuforums.org/showthread.php?t=1946145") 
Could you tell me

---

### Post by mörgæs on 2013-04-21
The text at the bottom below the line is called a signature, and it's part of all posts (like this one).

---

