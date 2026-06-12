---
title: "Lock Screen Loop"
date: 2020-10-23
forum: General Help
---

### Post by jakel20062 on 2020-10-23
I have an issue where I can log in fine but if my screen locks due to inactivity once I put my password in the screen logs me in but immediately goes blank and locks the screen again. I have tried all the possible solutions which I found online, grub, xauthority, reinstalling desktop manager and tmp folder permissions but nothing seems to be working. Any help would be appreciated. This is after a fresh install of Groovy Gorilla.

---

### Post by uRock on 2020-10-23
Hello and welcome to the forrums,

Try hitting Ctrl + Alt + F3, which will bring you to a terminal login.
Enter your username and hit Enter
Enter your password, which the terminal will not show as you type, then hit Enter,
Run the following command to check the ownership of the Xauthority file,
```
ls -lah | grep -i Xauthority
```
If it shows the owner as being the owner, then this is the problem,
This is how it should look;
```
ls -lah | grep -i Xauthority
-rw-------  1 username username   56 Oct 23 15:22 .Xauthority
```
If it shows root, then run the following command;
```
sudo chown username:username .Xauthority
```
If it asks for a password, then your usual password should work.
You can review the change by rerunning the first command.
If all looks correct, then hit Ctrl + Alt + F7 to get back to your normal login screen.

Found that answer [here]("https://www.maketecheasier.com/fix-ubuntu-login-loop/#:~:text=Instead%2C%20press%20Ctrl%20%2B%20Alt%20%2B,provide%20your%20password%20when%20asked.").

---

### Post by jakel20062 on 2020-10-24
I have investigated this, by doing a fresh install and going through my gnome-shell-extensions one by one and found that the problem was BottomPanel which caused an error with 20.10 and created the problem.

---

