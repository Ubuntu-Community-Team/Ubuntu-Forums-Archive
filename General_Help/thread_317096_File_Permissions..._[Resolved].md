---
title: "File Permissions... [Resolved]"
date: 2006-12-11
forum: General Help
---

### Post by tbonejo on 2006-12-11
My wifes account, I was of course messing around...anyways when she logs on it save it cant save the default session and language, that it cant write to .dmrc file and it needs to be set to 644?

How and what do I need to do?


Thanks,

Tom

---

### Post by aysiu on 2006-12-11
Log into your account and type this command into the terminal: ```
sudo chmod 644 /home/tomswife/.dmrc
``` Substitute in your actual wife's username for *tomswife*.

---

### Post by bodhi.zazen on 2006-12-11
sudo chmod 644 .dmrc
	sudo chown username .dmrc
	sudo chmod 755 /home/username
	sudo chown username /home/username

	OR

	sudo chown  username userfolder 
	sudo chmod 755 /home/userfolder
	sudo rm -rf /home/userfolder/.dmrc

Use your wife's log-in username for "/home/username"
	[http://www.ubuntuforums.org/showthread.php?t=168015](http://www.ubuntuforums.org/showthread.php?t=168015)
	[http://ubuntuforums.org/showpost.php?p=875518&postcount=8](http://ubuntuforums.org/showpost.php?p=875518&postcount=8)

---

### Post by tbonejo on 2006-12-11
Thanks to both of you, it worked.

Im really liking this ubuntu better than before.


Thanks again,

Tom

---

