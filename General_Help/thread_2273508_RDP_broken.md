---
title: "RDP broken?"
date: 2015-04-13
forum: General Help
---

### Post by lsutiger on 2015-04-13
Using 14.04.2. 
Yesterday afternoon from home, I attempted to RDP into a cloud server our company uses. I have been using Remmina for this particular RDP since October 2014. Well, yesterday I get a message "Unable to connect to RDP server xxx.xxx.xxx.xxx". Hmm, thought maybe just offline. It's Sunday, I won't worry about it until tomorrow.
First thing I do when I get to work is attempt to RDP into the server. Same message, different computer, same OS install and using Remmina. I then ask my coworker to do so using Windows. No problem. I try from my Win 7 virtualbox install. No problem.
Hmmm...Maybe the session file is corrupt? I delete the session, remake it with a different name. Same message.
Scratching my head. I install Remote Desktop Viewer (Vinagre). Same message!
I then install KRDC to try a KDE package. Guess what - IT WORKS!
So my guess is that there was an update that broke RDP for Ubuntu/Gnome?
Anyone else had this problem? If so. did you do anything to fix it? If not, would any of you want to assit me in troubleshooting this issue? I really like Remmina and would like to continue using it.
Thanks

---

