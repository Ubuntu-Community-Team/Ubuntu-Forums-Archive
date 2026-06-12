---
title: "Untaring dotted files"
date: 2015-04-02
forum: General Help
---

### Post by mohtasham1983 on 2015-04-02
Hi,

I just made a backup of my data, added them all into a tar file and uploaded Google drive.

Then I downloaded the tar file on my new machine. When I open the tar file using Ark in KDE or the app that comes with Gnome, I can see a directory called configs that contains all my config files starting with ".". However when i extract my tar file using Ark or that gnome app, those dotted files don't get extracted.

I also used the following to untar my tar file with no luck:

```
tar -xzvf my_file.tar.gz
```

Any idea how I can retrieve those dotted files?

Thanks

---

### Post by yancek on 2015-04-02
Files beginning with a '.' are hidden files so if you use a file manager to look in the directory in which the files were extracted, select from the View tab, Show hidden files.  Or you can run the command:  ls -la on the directory in which the files were extracted.

---

### Post by mohtasham1983 on 2015-04-02
I forgot to mention that I was using ls -la to view the files. They were all missing.

Since I only had a couple of config files, I was able to open them one by one using Ark, copy the content and paste them into new files. It worked for me now, but it wouldn't if I had lots of them.

---

### Post by kjohri on 2015-04-02
It might have something to do with how the tar archive was created. You can try the sequence,

1. To create tar archive, from the command line,
    cd <root-directory of the tree to be archived>
    tar -cvzf ~/tmp1/abc.tar.gz .

2. To untar, 
    tar -xvzf ~/tmp1/abc.tar.gz

---

### Post by yancek on 2015-04-03
What command do you use to create the file?  When I use:  tar cpvf ... to create a backup, it includes all hidden files and I need to add an exclude parameter if I don't want them.

---

