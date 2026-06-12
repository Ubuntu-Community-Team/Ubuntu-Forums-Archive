---
title: "splitting a 123GB picture file into smaller files"
date: 2018-08-18
forum: General Help
---

### Post by idkwhatimdoing1.0 on 2018-08-18
Hello, I know there's a method called split and many more than can do this kind of things but they seem to all split it in text lines or in bye sizes. SO basically I have a 123GB file size that I need to upload to the Microsoft OneDrive and since the file is so big the uploading just freezes and crashes every single time so basically I want to divide that file in like around 10-15 GB files. But I don't know what the command is to split that file because all the pictures and videos have different sizes so I do not know if the pictures would be cut off or something like that. This might sound stupid but the file is so big that a lot of computers seem to have trouble copying it so I do not have a back-up hence why I don't want to risk anything.

---

### Post by aysiu on 2018-08-18
Microsoft says you can't direct upload large files, but you can add the files to the OneDrive desktop app:
[https://support.office.com/en-us/article/fix-problems-uploading-files-on-the-onedrive-website-9afcc4a0-e344-4bc9-9c9d-59d3e802247e](https://support.office.com/en-us/article/fix-problems-uploading-files-on-the-onedrive-website-9afcc4a0-e344-4bc9-9c9d-59d3e802247e)

I'm sure they don't have a native Linux OneDrive app, but maybe have a look here for a workaround?
[https://medium.com/@glmdev/onedrive-sync-for-linux-ubuntu-2bcbf6777ee4](https://medium.com/@glmdev/onedrive-sync-for-linux-ubuntu-2bcbf6777ee4)

---

### Post by HermanAB on 2018-08-19
You can use split, tar, 7zip, dd...

I probably don't need to tell you to read the man pages...

---

### Post by idkwhatimdoing1.0 on 2018-08-19
yes I know I can use split but what is it the correct method?

---

### Post by The Cog on 2018-08-19
Try:
```
split -b 15G -d bigpig.jpg bigpic
```

---

### Post by idkwhatimdoing1.0 on 2018-08-19
um that doesnt work because I have over 24000 pictures and videos together... So I can't select one

---

### Post by The Cog on 2018-08-19
You have 24000 pictures all over a hundred GB? It'll take a while, but you can script it.
```
find -name '*jpg' -exec split -b 15G -d '{}' '{}' \;
```

---

### Post by idkwhatimdoing1.0 on 2018-08-19
No, I have a file like a folder that had around 24000 pictures and videos and in total it adds up to 123 GB. I want the folder to be separated in equal amounts of pictures... So like one folder full of 24000 pics totalling 123GB of pictures I want that transformed to 7-8 folders each with around 10-15 GB of pictures

---

### Post by mdurham on 2018-08-19
What is "a file like a folder"? 
How did you create "a file like a folder"?

---

### Post by Impavidus on 2018-08-20
Sounds like some archive format. I think the way to go is to unpack the archive, then create new archives, each containing 10-15 GB of data. As image and video files cannot be compressed by the archive format (because they are already compressed to the max using lossy techniques; the lossless compression of archive formats can't beat that), you just have to collect 10-15GB of image/video files, then pack them into an archive. It should be doable to write a script for that.

---

### Post by SeijiSensei on 2018-08-20
Maybe use something like
```
tar -czf archive1.tar.gz foldername/[a-d]*
```

That should create a compressed tar archive of all files beginning with the letters A through D in foldername.  You could use the same logic with zip.

If you have mixed-case filenames use [a-dA-D].

---

