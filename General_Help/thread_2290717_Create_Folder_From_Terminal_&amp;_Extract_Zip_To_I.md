---
title: "Create Folder From Terminal &amp; Extract Zip To It"
date: 2015-08-14
forum: General Help
---

### Post by Zim_Zim_Zalabim on 2015-08-14
I have been manually creating the folder, but I Thought this could all be combined into one command in terminal.  How can I create a folder in my \Downloads folder and extract a zip to it?
(and for clarity I do not want the folder to be hardcoded as NewFiles - I would want to enter a name each time meaningful to the actual zip I am extracting)
I have been using this to simply extract
```

unzip file.zip -d NewFiles
```


EDIT --- 
and I just discovered I could create a directory through terminal by using this
```
mkdir ./Downloads/FolderName
```

Anyone care to explain how to combine the two?

---

### Post by howefield on 2015-08-14
Something like...

```
mkdir NewFiles && unzip file.zip -d NewFiles/
```

or for a tar.gz file...

```
mkdir NewFiles && tar -xf file.tar.gz -C NewFiles/
```

---

### Post by Zim_Zim_Zalabim on 2015-08-14
That works perfectly!  Thank you so much for that!

One follow-up question, how could I extract ALL .rar files in a directory with one comand?  So extract all .rar files in ./Downloads/folderwithrar but extract them to ./Downloads/FilesOnly

---

### Post by howefield on 2015-08-14
From the "folderwithrar" directory, something like..

```
mkdir ~/Downloads/FilesOnly && find . -name "*.rar" -exec unrar e -r {} ~/Downloads/FilesOnly \;
```

---

