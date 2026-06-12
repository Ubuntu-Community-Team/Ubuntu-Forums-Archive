---
title: "&quot;Deleted&quot; protected folder, lost hard drive space!"
date: 2006-11-18
forum: General Help
---

### Post by hypersonic5 on 2006-11-18
Here is the scenario. I was playing around with Reconstructor, since it seemed like a neat idea to make my own custom distro. What this program does is it takes an ubuntu iso image and allows you to edit it. In order to do this it needs 2.4 gigs of space to uncompress your iso in order to change things around. So I started playing with it, and halfway through decided it was too much of a hassle. I close the program and then tried to delete the 2.4 gig folder it had created in my home directory. It was protected by root access so I just used a script that I had gotten from Automatix to open up my home directory with root access in nautilus and attempted to "move to trash" the folder. The folder disappeared, but didn't show up in the trash can. Worse yet, my filesystem indicates that the file still exists (it had around 7 gigs free before I installed it, and now says only 4.7 or so are free).

So now I have a huge folder that is taking up a lot of space on my drive that I cannot find and delete. And what does this genius, yours truly, decide to do to figure out how to fix it? I reinstalled reconstructor again and went through the whole process a second time, hoping that instead of making a new folder, it would make my old one reappear. Not only did that not work, but now I have another 2.4 gig folder in my home directory. Needless to say, I'm not going to attempt to delete this one the same way.

So I need some help. First of all, how would I go about deleting a root access only folder safely? Second, is there any way to either "find" the first invisible folder, or somehow make my filesystem display the remaining size properly? Maybe force some kind of recount of the filesystem? Do you know of anything else that might help me in this situation?

Thanks a bundle in advance.

hyper

---

### Post by catlett on 2006-11-18
First, rm is the comand for remove and sudo make you root
```
sudo rm /home/hypersonics/reconstructor
```
Second, maybe the folder is hidden? Use Ctrl H (that is the keyboard key control and the key capital h at the same time) when browsing files in nautilus ti show hidden files. Maybe it is hidden in home or trash?

---

### Post by hypersonic5 on 2006-11-18
That is what I thought initially as well, that it might just be hidden. But I toggled the hidden files view and found nothing, not even in the trash. It very strange. The thought of misplacing a 2.4 gig folder is very silly; I don't know how it could have happened.

Oh, by the way, I tried the command you showed me and I get:

rm: cannot remove `/home/***/reconstructor': Is a directory


Best regards,

hyper

---

### Post by hypersonic5 on 2006-11-18
Oh, and I just tried the rmdir command and it wont delete it because it says the directory is not empty. ](*,) :-?

---

### Post by scxtt on 2006-11-18
sudo rm -rf /home/hypersonics/reconstructor

---

### Post by hypersonic5 on 2006-11-19
Okay, I got rid of that folder. Thanks for that command scxtt. I wish I knew about that before :(

Now, does anybody have any idea what happened to folder that disappeared?

---

### Post by bettlebrox on 2006-11-19
Try this:

cd ~; du -hs .[a-z]*|grep G;

And see if you can find any directories in your home that are Gigs in size.

After posting this, I'm thinking that if you opened Nautilus as root and moved the directory to Trash that the directory is in root's trash and not yours.

---

### Post by hypersonic5 on 2006-11-19
bettlebrox:

That does sound very logical! How exactly would I be able to access root's trash can? I tried the same script that got me into this mess on the trash can and it is still empty. I'm hoping that root has a hidden trash can somewhere?

Oh, and I get nothing with that command you gave me.

Oh, and thanks for all of the help guys! You are great. Ubuntu has the greatest and friendliest community around! Just one more reason why I run Ubuntu as my main OS :)

---

### Post by hypersonic5 on 2006-11-19
All right, I resolved the problem! I found the hidden trash folder in root's folder and what do you know? There is my missing folder! Thanks a ton for all of the help everyone!

---

