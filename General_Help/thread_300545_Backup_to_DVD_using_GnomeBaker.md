---
title: "Backup to DVD using GnomeBaker"
date: 2006-11-15
forum: General Help
---

### Post by eugenia on 2006-11-15
There was a post a couple of weeks ago by "kindafunnylookin" titled "I can't get my_backup.tgz_ file onto DVD with GnomeBaker"

I have exactly the same problem but none of the solutions in the replies from seem to work for me.

I have changed the permissions to 777 and ownership to myself and even copied the archive to my Desktop but Gnomebaker still won't let me add either of the files '20061116.tar.gz' or '20061116.tgz'

I made the archive with the command 
sudo tar cvzf /archives/20061116.tar.gz /home/ and after looking at the post I changed the extension so it was the same in case that was the problem
sudo tar cvzf /archives/20061116.tgz /home/
Both files are 2.2GB (ray@wannabee:/archives$ sudo du *.tgz
2259736 20061116.tgz)

Again after looking at the post I ran GnomeBaker as root I got an error
ray@wannabee:~$ sudo gnomebaker
libnotify-Message: Unable to get session bus: No reply within specified time

** (gnomebaker:17344): WARNING **: dataproject_add_to_compilation - failed to stat file [/archives/20061116.tgz] with ret code [-1] error no [Value too large for defined data type]

GnomeBaker works because I have been using it for burning files without any problems all week.

Can anyone help please

---

### Post by organica on 2006-11-15
This may be unrelated but have you tried to chown the tgz files to your user:group and burn with gnomebaker as a user and not root?

---

