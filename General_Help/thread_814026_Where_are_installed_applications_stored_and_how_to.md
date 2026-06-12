---
title: "Where are installed applications stored and how to identify the executable"
date: 2008-05-31
forum: General Help
---

### Post by oserdavid on 2008-05-31
Openoffice needs to identify my mail program. At which point it dawned on me that I haven't the faintest idea where to tell it to start looking. There doesn't seem to be a directory I can recognise as 'Program Files'. I'm using Mozilla Thunderbird (Thunderbird) for mail. I've found a number of directories called Thunderbird, and subdirectories, but none seem to contain a file which Openoffice recognises as appropriate to execute. So... in more general terms, where/how do we find our installed applications in Ubuntu (8.04) and what file type(s) execute(s) an application?

It's amazing how far you can get with an OS without discovering such fundamentals. I even managed to get sound working in Skype (but don't ask me to tell you how, because I've already forgotten. All I know is - it was too complicated by far).
David

Edit - a similar question arises in use of Wine, which I am using for Mailwasher Pro (I do not feel the need to pay again for the Linux version, since, using a dual boot machine, I never use the app on more than one machine/occasion at the same time). Mailwasher Pro running under Wine cannot find my default mail application in Ubuntu. I suspect this is far more complicated than the query involving two Linux applications needing to get in touch with each other, but maybe there is a solution?

---

### Post by x1a4 on 2008-05-31
Hi,

On non-Windows systems software  applications aren't stored the same way as on windows.  Binaries and other executables are in /bin/ /usr/bin/ /sbin/ and /usr/sbin/ and sometimes /usr/local/bin/ except for games which are in /usr/games/  

Libraries are in /lib/ and /usr/lib/

Global settings are in /etc/ and user settings are in a user's home directory. 

Thunderbird's executable is /usr/lib/thunderbird/thunderbird and it's symlinked as /usr/bin/thunderbird which is what you should use.

Look [here]("https://help.ubuntu.com/community/LinuxFilesystemTreeOverview") and  [here]("http://www.ubuntugeek.com/linux-or-ubuntu-directory-structure.html") for more info on Ubuntu's directory structure.

---

### Post by oserdavid on 2008-05-31
Many thanks x1a4 - did the trick.

By the way - seems I spoke too soon regarding Skype - recording for which has ceased to work again. Back to my drawing board... trouble is - there are such a large number of sound combinations to fiddle with - but it does, largely appear to be a problem with the OS itself, as you shouldn't really need to be doing this.

I'm not going to post a query about this, as there are so many already on the forums.

---

