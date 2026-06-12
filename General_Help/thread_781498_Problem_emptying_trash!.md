---
title: "Problem emptying trash!"
date: 2008-05-04
forum: General Help
---

### Post by magnus0 on 2008-05-04
I cannot empty the trash bin. When I click Empty Trash, it shows a progress bar, but the files don't get deleted. When I go to trash bin and delete them manually, I get a permission error. How can I change the permissions on those files, so I can delete them?

---

### Post by jimbob on 2008-05-04
Check out this link.  Evidently trash has been moved in Hardy.

[http://ubuntuforums.org/showthread.php?t=759544&highlight=.trash](http://ubuntuforums.org/showthread.php?t=759544&highlight=.trash)

---

### Post by charkoal on 2009-03-09
i know where the trash is, but still cant empty it :(

---

### Post by Dysport on 2009-03-09
have you tried it via console command "sudo rm [file]"?

---

### Post by UbuntuNerd on 2009-03-09
try this command:
```
sudo rm -rf ~/.local/share/Trash
```
if that doesn't do it try this:(where user is your login name)
```
sudo -i
```
then
```
rm -rf /home/user/.local/share/Trash
```
still can't empty it, try this solution which always works, in a terminal:
```
gksudo nautilus
```
browse to this location '/home/user/.local/share/Trash' and delete the folder.

---

### Post by charkoal on 2009-03-10
thanks that was the solution i was after :D

---

