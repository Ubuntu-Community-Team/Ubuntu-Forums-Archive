---
title: "print to file as default"
date: 2015-12-30
forum: General Help
---

### Post by cmcanulty on 2015-12-30
I have seen this asked before but no satisfactory answer. I would like to set "Print to File" as the default printer, not print pdf as the print to file lets you select the folder to print to and type your own title. 90% of the time I print to pdf rather than hard copy. I can select print to file every time but it would be nice to make that the default. Thank you

---

### Post by DuckHook on 2015-12-30
You need to define a virtual pdf device as an actual printer before you can select it as a default. Years ago, I recall doing this by installing the package:```
sudo apt-get install cups-pdf
```but my knowledge is very rusty. Haven't used it for years. Don't know if it conflicts with anything else. Give it a whirl and see if it fits the bill. If memory serves, after install, you need to add a printer, but you should now have an option of "PDF Generic" or something like that.

---

### Post by cmcanulty on 2015-12-30
that does just as I said you can pick default pdf but no option of where to save it or what to name it, which print to file does

---

### Post by DuckHook on 2015-12-30
Now that you mention, I do recall that you are correct. Its output options are very primitive. No save dialogue or naming option. It gets you one step closer at least, by giving you ability to declare a default, but the minuses are worse than this one plus.

I don't have any other ideas. Sorry.

---

### Post by cmcanulty on 2015-12-30
thanks, maybe someone else will have a solution seems rather odd print to file always appears as an option but can't be set to default. If I knew the correct config file maybe it could be edited manually.

---

### Post by monkeybrain20122 on 2015-12-30
since you use print to file all the time just remove cups-pdf.

---

### Post by cmcanulty on 2015-12-31
OK but what I am asking is how to make print to file the default

---

### Post by monkeybrain20122 on 2015-12-31
> **cmcanulty said:**
> OK but what I am asking is how to make print to file the default

Yeah but it is the same thing in the end. If cups-pdf, which you don't use anyway, is not present then the only thing left would be the default, wouldn't it?

---

### Post by cmcanulty on 2015-12-31
no I have several printers for different locations

---

### Post by monkeybrain20122 on 2015-12-31
Google turned up some very old threads
[http://ubuntuforums.org/showthread.php?t=1228123](http://ubuntuforums.org/showthread.php?t=1228123)
[http://ubuntuforums.org/showthread.php?t=1043339](http://ubuntuforums.org/showthread.php?t=1043339)

---

