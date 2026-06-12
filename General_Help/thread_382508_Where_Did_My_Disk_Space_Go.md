---
title: "Where Did My Disk Space Go?"
date: 2007-03-12
forum: General Help
---

### Post by iXneonXi on 2007-03-12
OK, so back in the dark ages when I had Windows I would use a nifty UI tool called "Folder Size Shell Extension."

This program would allow me to right click my C: drive and it gave me the option to check the sizes of all of the folders.  I could also sort by size in a descending list which gave me a good estimate of where the heck went all my disk space.

Is there a way to do this in Linux? I know there are command line tools like 'du' which allow me to see how much space things are taking up, but to be able to sort all folders in a descending list based on disk space usage.. all from a GUI - that would be great.

Help me out, any input appreciated.

---

### Post by zvacet on 2007-03-12
Maybe Baobab is what are you looking for.

---

### Post by tagra123 on 2007-03-12
In the terminal  you can use

df -h

or 

du -h

there are many other switches -- for help 

man du

or

man df

---

### Post by tszanon on 2007-03-12
Definitely, Baobab. I asked the same question a while ago and, for sure, that's the program I was looking for.

---

### Post by mbeierl on 2007-03-12
I never realized it, but Baobab is usually found under: Accessories -> Disk Usage Analyzer.

---

### Post by ComputerGuy56 on 2007-03-12
> **mbeierl said:**
> I never realized it, but Baobab is usually found under: Accessories -> Disk Usage Analyzer.

So that's what the program does..... But I just tested it, and I'd say it's perfect for what you need.

---

### Post by tszanon on 2007-03-12
> **mbeierl said:**
> I never realized it, but Baobab is usually found under: Accessories -> Disk Usage Analyzer.

In Edgy, it is installed by default, labeled "Disk Usage Analyser" (just as you said). But in Dapper, it's not. After installation, it is found under Accessories, but labeled "Baobab".

---

### Post by ezsit on 2007-03-12
> Baobab is usually found under: Accessories -> Disk Usage Analyzer

I tried this program and it told me my / filesystem was 100% full. It also told me my /home filesystem was 100% full. df told me otherwise, my / filesystem has 2.9 GB used on a 29 GB partition and my /home filesystem has 20 GB used on a 250 GB partition. Hence, I do not trust Baobab.

---

### Post by khedron on 2007-03-12
On the KDE side, you could try **kdirstat**.

An alternative would be Konqueror (the file manager) as it has a 2D file size view mode (Go into View -> View Mode -> File Size View). If you ever used SpaceMonger on Windows, this is just like it.

---

### Post by iXneonXi on 2007-03-18
Thanks, Baobab seems to be doing just fine.

---

