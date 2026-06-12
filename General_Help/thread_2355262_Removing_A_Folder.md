---
title: "Removing A Folder"
date: 2017-03-10
forum: General Help
---

### Post by shane_faulkinbury2 on 2017-03-10
Can someone help me out here?  I'm trying to delete Firefox and reinstall it.  I have already uninstalled Firefox and reinstalled it, but my bookmarks still show up.  So I removed my bookmarks and they still show up after rteinstalling.  So I did a seartch for every thing Firefox related on my computer and found a folder called UADescription(Firefox 3.0 on current)  and I'm trying to remove that, but I get this.
```
$ sudo su[sudo] password for bubba: 
root@bubba-110-194:/home/bubba# cd /usr/share/kservices5/useragentstrings
root@bubba-110-194:/usr/share/kservices5/useragentstrings# sudo rm -r -f UADescription (Firefox 2.0 on current)
bash: syntax error near unexpected token `('

```

How can I remove a folder that has a ( and a ) in it?

---

### Post by TheFu on 2017-03-10
~/.mozilla/ is probably what you want.

An easy way to determine if something is a system setting or a personal setting is to create a new userid and login with that, then see if the issue still happens. Linux is multi-user, so take advantage of that. Don't forget to remove it afterwards.

Installations of programs using the package manager is completely separate from settings stored in your HOME (or any other userid's HOME).

Removing stuff under /usr/ without using the package manager that isn't in /usr/local/ is a really, really, really, bad idea.

---

### Post by shane_faulkinbury2 on 2017-03-10
Well I removed everything with package manager and reinstalled with the terminal.  The bookmarks and addons are still there!  I'm at a loss on how to get rid of the entire program.

---

### Post by &amp;KyT$0P# on 2017-03-10
Bookmarks are stored inside your [Firefox profile]("http://kb.mozillazine.org/Profile"), which is located inside [FONT=Courier New]~/.mozilla/firefox/[/FONT].  Did you try renaming this folder?

---

### Post by shane_faulkinbury2 on 2017-03-10
I can't find [COLOR=#000000][FONT=&amp]~/.mozilla/firefox/[/FONT][/COLOR] where's the location?

---

### Post by raleigh3 on 2017-03-10
It is under /home/yourname/.mozilla/firefox.

If you do not want any old bookmarks or addons, just delete the firefox directory before you reinstall Firefox.

---

### Post by vasa1 on 2017-03-10
> **shane_faulkinbury2 said:**
> ... found a folder called UADescription(Firefox 3.0 on current)  and I'm trying to remove that, but I get this.
```
$ sudo su[sudo] password for bubba: 
root@bubba-110-194:/home/bubba# cd /usr/share/kservices5/useragentstrings
root@bubba-110-194:/usr/share/kservices5/useragentstrings# sudo rm -r -f UADescription (Firefox 2.0 on current)
bash: syntax error near unexpected token `('

```

How can I remove a folder that has a ( and a ) in it?
Does anyone else have "/usr/share/kservices5/" on their system? I don't seem to have any such folder.

---

### Post by shane_faulkinbury2 on 2017-03-11
I think I'm about to give up.  I've removed everything Firefox related except .png files and the UADescription (Firefox 16 on current) files because my terminal won't let me because of the paranthesis and reinstalled.  The stupid bookmarks and addons are still there! :-|:sad::-x:redface::x:frown:

---

### Post by &amp;KyT$0P# on 2017-03-11
shane_faulkinbury2, did you also completely quit Firefox, then run this command in Terminal? -
```
mv -v ~/.mozilla/firefox ~/firefoxOLD
```

---

### Post by TheFu on 2017-03-11
Shane,

In my Linux classes, I teach that 
**cd ~** == **cd $HOME** == **cd** {with nothing} == **cd ~/** in the first 15 minutes.

A basic understanding of relative directories would have saved this user a bunch of effort as would the fact that bookmarks aren't stored globally on the system, but inside the userid HOME directory. Whoever helped with initial training failed. 2 hrs in a beginning Linux class should have solved that or reading the first 2-3 chapters of a beginning Linux/Unix book.

This issue was a 10 second problem. 

Sadly, it appears that my first reply was completely ignored. We all get fixated on things, sometimes those things are completely incorrect. We are positive step A is required, when it isn't. Anyway, to remove a directory with special characters, there are many possible solutions. A simple regex would pay off there.  **rm UADescription*** would have been enough.

BTW, I searched my 30 systems for "*useragentstrings*" named for any file and directory and found none. Similarly, looked for *UADescription* (case insensitive) and found none.

We all started out not understanding these same things. I was lucky and my job sent me to training to learn the fundamentals. I was a mainframe programmer prior to that, so if I can learn it, anyone can.

---

### Post by Dennis N on 2017-03-11
> The bookmarks and addons are still there!

If removing all bookmarks and add-ons is your remaining goal,

For Bookmarks:
Bookmark Icon on toolbar > "Show All Bookmarks" > select all (ctrl+A), and then delete (rt. click menu delete or delete key).

For Add-ons: 
Tools Menu > Add-ons, every extension and theme has a remove button next to it.

---

### Post by shane_faulkinbury2 on 2017-03-11
Nope.

---

### Post by The Cog on 2017-03-11
Uninstalling and reinstalling the firefox application will not remove your personal firefox settings that are stored in your home folder. After reinstalling and restarting firefox, it will find your personal settings and re-use them. What you need to do instead is to delete your personal firefox settings (while firefox is not running or it will just recreate the settings folder from memory).

To delete your personal firefox settings, go the folder .mozilla which is in your home folder (because it starts with a dot it is a hidden folder, you need to tell your file manager to show hidden files), and delete the firefox folder you find inside it.
This command will do it from the command line:
```
rm -rf ~/.mozilla/firefox
```
The ~ means "my home folder", e.g. /home/shane or whatever your username is.

---

### Post by deadflowr on 2017-03-11
I'd just look into creating a new profile
In a terminal run:
```
firefox --ProfileManager
```
Click create profile
Make a new profile, (probably give it some funky name, or whatever)
Click on Finish.

Back in the main profile manager page highlight the old profile (If only one then it'll be marked/called default) and click on Delete profile
(it'll ask if you want to delete or not delete the files for the profile, your choice.

Then back again at the main profile manager page. double click on the new profile in the profile list and it'll open the new profile.
And should remain as the current profile from now on, or until you change it to another profile.

Hope it helps

Also, as per the rm command, try wrapping the file in quotes, like
```
rm "file that contains oddness like ( wow that is odd)"
```

and...
> Does anyone else have "/usr/share/kservices5/" on their system? I don't seem to have any such folder.
That's a sign of at one point having kde installed, whether as a desktop or an old install.
(if an old install it's quite possible any reinstall/fresh install could have kept the legacy files if the file system was not formatted.
A reinstall on an unformatted system will only overwrite those files that the installer writes, but will leave those files that have nothing to do with it alone, if that makes sense;
I learned this when I had an install of 15.10 but decided to reinstall 14.04.1 and when I rebooted, I was running the 4.2 kernel, which the install of 14.04 did not have within it.
(^most likely off-topic, btw, and possibly totally irrelevant)

---

### Post by shane_faulkinbury2 on 2017-03-11
Thanks deadflower, great thinking!  I'll just create a new profile!

The quotes didn't work unfortunately.  :(

---

### Post by raleigh3 on 2017-03-11
I have it on my system.     

```

 Ubuntu 16.04.2 LTS  16.04 xenial
```

---

