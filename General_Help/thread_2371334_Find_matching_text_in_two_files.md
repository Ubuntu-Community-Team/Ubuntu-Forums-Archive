---
title: "Find matching text in two files"
date: 2017-09-13
forum: General Help
---

### Post by andrew772 on 2017-09-13
Hello. Does such a program exist that can be used to search two text files and return a list of text that is in both files? so it's not a straight compare and I'm not specifying what text to search for, it just returns text that is in both files, with a minimum length of say three characters so it doesn't just give me a list of full-stops, etc? Thanks.

---

### Post by vasa1 on 2017-09-13
Have you looked at *grep*?
```
$ grep -n gatekeeper stylish.txt stylish2.txt
stylish.txt:237:@namespace xul url(http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul);
stylish.txt:1304:@namespace url(http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul);
stylish.txt:1599:@namespace url(http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul);
stylish2.txt:237:@namespace xul url(http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul);
stylish2.txt:1304:@namespace url(http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul);
stylish2.txt:1599:@namespace url(http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul);
$
```

---

### Post by andrew772 on 2017-09-13
I have used grep but unfortunately it doesn't seem to be able to do what I need. I don't want to specify an exact string to search for, I want it to tell me what text is in both. I guess in your example it would be something like

```

$ somecommand stylish.txt stylish2.txt
@namespace xul url(http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul);
@namespace url(http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul);
@namespace url(http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul);
$

```

---

### Post by vasa1 on 2017-09-13
So you want to find common strings in each file? Look at the *comm*command.

---

### Post by andrew772 on 2017-09-13
comm nearly does what I need it to! I want to be able to find common strings and not just common lines, the matches could also be in totally separate parts of the files. I can't just sort them either because the formats are different.

---

### Post by vasa1 on 2017-09-13
You had better provide actual examples so that people can address your needs properly. And what you mean by different formats?

---

### Post by andrew772 on 2017-09-13
They are both text format files but one is XML the other is CSV. Example usage could be one which searches a dictionary file with a list of baby names, to return a list of all baby names which are actual words. I'm trying to side-step any actual XML and CSV file parsing by doing a raw commonality search.

---

### Post by untrustytahr on 2017-09-13
> **andrew772 said:**
> I have used grep but unfortunately it doesn't seem to be able to do what I need. I don't want to specify an exact string to search for, I want it to tell me what text is in both. I guess in your example it would be something like

Grep can do darn near everything except make coffee if you look hard enough.:D

Have you tried
```
grep -Fwf file1 file2
```

file1 would be the search string file.  File2 would be the file being searched.

---

### Post by andrew772 on 2017-09-13
I need to buy a book on grep or something! It seems to work, but has highlighted another unrelated issue I need to resolve, so this thread is as good as solved now, thanks!

---

