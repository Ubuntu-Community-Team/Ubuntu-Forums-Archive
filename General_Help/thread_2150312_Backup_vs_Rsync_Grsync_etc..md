---
title: "Backup vs Rsync Grsync etc."
date: 2013-05-31
forum: General Help
---

### Post by AgentZ86 on 2013-05-31
Hi all

I'm wondering about the default backup tool included with Ubuntu 12.04 and 13.04 vs rsync or rsync with some front end GUI such as Grsync or something

I'm not too concerned with the time it takes to run a Ubuntu backup, well maybe only a little but more concerned with reliability.

I use to run an SME server with softraid 0 or softraid 1 which was a realtime mirror which is what I prefer but it doesn't have to be real time I guess. And I don't really want to run a seperate box for a server anymore either. 

Anyhow if rsync fails for some reason what happens on the destination are they corrupted ? 
Backup has a restore feature so I'm guessing it makes more then one backup each time for restore purposes, but I don't really need to fill up the drive like this either.

Today I setup the Ubuntu backup and ran the backup to a network folder on another computer which seems to work ok too.

Advise needed please

What do you think ?
Thanks

---

### Post by sudodus on 2013-05-31
If you are used to the command line, I think rsync is a great tool. You can make some scripts, that do what you want and keep running those scripts. The manual ```
man rsync
``` is good and there are specialized tutorials on the internet.

I think you can test what happens in your particular system, if the connection is broken during the backup, or if something else happens, that would make the backup fail. [COLOR=#696969](Maybe you don't want to perform a power network failure.)[/COLOR]

Generally it is a good idea to test the backup: Try to restore from it! You can't really rely on a system that is not tested all the way.

---

### Post by AgentZ86 on 2013-06-01
yeah I'm reading rsync tutorials now

Does rsync actually make a copy of the folder or does it work like the ubuntu tool that is included with ubuntu ?
The ubuntu tool give you a lot of  difftar.gz files

I'm not sure if I want that or if I a working copy on the network would be best.

If the source fails a working copy would still be accessible

---

### Post by SeijiSensei on 2013-06-01
Rsync will make a complete snapshot of the source directories and files if run with the "-a" switch.  If the transfer gets interrrupted for some reason, rsync will resume with the file it was downloading before.  It uses file datestamps to identify changed files.  When rsync begins to download a file it creates a "hidden" file on the target.  When the file is complete it is renamed to its actual filename.

---

### Post by sudodus on 2013-06-01
Rsync copies the directories and files, and if possible it keeps the file properties (read,write,execute, ownership ...) in backup mode. It does not make a cloned copy of the source, so the files may reside in different places on the target disk area. It does not create differences, but finds the new and changed files and makes new copies of them. The default behaviour is to keep files that are deleted from the source, but you can select to delete those on the target, 'synchronizing'.

---

### Post by AgentZ86 on 2013-06-03
I guess I'm concerned that I don't understand the default ubuntu backup tool that perhaps I should create my own script to run an rsync cron job or something.

The ubuntu backup tool doesn't give me any particular time to run it either it just says daily, monthly etc. 
What is all that about ?

Can anyone explain how the default tool works and what it does exactly ? I'm not sure I like the way it works but I don't know because I don't really understand what it's doing.

---

### Post by sudodus on 2013-06-03
> **AgentZ86 said:**
> I guess I'm concerned that I don't understand the default ubuntu backup tool that perhaps I should create my own script to run an rsync cron job or something.

I think it is a good idea to make something that you understand and can rely on :-)

[COLOR=#696969]I don't know more than you about the Ubuntu backup tool.[/COLOR]

---

### Post by AgentZ86 on 2013-06-03
me too, 

I'm doing a restore right now just to test out the default ubuntu tool but it looks like it overwrites the exising folder that is the source
So that doesn't seem too good right off
I guess I'll start reading rsync docs but I'm starting to like the idea of Grsync a bit better now. 
The reviews for the default ubunt are NOT good either.

---

### Post by rewyllys on 2013-06-03
> **AgentZ86 said:**
> me too . . . . starting to like the idea of Grsync a bit better now. 
The reviews for the default ubunt are NOT good either.
I suggest that you install LuckyBackup. It's essentially a GUI for rsync that incorporates cron, and it's very easy to use.

For over 2 years, I've been using it to make a daily backup at 0100. It's my habit to check on its work when I first log on the next morning, and it has never missed backing up every file I had changed on the preceding day.

---

### Post by Zill on 2013-06-03
> **rewyllys said:**
> I suggest that you install LuckyBackup. It's essentially a GUI for rsync that incorporates cron, and it's very easy to use...
+1 to [luckyBackup]("http://luckybackup.sourceforge.net/"). (It's in the repos)

It is a fairly intuitive GUI which also has a good manual and active support from the developer, Loukas Avgeriou.  luckyBackup can be run either as a user or the superuser if you want to backup system files or multiple user home directories.  No compression or encryption is involved and so the backed-up directories can easily be restored, even without using luckyBackup.
In addition, historical snapshots of changes are kept and so earlier backups can also quickly be restored.

---

### Post by AgentZ86 on 2013-06-03
Thanks I was looking at luckyBackup too with the cron job built in NICE.

So what does the default ubuntu backup tool use anyhow ? I don't plan to use it but just curious

---

