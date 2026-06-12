---
title: "duplicity - recover"
date: 2019-02-03
forum: General Help
---

### Post by jgw on 2019-02-03
I have a bunch of backup files from the duplicity program.  I am trying to get to a specific file (firefox profile for backup files).  I do not want to reinstall a bunch of this stuff so much as drill down to the folder I want and the extract the stuff I want and then import just that stuff.  I don't think I have the option of restoring to a specific folder.  I have read about manually 'restoring' and get a bit paranoid as there are a LOT of these files.  One of the saving graces is that there is a text file, at the top of all the difftar.gz files.  I have tried to use the archive manager to do this but failed (just changed the .difftar.gz to .difftar)   I also noted that there are a LOT of messages about this stuff but no real solutions that I found.

Thoughts?

Thank you.................

---

### Post by dragonfly41 on 2019-02-03
I understand that [ripgrep searches gz files]("https://github.com/BurntSushi/ripgrep/issues/918").

[Installation instructions.]("https://github.com/BurntSushi/ripgrep")

---

### Post by CatKiller on 2019-02-03
> **jgw said:**
> I don't think I have the option of restoring to a specific folder.  I have read about manually 'restoring' and get a bit paranoid as there are a LOT of these files.

You do have the option to restore them somewhere of your choosing. If it's possible to only retrieve particular files it isn't easy to do: the tool isn't intended for that.

There are a lot of files because it keeps two full backups (which is itself a lot of files) and then the diff for each backup you've done since the last full backup, which is every day by default, I believe.

---

