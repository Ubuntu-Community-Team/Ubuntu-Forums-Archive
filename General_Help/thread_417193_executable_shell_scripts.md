---
title: "executable shell scripts"
date: 2007-04-21
forum: General Help
---

### Post by tallguy1967 on 2007-04-21
Does any body know how to make a shell script just execute when double clicked, rather than a text box popping up and being asked "Do you want to run "test.sh", or display its contents?".

Thanks in advanced.

---

### Post by dreadlord_chris on 2007-04-21
right-click the file, select Properties > Permissions > check the box *Is Executable* > OK

---

### Post by tbroderick on 2007-04-21
Or open a terminal and type;
```
chmod +x /path/to/test.sh
```

---

### Post by tallguy1967 on 2007-04-21
Thanks to you both. The file is executable, I used the chmod method. When I have created batch files in Windows and double click them, they just execute however shell scripts in ubuntu give me a pop up window asking me if I want to;-

Do you want to run "test.sh", or display its contents?

Underneath this there are four options. If I select run the file runs. I was wandering if it is possible to have the file just execute when it was double clicked and not make me click another button.

---

### Post by kevinlyfellow on 2007-04-21
I don't think you can specify individual files to execute without being asked, but...

In nautilus go to edit -> preferences

Under the behaviour tab, there are options for "Executable text files"

---

### Post by tallguy1967 on 2007-04-21
kevinlyfellow that is Fantastic!!!!!


I have done that and it works a treat, Thanks to everybody for your help with this.

---

