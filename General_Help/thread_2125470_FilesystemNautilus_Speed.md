---
title: "Filesystem/Nautilus Speed"
date: 2013-03-14
forum: General Help
---

### Post by krustenBrot on 2013-03-14
This is more like a general question than an actual problem.

I was wondering how displaying in the Explorer on Win7 can be a lot faster than doing the same task with Nautilus on Ubuntu. Dont get me wrong i am not talking about opening up the Application - it is just when i look at my homefolder in Nautilus it always takes a second until everything is there, it looks like my machine is fetching the information displaying it on the go, while doing that in the explorer: everything is right there like it is precached or indexed. Now my Question: Where is the difference? I got a SSD in my machine so there shouldn't be any lag. Is Nautilus actually **not** indexing everything and has to look it up every time I open up a Folder?

Oh...and where has that Spellchecking gone? :(

---

### Post by rnerwein on 2013-03-14
> **krustenBrot said:**
> This is more like a general question than an actual problem.

I was wondering how displaying in the Explorer on Win7 can be a lot faster than doing the same task with Nautilus on Ubuntu. Dont get me wrong i am not talking about opening up the Application - it is just when i look at my homefolder in Nautilus it always takes a second until everything is there, it looks like my machine is fetching the information displaying it on the go, while doing that in the explorer: everything is right there like it is precached or indexed. Now my Question: Where is the difference? I got a SSD in my machine so there shouldn't be any lag. Is Nautilus actually **not** indexing everything and has to look it up every time I open up a Folder?

Oh...and where has that Spellchecking gone? :(
hi
i bet i can tell you what's your problem --> it's the structure of your folder. i think you get a couple of files in one directory (right ?).  if you access the folders the system have to
lock them (unix/linux) isn't working about - ok nothing will hapen. the access is atomic. if i am wrong tell me.
create your directories: your_home/subfolder_bla ... subfolder_blu (even structured).
ciao
p.s. you can speed up the performance with mount options (assumed you got a well structured partitions: e.g. own / - own /home - own /usr ... partition and so on)
have fun

---

### Post by krustenBrot on 2013-03-14
No the structure isnt the Problem i mean in general it is a bit slower to open folders, it doesnt matter if its a folder with 2 files or 2000. Is Ubuntu Indexing the filesystem?

---

### Post by roly33 on 2013-03-14
I'm not a Linux expert,  but I know that in Windows you have the option to Index your File System, but can't seem to remember seeing an option the last time I used Ubuntu,  so it could be that Windows is Indexing the File System while Ubuntu isn't. 

Roland

---

### Post by sudodus on 2013-03-14
> **krustenBrot said:**
> No the structure isnt the Problem i mean in general it is a bit slower to open folders, it doesnt matter if its a folder with 2 files or 2000. Is Ubuntu Indexing the filesystem?

I don't think ***nautilus*** is using indexing, but I'm not sure. But I know that ***locate*** is using indexing, which makes it fast compared to for example find. But it will not find files created after the database was updated.

See this link [[COLOR=#ff0000]http://www.linfo.org/locate.html[/COLOR]]("http://www.linfo.org/locate.html")

---

### Post by LewisTM on 2013-03-14
I never understood what was up with Nautilus. Every time I click a folder, the pointer becomes an hourglass for a split second (can be longer for large directories) and there is a lag in file listing. I never see that with Thunar or PCManFM. 

So I'm with you on this one. Nautilus seems to process something every time it opens a directory.

---

### Post by sudodus on 2013-03-14
> **LewisTM said:**
> I never understood what was up with Nautilus. Every time I click a folder, the pointer becomes an hourglass for a split second (can be longer for large directories) and there is a lag in file listing. I never see that with Thunar or PCManFM. 

So I'm with you on this one. Nautilus seems to process something every time it open a directory.

That rings a bell. Nautilus has ambitions to manage the desktop unless you call it with

```
nautilus --no-desktop
```

See ```
man nautilus
```

---

### Post by LewisTM on 2013-03-14
> **sudodus said:**
> That rings a bell. Nautilus has ambitions to manage the desktop unless you call it with

```
nautilus --no-desktop
```

See ```
man nautilus
```
I run XFCE and Nautilus does not manage the desktop. Don't use it very often to be honest.
Much of the touted "speed" of Thunar and PCManFM comes from quick file listing, which Nautilus has never been able to achieve, much to my bewilderment.

---

### Post by krustenBrot on 2013-03-15
> **LewisTM said:**
> I never understood what was up with Nautilus. Every time I click a folder, the pointer becomes an hourglass for a split second (can be longer for large directories) and there is a lag in file listing. I never see that with Thunar or PCManFM. 

So I'm with you on this one. Nautilus seems to process something every time it opens a directory.

That is exactly what i meant. I doubt there is a fix for it, but i am still curious **why** it behaves that way.

---

### Post by krustenBrot on 2013-03-19
I guess this answers it:
>  Much of the touted "speed" of Thunar and PCManFM comes from quick file  listing, which Nautilus has never been able to achieve, much to my  bewilderment.
Thanks LewisTM!
Thread marked as solved. :)
*edit: The marked as solved function appears to be removed. It is **solved** anyway ;)*

---

