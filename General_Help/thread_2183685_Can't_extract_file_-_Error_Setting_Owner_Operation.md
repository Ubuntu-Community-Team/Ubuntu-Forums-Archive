---
title: "Can't extract file - Error Setting Owner: Operation Not Permitted"
date: 2013-10-25
forum: General Help
---

### Post by jferreir on 2013-10-25
I'm trying to extract the PS3 Media Server tar.gz file, but I keep getting the same error message of "Error Setting Owner: Operation Not Permitted". I'm running Ubuntu 13.10, which is basically fresh. I also installed 7zip, but I don't think that's causing it. Can anyone help me out? I've had Ubuntu installed for only a week and I'm pretty clueless. 

Thanks!

---

### Post by rahul.tejwani03 on 2013-10-26
Same issue with me!!!!

---

### Post by Rowan_ on 2013-10-26
This is occurring to me as well after a clean install of 13.10.  If I open nautilus from terminal (sudo) nautilus I can extract the file, but the extracted files are locked and when I try to unlock them nautilus crashes.
help!

---

### Post by gaseeley2 on 2013-10-27
> **Rowan_ said:**
> This is occurring to me as well after a clean install of 13.10.  If I open nautilus from terminal (sudo) nautilus I can extract the file, but the extracted files are locked and when I try to unlock them nautilus crashes.
help!
Open a terminal and cd to the directory with the tar file.  Then "[FONT=Ubuntu Mono]tar -xvzf myTar.tar.gz".  Type "man tar" to figure out what will happen.  Maybe Nautilus is broken?[/FONT]

---

### Post by oldos2er on 2013-10-27
> **jferreir said:**
> I'm trying to extract the PS3 Media Server tar.gz file, but I keep getting the same error message of "Error Setting Owner: Operation Not Permitted". I'm running Ubuntu 13.10, which is basically fresh. I also installed 7zip, but I don't think that's causing it. Can anyone help me out? I've had Ubuntu installed for only a week and I'm pretty clueless. 

Where in the file system are you trying to extract the *tar.gz? It's normal for your user not to have write permissions outside of your /home/user/ folder. You can either 1) extract the file somewhere within your home folder, or 2) elevate your user's permissions using [sudo]("https://help.ubuntu.com/community/RootSudo") (or gksudo graphically) to extract to a system folder; for example ```
 sudo tar xvzf foo.tar.gz /opt/
```

---

### Post by Sparksman on 2013-10-28
greetings gentleman!

the bug is confirmed... a fix is proposed!

  
more infos:

  [URL="https://bugs.launchpad.net/ubuntu/+source/file-roller/+bug/1238266"]
https://bugs.launchpad.net/ubuntu/+source/file-roller/+bug/1238266[/URL]

  

cheers!

---

