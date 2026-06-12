---
title: "how to install IE explorer using WIne?"
date: 2007-05-07
forum: General Help
---

### Post by onlybui on 2007-05-07
Hi I have IE explorer installed using IEs4Linux but the thing is I need to install a different program that requires IE explorer using Wine,  So I'm guessing I need to install IE explorer using WIne and it gives me this

process  tid      prio (all id:s are in hex)
0000000c 
        0000000e    0
        0000000d    0
0000000a (D) C:\windows\temp\IXP000.TMP\ie6wzd.exe
        00000010    0 <==
        0000000f    0
        0000000b    0
00000008 
        00000009    0


I need to install Internet Explorer 4.01 SP1 or later....

---

### Post by hikaricore on 2007-05-07
[http://www.tatanka.com.br/ies4linux/page/Installation](http://www.tatanka.com.br/ies4linux/page/Installation)

---

### Post by liorwohl on 2007-05-07
copy folder: _~/.ies4linux/ie6_ to _~/_
delete folder: _~/.wine_
and rename the "ie6" folder you have copy before to ".wine"

this will remove your current wine applications but then you will have IE6 and you will be able to reinstall everything again and to install the application which require IE.

(some folders are hidden, to see them click _View->Show Hidden Files_ on the file browser)

---

### Post by onlybui on 2007-05-09
Ok I did that now it just shows grey with next and cancel and it wont install...

getthing this error 
fixme:propsheet:PROPSHEET_CollectPageInfo Could not load resource #0000?
err:win:CreateWindowExA bad class name "RICHEDIT"
err:win:CreateWindowExA bad class name "RICHEDIT"

---

### Post by derek45 on 2007-05-11
not sure if this wil help or not . . . . .

[http://www.psychocats.net/ubuntu/ies4linux]("http://www.psychocats.net/ubuntu/ies4linux")

---

