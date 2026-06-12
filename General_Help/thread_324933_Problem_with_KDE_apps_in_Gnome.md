---
title: "Problem with KDE apps in Gnome"
date: 2006-12-24
forum: General Help
---

### Post by Lasse_ on 2006-12-24
Hi all and happy Chistmas!

I'm having some trouble running KDE applications like Amarok and Kaffeine in Gnome.

I need to run those as root in order to get them work. If I try to launch either of those apps as a normal user, I get a series of error messages saying something about dcopserver not running and some other KDE related errors. Messages vary between those two applications, Amarok complains about the dcop server (?) and Kaffeine just won't start. As a sudo user, I can run Amarok fine but it has no effect on Kaffeine.

Amarok also complains that it hasn't acces to .KDE folder in my /home/. I searched the forum for a solution and I came by this problem with someone trying to use KDE with Gnome and in order to get KDE to boot he needed to run it as a sudo user. The solution for that problem was to change the read/write rights of one's /home to 777 with chmod, like this: 

```
sudo chmod -R 777 /home/user/
```

I did that and Amarok and Kaffeine started to work fine but while booting to Gnome I get this messages complaining about the home folder's rights, which should be 644 enabling the window manager to write some confs to /.dmrc folder. Chmodding from 777 to 644 just brings back the original problem with the KDE applications.

 Any ideas?

---

