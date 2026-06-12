---
title: "incorrect $home permissions and .dmrc file"
date: 2006-12-12
forum: General Help
---

### Post by jordilin on 2006-12-12
I have the following problem and I've already seen different threads about the following message when logging in:
> User's $ HOME /.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. **Users $ HOME directory must be owned by user and not writable by other users**.
I've solved it by deleting the .dmrc file and changing /home/username permissions to 700. Incredibly, my /home/username had rwxrwxr-x permissions. I don't remember which are the defaults permissions in /home/username. Can't you take a look guys (ls -l). If when installing Ubuntu they are 700, who the hell changed the permissions to 775?? I mean, my home directory was writeable  and readable by others. I'm the only one who uses this computer, but having these security flaws is horrible. I took for granted that the only one who can access my home/myusername it's me and nobody else.

---

### Post by jordilin on 2006-12-12
and take a look at the notice:
> Users $ HOME directory must be owned by user and not writable by other users.

it gives me the idea that sth changed my permissions. Really scary.

---

### Post by ayoli on 2006-12-12
by default your main group is your named as your username and your home have 775 perms because you're supposed to be alone in this group, so your home is only readable from others. if you change your main group to another (ie: users) you have to change your home/user perms to 755 (or 700 if you are paranoid and don't want other users able to read your files)

---

### Post by Barney on 2006-12-14
"User's $ HOME /.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. Users $ HOME directory must be owned by user and not writable by other users."

Same problem here - machine has been working flawlessly for three months; and then this.

Standing by for a definitive fix to this vexing situation.

---

### Post by bodhi.zazen on 2006-12-14
.drmc file permissions:
	sudo chmod 644 .dmrc
	sudo chown username .dmrc
	sudo chmod 755 /home/username
	sudo chown username /home/username

	OR

	sudo chown  username /home/userfolder 
	sudo chmod 755 /home/userfolder
	sudo rm -rf /home/userfolder/.dmrc

	[http://www.ubuntuforums.org/showthread.php?t=168015](http://www.ubuntuforums.org/showthread.php?t=168015)
	[http://ubuntuforums.org/showpost.php?p=875518&postcount=8](http://ubuntuforums.org/showpost.php?p=875518&postcount=8)

---

### Post by Barney on 2006-12-14
bodhi.zazen,

sudo chmod 644 .dmrc
sudo chown username .dmrc
sudo chmod 755 /home/username
sudo chown username /home/username

WORKED!  Thank you.

This may be some kind of record for this forum, as I had the correct solution in three (3) minutes after I posted!

---

### Post by MiD-AwE on 2006-12-21
I recently installed edgy and my wife's account worked perfectly, though mine had this identical issue. I'm just sounding in to say that the above solution worked for me also. Thanks.

---

