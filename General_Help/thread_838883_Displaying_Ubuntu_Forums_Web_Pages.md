---
title: "Displaying Ubuntu Forums Web Pages"
date: 2008-06-23
forum: General Help
---

### Post by TopEnder on 2008-06-23
Good day Al & Thanks in Advance,

I have problems in displaying Ubuntu Forums Web pages in both Epiphany 2.22.2 and FireFox 3.0.  Pages only partially load The only clue I have is from Epiphany's Tools/ Error Viewer or Firefox Tools/ Error Console / Warnings: - 
[SIZE="1"][COLOR="Blue"][SIZE="3"]CSS Parser error in [http://ubuntuforums.org/clientscript/vbulletin_css/style-88077170-00098.css](http://ubuntuforums.org/clientscript/vbulletin_css/style-88077170-00098.css) on line 484 and column 22:
Error in parsing value for property 'text-decoration'.  Declaration dropped.[/SIZE][/COLOR][/SIZE]

[COLOR="Blue"][SIZE="1"]CSS Parser error in [http://ubuntuforums.org/showthread.php?t=773851:](http://ubuntuforums.org/showthread.php?t=773851:)
Error in parsing value for property 'display'.  Declaration dropped.[/SIZE][/COLOR]"

Any help in solving this problem would be appreciated.

---

### Post by rraj.be on 2008-06-23
Try this.

```
sudo update-alternatives --config java


sudo update-alternatives --config javac
```

---

