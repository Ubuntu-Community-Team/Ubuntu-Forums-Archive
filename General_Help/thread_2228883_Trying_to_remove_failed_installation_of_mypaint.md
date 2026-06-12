---
title: "Trying to remove failed installation of mypaint"
date: 2014-06-10
forum: General Help
---

### Post by grey1beard on 2014-06-10
Having an old usb genius 5x4 tablet, I've tried plugging it in to my hp g7000 laptop, but to no avail.
It seems to detect it OK, and the cursor moves about(no mouse is installed currently), and reading that trying it mypaint would be a next test, I tried downloading it following the instructions on the Ub documentation page for Mypaint.
The final instruction  rm -r mypaint-0.7.1* produced an error(mypaint-0.7.1* didn't exist).
But I went to Applications/graphics and it seemed to be installed.
I launched it, but the tablet didn't work properly - it would select different brushes, and open menus, but not produce any visible strokes on the page, behaving like a mouse.
I could produce the same effect with the trackpad on the laptop( with or without the tablet plugged in).

I then decided to remove the package with synaptic, and having done so, I checked the applications/graphics menu, and  found the programme still present, but with a barred circle in red icon.
Mypaint still launches from it, and the version number is 0.7.1., as given on the 'About' menu.

I tried to download version 1.0 from the Mypaint site, and according to synaptic, I have
version 1.0.0-1 of mypaint, and of mypaint-data installed.

Please advise on how I can at least sort out mypaint before I tackle the tablet problem.

John

---

### Post by LastDino on 2014-06-10
```
sudo apt-get purge {program}
```

Use whatever synaptic is telling you which is installed of mypaint in place of ''program''.

---

### Post by grey1beard on 2014-06-10
Hi Last Dino,
It removed the program according to what synaptic reports, but the 0.7 version still exists on the application/graphics menu, and launches !

Regards,
John

---

### Post by grey1beard on 2014-06-10
Duplicate post

---

### Post by grey1beard on 2014-06-10
**Update**
I used the search tool to find mypaint and found ver 0.7  as a hidden file in my home folder !

What's the safest/cleanest way to get rid of this ?

---

### Post by LastDino on 2014-06-10
I've never came across something like that but have you tried to purge ver0.7 separately? And probably then run clean command.

---

### Post by Erik1984 on 2014-06-10
> **grey1beard said:**
> **Update**
I used the search tool to find mypaint and found ver 0.7  as a hidden file in my home folder !

What's the safest/cleanest way to get rid of this ?

Hidden folders (if you mean hidden by having a dot as first character of the name) in your home folder are a normal way (convention) to store the config of applications.

---

### Post by grey1beard on 2014-06-10
Sorry folks, it's not a hidden folder at all - my bad.
In my Home folder, it appears as **mypaint-0.7.1**
So in Terminal - 

> john@john-HP-G7000-Notebook-PC:~$ sudo apt-get purge mypaint-0.7.1
[sudo] password for john: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package mypaint-0.7.1
E: Couldn't find any package by regex 'mypaint-0.7.1'

Now puzzled(not for the first time), so grateful for someone to point out what I'm doing wrong.

John

---

### Post by grey1beard on 2014-06-11
I've done a search for all instances of mypaint, and have attached the screen prints, just in case that gives anyone a clue to the solution.

John

---

### Post by grey1beard on 2014-06-12
Having no other ideas, what if I were to individually remove each file/folder that the Mypaint search brings up ?

It seems like a very slow method, but does anyone have a better solution ?

John

---

### Post by grey1beard on 2014-06-12
I've started by using synaptic to 'remove completely'  *mypaint ver 1.0.0-1* and *mypaint data*, which was all it listed.
I then opened my home folder with hidden files visible, and sent *mypaint-0.7.1* and *.mypaint* to the rubbish bin.
I then did a new search for mypaint, and the attached screen shot shows the situation now.
I am planning to remove these, possibly one at a time, using Terminal, unless I have any postings on this thread in the next 24 hours offerring an alternative suggestion.

John

---

