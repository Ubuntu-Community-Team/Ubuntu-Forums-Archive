---
title: "Opening a php file opens many firefox tabs"
date: 2007-08-30
forum: General Help
---

### Post by dopple on 2007-08-30
Hi folks. I've been using Ubuntu for a good few months now and this is the first time I've actually had to post for help so I reckon I've done pretty well.

I'm running Ubuntu 7.04 and have a LAMP set up (just for local web dev).

When I try to open a php file from the file browser to view it in firefox, it will open loads of blank tabs continuously until I try to stop. (I let it get to 73 just now, out of curiosity).

I can't see anything in the Firefox (2.0.0.6) prefs.
Can anyone shed any light on this?
Cheers
Dopple

---

### Post by eggdeng on 2007-08-30
> I try to open a php file from the file browser to view it in firefox
The php file needs to be interpreted by the server to produce output. If I read you right, you are bypassing the server. Assuming you have saved the file to your document root (/var/www), you need to open it from the browser by typing localhost/name_of_my_file.php in the address bar.

---

### Post by dopple on 2007-09-01
Apologies for not getting back to you sooner, I didn't seem to get a notification of a reply.
Thanks for your help. I'll just keep the directory bookmarked.
Dopple

---

