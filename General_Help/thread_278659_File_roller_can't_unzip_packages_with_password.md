---
title: "File roller can't unzip packages with password"
date: 2006-10-16
forum: General Help
---

### Post by walden2 on 2006-10-16
Hey! I've been downloading some .rar packages protected with password, but, when I try unzipping it with File Roller, it wouldn't let me (it throws me some warning message I don't remember now). So, I must go back to Windows with the package, unzip it using WinRar and return to Dapper with the unzipped package. I'm tired of this! How can I enter passwords with File Roller (or another software)?
I'm waiting anxiously your help.

---

### Post by skymt on 2006-10-16
Try this:

* Open a terminal (Applications > Accessories > Terminal)

* Type "unrar e "

* Drag your file to the terminal window

* Enter your password

---

### Post by eeGhoong0ais on 2006-10-16
I don't think rar is installed by default - File Roller is just a front end to other utilities like gzip, rar etc. Try ```
rar e filename.rar
``` to see whether you have a working rar - if not, ```
sudo apt-get install rar
``` will get it for you.

... I just did a little checking, and it seems that File Roller doesn't know how to deal with .rar archives that have both the individual files and the archive's table of contents encrypted. So, in those cases you'll need to use the command line as described above.

---

### Post by walden2 on 2006-10-16
Thanks a lot people! It seems like I needed to do that "sudo apt-get install rar" thing (sorry, you're watching a newbie with all his shine).

---

### Post by mrbhave on 2008-07-03
For those who are interested in a GUI-based archive manager with password support, check out [XArchive]("http://xarchive.sourceforge.net/") (not [XArchiver]("http://xarchiver.xfce.org/"), which also lacks support to handle password-protected archives). 

To install, open a terminal and copy/paste or type the following command.
```

sudo apt-get install xarchive
```

After opening the archive in XArchive, it may indicate that there are no files in the archive.  Ignore this and click the "Extract" button.  Follow the prompts, the last of which will open a terminal window prompting you to enter the password.

---

