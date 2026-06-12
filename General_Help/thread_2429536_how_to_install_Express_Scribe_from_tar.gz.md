---
title: "how to install Express Scribe from tar.gz?"
date: 2019-10-19
forum: General Help
---

### Post by alyssajesse on 2019-10-19
Hi,


Sorry if this is in the wrong place! 

I'm trying to download Express Scribe on kubuntu 19.04. 

I've downloaded scribe.tar.gz from [https://www.nch.com.au/scribe/linux.html](https://www.nch.com.au/scribe/linux.html) 

I've tried to follow instructions from: [https://sourcedigit.com/20839-extract-install-tar-gz-files-ubuntu/](https://sourcedigit.com/20839-extract-install-tar-gz-files-ubuntu/)

And the following has happened: 


[FONT=monospace][COLOR=#000000]$ sudo tar xzvf scribe.tar.gz                 [/COLOR]
 
tar (child): scribe.tar.gz: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now


I'm not exactly new to ubuntu, but I manage to bluff my way through and hence don't know anything and I'm probably missing something very obvious. Any help would be much appreciated!

Thank you in advance!
[/FONT]

---

### Post by Holger_Gehrke on 2019-10-19
A .tar.gz is an archive-file. I don't know KUbuntu all that well, but I'm sure there's some kind of archive-manager installed that can unpack these in a graphical environment. That's probably the easier way to do it.

The less easy way is to learn a bit about the way the command line works. There's something called the 'working directory'. All programs expect files for which you don't give a path to them to be in the current working directory. Directory is just another name for what most GUI-users would call a 'folder'. You can tell what the current working directory is by looking at the prompt (the text to the left of the cursor). It's usually set to show your user name, an '@', the machine name, a ':' and the current working directory followed by a '$'. It will probably show '~' as your working directory, which is shorthand for your home directory. If you didn't save your file directly in your home directory but in some subdirectory of it, tar can't find the file unless you tell it where it is. So it should be 'tar xzf ~/Downloads/scribe.tar.gz' if you saved the file in the directory '~/Downloads'.

A small warning: tar extracts the archive to the current working directory, so if there's lots of stuff in there that isn't in a directory of it's own it will mess up your home directory if you extract it there. You can have a look at the contents of the archive by telling it to list them: 'tar -tzf ~/Downloads/scribe.tar.gz'. To be on the save side you can make a new directory ('mkdir scribe') and make that the current working directory ('cd scribe') before extracting.

Holger

---

### Post by alyssajesse on 2019-10-19
Thanks for your explanation Holger!

I followed your instructions and received this in return:

[FONT=monospace][COLOR=#000000]tar xzf ~/Downloads/scribe.tar.gz[/COLOR]

gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Error is not recoverable: exiting now

Are you able to help further? 

Thanks in advance![/FONT]

---

### Post by Holger_Gehrke on 2019-10-19
OK, the good news first: the file is in ~/Downloads.

The bad news: something is wrong with the file.

'tar' only packs all the files together into one file and then uses another program to do the compression. The 'z' option tells tar to use gzip for compressing and decompressing. And the error message means gzip doesn't recognize the file as something it can decompress. 

I've downloaded the file from the URL you gave and it definitely can be uncompressed using 'tar xzf ...' so something must have happened to your file - transmission error, or something like that. 

There's actually only one file in the archive, an executable named scribe that needs to be called with 'sudo' because it does the actual installation and writes to /opt which you can't do as a normal user.

Holger

Edit: I've installed the program and it seems to work. There's one decidedly ugly problem, though. The installer directly starts the program and that saves a configuration to the directory '~/nch/. Remember that I told you the installer needs to run as root (started with sudo) ? The program still runs as root and writes a configuration owned by root and only writable by root. So if you start the program the second time it will crash. The fix is easy: 'sudo chown -R USERNAME ~/nch' (substituting your username for USERNAME).

---

### Post by alyssajesse on 2019-10-20
Hello Holger,

Thank you for your help, I really appreciate it. During one of my attempted installs I realised the file was from 2009! I have been in touch with the company directly and they informed me that they no longer develop for Linux, and they have discontinued support. Annoyingly they don't mention this on the site and still have the download available. Because of this I've decided to try find another solution to my transcribing needs. 

Thanks again!

Alyssa

---

