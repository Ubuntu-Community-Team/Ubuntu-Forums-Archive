---
title: "Problems in uninstalling insync"
date: 2018-02-17
forum: General Help
---

### Post by josep2 on 2018-02-17
When I intend to unisntall the program "insync" (sudo apt-get remove --purge insync or sudo aptitude remove insync) I obtain an dpkg error:

Traceback (most recent call last):
  File "<string>", line 5, in <module>
zipimport.ZipImportError: not a Zip file

And finally the script postinstallation gives error 1

I've tried it several times, without success. Any idea about? How can one erase a program when when the expected procedures do not work?

Thanks in advance.

---

### Post by cruzer001 on 2018-02-17
I searched Google "remove insync" and looks like manually removing the package would work.

Use your file manager to search for "insync" and remove/purge those files.

[https://help.ubuntu.com/community/AptGet/Howto#Removal_commands](https://help.ubuntu.com/community/AptGet/Howto#Removal_commands)

Also check your sources list for insync.

[https://help.ubuntu.com/community/Repositories/Ubuntu#Other_Software_Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Other_Software_Tab)

You may want to have a look for yourself in case I missed something or a better way to do it.

---

### Post by josep2 on 2018-02-17
Thanks for your answer, but I have asked precisely because those methods do not work for me... I'm obtaining always "Sub-process /usr/bin/dpkg returned an error code (1)"... and the program remains... Any idea about?

---

### Post by cruzer001 on 2018-02-17
Ok I think I now follow what your saying.  This is a problem created by insync which has cause apt-get to error out on anything you try.  If apt-get will not allow you to remove a file, then try renaming the file.  

Have a read here first.
[https://forums.insynchq.com/t/insync-not-starting/1832/2](https://forums.insynchq.com/t/insync-not-starting/1832/2)
[https://forums.insynchq.com/t/insync-1-2-10-miss-configuration-settings-after-a-computer-reboot/1271](https://forums.insynchq.com/t/insync-1-2-10-miss-configuration-settings-after-a-computer-reboot/1271)
[https://unix.stackexchange.com/questions/316264/insync-messed-up-apt-and-i-cant-do-apt-get-update-upgrade](https://unix.stackexchange.com/questions/316264/insync-messed-up-apt-and-i-cant-do-apt-get-update-upgrade)

---

### Post by josep2 on 2018-02-18
Thanks a lot! The key for me has been to eliminate this file: /var/lib/dpkg/info/insync.prerm After that, I have been able finalle to erase this program! 


Thank you very much!

---

### Post by cruzer001 on 2018-02-18
Welcome :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by josep2 on 2018-02-18
Thanks again! I had forgotten to mark the thread as solved. So appropriate memory on your part!

---

