---
title: "Need tool to search for files on all drives."
date: 2016-03-08
forum: General Help
---

### Post by midhun4 on 2016-03-08
i HAve 5 HDD (internal) connected to my computer,sometimes whn i need to search for a file ,i need to search each HDD which takes ages to come up with,Tried cat fish ,Bt tht too searches only the place whre its s assigned to ,I need a whole compter search including my HDDs,is there any software which will help me to do it?

---

### Post by sudodus on 2016-03-08
You can make a shellscript and run the ***find*** command for each of the HDDs one after another, but it is also possible to run it from the root and search all mounted file systems.

Examples:

```
sudo find / -name file-name
```

or with wild-cards

```
sudo find / -name "*string*"
```

Read more about find in ```
man find
```

***find*** can be risky with some options, so you may want to avoid using it with sudo. Then you should redirect the error output to avoid getting spammed by 'Permission denied' messages.

```
find / -name "*string*" 2>/dev/null
```

---

### Post by gordintoronto on 2016-03-08
You might also try: locate part-of-filename

---

### Post by oldos2er on 2016-03-08
Recoll can be set up to search any local mounted partition. It's in the repositories.

---

### Post by SeijiSensei on 2016-03-08
I find locate invaluable.  The results are usually so extensive though that I pipe them through grep.

For instance 
```
locate string | grep /home/seiji
```
to find files with "string" in their full paths but limiting the results to paths that include my home directory.

You can also pipe the results to a file
```
locate string > results.txt
```
then peruse it at your leisure.

If you make changes to the file system and want to include the results right away, use updatedb
```
sudo updatedb
```
You need to run it with root permissions.  It will update the database that locate uses.  It might take a minute or two depending on the size of your filesystem.   You can control which paths are indexed by editing (as root with sudo) the file /etc/updatedb.conf.  You'll see some examples there.

---

### Post by midhun4 on 2016-03-09
I am looking for smething like catfish ,but which can search the whole computer including the mounted HDDs also.Pls let me know whethr its possible ,


I just not only wanna search files,i want them to be copied too ,usually they are big files ,say like 1 gb r like that.pls let me know if its possible

---

### Post by slickymaster on 2016-03-09
oldos2er already recommended you one, [Recoll]("http://www.lesbonscomptes.com/recoll/features.html")

There's also [gnome-search-tool]("https://launchpad.net/ubuntu/+source/gnome-search-tool/3.6.0-1")

---

### Post by sudodus on 2016-03-09
Please tell us what you want to do - backup or search for some particular group of files - or something else! The advice will be different depending on what is your ultimate goal behind the details that you have asked for.

-o-

If you want an advanced copy or synchronizing program, there is ***rsync***. The manual is well written. Please read it and ask for help if you need help with some detail :-)

There are GUI programs with rsync under the hood if that is what you want. There are also many backup programs, that will find new and modified files, for example 'dry run' with rsync to find them and a real run to copy them.

---

### Post by midhun4 on 2016-03-10
> **sudodus said:**
> Please tell us what you want to do - backup or search for some particular group of files - or something else! The advice will be different depending on what is your ultimate goal behind the details that you have asked for.

-o-

If you want an advanced copy or synchronizing program, there is ***rsync***. The manual is well written. Please read it and ask for help if you need help with some detail :-)

There are GUI programs with rsync under the hood if that is what you want. There are also many backup programs, that will find new and modified files, for example 'dry run' with rsync to find them and a real run to copy them.



I wil tell U n detail ,I have 4 HDD connected to my system,There are files in each hard disk ,most of times i need to search the whole 4 hdd to get a file ,say like a doc file or a media file,I tried Catfish ,but catfish only searches the places whre i assign it to ,there is no option to select all drives and search in each of them simultaneously,I need to know whethr i can find anything which will help me with a option of whole computer scan,including all my hdds.

Hope u understand my query this time ,pls suggest ,

---

### Post by buzzingrobot on 2016-03-10
Are all those drives mounted and part of the filesystem?  If so, any search beginning at '/' will work its way through the filesystem and, hence, each of the drives.

Real time searches of a large filesystem won't be especially fast.

A tool like recoll creates an index of file content as well as file names and then searches that index. The index takes a finite amount of time to create and must be updated regularly, but the payoff is in the much faster search function.

---

### Post by sudodus on 2016-03-10
We have already replied with suggested tools according to that request: ***find, locate, recoll*** (and ***rsync***, with the additional ability to copy what you find).

Please try all those suggested tools! I think at least one of them will solve your problem (if you keep the partitions on your drives mounted).

---

