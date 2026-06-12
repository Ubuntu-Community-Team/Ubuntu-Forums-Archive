---
title: "Recoll editor applications"
date: 2013-05-28
forum: General Help
---

### Post by CindyP on 2013-05-28
I have begun to learn how I can incorporate the recoll search functionality into my daily routines.  Working from the recoll results list seems very useful - like opening the containing folder in my file manager or opening a file using its default application but the default configuration points to a number of applications that are not installed or used in my setup. 

The two holding me back are:

I use the nautilus file manager (Ubuntu 12.04) and not dolphin
I get an error when opening a general text file "The viewer specified in mimeview for text/plain: emacsclient is not found"

I imagine that the lines below are the lines I need to change in the preferences "editor applications" GUI but how do I specify nautilus file manager for instance and how do I point to another text editor?   I tried just replacing "dolphin" with "nautilus" but that didn't seem to work.   I am also guessing that an emacsclient might be a generic variable and not a real program?

application/x-fsdirectory = dolphin %f
inode/directory = dolphin %f
application/x-fsdirectory|parentopen = dolphin --select %(childurl) %f
inode/directory|parentopen = dolphin --select %(childurl) %f

text/plain = emacsclient  %f

Thanks

---

### Post by CindyP on 2013-05-29
I finally found a way to make the right selections in the recoll Preferences dialog to get the correct helper applications set up.  

Recoll --> Preferences --> (user interface tab) Gui Configuration --> Choose editor applications --> tick "Use desktop preferences as default"
then close that dialog, OK on the Preferences window
Log off and back on

I am sure I tried changing that earlier but possibly didn't make the correct confirmations or logged out.

---

