---
title: "Error - &quot;Parsing Filters not supported&quot;"
date: 2016-04-30
forum: General Help
---

### Post by pat4 on 2016-04-30
Hi, 
Ubuntu 16.04 - 64bit 

Trying to extract multi-part archives using Archive Manager (File Roller) I get the message:   "Parsing Filters not supported"

I seem to be able to extract single part archives OK.

Any help with this please?


Regards,

---

### Post by T.J. on 2016-04-30
> **pat4 said:**
> Hi, 
Ubuntu 16.04 - 64bit 

Trying to extract multi-part archives using Archive Manager (File Roller) I get the message:   "Parsing Filters not supported"

I seem to be able to extract single part archives OK.

Any help with this please?


Regards,


Was it a multipart rar?  File-roller is a bit quirky.  We might be able to get the files to extract on the CLI if all else fails: 
*unrar x <filename>*

---

### Post by pat4 on 2016-05-01
> **T.J. said:**
> Was it a multipart rar?  File-roller is a bit quirky.  We might be able to get the files to extract on the CLI if all else fails: 
*unrar x <filename>*

I have had trouble mainly with multi-part rar files but today I am also getting the error message on trying to extract single part rar files. 

Extraction via the CLI is probably possible but inconvenient.

I have a laptop with 16.04 installed and have no problems extracting files on there. I am assuming from this that there is some sort of error in the files on this computer..

Any suggestions as to where the problem might lie are welcome.

Regards, Pat.

---

### Post by pat4 on 2016-05-01
I know it isn't perhaps polite to reply to ones own posts but I seem to have solved the problem.

I did bit of digging and came across a webpage in Portuguese (!) which indicated the rror was due to "Unrar" not being installed.

I installed Unrar ( sudo apt-get install unrar ) and rebooted. 

Problem seems to have been resolved.

---

### Post by T.J. on 2016-05-01
That was exactly my next suggestion.  Glad it worked.  Please mark the thread as "Solved" in a few days if there are no further problems.

---

### Post by pat4 on 2016-05-02
Done... Thank you very much for your helpful suggestions. Much appreciated.

---

### Post by b3hr3ns on 2016-08-11
[COLOR=#000000]"sudo apt-get install unrar"  worked for me!  Thank you @Pat4[/COLOR]

---

