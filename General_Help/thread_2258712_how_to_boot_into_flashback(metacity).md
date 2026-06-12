---
title: "how to boot into flashback(metacity)"
date: 2014-12-29
forum: General Help
---

### Post by stribor40 on 2014-12-29
Is there a way to have it set up so my Gnome defaults into Gnome Flashback. Right now it is my desktop looks like this...
[ATTACH=CONFIG]258882[/ATTACH]

---

### Post by deadflowr on 2014-12-30
You'll log into which ever desktop session you last logged into.
So if you last logged into gnome-flashback-metacity, then that'll be which one you log into next time.

Of course, though, post #1 leaves a lot to be desired. Like how did you logged into the session shown in the screenshot?

---

### Post by stribor40 on 2014-12-30
I have dual boot windows and ubuntu.   From grub i just chose ubuntu and thats it.  I am never propted for anything.  
When i try to switch user(i am only user) then i get promp with ubuntu logo which lets me chose flashback but once i power off and go into it again i am back to screenshot

---

### Post by deadflowr on 2014-12-30
Well the screenie is of ***A*** flashback session.
I cannot tell if it is no effects/metacity or effects/compiz.

You have autologin enabled so the behavior of logout and then showing the login screen where you can switch which session to run is normal.

---

### Post by stribor40 on 2014-12-30
When i switch user(to me) at the prompt i am presented(by clicking on ubuntu icon) with multiple options.  How do i make one of those option as a default every time i boot into ubuntu?

---

### Post by stribor40 on 2014-12-30
I guess what i am asking is how do i get this [http://linuxlookup.com/files/imagecache/800x600/ubuntu_11.10_login.png](http://linuxlookup.com/files/imagecache/800x600/ubuntu_11.10_login.png)
(disregard versions of gnome in this image) to show up every time i boot into ubuntu? 
I would like to have that prompt every time i boot

---

### Post by deadflowr on 2014-12-30
Go to system settings >> user accounts(or look for user accounts in the menu; I think it's under Administration), and click on the lock in the top right corner enter your password and then toggle the auto login button to off.
Do not do anything else, except to close the window.
(Sometimes people think they can play with the password setting and it says disable which they assume means make it so they can use the system without a password, which is wrong; That option disables the account, basically. So avoid it)

You probably set autologin during install, which has the option to do so.

---

