---
title: "Can not install and run Seamonkey"
date: 2019-02-20
forum: General Help
---

### Post by raleigh3 on 2019-02-20
I am trying to install Seamonkey.
  
I am using the method shown here.

  [Why isn't Mozilla SeaMonkey available in the repositories? How can I install it?]("https://askubuntu.com/questions/397272/why-isnt-mozilla-seamonkey-available-in-the-repositories-how-can-i-install-it")

  When I try to do the key command, my connection times out.

  ```
andy@7:~$ sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com C1289A29
Executing: /tmp/apt-key-gpghome.mMHsuyF3KI/gpg.1.sh --recv-keys --keyserver keyserver.ubuntu.com C1289A29
gpg: keyserver receive failed: Connection timed out
     

```I have also tried installing Seamonkey and running seamonkey and seamonkey-bin which use to work.

But get the message

```
Failed to execute seamonkey
Failed to execute child process “/home/andy/Seamonkey/seamonkey/seamonkey” (No such file or directory).
```

---

### Post by Frogs Hair on 2019-02-20
Those instructions date back to 2013. You may have to enable nautilus the run/execute programs in preferences and make sure you have the proper 32 or 64 bit version. I have run FF from folders recently.  

[https://www.seamonkey-project.org/](https://www.seamonkey-project.org/)

---

### Post by &amp;KyT$0P# on 2019-02-20
You could try instead downloading it from the official website (Frogs Hair already posted the link) and install it by [this method]("https://ubuntuforums.org/showthread.php?t=2323075&p=13516314&viewfull=1#post13516314").

---

### Post by raleigh3 on 2019-02-21
I got it installed. 


 I found the debian package here
[URL="https://sourceforge.net/projects/ubuntuzilla/files/mozilla/apt/pool/main/s/seamonkey-mozilla-build/"]
[https://sourceforge.net/projects/ubuntuzilla/files/mozilla/apt/pool/main/s/seamonkey-mozilla-build/](https://sourceforge.net/projects/ubuntuzilla/files/mozilla/apt/pool/main/s/seamonkey-mozilla-build/) 1[/URL]

---

