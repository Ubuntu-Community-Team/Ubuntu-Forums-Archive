---
title: "Encoding problem /Bluefish/CP1256"
date: 2008-03-17
forum: General Help
---

### Post by recreativo on 2008-03-17
I have a website which uses the encoding cp1256(Arabic), I developed it in Windows, when I  open the files with bluefish it doesn't recognize the arabic text(it appears as ???), and in the the preferences window of bluefish I can't find this encoding

I enabled Arabic. I can write in Arabic and even name files in Arabic ... I am also able to write in arabic in bluefish, but using UTF-8 encoding, I know I can convert the files to UTF-8 but I really want to use cp1256, because my database is using this encoding,,

It seems I need to do something extra to make bluefish recognize the cp1256 encoding,,, any idea how to do this? any recommendations for another PHP editor which supports this encoding?

thank you in advance

---

### Post by recreativo on 2008-03-17
Solved! 
bluefish doesn't include the cp1256 automatically, one has to add it to config file, or open a html file that has  the encoding explicitly written between headers, my pages were in php and the encoding was not visible to bluefish:)

---

### Post by amelie on 2008-04-04
Hello, recreativo!
How did you add the new encoding to the config file ( I have the same problem as you did  ;) )

---

