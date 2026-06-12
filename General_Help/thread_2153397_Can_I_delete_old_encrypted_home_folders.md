---
title: "Can I delete old encrypted home folders?"
date: 2013-06-10
forum: General Help
---

### Post by kittkatt on 2013-06-10
Hello,

I've got several old home folders that have been encrypted thanks to the ubuntu default option in the installation menu.  I don't care about the files but want to free up room on my harddrive.  Can I just "rm -rf" the folders to free up the space?  Right now when I click on the folders only two files are visible "Access-your-private-data.desktop" and "README.txt";  the folder properties state that it only has a size of 100 bytes which is definately wrong.   

Again, just wondering if I can "rm -rf" the folder to free up the space on my HDD.  Or do I have to boot up using an alternate OS, mount the folder, decrypt and then delete it that way somehow?

---

### Post by searchfgold6789 on 2013-06-11
As long as the accounts themselves are deleted, a quick ```
sudo rm -rfv
``` to the home directory (/home/[username]) should do the trick.

---

### Post by kittkatt on 2013-06-11
> **searchfgold6789 said:**
> As long as the accounts themselves are deleted, a quick ```
sudo rm -rfv
``` to the home directory (/home/[username]) should do the trick.

Ok, just tried this.  As I feared, the operation only superficially deleted the folder and the two files "Access-Your-Private-Data.Desktop and README.txt"; there was no corresponding increase in free space.  Now, without a full reformat of the entire disk, I believe those files will permanently take up space on the HDD since they are encrypted and there is no way to access them since I deleted the home folders as was suggested.

Let this serve as a warning to anyone else who wishes to do the same thing.

---

### Post by searchfgold6789 on 2013-06-11
Those two files were a README and a shortcut to the program designed to help the user access the data, which should be stored in `/home/[username]/.private`. Deleting them would only get you the 100 Kb. Are you sure you deleted the home directory itself, not just the Desktop folder or something else? What is the command you used and the output?

---

### Post by cool110 on 2013-06-11
> **searchfgold6789 said:**
> Those two files were a README and a shortcut to the program designed to help the user access the data, which should be stored in `/home/[username]/.private`. Deleting them would only get you the 100 Kb. Are you sure you deleted the home directory itself, not just the Desktop folder or something else? What is the command you used and the output?

/home/[username]/.private is a symlink to /home/.ecryptfs/[username]/.private 
Deleting /home/.ecryptfs/[username] will free up the disk space.

---

