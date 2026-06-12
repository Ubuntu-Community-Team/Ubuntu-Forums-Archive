---
title: "Recovering deleted tex files"
date: 2013-04-23
forum: General Help
---

### Post by AmadeusOK on 2013-04-23
Hi All,

I do most of my work using Latex. By mistake I deleted all the tex files from a particular subdirectory I was working on. I deleted them using the rm command. Is there any way I can recover these files? I tried programs like scalpel and foremost but they don't have an option for tex files. Any suggestions will be greatly appreciated. 

AmadeusOK

---

### Post by Impavidus on 2013-04-24
There are some file recovery tools you could try, if the data hasn't been overwritten yet. They should search for plain text files. There must be a function for that. I don't know much about file recovery tools, but you can search the fora. Else, if you still have the .dvi/.ps/.pdf files you may be able to reconstruct at least the text automatically using a pdf to text tool, but you'd still have to do the LaTeX commands yourself.

Precisely to avoid your kind of problem I keep backups of my tex files in a separate directory. Not on a separate drive, as it has to be as easy as possible to make them regularly. Of course there are also less frequent backups on other drives and encrypted backups in the cloud. To make those local backups I first used tar -czf, but after I once mistyped and gave the command tar -xzf (after all, c and x are next to each other), replacing the new files with the old backup instead of making a new backup, I wrote a script that does the job automatically.

---

### Post by alphaamanitin on 2013-04-24
My understanding on recover from a rm deletion is you are pretty much hosed.  Way too much work and effort to recover.  Have to unmount the drive and use something like [http://extundelete.sourceforge.net/](http://extundelete.sourceforge.net/) and there are limits on the drive structure you can recover from (e.g. ext3).  I would suggest in the future, as I need to set up myself as I recently did lose a file that wasn't needed but annoying to lose, you set up an alias so that rm moves the files to trash. Some on on here suggested it and showed the alias for it, but I cannot remember it.  

I know [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") is a pretty powerful file recovery method.  Heck, I even used it to recover an entire Windows XP NTFS drive that I accidentally reformatted to FAT32 using the quick format option in g-parted.  I am not sure though, lots of people say that unless you try recovery pretty much immediately your chances are going to really suck.

AlphaA

---

### Post by oldfred on 2013-04-24
Did you try Photorec?

You can set which files to look for, does not speed process which is slow as it still has to look at entire drive, but it seems to look for most types of text files. You can unchoose all the other types.

>  [X] tx?  Text files with header: rtf,xml,xhtml,mbox/imm,pm,ram,reg,sh,slk,stp,jad,url
 [X] txt  Other text files: txt,html,asp,bat,C,jsp,perl,php,py/emlx... scripts



---

