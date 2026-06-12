---
title: "E-mail client"
date: 2007-01-03
forum: General Help
---

### Post by BlackJack on 2007-01-03
Please be patient as I am not real good with Linux. I am an old time Windows user and go all the way back to DOS, however I have only looked at Linux a little bit off and on over the years.

One of the things that I like about Outlook under Windows is that it keeps all of its data (not the configuration, but the data like e-mail, calendar, contacts, etc…) in one file. This makes it easy to backup and move from one system to another.

I have looked at Evolution and Kontact but both of these clients keep this data in multiple files in multiple directories. Does anybody know of an e-mail client under Linux that does keep all of this information in one file?

Thanks………

---

### Post by fimbulvetr on 2007-01-03
> **BlackJack said:**
> Please be patient as I am not real good with Linux. I am an old time Windows user and go all the way back to DOS, however I have only looked at Linux a little bit off and on over the years.

One of the things that I like about Outlook under Windows is that it keeps all of its data (not the configuration, but the data like e-mail, calendar, contacts, etc…) in one file. This makes it easy to backup and move from one system to another.

I have looked at Evolution and Kontact but both of these clients keep this data in multiple files in multiple directories. Does anybody know of an e-mail client under Linux that does keep all of this information in one file?

Thanks………

One of the main advantages linux has over windows is that it doesn't store things all in one file(don't even get started on the registry:)). Similiar to applications, it's generally a good thing to separate duties because it keeps programs/files fast and efficient because it doesn't turn apps into Jacks of all trades.

AFAIK, there are no programs that keep everything (contacts, calendar, email) in one place, but it's still trivial to accomplish your backups/moves:

If you have evolution, for example, you would do (from the cmdline, though you can use file-roller to accomplish the same in the gui):

```

cd ~/
tar -cvf evolution_backup.tar .evolution

```

And boom, you have a file named evolution_backup.tar with permissions, users, groups, file structure, etc still intact. Untar this file in a new homedir and evolution will be essentially identical to how the backed up evolution was.

---

### Post by nkassi on 2007-01-03
It doesn't not store all mail in one file but Mozilla Thunderbird would be a good email client to try out. It's can be installed with synaptics.  Thunderbird stores each actual folders that you create as a file. It's not quite the same as a .pst file but you this way you don't risk losing all your emails if for some odd reason the file was to become corrupted. (I had this sort of thing happen with .pst files at work.)

To backup thunderbird email, you simply can copy the .mozilla-thunderbird folder. (to find this folder in go to your Home Folder under Places and in the toolbar click on View->Show Hidden files) You can easily create an archive file (zip file) by clicking right on the folder and selecting create archive. 

I hope that helped you. 

Nic
P.S. Sorry if this sounded a little dumbed down but I don't know your skill level.

---

### Post by meng on 2007-01-03
Even outlook doesn't keep all the information in one file: there's outlook.pst and archive.pst, if I recall correctly
AND
keeping all data in one file does not necessarily make it more portable, particularly if it's a proprietary format! It depends what you mean by portable - easy to transfer from one Windows machine to another, or easy to transfer from one system to another regardless of OS. Anyway, transferring from one Windows installation to another is not trivial, it's not just a matter of overwriting the outlook.pst and archive.pst files, there is some other step required (although I don't recall what that is).

---

### Post by darrenm on 2007-01-03
Thunderbird doesn't store everything in one file. It stores it in one directory

~/.mozilla-thunderbird

Just copy that directory to backup. If you need to restore copy it back as said above.

I can guarantee you won't need to use scanpst either ;)

---

### Post by koenn on 2007-01-03
Typically, al user-specific data (preferences, data, ...) is in your home directory. That includes your mail.
As posted before; Thunderbird keeps your mail in a folder somewhere in your home. 
It's easy to move around. I copied the thunderbird folder from my Windows system into the appropriate place in my home directory when I moved to Ubuntu and kept all mail and all settings. 
What more could you want ?

---

### Post by DJ_Peng on 2007-01-03
What nobody's mentioned so far is that Mozilla is also working on a calendar application on several fronts. You've got Sunbird, their stand alone calendar, and you have Lightning, which integrates the calendar into Thunderbird, *a la* Outlook. You can check them all out on Mozilla's [Calendar Project](http://www.mozilla.org/projects/calendar/) page. My only problem so far with Lightning is that it can't sync up to my PDA yet, but they're working on it.

And just a hint, if you like Thunderbird 1.5 you'll love Tb2. I've been playing with it since it was an early alpha  and I love what they're doing with it.

---

### Post by oyvindaa on 2007-01-04
> **DJ_Peng said:**
> 
And just a hint, if you like Thunderbird 1.5 you'll love Tb2. I've been playing with it since it was an early alpha  and I love what they're doing with it.

Is that so? What are the main differences between 1.5 and 2.0?

---

### Post by DJ_Peng on 2007-01-04
A complete visual refersh, message tags, Unreadand Favorites Folder views, and a whole  lot more. You can get more info in the [Mozilla Thunderbird 2 Beta 1 Release Notes](http://www.mozilla.com/en-US/thunderbird/releases/2.0b1.html).

---

