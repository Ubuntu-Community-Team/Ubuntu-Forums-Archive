---
title: "I can not rename the file or directory"
date: 2007-01-25
forum: General Help
---

### Post by chinese_ys on 2007-01-25
Hi, dudes

Everything looks fine in my ubuntu edgy, but the rename of the file or directory does not work fine, some time works, some time halts!! I am Chinese, I use english as the default language to login,but I still have to use Chinese IM sometimes which works fine. When I want to rename a file or a directory, no matter Chinese or English, the keyboard seems down! But it really works well in editor and web explorer. 

by the way, i also use beryl and kiba-dock. Is there any connection to this problem?

So, some body be expert in this may help me!

Thanks!

---

### Post by bodhi.zazen on 2007-01-26
What files are you trying to change ? I think you have a permissions problem:

[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

---

### Post by chinese_ys on 2007-01-26
thanks man, actually i want to renamw some file in my flashdisk. but it does not work. is that the permission problem?

---

### Post by taurus on 2007-01-26
Is your flashdrive ntfs or fat32 filesystem?

---

### Post by lamego on 2007-01-26
What error do you get when you try the rename ?

---

### Post by chinese_ys on 2007-01-26
> **taurus said:**
> Is your flashdrive ntfs or fat32 filesystem?

my flashdrive is fat filesystem

---

### Post by chinese_ys on 2007-01-26
> **lamego said:**
> What error do you get when you try the rename ?

there is no error prompt, but no response at all. the keyboard seems down in that situation!

---

### Post by taurus on 2007-01-26
What command did you use to change the name of a file on your flashdrive?

---

### Post by chinese_ys on 2007-01-26
> **taurus said:**
> What command did you use to change the name of a file on your flashdrive?

I did that in the desktop, and I also tried rename

---

### Post by taurus on 2007-01-26
Try to run it from a terminal with the sudo in front.

Applications -> Accessories -> Terminal
```
sudo mv **oldname** **newname**
```
Otherwise, try using "**gksudo nautilus**".

---

### Post by chinese_ys on 2007-01-26
> **taurus said:**
> Try to run it from a terminal with the sudo in front.

Applications -> Accessories -> Terminal
```
sudo mv **oldname** **newname**
```
Otherwise, try using "**gksudo nautilus**".

thanks very much man, I can use mv to realize the rename stuff, but i am afraid I can not use mv to rename my directory.

---

### Post by taurus on 2007-01-26
What exactly did you run and what kind of error message did you get?

---

### Post by chinese_ys on 2007-01-26
> **taurus said:**
> What exactly did you run and what kind of error message did you get?
the only thing i did is right-click on the file or directory in my flashdrive and rename, press the keys on keyboard, no response..........

---

### Post by taurus on 2007-01-26
Can you please run the command from a terminal to see what's the error message is?  Otherwise, <Alt>F2 and then type **gksudo nautilus**.  Then, see if you can rename from there.

---

### Post by chinese_ys on 2007-01-26
> **taurus said:**
> Can you please run the command from a terminal to see what's the error message is?  Otherwise, <Alt>F2 and then type **gksudo nautilus**.  Then, see if you can rename from there.

alright, I will do your suggestion latter, because I do not have a ubuntu box now. Thanks alot man! I will let you know what happens there.

---

### Post by chinese_ys on 2007-01-26
> **taurus said:**
> Can you please run the command from a terminal to see what's the error message is?  Otherwise, <Alt>F2 and then type **gksudo nautilus**.  Then, see if you can rename from there.

Hi, buddy

it really works now, but can you explain to why and what does that gksudo means please?

thanks!

---

### Post by taurus on 2007-01-26
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by anoopjohn on 2007-04-04
I have the same problem. I am unable to rename a file on the desktop using the rightclick rename option. however i can mv file to the new name. i had this problem once on an older system when i installed the malayalam language support options for ubuntu. i think this is the same scenario reported here except that it is chinese language . i was able to fix the problem last time. but i dont remember how. any ideas

---

### Post by anoopjohn on 2007-04-04
I recreated the same situation. Here is the fix
Right Click on the file on desktop or in filemanager
Click on Rename option
Again right click inside the filename and select Input Method. 
Mine works when default or SCIM is selected
Hope this helps

---

