---
title: "Meld Diff - directory comparison help?"
date: 2013-01-24
forum: General Help
---

### Post by irishetalon007 on 2013-01-24
Yello!

I'm having trouble interpretting the results from Meld Diff's directory comparison. I have 2 almost identical directories (each 30 GB) and they don't have exactly the same files and size (which they should) so I used meld diff to try to figure out why. 

After scanning, Meld Diff shows 2 panes. in the left pane, everything in the directory is listed and in bold GREEN color. in the right pane, the same stuff is listed but with a strikethrough and in grey color.

Any Ideas? All I want to do is show the differences between the directories.

Thanks in advance!

---

### Post by sdpagent on 2013-01-25
This is not the answer you are looking for probably. But I find that SVN is a perfect tool for such a situation. You could create an svn repo. Make one of the folders the initial import, before checking out the repo and then copying the contents of the other folder within it. Then do a commit, and you should get a diff which shows you all the files that have changed and the changes within. I use RabbitVCS gui for SVN and it works great screenshot below:
[IMG]http://img1.uploadscreenshot.com/images/orig/1/2408013316-orig.png[/IMG]
Also worth mentioning that double clicking on one of the files will bring it up and show you the meld of the two files, clearly showing you the changes that have occured to that one file.

---

### Post by stinkeye on 2013-01-25
FreeFileSync allows you to compare and synchronize and is fairly easy to grasp.
```
sudo add-apt-repository ppa:freefilesync/ffs
sudo apt-get update
sudo apt-get install freefilesync
```
One bug...you may have to paste in the path to directories to compare instead of
using the browse button.

---

### Post by kjohri on 2013-01-25
From the command line,

diff -Nur directory-1 directory-2 > differences

Check the file *differences* in a text editor for differences between the two directories. For interpretation of diff output, refer to the link,

[http://www.softprayog.in/tutorials/using-diff-patch](http://www.softprayog.in/tutorials/using-diff-patch)

---

### Post by Merrattic on 2013-01-25
You should find all your answers here (or abouts)

[http://meld.sourceforge.net/screenshots.html](http://meld.sourceforge.net/screenshots.html)

---

