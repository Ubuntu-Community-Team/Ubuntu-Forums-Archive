---
title: "Duplicity backups, holy cats!!"
date: 2014-10-27
forum: General Help
---

### Post by dannyboy79 on 2014-10-27
At some point I must have setup a duplicity backup for my server and I was doing some house cleaning on my drives and found a folder which has a ton of duplicity files in it. Here's the list of files
[http://paste.ubuntu.com/8712982/](http://paste.ubuntu.com/8712982/)

looking at them I have no idea which ones I can delete. Can someone please assist me in figuring out which of these files I can delete? I suppose I should be more familiar with the software Im using but I don't understand the sigtar vs the difftar vs the manifest files. Any help would be appreciated. Thank you

---

### Post by mastablasta on 2014-10-28
I am guessing that reading the duplicity manual would help at this point. 

however I would guess that manifest lists the files, diffstar look like they are snapshots and the final ones look like signatures of the files (did you maybe setup some encryption or it has some way to store file signatures (like MD5SUM so it can restore them safely).

---

### Post by dannyboy79 on 2014-11-02
ok, well i'm thinking i just need to start over BUT now the trouble is i don't see where duplicity is being ran from? i've checked my crontab, roots crontab, i've checked each individual /etc/cron  folder but i don't see anywhere that's doing the duplicity backups. can anyone help please?

---

