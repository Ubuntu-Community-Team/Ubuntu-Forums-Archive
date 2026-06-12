---
title: "rsync question &amp; help"
date: 2007-12-22
forum: General Help
---

### Post by netvampire on 2007-12-22
Hey,

I am semi new to kubuntu but I have been getting the hang of it. I have been tinkering with rsync but am having trouble getting rsync to do what i want. Hopefully someone on this forum can help me out.

My situation is as follows. 
I have a desktop (running win xp), a laptop (running win xp)  and a kubuntu server machine. I want a folder between all 3 computers to be synchronized daily.  I can get the folder ssynchronized with no problems. And it syncs the items with the most recent time stamps which are great.  If i create a new folder on say my desktop, rsync has no problem duplicating its contents on the kubuntu machine. 

MY PROBLEM is that if i delete a directory from the folder on my desktop/laptop  that is syncronized then the moment rsync is run again, all the files for that directory are copied back over. I am not sure how I can make it so this does not happen. I am not sure if it is possible with rsync. After all it is able to identify if a new folder has been created and it copies those files over, so how does it distinguish between the two. 


On the windows machines I am running cygwin. I created a bat file and added it to the Scheduled Tasks program in windows. The contents for my syncing are as followed: 


```

C:\cygwin\bin\rsync.exe -qrtzu --password-file=c:\cygwin\secret --exclude="- System Volume Information/" --exclude="- RECYCLER/" "/cygdrive/s/." --backup --backup-dir=/cygdrive/s/cacheBackup/ uname@192.168.1.107::unamesync

C:\cygwin\bin\rsync.exe -vr --password-file=c:\cygwin\secret uname@192.168.1.107::unamesync "/cygdrive/s/."



```


Can anyone offer me advice on how to solve my delete-sync issue. I checked the rsync documentation and I know they have a ton of options including -delete-after or -delete-delay and stuff, but I just cannot identify if any would work for me in the manner that I need it to.

THANKS!

---

### Post by p_quarles on 2007-12-22
I believe the option you want is simply:
```
--delete
```
That will delete any files in the destination directories that no longer exist in the local directories, and will thus prevent them from syncing back to the local. 

Use this option with caution, though. ;)

---

### Post by netvampire on 2007-12-22
thanks for the response......
i do not believe the delete option, my problem will be as follows

For Example:
Suppose on my laptop i create a new directory called 'abc' and sync that onto the kubuntu server. When my desktop goes to sync with the kubuntu server, the folder 'abc' is not stored locally, and thus will be deleted off of the server. 

Any thoughts on solving this problem?

---

### Post by p_quarles on 2007-12-22
I'm not absolutely certain this will solve the problem, but it will be easy to find out by using the --dry-run option with rsync.

I think you can just reverse the direction of the transfer. In other words, say you've copied your updated folders from your laptop to the server. At this point, your problem is that if you run the following on your desktop machine:
```
rsync -yadda --delete c:my-windows-drive username@server://syncdir
```
You'd be deleting overwriting the backup of your laptop with a mirror of your desktop.

However, if you were to switch the source and destination:
```
rsync -yadda --delete username@server://syncdir c:my-windows-drive
```
You would be creating a mirror of the server's sync folder on your desktop. 

That should work, but like I said, included the --dry-run option the first time you do this to make sure that it will behave as expected. To shorten this process, you could just create two separate scripts for syncing folders, one for new data on the local machines, and one for new data in the server's share.

---

### Post by netvampire on 2007-12-22
thanks for the info. i will do some more tinkering and see where i end up .

---

### Post by netvampire on 2007-12-24
for those that are interested, i realized rsync is not really that good for two-way syncing so instead i installed unison and ahve that running flawlessly.

---

