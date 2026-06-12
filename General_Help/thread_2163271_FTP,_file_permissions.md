---
title: "FTP, file permissions"
date: 2013-07-17
forum: General Help
---

### Post by scarabcoder on 2013-07-17
I am currently making a game, and I want to keep an online score. I know how to store the text of an online file in a variable, and how to upload things over FTP. I created a user account called score on my computer, and set the home folder to a folder called ftp. I installed vsftpd on my computer, and ran it. I can connect to my computer and the folder via Filezilla, but I don't have any permissions to delete or change the score file over FTP. Can someone please tell me how to let the FTP user change JUST the score file? Thanks ahead of time,
--Scarabcoder

---

### Post by Jonor on 2013-07-18
File permissions can be accessed by mouse right clicking on the file and selecting properties > permissions and allow others to read and write. 
If you used root to make them you'll need it to change them too (sudo nautilus in a terminal for the nautilus file browser and drill down to the file).

---

