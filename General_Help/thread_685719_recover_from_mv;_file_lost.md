---
title: "recover from mv; file lost"
date: 2008-02-02
forum: General Help
---

### Post by EnsignR on 2008-02-02
Trying to break my GUI habbit, I used the terminal to move a rather large avi file from a directory inside my home folder to a shared media directory on my old XP drive.

mv *.avi /WinDrive/Share/Media/Videos/

I am not sure if I screwed up the syntax or permissions were the problem, but the move failed - although it took a long time suggesting it re-wrote the data - and the file seems to have disappeared.

I can't post the exact error message as my terminal screen buffer has lost it due to the output of the find command I ran (find / missingfile.avi). I've tried using that, the Search for Files in the menu, and manually checking my .Trash and root's (who doesn't have one). I even tried using nautilus as root and using the search there, which ran for hours without a result.

I did a sudo touch /forcefsck so it would check run fsck next boot, but have since decided rebooting may not be the best option.

Does anyone know a way I can recover the lost video? I am assuming at this point the file is unrecoverable, but I'd love to be proven wrong and any help would be appreciated. 

And now for the rant. Why does mv remove the original data if the write is not successful? Across two volumes, as this move is, I would have thought move would be akin to copy file to new location and then delete original IF (and only if) copy was successful.

---

### Post by ~LoKe on 2008-02-02
Sounds like the move was successful.

```
sudo updatedb
locate missing.avi
```

---

### Post by EnsignR on 2008-02-02
Thanks ~LoKe
The file is now where the mv command intended it to be :D


Oh happy day :D

---

### Post by ~LoKe on 2008-02-02
Glad you got it worked out!  The thing about locate (and possibly find) is that it uses a file index to make searching faster.  You need to update that index (sudo updatedb) for it to add new files to the database.

---

