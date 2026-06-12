---
title: "trash empty"
date: 2008-01-07
forum: General Help
---

### Post by Kalidor on 2008-01-07
I tried to install libgpod2 as described in a guide of this forum, but didn't succeed. I managed to delete every file related to this attempt and trashed the folder libgpod-0.6.0 where i had decompressed everyfile and run everything. Turns out it can be put in the trash but cannot be removed from the trash in anyway. I can't remove it completely... It says i can't remove a specific file in that folder cause i don't have permission to modify the parent older. So I decided  to start nautilus and quite ridiculously, qhen i enter the trasch can with nautilus it is empty! My guess is that in several attempt as a root user i actually succeeded in deleting this folder and all of its file, but i don't understand why it still shows in the trash as a normal user.

---

### Post by rodo-&gt;dave on 2008-01-07
start a terminal and then:

$> cd ~/.Trash

$> ls -al 

if you see more than . and .. then there is more stuff in it.

PS. make sure the cd ~/.Trash worked :)

---

### Post by Kalidor on 2008-01-07
I indeed see more. ******* libgpod-0.6.0 for instance. So... what do you say ?

---

### Post by dannyboy79 on 2008-01-07
i say

sudo rm -rf ~/.Trash/

that will forcefully remove all files/folders within that directory.

---

### Post by SOULRiDER on 2008-01-07
Theres no need to sudo, in fact, sudo might make it not work.
```
rm -r ~/.Trash/
```

---

### Post by Kalidor on 2008-01-07
Now the command cd ~/.Trash returns
 bash: cd: /home/joubert/.Trash: No such file or directory
The icon of the trash down on the left side of the desktop shows it's full. When i click on it to open the folder it shows the trash can is empty.

---

### Post by rodo-&gt;dave on 2008-01-07
$> mkdir ~/.Trash

---

### Post by Kalidor on 2008-01-07
Solved

---

### Post by dannyboy79 on 2008-01-07
if something is moved from a folder that was previously root owned than I believe that you would need to use sudo. Also, sudo would never make it "not work" as any command with sudo gives root privelages and root can do anything.

---

### Post by SOULRiDER on 2008-01-07
But the ~ may make it look in /root/ and not /home/user/ im not 100% sure about this though.

---

