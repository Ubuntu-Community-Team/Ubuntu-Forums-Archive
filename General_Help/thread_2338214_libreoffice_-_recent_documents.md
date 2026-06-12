---
title: "libreoffice - recent documents"
date: 2016-09-25
forum: General Help
---

### Post by Kevin McCready on 2016-09-25
Hoping someone can help me change the way "recent documents" works.

When I open calc I ONLY want to see the last spreadsheets.
When I open the writer I ONLY want to see the last word documents.
etc

Thanks in advance. I've been tearing my hair out, what's left of it.

---

### Post by vasa1 on 2016-09-25
In case there's no solution from within LibreOffice, schragge's code in your older thread still works:
Source: [Lubuntu - script for "recently used" files]("http://ubuntuforums.org/showthread.php?t=2125130")

---

### Post by Kevin McCready on 2016-09-26
Thanks Vasa
Here it is
```

find -ctime -1 -type f -exec bash -c 'select f;do [[ -n $f ]]&&xdg-open "$f"||exit;done' _ '{}' +

```
Can you help me modify it to only give me files with a certain extension that I've accessed in the last month?

---

### Post by vasa1 on 2016-09-26
```
find ~/Dropbox/ -iname "*.ods" -mtime -30 -type f -exec bash -c 'select f;do [[ -n $f ]]&&xdg-open "$f"||exit;done' _ '{}' +
```will find only spreadsheets in my Dropbox folder (because of ".ods") and mtime -30 should provide simpler output than ctime.

• mtime — the time that the contents of a file were last modified
• atime — the time that a file was read or accessed
• ctime — the time that a file’s status was changed

I think someone with more coding skills can get that stuff into Zenity (or something like that) so you won't need to use a terminal.

---

### Post by howefield on 2016-09-26
There is an extension called [History Master]("http://extensions.openoffice.org/en/project/history-master").

Not sure how well this works as it is pretty old, but have tested on Libreoffice and it seems to be ok. YMMV.

---

### Post by Kevin McCready on 2016-09-26
Cool. Thanks Vasa. Awesome. People have been encouraging me to learn how to write scripts but I think the learning curve to get to that level would take a while. Seriously, how long would it take to learn do you think (I know it's a how long is a piece of string question)?

---

### Post by vasa1 on 2016-09-26
> **howefield said:**
> There is an extension called [History Master]("http://extensions.openoffice.org/en/project/history-master").

Not sure how well this works as it is pretty old, but have tested on Libreoffice and it seems to be ok. YMMV.

Can it be set to show just recent Calc files or just recent Writer files? I've disabled Recent Files  in LibO and so I don't know what it does.

Edit 
HM 1.1.1 offers what OP wants: > Find recent documents of a same typeI could install it in LibreOffice 5.2.1.2 (although I'll stay with Kupfer for my needs).

---

### Post by howefield on 2016-09-26
> **vasa1 said:**
> Can it be set to show just recent Calc files or just recent Writer files? 

Yes... turns a list of recently opened documents like this

[ATTACH=CONFIG]271363[/ATTACH]

into this after filtering for spreadsheets.

[ATTACH=CONFIG]271364[/ATTACH]

---

