---
title: "How to give more option sudoers list"
date: 2013-07-03
forum: General Help
---

### Post by nammunayak on 2013-07-03
Hello,

I have sudoers file in which I have entry to not ask sudo password for "tune2fs" command. It worked really well. The line as below

 "username ALL=NOPASSWD:/sbin/tune2fs"

Now I would like to add another command i.e apt-get which I don't want to ask sudo password to enter. I would like to add to this option in same line 

"username ALL=NOPASSWD:/sbin/tune2fs;/usr/bin/apt-get"

But it fails and asks for sudo password to enter. I don't want to add new line again with different command. Is there any way so that I can add all command in one line itself.

Thanks in advance

---

### Post by TheFu on 2013-07-03
Use a Cmnd_Alias - **man sudoers** explains.

Also, did you try a comma instead of the semicolon? Cmnd_Spec_List in the man page says to use a comma or am I reading that wrong?

---

### Post by nammunayak on 2013-07-04
Thank you very much. It worked fine.

Thanks once again.

---

