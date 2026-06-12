---
title: "unicode support from file roller?"
date: 2013-02-06
forum: General Help
---

### Post by cjohn124 on 2013-02-06
Hi,

I downloaded a zip file with its name containing Chinese characters, and they are in unicode. Well, it could be displayed well in my terminal if I use "ls" command.

But, when I tried to use file roller (archive manager) to show its content, it displays a folder name showed as "?????". I knew it is a Chinese-character folder name in the zip file, and it can be showed well in Windows XP.

But how to let file roller translate those "?????" into native Chinese characters?

My Ubuntu version is 12.04.

[Update]:
Later, I tried to install 7-zip with "sudo apt-get install p7zip-full",  it finished well without any problem. Now when I open the same zip file  with archive manager (file roller) again, the "?????" characters are  gone, but the folder name is still unrecognisable, as can see from the  attached screen shot.

[IMG]http://cjohn.webs.com/tmp/fileroller_chn.png[/IMG]

Any idea to make it display Unicode character correctly?

By the way, it looks like file roller uses 7-zip as its back-end tool to open zip files once I have it installed. But I didn't find any place this association is set up. Any suggestions?

---

### Post by cjohn124 on 2013-02-07
Anyone please help? Thanks.

---

### Post by Vaphell on 2013-02-07
zip is not really a unicode friendly format and afaik uses codepages. Older windows systems do that too, there are separate codepages for arabic, western, central/eastern european, hindi, far east languages and if you use the wrong one, you see garbage.

---

### Post by cjohn124 on 2013-02-07
Sad news. But isn't there a cure?

---

### Post by cjohn124 on 2013-02-07
Answer from a Chinese forum:

The file is GBK encoded, not UNICODE.

But it could be extracted correctly  in command line:
unzip -O CP936 xxx.zip

Still, I want to know if there is a way to view the zip file's content directly in the GUI of Archive Manager.

---

