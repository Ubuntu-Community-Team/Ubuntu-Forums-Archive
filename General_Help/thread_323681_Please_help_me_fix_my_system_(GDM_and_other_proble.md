---
title: "Please help me fix my system (GDM and other problems)"
date: 2006-12-22
forum: General Help
---

### Post by Kunio on 2006-12-22
Hi im a noob 2 days ago i got the GDM error becouse my hdd was full and i cant log in now i want i want to fix my problem by reinstaling Ubuntu but i got my cd-rom broken and cant use the CD i have downloaded the .iso file with the OS from ubuntu.com and want to instal it by boting the .iso file while my system is startiing WITHOUT CD rom dvd rom and fdd is there a way to fix my problems ?  please help me if you can and sorry for my bad english and sorry for my 1 post here is a post like this.. 
Merry Christmas :cool:
PS: how to bot in "safe mode" ?

---

### Post by shane2peru on 2006-12-22
Ok, we are going to need a little more info.  Can you let us know what happens when you boot into Ubuntu?  Do you at least get a log in screen?  What does the error say?  Do you know how much room you have on your hdd?  If you can get booted into a terminal we can probably fix some of this.  If not, I'm not sure you you can install without a CDROM, I know it has been done, but I don't know much about it.

Shane

---

### Post by Kunio on 2006-12-22
Hi thanks for reply :) 

Yes im geting to the log in screan user name & password then it shows the GDM error (GDM could not write your authorization file this could mean that you are out of disc space or that your home directory could not be opened for writing in any case its not possible to log in please contact the system administrator) im 99% sure i dont have any room on the partition left becouse when i 1 instaled ubuntu i gave only 3 gigs of space for the instalation thinking i wouldnt use it anyway (im GOING ot use it:) basicly i want to log in and put the rest of my space in the ubuntu partition or if this is not possible i want to reinstal the system and start from begining :-k

---

### Post by shane2peru on 2006-12-22
Well, I just did a quick search on Google for booting Ubuntu with a net install, but didn't find anything.  I will have to leave this to someone that is a little experienced than I.  I'm know there are ways to install without CD, but I'm not sure what they are.  Do you have the ability to boot from a USB device?  

Shane

---

### Post by Kunio on 2006-12-22
THanks for looking i do not have the ability to bot from USB device i just got a old cd rom but it stops when it starts adding live user :s anyway i can use the console im going to rebot now and see if it works
EDIT: Yes i can use the console + recovery mode is there a way to delete some unwanted files so i can bot it and learn to use this wonderfull system?

---

### Post by shane2peru on 2006-12-22
Great, glad to hear you got it fixed.  :D 

Shane

---

### Post by Kunio on 2006-12-22
No no you got me wrong :) i dont know what to do next i can only go as far as the log in window i can use recovery mode but i dont know what to write there (im still learning) i can also use the console ctr+alt+f1 btw maybye it would be possible to resize my (D:) - linux from windows lets say giving it 7 g more space but when i use Partition magic it says the partition is bad witch is strange becouse i can use it on windows:confused:

---

### Post by shane2peru on 2006-12-22
Oh, ok, if you can get it that is good.  You will need to log in with your user name and password.  If it doesn't let you try logging in as root and your password.  Be carfull with this as you can mess up important things.  You will need to go to your home directory like this:
```
cd /home/username 
```

After that you will want to search for some files that you can delete and then delete them using ```
rm filename
```  Be carefull not to remove things that you need.  If you really didn't use too much of Ubuntu before, I really don't understand how your /home/username directory could have anything in it.  If all is on one partition you can try this:```
sudo apt-get clean
```  That will free up some space.  If you still need space try removing some games ```
sudo apt-get remove gnome-games
```  This will free up a little space.  Once we get in I believe we can get some more space.

Shane

---

### Post by Kunio on 2006-12-22
Shane im writting it from dd thank you wery much for your help!:)

---

### Post by shane2peru on 2006-12-22
no problem, do some searching on the forums for expanding your partition :D   There is probably something posted on how to do that.  If not I would make another partition for your /home directory.  That may be tricky since you will need to change your mount points.  It is out of my range.  Glad I could be of help!

Shane

---

