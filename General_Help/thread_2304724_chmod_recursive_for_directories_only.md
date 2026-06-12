---
title: "chmod recursive for directories only"
date: 2015-11-29
forum: General Help
---

### Post by thombark2 on 2015-11-29
I am trying to copy from a HDD to my local drive. There are many many files on the drive. Some of the directories have "none" in the "group" and "others" permissions, so I cannot copy these. I would like to change the "others" permission recursively to "read", but I don't want to change the permissions of each file within the directories. The desktop that has the HDD connected is running an ancient copy of Ubuntu - 10.04!

Thanks

---

### Post by HermanAB on 2015-11-29
Hmm, globbing and recursion in Bash is done via the 'find' command, with the 'exec' option.

So, what I would do, is craft a find that will get the directories and then exec the chmod command.

Google for 'linux bash find directory example' and the very top one points to stackoverflow.

Another google for 'linux bash find exec example' and you'll know more about find than you ever wanted to.

Ferinstance:
find . -type d -exec "chmod yourusername: {}" \;

---

