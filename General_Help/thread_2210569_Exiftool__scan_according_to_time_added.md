---
title: "Exiftool : scan according to time added"
date: 2014-03-11
forum: General Help
---

### Post by vikler on 2014-03-11
[COLOR=#000000][FONT=Verdana] I have a folder that contains many .jpg files, and every day new files add. I clean older files from time to time, but still there are a lot of them. I scan them all with exiftool to make sure I don't miss files I need (containing specific information in Caption-Abstract tag). [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]However, it takes A LOT of time to scan all files. So I was wondering if it was somehow possible to only scan files that were added today? Or in last hour? Something similar to [/FONT][/COLOR]**find**[COLOR=#000000][FONT=Verdana]'s [/FONT][/COLOR]**-mtime**[COLOR=#000000][FONT=Verdana] option.[/FONT][/COLOR]

---

### Post by tgalati4 on 2014-03-11
This function is normally done with a photo manager, such as *shotwell*.  Do you currently use a photo manager?

Use *find* with the -mtime switch then pipe the results to exiftool to narrow down the search.

---

