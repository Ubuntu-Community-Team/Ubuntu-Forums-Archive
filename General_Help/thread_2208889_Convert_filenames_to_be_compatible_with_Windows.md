---
title: "Convert filenames to be compatible with Windows"
date: 2014-03-02
forum: General Help
---

### Post by adrien-cordonnier on 2014-03-02
Hello,

I have an external hard drive with a NTFS partition. I would like to access its data both from Ubuntu and Windows. Yet, the files have been copied from Ubuntu and many of them have invalid characters for Windows ([COLOR=#333333][FONT=helveticaregular]/ ? < > \ : * | ")[/FONT][/COLOR]. There are way to many such files to rename them manually (several thousands). 

I thought it would be easy to find a tool to remove or replace the invalid characters automatically. Actually, I have not found. The closest solution is detox (a tool in the package of the same name). Yet it strips all accents, spaces, etc and keeps only [a-zA-Z0-9]. Too much information would be lost as many filenames are in French, Finnish, Russian or Polish. I have found quick and dirty scripts but they do not check if renaming would overwrite another file.

I would think that this filename problem of sharing data is quite common. Do you know any ready solution?

---

### Post by oldfred on 2014-03-03
I do not have solution to your issue, but to prevent it in the future mount NTFS with windows_names

 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
For ntfs UUID shown is example only see below:
UUID=XXXXXXXXXXX   /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

---

### Post by Vaphell on 2014-03-03
in case of forbidden chars *[noparse]rename 'y/:?<>|*"\\/.../'[/noparse]* should do the trick
first section of y/// lists chars to substitute, second lists their replacements in order, y/c1,c2,c3,.../r1,r2,r3,.../
so you can define exactly what you want. Stripping/replacing with a constant string/char can be done with the tried and true 's/[<chars>]/.../g'


```
$ touch '&#261;:&#281;?µ<&#359;>ð|f*&#331;\&#295;"i'
$ rename -nv 'y/:?<>|*"\\/12345678/' *[\:\?\<\>\|\*\"\\]*
&#261;:&#281;?µ<&#359;>ð|f*&#331;\&#295;"i renamed as &#261;1&#281;2µ3&#359;4ð5f6&#331;8&#295;7i
$ rename -nv 'y/:?<>|*"\\/-+!#$%^&/' *[\:\?\<\>\|\*\"\\]*
&#261;:&#281;?µ<&#359;>ð|f*&#331;\&#295;"i renamed as &#261;-&#281;+µ!&#359;#ð$f%&#331;&&#295;^i
$ rename -nv 's/[:?<>|*"\\]/-/g' *[\:\?\<\>\|\*\"\\]*
&#261;:&#281;?µ<&#359;>ð|f*&#331;\&#295;"i renamed as &#261;-&#281;-µ-&#359;-ð-f-&#331;-&#295;-i

```

-n is dry run, so drop it if you like what you see and want to actually perform the operation. *rename* also skips overwrites by default, unless told otherwise with *-f*, so it's safe.

---

