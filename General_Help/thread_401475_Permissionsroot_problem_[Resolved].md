---
title: "Permissions/root problem [Resolved]"
date: 2007-04-04
forum: General Help
---

### Post by keithk50 on 2007-04-04
Following the sucessful download of of RealPlayer via their website I now have the RealPlayer folder sitting on the desktop.   The folder (and all files) are owned by root and will not allow me to move it into my home folder.   Although the player is working okay (had a lot of problems trying to install it since moving to Ubuntu a couple of months ago) I have obviously done something wrong in the Terminal during installation.   How do I get the folder off the desktop and 'put it to bed' in the correct location?        
Any help appreciated.

---

### Post by zvacet on 2007-04-04
```
cd /Desktop
```
```
sudo cp program_name /home/username/folder_of_your_choice
```

After you do that you can remove it from Desktop
```
sudo rm -r program_name
```
You have to be in Desktop directory

---

### Post by aysiu on 2007-04-04
Read this:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by keithk50 on 2007-04-04
Thanks guys, I really appreciate the help.

---

### Post by keithk50 on 2007-04-05
After entering cd /Desktop into the Terminal the message came back 'no such file or directory'.  I tried this several times but the same output appeared.   When I tried 'mkdir Desktop' the output was "can not make directory, file exists"
Any suggestions?    Thanks.

---

### Post by aysiu on 2007-04-05
You don't need to use the terminal if you follow the link I posted earlier.

There's a typo in zvacet's post. It should say ```
cd ~/Desktop
```

---

### Post by keithk50 on 2007-04-05
Thanks for the reply.   Problem solved.   I have read the link you kindly supplied me and it is starting to sink in.   Thats what happens when you use windows for years and the brain ceases to work in any logical manner.   Take care.

---

