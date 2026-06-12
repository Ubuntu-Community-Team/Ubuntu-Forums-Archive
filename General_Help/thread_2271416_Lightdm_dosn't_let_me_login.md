---
title: "Lightdm dosn't let me login"
date: 2015-03-30
forum: General Help
---

### Post by obake2 on 2015-03-30
I have been using Ubuntu Gnome(shell) 14.04 for quite some time, and decided to install Xubuntu-Desktop so that I can try out how Xfce is faring in Ubuntu. 

I installed Xubuntu-desktop and chose lightdm as the login manager. After the installtion was over, I restarted the computer and when the Login Manager (lightdm) showed up and typed my password, it didn't let me login. I tried to login to Xfce (Xubuntu), Xfce, Gnome, Gnome Classic to no vail. Everytime I login it throws me back to lightdm again.

What could I do to fix this?


Thank you in advance guys ^_^

---

### Post by obake2 on 2015-03-30
Hello everyone. Just wanted to inform you that I was able to solve the problem by removing the files .Xauthority from my home directory. I backed up the files just in case, but I'm glad it worked.

```
rm /home/<user>/.Xauthority
```


The solution was [found here]("http://askubuntu.com/questions/316778/ubuntu-13-04-cant-login-to-unity-keep-going-back-to-login-screen-with-all-us").

---

