---
title: "unmet dependencies..."
date: 2017-03-24
forum: General Help
---

### Post by ddenney on 2017-03-24
Hello. Sorry if I put this question in the wrong category. I'm having a problem with installing a program called AceStream. I type in terminal:

> sudo apt-get install acestream-full and it always tells me:

> Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 acestream-full : Depends: acestream-engine (>= 2.1.6-1raring4) but it is not going to be installed
                  Depends: acestream-player (>= 2.1.6-1raring2) but it is not going to be installed
                  Depends: acestream-mozilla-plugin (>= 2.1.6-1raring2) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

I added to my sources.list: > #AceStream
deb [http://repo.acestream.org/ubuntu/](http://repo.acestream.org/ubuntu/) raring main

I then typed in terminal:

> sudo wget -O - [http://repo.acestream.org/keys/acestream.public.key](http://repo.acestream.org/keys/acestream.public.key) | sudo apt-key add -

I got the terminal commands from acestream.org, so I really don't know if I'm doing something wrong or not. Thanks for any help.

---

### Post by QIII on 2017-03-24
Hello!

Which release of Ubuntu are you using?  Raring Ringtail is far, far beyond end of life.

---

### Post by ddenney on 2017-03-24
Ooops... sorry. I forgot to put my version in my original post. It's Ubuntu 16.04.2 LTS (Xenial Xerus).

---

### Post by ddenney on 2017-03-24
Forget about it. I found the prog at **Ubuntu Software**. Thanks anyway.

---

