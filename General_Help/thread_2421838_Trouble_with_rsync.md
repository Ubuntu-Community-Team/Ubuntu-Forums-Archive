---
title: "Trouble with rsync"
date: 2019-06-27
forum: General Help
---

### Post by Andrew_Benjamin on 2019-06-27
I have a mail server (Server A) at IP 1.2.3.4 and a backup server doing other stuff at 2.3.4.5 (Server B).

I'd like to copy the contents of /var/vmail from Server A to directory /MailBackup on Server B and then, in the future, copy all files on A that aren't on B (don't care if they are on B but not A) without copying everything again.  Each night, the system dumps a new backup in /var/vmail of all of my user's emails.  Supposedly, if yesterday's backup created a file called XYZ.EE from an email, then that filename will contain the same email the next day.

So, while logged into Server B, I used the command

rsync -rPz root@1.2.3.4:/var/vmail /MailBackup

This copied everything (I believe).

However, when I ran the command again an hour later, seemingly all the files started copying and moving again when NOTHING had been updated yet for the day.

So, here's the question:

What command do I need to issue to get all the files (by name) copied from Server A to Server B without copying files which already exist on both AND, not copying files which are on B but NOT on A back to A.  Again, I don't need/want A=B I just wand everything on A to exist on B (if there is more, that's OK).

Andrew

---

### Post by gdesilva on 2019-06-27
'rsync <files in A> <files in B'' should do the what you are trying to achieve and it appears that is exactly what you have done. If you are seeing files being re-copied, one explanation could be that your mailserver databases are regularly getting updated and hence rsync sees that as a change in the files. One would expect the mail databases to be updated quite a few times during an one hour period. I recently did a rsync of my Firefox profile and the only time I saw the files not being copied across was when I did absolutely nothing on the browser.

If you save the rsync command output to a text file then you can compare the two outputs to see which files exactly are getting copied across and work out the reason why.

Hope this helps

---

### Post by Andrew_Benjamin on 2019-06-27
In theory, the backup directory on Server A only gets updated once per day.  If actually true, there shouldn't have been any changes between the first and second run.

Andrew

---

### Post by gdesilva on 2019-06-27
Perhaps you may want to check this out ....

[https://stackoverflow.com/questions/13778889/rsync-difference-between-size-only-and-ignore-times](https://stackoverflow.com/questions/13778889/rsync-difference-between-size-only-and-ignore-times) and use the 'size-only' option?

---

### Post by HermanAB on 2019-06-28
Howdy, note that rsync also has a CRC option, which is arguably better than the size only option.

BTW, when you go to all the effort of setting up rsync, then you can just as well go the extra little bit and configure it to save multiple versions with hard links: [http://www.mikerubel.org/computers/rsync_snapshots/]("http://www.mikerubel.org/computers/rsync_snapshots/")

There is also [rdiff-backup]("https://www.nongnu.org/rdiff-backup/"), which does the same kind of thing, but maybe better.  I prefer the simplicity of the original idea of Mike Rubel though.

---

