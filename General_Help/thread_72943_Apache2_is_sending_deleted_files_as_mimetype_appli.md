---
title: "Apache2 is sending deleted files as mimetype application/x-trash"
date: 2005-10-07
forum: General Help
---

### Post by GraemeWorthy on 2005-10-07
I've got a headache about this.

I've just deleted a file from a directory that I have served by apache. 
(it was an index.html file)
and now loading the directory with a browser it starts downloading a file with the mimetype application/x-trash.

wget actually is able to retrieve the deleted file with no problems.

---

### Post by fr3ak on 2006-04-25
OK... I spent ages trying to figure it out, the problem only exists for mozilla based browsers (I hate to say it but IE is not affected) but I have found out where the MIME types is found and controlled from... /etc/mime.types in there is where it points to .old .bak etcetera, thinking that this may be the cause i just changed the types to html php... bingo no file trying to be downloaded, but also no page being found at all... so weird. So if you type the whole address [http://foo.com/index.html](http://foo.com/index.html) or php it loads the page no problem but if you just try to load the root it can't find the file... so who is being to tricky? Firefox or Apache? Please enlighten him ^ me the rest of the world if you have found a solution.

---

