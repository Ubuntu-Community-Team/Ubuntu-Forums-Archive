---
title: "Find (Solved)"
date: 2006-10-22
forum: General Help
---

### Post by Dylan103 on 2006-10-22
I have this game called Linerider, I downloaded the .swf, and made a html that had iframe to include it, i saved it, and want to find the file.
On a site it says to find it do this

2. Navigate to your documents and settings folder in windows explorer. Then go to the folder with your logon name, application data, macromedia, flash player, shared objects, there will be a folder with a lot of numbers open it, find the localhost folder, and navigate to the folder you saved the lineflyer program.

How would I do that on ubuntu? The filetype is .sol

---

### Post by aysiu on 2006-10-22
Paste these commands in the terminal: ```
sudo updatedb
locate sol
locate rider
``` The first command will take a few minutes.

---

### Post by Dylan103 on 2006-10-22
"locate rider"
Worked. Thanks

---

### Post by nikoPSK on 2007-11-25
thanks alot aysiu! That was a load off my shoulder's:p. 

@dylan, you're using this cause of inkskape?

---

### Post by nikoPSK on 2007-11-25
It's only finding tracks form the web version, not saying thats bad, but I would like it to find tracks from the swf I'm opening with firefox from my desktop.

---

