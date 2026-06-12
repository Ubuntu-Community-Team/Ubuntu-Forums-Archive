---
title: "Can log in as Guest, Root and new Testing user but can't log in with main user"
date: 2013-10-28
forum: General Help
---

### Post by bachtobach on 2013-10-28
I rebooted my machine and couldn't get past a screen saying Checking Battery State. I googled around and managed to create a new user (Testing) and I am currently logged in with that and everything seems ok but when I try to log in with my main user profile it flashes a black screen with some writing at the top and then goes back to the log in screen, the writing doesn't stay long enough for me to see what it says. 

I'm using xubuntu 12.04. 

Is there any way to reset the settings in the profile or something? I don't understand what couldn't happened that allows me to log is as a different user but not the main one.

---

### Post by pqwoerituytrueiwoq on 2013-10-28
ctr+alt+f1
login run 
rm ~/.Xauthority*
ctr+alt+f7
try to login

---

### Post by bachtobach on 2013-10-28
I just tried that but it didn't fix it. This time I saw the Checking Battery State message just before it flashed back to the login screen.

---

### Post by bachtobach on 2013-10-28
I seem to have fixed it. I found some instructions which detailed creating a password for root and logging in with that and then moving all the .* files and folders in to a backup folder and then logging out/logging in with main user again. That enabled me to get in again but I had some issues with permissions which I think I've fixed now as well by following the instructions in another thread here with [some chown commands ]("http://ubuntuforums.org/showthread.php?p=6161267"). Thanks for the help, I think this is solved now.

---

