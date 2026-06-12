---
title: "GUI directory comparison tool"
date: 2014-06-24
forum: General Help
---

### Post by spockswhitepants on 2014-06-24
I am looking for a program that compare two directories and will give me graphical results (something like a simulated rsync, but with a GUI), letting me choose which version I want to keep. I tried kdiff3 and while the interface is great I didn't see a way to get it to ignore the file contents. For my purposes I just want to look at the metadata (name/size/date/etc), and not scan through a lot of potentially large files doing a byte by byte comparison. It does the job, but it is slow. Any suggestions?

---

### Post by dragonfly41 on 2014-06-24
Currently I'm using **meld** (in Ubuntu Software Centre) to compare directories containing files.

Then I have a simple bash script which runs **meld** in command line mode.

I'm not sure if this is what you want.

---

### Post by ajgreeny on 2014-06-24
It's a bit longwinded but you can run a long command using ls on each folder to produce a txt file of the content of each then pipe the two txt files through diff -y to give you a side-by-side list of the two folders
```
ls folder1 > txt1 && ls folder2 > txt2 && diff -y txt1 txt2
```
If you want more detail you could use** ls -la** instead of plain **ls**

---

### Post by tgalati4 on 2014-06-25
```
mc
```

---

### Post by ajgreeny on 2014-06-25
Good idea!

Using mc (midnight-commander) or another file manager with twin panes is such a good idea.  Why didn't I didn't think of something so simple?

It used to be possible to do that also in nautilus with an F3 press, but that is just another useful bit of nautilus that has now gone.

---

