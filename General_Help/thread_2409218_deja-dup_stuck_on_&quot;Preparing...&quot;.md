---
title: "deja-dup stuck on &quot;Preparing...&quot;"
date: 2018-12-29
forum: General Help
---

### Post by j-g-fager on 2018-12-29
Automatic backups fails after the first few times.

I have scheduled daily backups in deja-dup (version 37.1). If I start with an empty backup storage location (a NAS mounted as a local folder) the backup works twice (making a full backup the first time, and an incremental backup the second time).

However, the third and following times deja-dup gets stuck showing the process window: "Backing up... Preparing...". It never continues, I have waited more than an hour. The original backup takes a few minutes.

System: Ubuntu (v. 18.04.1)
deja-dup (v. 37.1)
duplicity (v. 0.7.17)

Any ideas how to solve this?

(I have used the same method with Ubuntu 14.04, which worked for several years, and still works.)

Update December 30, 2018: It appears to be the same problem as this one observed (and solved) in Fedora: [https://bugzilla.redhat.com/show_bug.cgi?id=1582654#c5](https://bugzilla.redhat.com/show_bug.cgi?id=1582654#c5) .

Anyone out there who knows how to solve this for Ubuntu?

---

### Post by clementc on 2018-12-31
Hi [**j-g-fager**]("https://ubuntuforums.org/member.php?u=2115100"),

I know that this might not be the answer you are looking for, but as deja-dup is only a front-end for duplicity, how would you feel about giving duply (a different frond-end running in Terminal) a go?

Please see duply's manpage [here]("http://manpages.ubuntu.com/manpages/bionic/man1/duply.1.html") and a nice tutorial on how to use it [there]("https://www.zetta.io/en/help/articles-tutorials/backup-linux-duply/").

---

### Post by j-g-fager on 2019-01-04
Thanks @clementc for the reply, I will give duply a try and see if it works.

Still, I find it frustrating that deja-dup (or maybe duplicity) does not work. I have the backup file area mounted all right (using samba). I can access it via the file manager, teminal window etc. The backup works twice via deja-dup (I have tried that from scratch several times). From the third time (incremental backup) it gets stuck on "Preparing...". Sigh...

---

### Post by clementc on 2019-01-04
Hi [**[COLOR=#000000]j-g-fager[/COLOR]**]("https://ubuntuforums.org/member.php?u=2115100"),

I understand your reasoning. If duply works for you then this will give us a first indication as to where the issue might lie (either in deja-dup or duplicity).

---

### Post by j-g-fager on 2019-01-06
Hi clementc, thanks, I have tried duply now and it works like a charm!

The backup problem is solved for me, but there seems to be issues with deja-dup.

---

### Post by clementc on 2019-01-06
Hi [**[COLOR=#000000]j-g-fager[/COLOR]**]("https://ubuntuforums.org/member.php?u=2115100"),

I am glad to hear that! Good to know that the issue is more likely to be caused by deja-dup which is only a GUI for duply CLI.

---

