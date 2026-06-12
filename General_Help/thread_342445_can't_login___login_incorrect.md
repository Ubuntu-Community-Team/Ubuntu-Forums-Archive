---
title: "can't login :  login incorrect"
date: 2007-01-20
forum: General Help
---

### Post by jonny407 on 2007-01-20
I just installed ubuntu and I am unable to login. I can't get it started because it keeps telling me" login incorrect". I know what my password is, but what would the username be? I was never asked to input a username during installation so I have no idea what it could be. When I boot up it says "home login:" what do I need to type here? I have tried using my password but then it just asks for my password then I get "login incorrect". How do I get past this?

---

### Post by xerxesv5 on 2007-01-20
At install there should have been a "Who are you" dialog. There were 2 questions here, "What is your name" and "What name would you like to logon with". The latter should be the user name. 

Also, remember that both username and password are CaSe sEnSiTiVe. Should this not help, there's something a bit more complicated you can try, but try this first. :)

---

### Post by jonny407 on 2007-01-20
I have installed twice thinking that I may have missed a screen like that, but I never get asked "who are you". I don't know what the username is because ubuntu never asks me to input one during installation.](*,)

---

### Post by xerxesv5 on 2007-01-20
Ok... that's obscure. What version of Ubuntu are you installing? And I'm assuming its onto a PC (as opposed to a Mac)?

---

### Post by jonny407 on 2007-01-20
Ubuntu 6.06. I just tried installing it again but all I get asked is for a "host name" which I made "home" and I get asked for a password, but I never get asked for a username.

---

### Post by bapoumba on 2007-01-20
hello, did you install from alternate cd ?
if so, your login is oem and the password the one you gave during the install procedure.

Login into oem session, open a terminal (> Accessories > Terminal) and run **sudo oem-config-prepare**. Give  your password. Next time you login, oem user will be deleted, and you will be prompted for a new login and password to create your user.

---

### Post by jonny407 on 2007-01-20
I had to use an alternate cd because the PC dose not have enough ram for the regular disc. I tried reinstalling again this time I used the "install in text mode" option. Finally it asked me for a user name :D

---

