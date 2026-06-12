---
title: "Windows Ubuntu File system"
date: 2008-04-22
forum: General Help
---

### Post by happysubby on 2008-04-22
Hello,

I was just wondering if there is a way for me in my machine (ubuntu 7.10 and windows xp dual boot) where, I can access files stored in ubuntu filesystem when I have booted windows. I know the other way around ( windows files from ubuntu) is possible if I go to places and computer. 

thanks

---

### Post by Pettman on 2008-04-22
There are to my knowlage at least 2 ext2/3 drivers available for windows, [http://www.fs-driver.org/](http://www.fs-driver.org/) and [http://sourceforge.net/projects/ext2fsd](http://sourceforge.net/projects/ext2fsd) (the first is probably the easiest to use and I think you should avoid creating files under windows as neither could make windows understand file-privileges)

---

### Post by Jammy4041 on 2008-04-22
Welcome to the Forums!

The reason why your windows partition cannot access your ubuntu partition is that windows only reads and writes to NT File System (Windows XP, Windows Vista, Windows 2000/NT etc and FAT (FAT 32 For Windows 98/ME and FAT 16 for Windows 95. 

Ubuntu, and indeed Linux, for that matter is (usually) formatted as Ext2 or Ext3. There's is not really anything to tell between them, except Ext3 supports journalling (NTFS supports journalling too -that's why it's better than say, FAT 16) 

The answer to your question is indeed yes: Ext2IFS- it installs on your windows control panel, you can assign your ubuntu partition a drive letter, like U:\. It includes a driver to let all windows apps natively access, read and write to your ubuntu partition.

You can download it here: [http://www.fs-driver.org/download.html](http://www.fs-driver.org/download.html)

Yes, you do lose the journalling functions,of your Ubuntu partition, but I don't really see that being a loss. 

In gParted, my Ubuntu partition is recognised as ext3. But when I'm in Windows XP, If I go to my Ubuntu drive in My Computer, select properties, it is recognised as ext2. (Strange!) If you really want f-s driver to let windows recognise your ubuntu partition as ext3, it's a bit risky. If however you want to take the plunge and make f-s driver recognise your ubuntu partition as ext3 visit [http://www.fs-driver.org/faq.html](http://www.fs-driver.org/faq.html)

I hope this helps

---

### Post by happysubby on 2008-04-22
cool thanks.

I am going to try it out!!

---

### Post by Jammy4041 on 2008-04-22
You are very welcome. Do feel free to psot anytime here. If there are any problems or you have any sugesstions with f-s driver you can email the project page [here]("mailto:info@fs-driver.org")

---

