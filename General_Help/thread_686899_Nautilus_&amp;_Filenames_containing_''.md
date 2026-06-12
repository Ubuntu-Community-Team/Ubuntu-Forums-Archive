---
title: "Nautilus &amp; Filenames containing '/'"
date: 2008-02-03
forum: General Help
---

### Post by Xyem on 2008-02-03
Just a quick question really about filename handling by Nautilus.

My other half saved an image ( from Firefox ) which contained several '/' characters. I thought this character was a restricted character ( due to it being the path separator ).

This came up as a problem when she tried to move the file from the desktop to another folder and an error dialog came up stating 'Invalid Parameters'. Renaming the file to not have '/' in it fixed the problem and let it be copied.

Am I correct in believing that '/' is a restricted character? And if so, why did Nautilus have no problem renaming the file but fail to copy it to another location?

Thanks for any input you can provide

---

### Post by ellis rowell on 2008-02-03
Yes it is a restricted character, I find it best to use - or _ for separating words. Even using a space can cause problems with file names, Some software cannot load files with names which contain spaces.

---

### Post by Xyem on 2008-02-04
I have come across such software before and my usual fix was to replace it with something better :P ( I understand that this isn't always possible though )

Personally, and perhaps wrongly, I refuse to replace spaces in filenames for another character if the spaces make sense.. for example, an audio file where the filename is likely to contain the title of the song. Especially considering such files ( in my situation ) are hosted on a server and shared ( via samba ) where space-replacement characters would look messy.

I still wonder how Nautilus was easily able to handle renaming the file but couldn't move/copy it..

Thanks ellis :)

---

### Post by Bodsda on 2008-02-04
Well i think renaming the file was easy because it is just a set of characters set in a field somewhere, all it has to do is locate the field (not the file) and delete all information from the beginning of the field to the end of the field, thus not caring what is actually inside the field

But copying was harder because mautilus actually has to find the file. eg. /home/user/file  has 3 / 's in it, so it has to navigate through 2 other folders to find the /file if you have a file with a / in it eg. home/user/fi/le  then nautilus sees that as, 4 / 's so 3 files to navigate, but gets confused when it cant find a /fi file 

anyway thats my thoughts on why its weird,.,.lol,.,. hope that helped

---

