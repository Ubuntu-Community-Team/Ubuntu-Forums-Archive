---
title: "Ideas for synching folders between desktop and laptop?"
date: 2008-01-31
forum: General Help
---

### Post by Rippy on 2008-01-31
I've got a desktop and a recently acquired laptop, both with windows 2000 and ubuntu 7.10 installed. However, I've realized that I'd like to have some files synched between them all: nothing big, just a bunch of image files (webcomic saves, actually ^^). This is no problem for between the OSes of a same PC, because my desktop has a secondary drive and my laptop has got a fat32 partition. I just save them to a drive both OSes can access. However, doing something similar between the desktop and laptop is a little trickier.

Basically, my ideal would be something that works just like foxmarks for firefox: it saves a master file of all your bookmarks, and automatically downloads/uploads changes from/to the server. They're not private files, and it's not a huge amount of data, so I'm thinking something like that could work.

Problem is, I have no idea if there's a free service for that. If not, do you guys think I could script something to do the job? I've heard of gmail being used for backups, maybe that could work?

Any ideas are appreciated. This isn't critical or anything, but I'd really like to get this working :P

---

### Post by peitschie on 2008-01-31
I had the same problem... my solution: [http://www.powerfolder.com](http://www.powerfolder.com)

The free version has a 10Gb limit on it, it's **java based so it runs on windows and linux**, but quite reliable and fast.  Can sync between multiple computers, and I have also had no troubles synching the same folder base from either linux or windows.  Highly recommended (no I'm not affiliated with them just very satisfied :))

---

### Post by Rippy on 2008-02-01
Hmm, it looks great, except that the online storage is only a 1Gb 30-day trial. I hardly ever have both my desktop and laptop on at the same time, so peer-to-peer isn't that useful me :P

---

### Post by danwood76 on 2008-02-01
In ubuntu you can use unison: [http://www.micahcarrick.com/11-07-2007/unison-synchronize-ubuntu.html](http://www.micahcarrick.com/11-07-2007/unison-synchronize-ubuntu.html)
its pretty good one click synchronize.

Not really sure if there are any sync tools that run on both linux/win.

regards,
Danny

-- edit --

Just looked on the unison site and they do a win32 version aswell.
So you should be able to setup your dual boot so you can sync from any of your OS's:
[http://www.cis.upenn.edu/~bcpierce/unison/download.html](http://www.cis.upenn.edu/~bcpierce/unison/download.html)

---

### Post by peitschie on 2008-02-01
Update: Foldershare ([https://www.foldershare.com/info/aboutFoldershare.php](https://www.foldershare.com/info/aboutFoldershare.php)) might be what you are looking for... it appears to be free....
Update 2: On second thought, FolderShare no longer supports linux (suprise suprise) as it is now owned by our local software overlord...

Hmmm... you didn't specify that you never run the computers at the same time ;-)... makes it a little more complicated.  Unison as suggested by danwood76 will be of no help either.

Your best bet might be something like [http://richard.jones.name/google-hacks/gmail-filesystem/gmail-filesystem.html](http://richard.jones.name/google-hacks/gmail-filesystem/gmail-filesystem.html).  This is a google file system, which means you can use Gmail to store just files.  That will give you 6Gb or so?  Then you can set up a local sync program (say Conduit:[http://www.conduit-project.org/](http://www.conduit-project.org/) or Unison...) to sync your local copy with the Google FS copy, which will then allow you to work offline as well.

Other than that, most other programs require both computers on at the same time ;-)

---

### Post by Rippy on 2008-02-01
Ooo, gmail filesystem + unison looks like exactly what I need.. Doesn't help me in windows, but with any luck I'll be using ubuntu so much I won't even notice :P Thanks!

---

### Post by peitschie on 2008-02-01
Windows side you can use something like the Miscrosoft SyncToy [http://www.microsoft.com/windowsxp/using/digitalphotography/prophoto/synctoy.mspx](http://www.microsoft.com/windowsxp/using/digitalphotography/prophoto/synctoy.mspx)... I've had no troubles with this... though it can be a little annoying to customize.  The good thing is it sync's deletions as well

---

### Post by Rippy on 2008-02-02
hmm, I can't seem to get GmailFS to install through synaptic. Well, I can install it, but then... nothing happens? Searching my drive for files with the name "gmail" only come up with files related to my gmail firefox extension. So, basically, it installs, but I have no idea what it's actually done or what to do from here. :/ I don't really want to install it manually, since I've broken many an ubuntu install by doing too much of that.

Edit: nevermind, the search function just doesn't search folder names, (can you set it to do that? it kind of sucks if you can't) and I found the files by checking the package contents of gmailfs on the ubuntu site. Setting things up now, hopefully it works.

Edit2: Great, now I'm stuck at an http Error 302, no matter how I try to mount it. Googling isn't helping either.

---

### Post by Rippy on 2008-02-02
Nevermind, I've come to a quite pleasant solution. I uninstalled gmailfs and am now using gspace for firefox. It won't sync automatically, but it makes up for it because it has an image viewer mode that can be scaled to juuust fit a webcomic. I still want to see if I can get some kind of script to sync it when I close firefox, but overall it'll serve my purposes I think.

Thanks for all the suggestions though, guys! Too bad gmailfs wasn't working for me.

---

### Post by sancho panza on 2008-02-02
See if Grsync works for you. Its basically a gui version of Rsync.
I use it to sync different files between different computers on any network.

---

### Post by migla on 2008-02-02
I have lots of photos on 2 computers, most of the files being on both, but possibly under different directory structures and some filenames possibly being duplicate for different photos.

I have an external usb hdd.

I would like to make it so that all photos where in all three places. Is this easy?

By the way, my directory structures for the photos are arbitrary (I just made new dirs now and then in case pictures from the camera had previously used names) and thus mainly pointless. I don't mind having all pics in one big dir as long as duplicate names for differing content is fixed automatically somehow.

---

### Post by John_T on 2008-02-03
> **migla said:**
> I have lots of photos on 2 computers, most of the files being on both, but possibly under different directory structures and some filenames possibly being duplicate for different photos.

I have an external usb hdd.

I would like to make it so that all photos where in all three places. Is this easy.

I use [unison]("http://www.cis.upenn.edu/~bcpierce/unison/") (available via synaptic package manager) for this, and a bunch of other synchronization tasks.  It's a superb tool. 

However, this :

> **migla said:**
> 
By the way, my directory structures for the photos are arbitrary (I just made new dirs now and then in case pictures from the camera had previously used names) and thus mainly pointless. I don't mind having all pics in one big dir as long as duplicate names for differing content is fixed automatically somehow.

bit makes life a little interesting!

You'll have to do a bit of work first, and make sure at least one location has everything you want, and base your synchronization profiles on that.  If you don't you'll end up with multiple versions of a lot of pictures.  

For example, you might create 2 synchronization profiles for each, one for Computer A to Portable HD, and another for Computer B to portable HD, assuming the 2 computers are on different networks) You could use your portable disk as a means to ensure both computers stay in sync, even if they're never connected.

This way, iIf your portable HD or either one of your computers dies or goes missing you won't lose any data.

It helps if you're a little systematic, but I guess it's not essential. Using folder names with date formats like yyyy-mm-dd can make life simpler, but different people like different systems.

---

### Post by migla on 2008-02-03
Thanks for the tip on *Unison*.

I'm leaning towards wanting to make sure all files have a unique filename, by somehow in a batch operation including the files md5 in the filename.

Otherwise there is a chance of me transferring 2 different photos with an identical filename (such as DSCN1536.jpg) onto 2 different computers on the same date, which would put them under an identical path as well. 

If I reset my cameras counter or use another camera of the same brand, I wouldn't need to take 10k photos in a day for duplicate names to appear. I'll start a new thread with my specific case...

Edit:[ Here's that new thread, named "Batch rename with md5sum, cp from several dirs into one (+learning shell commands)"]("http://ubuntuforums.org/showthread.php?t=686453")

---

### Post by fuelrod on 2008-04-27
Maybe a bash script is not the best option. I have written a uni-directional synchronization tool in PHP which backs up my data to a server I have in a back room every time I shut down my computer.

This might be more like what you are looking for since I think at least it would be hard to write something like that in bash. The hard part would be if you wanted to make in bi-directional.

---

### Post by galileon on 2008-05-17
[http://live.gnome.org/Conduit/Documentation](http://live.gnome.org/Conduit/Documentation)

---

