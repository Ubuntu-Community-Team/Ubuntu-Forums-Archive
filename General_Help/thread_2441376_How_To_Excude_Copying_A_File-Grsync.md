---
title: "How To Excude Copying A File-Grsync"
date: 2020-04-23
forum: General Help
---

### Post by Wadcutter on 2020-04-23
Anyone know if a there a way to exclude copying a file in Grsync? That was easily possible in Backintime which used rsync. I don't see an option for it in Grsync. I have a folder that is 59 GB to copy. If I exclude one large file, it drops it to only 8 GB to copy. Much more efficient and fast.

---

### Post by ajgreeny on 2020-04-23
It uses the same --exclude option as rsync which you can get from the **man** **rsync** which you add in the second tab of the transfer setup. I'm  on an Android tablet at present so can not give you more detail so look around and you will find it I'm sure.

There is probably a grsync manual as well but I've  never needed it so can't  help more with that.

---

### Post by Wadcutter on 2020-04-24
Thank you, ajgreeny. I tried to put a command in under "file" "Preferences" and it disabled Grsync so that I had to completely remove it and start over. I didn't think about the Additional options box in the second tab. I think I know the command ( or can pick it up from a search). Thanks.

---

### Post by ra7411 on 2020-04-24
> **Wadcutter said:**
> Thank you, ajgreeny. I tried to put a command in under "file" "Preferences" and it disabled Grsync so that I had to completely remove it and start over. I didn't think about the Additional options box in the second tab. I think I know the command ( or can pick it up from a search). Thanks.

The pic shows how I do excludes, I think it works...[ATTACH=CONFIG]285604[/ATTACH]

---

### Post by Wadcutter on 2020-04-24
That looks good. I'll try it and do a dry-run to see what happens. Thank you.

---

