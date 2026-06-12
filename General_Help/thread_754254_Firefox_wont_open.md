---
title: "Firefox wont open"
date: 2008-04-13
forum: General Help
---

### Post by Priamo on 2008-04-13
Everytime i click on the firefox icon, in the bottom says: Starting firefox... after several seconds it just closes.

---

### Post by tango_ninja on 2008-04-13
What version of firefox are you using? also, have you verified that the launcher path is pointing to the program?

try starting in terminal:
```
firefox
```

---

### Post by Sidewinder1 on 2008-04-13
If Tango's advice does not work, you could always try reinstalling Firefox. If you can find where your bookmarks are stored make a copy in another directory. Then go to Synaptic Package Manager and remove (uninstall) Firefox. Then 'mark for installation' Firefox and Firefox Gnome Support; then 'apply changes". HTH

---

### Post by Priamo on 2008-04-13
Im using the Version that the Gutsy brings

---

### Post by ibutho on 2008-04-13
Have you tried what tango_ninja suggested? Try it and post back the output.

---

### Post by Priamo on 2008-04-13
Yes i did, Nothing happend
and my Firefox version is 2.0.0.13
Why should i do :S
and when i try to install Opera Web Browser i have problems with dependencies...
:S ubuntu hasnt treat me well :(

---

### Post by sekinto on 2008-04-13
Did the "firefox" command not give you any output?
Also, what are your dependency issues when you try to install Opera?

---

### Post by Priamo on 2008-04-13
Nope it didnt give me any output...
libc6 when trying to install the .deb package

---

### Post by tango_ninja on 2008-04-13
hmmm try a remove/reinstall?
```
sudo apt-get remove firefox
sudo apt-get install firefox
```

---

### Post by Priamo on 2008-04-13
Yeah im going to try that.
If that dosent work im going just to remove ubuntu from my pc and install it again

---

### Post by fragos on 2008-04-13
I had this problem a couple of times and found If I dragged a plain text file to the Firefox icon it would start displaying file contents. Once started it seemed to act normally. I have no understanding of this but sometimes a little simple experimentation can get you going.

---

