---
title: "ubuntu is not executing .sh files it is always opening them in gedit?"
date: 2014-10-04
forum: General Help
---

### Post by vikashchandola26 on 2014-10-04
I know i need to change edit->preference->behavior 'view executable files...' to 'ask me each time'. I have changed it to ask me each time but still it is opening them in gedit. how can i open those file.?
I have added behavior windows screenshot(in case you want to see). 
I saw [Alvin Row]("http://askubuntu.com/users/114/alvin-row")'s answer in [this thread]("http://askubuntu.com/questions/38661/how-do-i-run-sh-files-in-terminal") . I tried to change that permission but as i tick on that box it gets unticked by itself. what's going on?

---

### Post by mcduck on 2014-10-04
The file needs to be have execute permission to count as executable file.

What comes to the permission unticking itself, that sounds like trying to change permissions on a file that's located on a filesystem which doesn't support Linux/Unix style ownerships and permissions. So, if the script you are having troubles with is on a Windows filesystem (FAT or NTFS) move it to a Linux one and you should be able to set the permissions.

---

