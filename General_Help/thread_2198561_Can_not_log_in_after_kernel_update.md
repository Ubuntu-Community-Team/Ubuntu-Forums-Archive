---
title: "Can not log in after kernel update"
date: 2014-01-09
forum: General Help
---

### Post by lsutiger on 2014-01-09
I was receiving an error after the latest kernel update as[ referenced here]("http://ubuntuforums.org/showthread.php?t=2198245"). After tinkering a bit, I also broke python. I fixed both problems, the first by the url references, the other by doing a reinstall of python, but now I can not login to my account via the GUI. When I do login, it loops back to the login screen. I am able to login to the guest account, but do not get a prompt on the tty1-7 screens. I currently have ssh access, so I can run command.

Could someone point me in the right direction?

---

### Post by jeanjd63 on 2014-01-09
Hello

You can try this :
You log in with your username and :
[B]df  -h 
df  -i 
[/B]You vérifies there is no filesystem around 100% in column Util%.
If no you can do :
[B]sudo  rm  .Xauthority .ICEauthority
[/B]
And you try to reboot.

---

### Post by lsutiger on 2014-01-09
Thanks for the quick reply!

One of the ways I foxed the original problem was by removing files because I was using 100% Inodes, which is now down to 45%, and nothing reporting near 100% at the moment. 
I will try to remove those files and reboot once I get to the computer.

Thanks again!

---

### Post by lsutiger on 2014-01-09
Ok. Tried removing the files but same result.

---

