---
title: "I deleted /opt/lib from my system"
date: 2013-01-16
forum: General Help
---

### Post by IAMTubby on 2013-01-16
Hey,
I deleted /opt/lib from my system
I was doing some copying and instead of doing
```
$cp file /opt/lib/, I did
$cp file /opt/lib

```
But as of now, everything seems to work ok. 

What do I do now ?
Is there a command to restore it or something, or should I manually create a mkdir /opt/lib and copy the contents from /opt/lib on another machine ?

Thanks.

---

### Post by The Cog on 2013-01-16
I assume you were trying to copy a file to a folder /opt/lib to create /opt/lib/file, but the directory didn't exists so you ended up creating a file called /opt/lib instead. If this guess is wrong, ignore this post.

I would be inclined to give the file its original name, create the directory and then move the file to the directory, like this:
```
mv /opt/lib /opt/file
mkdir /opt/lib
mv /opt/file /opt/lib/
```
although if the original file still exists, deleting the copy, making the directory and then copying would be OK too:
```
rm /opt/lib
mkdir /opt/lib
cp file /opt/lib/
```

---

### Post by IAMTubby on 2013-01-16
> **The Cog said:**
> I assume you were trying to copy a file to a folder /opt/lib to create /opt/lib/file, but the directory didn't exists so you ended up creating a file called /opt/lib instead. If this guess is wrong, ignore this post.
Sir, you understood my scenario perfectly, but I think /opt/lib existed. 
I am more worried about the data within /opt/lib which I have deleted. Is it some important data in /opt/lib. Is there a way to restore it at some point.

---

### Post by The Cog on 2013-01-16
I don't think there is a way to restore deleted data. But I don't see anything in your post that would have deleted data, other than perhaps overwriting a pre-existing file called /opt/lib.

---

### Post by IAMTubby on 2013-01-16
> **The Cog said:**
> I don't think there is a way to restore deleted data. But I don't see anything in your post that would have deleted data, other than perhaps overwriting a pre-existing file called /opt/lib.
Yes sir, I rewrote the file, means I basically deleted the file and replaced the system file with **my** file which is of no significance right ?
I was thinking if I should copy this folder from a different system and paste it on my system.

---

### Post by Impavidus on 2013-01-16
As far as I know, there is no system file called /opt/lib nor a system directory called /opt/lib/. Of course, you can create a file or directory named so, but it would only contain what you put in it yourself. The only thing that could have gone wrong in your case is that you may have replaced the file /opt/lib, which you would have installed yourself, by a new file or that you have replaced the file /opt/lib/file, which you also would have installed yourself, by a new file. I'm quite sure you haven't damaged your system.

The only difference between```
1$ cp file /opt/lib/
2$ cp file /opt/lib
```is that (1) would give you an error message if the directory /opt/lib/ didn't exist and (2) would copy to the file /opt/lib if the directory /opt/lib/ didn't exist.

---

### Post by tgalati4 on 2013-01-16
Normally, user-installed, or 3rd party applications get put in /opt, like flash player, firefox, googleearth, etc.  So those apps will definitely be broken.  Good thing you didn't delete /usr/lib.  I assume /opt/lib exists on your system, otherwise why would you want to put a file there?  I don't see it on mine (12.10).  Linux should work to put the file into the /opt/lib directory in either case.  If /opt/lib did not exist, then it exists now as a file, but not a directory.

Just keep a list of things that don't work anymore and reinstall them using apt-get, synaptic, or the software center.  Over time, you will get /opt/lib repopulated.

Be careful with your typing in linux.  Your computer will do exactly what you tell it to, no more and no less.

---

### Post by The Cog on 2013-01-16
Agreed, on normal install of Ubuntu, /opt is an empty folder. It contains neither a file or folder called lib. So the only thing you might have overwritten is something else non-standard that you installed earlier. 

I think probably you did not overwrite anything, which is why you cannot now detect anything broken.

---

### Post by IAMTubby on 2013-01-20
> **Impavidus said:**
> As far as I know, there is no system file called /opt/lib nor a system directory called /opt/lib/.
> **The Cog said:**
> 
I think probably you did not overwrite anything, which is why you cannot now detect anything broken.
Impavidus, The Cog , you were right. 
There was no such file in my system.
I think when I did cp file /opt/lib. It created a **file, not directory** called lib under /opt. And I deleted it on panicking. Thanks a lot for your replies. Marking the thread as solved.

> **tgalati4 said:**
> 
Be careful with your typing in linux.  Your computer will do exactly what you tell it to, no more and no less.
tgalati4, sure Sir. I'm glad I did not have to learn it the hard way.

---

