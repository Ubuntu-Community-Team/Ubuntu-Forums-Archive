---
title: "Make links to a Wine command"
date: 2007-08-27
forum: General Help
---

### Post by telovoyagarcar on 2007-08-27
Please pay attention !!! and read it all... thanks
I installed MSN Messenger using wine under the root account.
i can not access the root folder from the main user account that i want to run messenger from.
So i have to "su" in a terminal to become root, then navigate to /root/.wine/drive_c/Program Files/MSN Messenger
and from there "wine msnmsgr.exe" to launch the program.

I just need an icon in my user desktop that can take care of all this..

Thanks

---

### Post by Sikarian on 2007-08-27
Make a shell script.  Here's one I got

```

#! /bin/bash
# script to launch MSN

cd /root/.wine/drive_c/Program\ Files/MSN\ Messenger/
sudo wine msnmsgr.exe

```

Save as something like "msnmsg" and put it in your /usr/bin folder, then chmod +x on it to make it executable.

Give that a shot.  You'll have to type your su password when you run it, but it works.

---

### Post by Lord Illidan on 2007-08-27
> **telovoyagarcar said:**
> Please pay attention !!! and read it all... thanks
I installed MSN Messenger using wine under the root account.
i can not access the root folder from the main user account that i want to run messenger from.
So i have to "su" in a terminal to become root, then navigate to /root/.wine/drive_c/Program Files/MSN Messenger
and from there "wine msnmsgr.exe" to launch the program.

I just need an icon in my user desktop that can take care of all this..

Thanks

Why did you install it under the root account??

---

