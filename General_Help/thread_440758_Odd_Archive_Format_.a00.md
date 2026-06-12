---
title: "Odd Archive Format: .a00"
date: 2007-05-11
forum: General Help
---

### Post by nikki on 2007-05-11
Well, I was looking for some old files and stumbled upon an old source for this archive I wanted in a different format. I ended up finding it on a korean site with the extension .a00. An extension I've never seen before. I did a little bit of searching, and I can't find much on this extension. Is anyone perhaps able to shed some light on this format or a way I could try to open it? I did searches in synaptic and a quick google search, but I didn't find anything. The forums also didn't seem to have previous posts on this format.

Edit: Also, I have found it on the same site with the compression .alz , another format I'm not familiar with and can't seem to find for Ubuntu.

Thanks.

---

### Post by nikki on 2007-05-12
From what I've seemingly found, .a00 is only a part of a whole archive. Then, some other program is supposed to piece them together into one archive.

.alz seems to be a full archive. It seems to just be a korean format that is like .zip without a size limit. This is a link to the .alz site for the format: [http://www.altools.co.kr/main/main.aspx]("http://www.altools.co.kr/main/main.aspx"), however the site in English seems to be here: [http://www.altools.net/ALTools/ALZip/Features/ALZFormat/tabid/114/Default.aspx]("http://www.altools.net/ALTools/ALZip/Features/ALZFormat/tabid/114/Default.aspx") 

It seems Ubuntu just doesn't have support for opening this archive format.

---

### Post by nikki on 2007-05-12
Seems their free software to open the archive works through wine. Would be nice to see it natively supported however. The way it works, is that you get a .alz file and a bunch of smaller chunks of the archive. .alz is the file that puts all these chunks together into one archive. The smaller files like .a00 .a01 are the pieces for the .alz file.

---

### Post by qpieus on 2007-05-12
Your file could also be one part of a multi volume arj archive. arj was an archiving program that had some mild popularity in the mid 90s on usenet, although rar soon pushed arj off to the side.
It looks like there is an unarj program for linux according to a quick google search. You might be able to extract your file if you can install this unarj program.

---

### Post by sureinlux on 2008-04-13
Hi there,
 for extracting .a00 and .alz files, there IS a package by the name ```
unalz
``` in universe repos. Hope this helped.

---

