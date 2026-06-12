---
title: "[SOLVED] .dmrc Login error"
date: 2007-09-22
forum: General Help
---

### Post by JawsThemeSwimming428 on 2007-09-22
For the past two days I have been trying to get my two PC's (one running Feisty and a brand new Vista Home Premium machine) able to see eachother over my Linksys Wireless network. I followed Stormbringer's Samba guide ([http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)) and was able to see my Feisty share from my Vista machine. After a Vista and Feisty reboot, I can not access the mapped drive or even browse to my Feisty machine to remap it (they both have Static IP's). One thing I did notice... I tried to share my home folder, but when I rebooted I was presented with the following message onces I typed my password and hit Enter to log in:

" User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users."

I am not quite sure what that means or what I should do to fix it (or if it has anything to do with my network folder access problem above... In smb.conf I elected to share /home/willy which is my home directory).

I have not been able to resolve this issue, anyone that can help me out I would be VERY grateful!! Thanks.

---

### Post by bodhi.zazen on 2007-09-22
in a terminal: (use first set)

> 	sudo chmod 644 .dmrc
	sudo chown user_name .dmrc
	sudo chmod 755 /home/user_name
	sudo chown -R user_name /home/user_name

	OR, if that fails:

> 	sudo chown -R user_name /home/user_name 
	sudo chmod 755 /home/user_name
	sudo rm -rf /home/user_name/.dmrc

Where  user_name = your log-in name :p

---

