---
title: "history.db file. Do I need it?"
date: 2015-10-31
forum: General Help
---

### Post by mikodo on 2015-10-31
In my ~ I have a file called history.db. It is owned my user and group. I only have Xubuntu installed.

Here is what the file looks like when I open it up with LO Writer:  [URL="http://paste.ubuntu.com/13057163/"]http://paste.ubuntu.com/13057163/
[/URL]
It seems to be a Windows database. [URL="http://www.openthefile.net/extension/db"]http://www.openthefile.net/extension/db
[/URL]
I *THINK it showed up with [Launchy]("http://www.launchy.net/") I was trying before. That is gone now. I chose not use it in my Xfce desktop of Xubuntu. 

It may have showed up with my VPN [VIA]("https://www.privateinternetaccess.com/") but, I don't think so.

Other than that, everything else is pretty much stock Ubuntu repos installed, in my OS.

Shall I delete it?

Addendum27. Well, I stuck the file in trash. Closed everything and rebooted. I see no dysfunction because of doing that.

---

### Post by TheFu on 2015-11-01
File extensions don't matter to Linux. Use the "file" command to learn what the file probably holds. 'file' uses the "magic number" to determine the contents.

$ file /path/to/history.db

Opening a binary file isn't usually helpful. Using the 'strings' tool may provide some hints.
Often, a file like that would be a sqlite DB-that's my best guess.  The directory were it is located would provide more clues to the purpose.

---

### Post by mikodo on 2015-11-01
Thank you, TheFu.

I restored the file from trash, and ran:

```
file /home/mikodo/history.db

results:

/home/mikodo/history.db: data

```
"data" is the label name of a partition I symbolically link to from my $HOME, (Documents, other sub-directories ...).

I think this came about when I was playing with Launchy. I seem to remember it having a function to be able to open files of Documents and such. I didn't like it and didn't explore it much. It makes sense it would launch from a "data base". Launchy of course can be used in MS Windows. So like you said, it having a .db file format makes sense for Windows and Linux to read.

As Launchy is long gone, and I seemingly had no problems with "history.db" in Trash this last day, I am going to give it the boot.

Thanks, again!

---

