---
title: "Text editor that makes numbered backups?"
date: 2013-04-01
forum: General Help
---

### Post by vasa1 on 2013-04-01
I'm using Lubuntu 12.10 which comes with Leafpad. If I edit a text file, no backup is created and there doesn't seem to be any obvious way to create backups.

I'd like to use a text editor that can create backups preferably retaining multiple backups. In other words, if I edit temp.txt once and save it, the latest version would temp.txt and the backup would be something like temp.bak.1. The next edit would result in temp.bak.2 and so on.

(I'm not interested in an editor than brings in KDE dependencies.)

---

### Post by mechdave on 2013-04-01
You could always use nano and then use the backup modifier as Alt+B :) Nano is in standard install of Lubuntu 12.10 :)

---

### Post by vasa1 on 2013-04-01
> **mechdave said:**
> You could always use nano and then use the backup modifier as Alt+B :) Nano is in standard install of Lubuntu 12.10 :)
It looks like nano just keeps one version. I would like to have more.
Anyway, I asked here: [Is it possible to have more than just one backup when editing text files?]("http://unix.stackexchange.com/q/70744/15760")
The answer I got will keep me busy for quite a while ;)

---

### Post by schragge on 2013-04-01
[size=-1]*Double-post deleted.*[/size]

---

### Post by schragge on 2013-04-01
[jEdit]("http://manpages.ubuntu.com/manpages/precise/en/man1/jedit.1.html") is an [UltraEdit]("http://www.ultraedit.com/support/tutorials_power_tips/ultraedit/version_backup.html") clone and as such [has versioned backups]("http://www.jedit.org/users-guide/saving.html#backups"), but a proper VCS like [git](http://git-scm.com/) is inherently better.

---

### Post by HermanAB on 2013-04-01
Howdy,

What you want is a simple versioning system.  Coders will tell you to install git or subversion, but that is total overkill for text files.  I use RCS to version control the files in the /etc directory:

[http://www.aeronetworks.ca/howtos/rcs-howto.html](http://www.aeronetworks.ca/howtos/rcs-howto.html)

Many text editors allow you to integrate versioning commands into the context menus.

---

### Post by lykwydchykyn on 2013-04-01
Emacs can be configured to do this.
[http://www.gnu.org/software/emacs/manual/html_node/elisp/Numbered-Backups.html](http://www.gnu.org/software/emacs/manual/html_node/elisp/Numbered-Backups.html)

---

### Post by gordintoronto on 2013-04-01
If the text file is in a Dropbox folder, Dropbox itself will keep multiple versions.

---

### Post by mharv on 2013-04-01
[http://www.vim.org/scripts/script.php?script_id=41](http://www.vim.org/scripts/script.php?script_id=41)

---

### Post by LewisTM on 2013-04-01
> **gordintoronto said:**
> If the text file is in a Dropbox folder, Dropbox itself will keep multiple versions.
+1 for Dropbox. It will keep all versions for 30 days, transparently. I always store current projects in my Dropbox. That way, they are available from anywhere and are protected from unwanted deletion or modification. It's like a digital safety net.

I wish there was a simple Ubuntu tool that would provide real-time, transparent version control for files or directories, without a full blown VCS or cloud server. There is NILFS but it's a bit overkill, a simple daemon should do the trick.

Cheers!

---

### Post by lykwydchykyn on 2013-04-02
> **LewisTM said:**
> 
I wish there was a simple Ubuntu tool that would provide real-time, transparent version control for files or directories, without a full blown VCS or cloud server. There is NILFS but it's a bit overkill, a simple daemon should do the trick.


"git init ~" isn't so hard.  Make a script to stage and commit on logout or at regular intervals, and you've got it.

---

### Post by vasa1 on 2013-06-26
I've decided to go with gedit and this plug-in: [https://code.google.com/p/double-save-gedit/](https://code.google.com/p/double-save-gedit/)
It time-stamps back-ups.

---

