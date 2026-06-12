---
title: "Inserting newlines into text file using tr or sed or awk"
date: 2013-01-21
forum: General Help
---

### Post by sabersong on 2013-01-21
I've got a rather large text file, specifically a hosts file, that isn't formatted properly. It's all one line. I need to put a newline before every occurence of 127.0.0.1. I can't find a way to do it easily in Kate or LibreOffice, and I don't really understand enough about sed or awk to be able to figure it out. I tried using tr, but got varied results, some close, but none right. Most recently, I tried the example below, but it took out all the "127.0.0", and put "1" in a lot of places I didn't want it.

```
cat hosts | tr "127.0.0.1 " "\n127.0.0.1 " > newHosts
```

I'm new to this aspect of Linux, and I know I have a lot of reading to do to really understand tr and sed and awk, but can someone help me with this particular example?

---

### Post by steeldriver on 2013-01-21
```
sed 's/127.0.0.1/\n&/g'
```maybe? 'tr' only translates a single character at a time, I think

---

### Post by sabersong on 2013-01-21
> **steeldriver said:**
> ```
sed 's/127.0.0.1/\n&/g'
```maybe? 'tr' only translates a single character at a time, I think

That did it! Thanks so much for the help.

---

