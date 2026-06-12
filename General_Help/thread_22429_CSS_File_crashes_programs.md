---
title: "CSS File crashes programs"
date: 2005-03-27
forum: General Help
---

### Post by Kakalto on 2005-03-27
I've been messing around with webpage stuff recently, and found a template on oswd with XHTML and Cascading Style Sheet files. Any of the templates I download from there, come in archives. But when I try to open the archive, the archive program crashes. 

So, I rebooted into windows, and successfully extracted the files to a FAT32 partition. I can see the css files fine under windows, and edit them freely.

However, I'd like to know why a these CSS files crash my programs. Whenever I try to enter the directory that the css file(s) is(are) in, nautilus crashes. If I try to edit the css file with gedit, gedit crashes. However, VIM, Nano, Cat all display the file fine under the terminal. 

GFTP doesn't crash when in the folder, and can upload files. So, if I upload the CSS along with its webpage, it displays fine under firefox. If I look at the page under firefox locally, it displays fine.

Leafpad also displays the file fine.

I even checked with w3schools that the CSS was valid, and it was >_> 
The url of the site on the net is [http://home.ps.gen.nz/~ewan/](http://home.ps.gen.nz/~ewan/)

Could someone please tell me what I'm missing? Or atleast why this happens?

---

### Post by dseomn on 2005-03-28
It works in gedit for me. It's probably a locale problem, what's the output of ```
locale
``` and ```
mount
```?
N.B. run mount when the FAT32 partition is mounted (i.e. when you can access files from it).

Also, what version of Ubuntu are you using?

---

### Post by kassetra on 2005-03-28
[QUOTE=Kakalto]Could someone please tell me what I'm missing? Or atleast why this happens?[/QUOTE]

1. The archives could be written from windows - with some unusual flags or just written poorly - and in that case sometimes they'll crash the archiver program on your system...

2. I'm suspecting that they were written in windows with some special flags or archival process - especially since windows opened them fine.

3. Because the files are causing some issues with nautilus and gedit, my suspicion is that the files may also be encoded improperly as well.  -- If you edit them in leafpad and save them as a different file - does gedit still crash?

4.  The css can be perfectly valid but the document itself could be improperly encoded... which would give you errors and headaches.

Try editing them in leafpad and saving them as a different file... that will most likely clean up and encoding issues... 

I can guarantee you that normal css files will not crash your system, I work with them everyday.  :)

---

### Post by Kakalto on 2005-04-06
Thanks, I think that was the problem. I've done that, and I now have no issues with it.

---

