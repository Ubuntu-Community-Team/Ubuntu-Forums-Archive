---
title: "can't empty item from trash"
date: 2008-05-29
forum: General Help
---

### Post by constantgamer247 on 2008-05-29
okay, so i can empty any thing I want from trash can except a CIV3 folder

i copied the disc of civilization 3 on to my ubuntu desktop (hardy heron), then moved it to the trash, then clicked empty trash and it wont let me, I can put a folder in there and I am aloud to empty that, if I try to empty the CIV3 folder I get nothing or an error saying some thing about insufficient privileges, 

plz help  :confused:

gabe

---

### Post by constantgamer247 on 2008-05-29
sry it says permission denied

---

### Post by umattu on 2008-05-29
Try it from the terminal

cd ~/.Trash
then
sudo rm -r *

This should do it for you.

---

### Post by constantgamer247 on 2008-05-29
i got for the 1st
bash: ch~/.Trash: No Such file or directory

and for ur 2nd command i got 
bash: rm-r*: command not found

---

### Post by fragos on 2008-05-29
An 8.04 update has moved trash from /home/{user}.Trash to /home/{user}/.local/share/Trash/files. .Trash is deleted. I had some stuff in trash across the change and the trash applet was confused. I removed the applet and added it back again and all is well.

---

### Post by kureyamu on 2008-05-29
hello constantgamer247

2 things to try

(1) first the easy one - right click on your Trash icon and select Open; right click on the file in your Trash bin and select Properties at the bottom of the right click menu; in Properties, select Permissions - you may be able to change the permissions to Read and Write  (if only Root is permitted to do this it will be greyed out, and so you will have to try the command line in a terminal again) 
at the top of Permissions it will say Owner: constantgamer247 (or if your name is John, it will say John)
and then it will say Access: Read
Here you can use the drop down menu and change Read to Read and Write; 
the padlock icon should disappear from your file in Trash and then you can delete it.
this system works with most files.

if it doesn't work, go into a terminal and use the command sudo to become administrator (sudo = super user do)
to see the contents of your Trash file you can use ls -a (ls -a = list -all, note that there is a space after ls):
also note that you must use a space between every unit of sense, i shall type (space) to show you where to put a space:
three command lines you can use in a terminal are below:
 
sudo ls	 -a 	/home/constantgamer247/.local/share/Trash/files/

(change constantgamer247 to your ubuntu login name;
you will be asked to give your login password, you will not see the letters as you type but the system will;
the spaces are as below:
sudo (space) ls (space) -a (space) /home/constantgamer247/.local/share/Trash/files/
you will now see the file that you cannot delete as user, but you are now going to delete as administrator;
next you must change directory to your Trash file with the following command line, you do not need the sudo command for this:)

cd /home/constantgamer247/.local/share/Trash/files/

(the space is as below:
cd (space) /home/constantgamer247/.local/share/Trash/files/
make sure your new directory address is on the left of the cursor before you use the powerful remove command:)

sudo rm -r*

(the spaces are as follows:
sudo (space) rm (space) -r*
this command will remove everything in your current directory, which is Trash)

the reason why you had Command Not Found before was (a) wrong directory and (b) maybe not putting in the correct spaces or forgetting to use the command sudo 

regards

kureyamu

---

### Post by kureyamu on 2008-05-30
hi

i meant the reason why you had Command Not Found before was that you were giving the wrong path ...

regards

kureyamu

---

