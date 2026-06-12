---
title: "How to install add on cd ?"
date: 2005-08-05
forum: General Help
---

### Post by bill on 2005-08-05
I download the add on cd and burned it on a cd,i typed (sudo sh/media/cdrom 0/install.sh) in root terminal but it says command not found.The thing i don't understand is instructions says something about installing a script,how would i go about that?
Thanks Bill

---

### Post by andlinux21 on 2005-08-05
did you type the command or did you cut and paste it?  If it saw the Cd in the drive it should just install I didnt have a problem with it. :)

---

### Post by professor_chaos on 2005-08-05
I noticed syntax errors in your command.

if your cdrom is indead "/media/cdrom 0"    ... then you would need to handle the whitespace (or space) between the cdrom and 0 with "/media/cdrom\ 0"

I doubt this is the case as my path is /media/cdrom0 (no spaces).

also, I believe you need a space between the sh and the path.

Try ```
sh /media/cdrom0/install.sh
``` 

if your using bash try typing ```
sh 
``` (note the space after sh) And then ```
/med
``` and then press the TAB-key, which will auto complete the rest of /media. Then you can autocomple the rest of cdrom0, by doing the same thing and the same for the install.sh file. (I think current versions of csh and tcsh will work too) to make sure the path is correct.

---

### Post by bill on 2005-08-05
professor chaos
Thank you, for the help the spaces were the problem i got everything installed.
Bill

---

