---
title: "Problems Installing Anything"
date: 2007-05-25
forum: General Help
---

### Post by ronmarley1 on 2007-05-25
When I try to install anything, I get errors about msttcorefonts.  I tried running:
sudo dpkg --configure -a
 and I get:
Setting up msttcorefonts (1.8ubuntu1) ...
warning: /usr/share/fonts/X11/truetype does not exist or is not a directory
warning: /usr/lib/X11/fonts/truetype does not exist or is not a directory

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

--14:26:45--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]

    [ <=>                                 ] 3,796         --.--K/s             

14:26:45 (259.17 MB/s) - `./andale32.exe' saved [3796]

--14:26:45--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/arialb32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/arialb32.exe)
           => `./arialb32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]

    [ <=>                                 ] 3,796         --.--K/s             

14:26:45 (78.06 MB/s) - `./arialb32.exe' saved [3796]

--14:26:45--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/arial32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/arial32.exe)
           => `./arial32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]

    [ <=>                                 ] 3,796         --.--K/s             

14:26:45 (249.20 MB/s) - `./arial32.exe' saved [3796]

--14:26:45--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/comic32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/comic32.exe)
           => `./comic32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]

    [ <=>                                 ] 3,796         --.--K/s             

14:26:45 (182.51 MB/s) - `./comic32.exe' saved [3796]

--14:26:45--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/courie32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/courie32.exe)
           => `./courie32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]

    [ <=>                                 ] 3,796         --.--K/s             

14:26:45 (177.51 MB/s) - `./courie32.exe' saved [3796]

--14:26:45--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe)
           => `./georgi32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]

    [ <=>                                 ] 3,796         --.--K/s             

14:26:45 (185.13 MB/s) - `./georgi32.exe' saved [3796]

--14:26:45--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/impact32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/impact32.exe)
           => `./impact32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]

    [ <=>                                 ] 3,756         --.--K/s             

14:26:45 (173.27 MB/s) - `./impact32.exe' saved [3756]

--14:26:45--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/times32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/times32.exe)
           => `./times32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]

    [ <=>                                 ] 3,796         --.--K/s             

14:26:45 (110.76 MB/s) - `./times32.exe' saved [3796]

--14:26:45--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/trebuc32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/trebuc32.exe)
           => `./trebuc32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]

    [ <=>                                 ] 3,796         --.--K/s             

14:26:45 (239.97 MB/s) - `./trebuc32.exe' saved [3796]

--14:26:45--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe)
           => `./verdan32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]

    [ <=>                                 ] 3,796         --.--K/s             

14:26:45 (223.42 MB/s) - `./verdan32.exe' saved [3796]

--14:26:45--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/webdin32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/webdin32.exe)
           => `./webdin32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]

    [ <=>                                 ] 3,796         --.--K/s             

14:26:45 (223.42 MB/s) - `./webdin32.exe' saved [3796]

andale32.exe: no valid cabinets found

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts
rgoodwin@ubuntu2112:~$

---

### Post by ronmarley1 on 2007-05-25
The heck with it, I'm reinstalling.  Again.

---

### Post by dannyboy79 on 2007-05-25
well if you don't want msttcorefonts, than just
sudo apt-get remove msttcorefonts
and you should be ok. if you do want them, then check this out. [http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg346480.html](http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg346480.html)

---

### Post by dannyboy79 on 2007-05-25
> **ronmarley1 said:**
> The heck with it, I'm reinstalling.  Again.

WOW, what impatience. You waited a whole 14 minutes :-). Why in the world would you reinstall due to this? Would you reinstall Winbloz if you couldn't figure out how to make windows update work? NO, you wouldn't. You'd look for a solution and look to the community for help which is what you did. You just didn't wait long enough. 

A reinstall wouldn't fix this if you did whatever it is you did the first time to get to this point in the first place,  just so you are aware.

---

### Post by ronmarley1 on 2007-05-25
Sorry, double post.

---

### Post by ronmarley1 on 2007-05-25
> **dannyboy79 said:**
> WOW, what impatience. You waited a whole 14 minutes :-). Why in the world would you reinstall due to this? Would you reinstall Winbloz if you couldn't figure out how to make windows update work? NO, you wouldn't. You'd look for a solution and look to the community for help which is what you did. You just didn't wait long enough. 

A reinstall wouldn't fix this if you did whatever it is you did the first time to get to this point in the first place,  just so you are aware.

Hi Everyone,
Sorry if I seemed impatient.  I did not mean to imply that that I did not get an answer soon enough.  I looked and looked for an answer, and after spending 1/2 hr., decide that it'd just be better to reinstall, since it only takes me about 25 mins.  
Since this was a fresh install of Fiesty, and a couple of other things were a bit wacky, I figured that I'd just start over.  
I intended for my reply to my own post to indicate to others, "Don't bother replying, I'm just going to reinstall."
Sorry if I offended anyone.
;)
PS, a reinstall did seem to fix the problem.  Apt was really goofy from the get go.   
PPS, dannyboy79, Thanks to you and Milwaukee for hosting the Indians this Spring when we were snowed out.

---

### Post by dannyboy79 on 2007-05-26
no problem regarding Miller Park, we sure paid enough for it to be built, I say, use it, I don't care who plays in it. :-)
Also, I am glad you got your issue resolved but there was a solution without reinstalling. Also, don't take it to heart regarding my comment about being impatient.

---

