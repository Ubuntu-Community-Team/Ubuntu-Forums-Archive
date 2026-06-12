---
title: "Unable to open a multi-part zip archive"
date: 2014-06-12
forum: General Help
---

### Post by martianexpatriate on 2014-06-12
I recently paid for a product which includes several files which were zipped. It is apparently a two part archive, with one named 3a and the other named 3b. They need to be combined in some way to be unzipped. I have no idea what that way is.

I have been messing around with this for days now. It's possible that there is some specific way to write a tar statement to get it to deal with this, but I have no idea what it is. It's also possible that the zip format is alien enough it won't recognize it. I have gone to the ubuntu software center and downloaded three different archiving programs to try to open the archive, and none of them appear to work despite multiple tries.

If somebody could tell me what to do, I would appreciate it.

---

### Post by sudodus on 2014-06-12
Welcome to the Ubuntu Forums :-)

You have to tell us more about your two part archive and the product that you paid for. Otherwise we can only guess.

But even before that you should ask from the company selling the product, how to use it, and to read very carefully the instructions that should come with it.

---

### Post by martianexpatriate on 2014-06-12
> **sudodus said:**
> Welcome to the Ubuntu Forums :-)

You have to tell us more about your two part archive and the product that you paid for. Otherwise we can only guess.

But even before that you should ask from the company selling the product, how to use it, and to read very carefully the instructions that should come with it.

I had hoped there was some standard way of opening archives. There are no instructions that come with it. The Blender Cookie people took my money, then sent me a multiple part zip archive... I don't know what kind it is. Chapter three is two files which can be unzipped, labeled part A and B. That's it.

I sent them an email asking for help, and they said they weren't familiar with Ubuntu but would get back to me, and they haven't.

---

### Post by sudodus on 2014-06-12
What have you tried? For example, have you tried to

1. put all files belonging to the zip archive into the same directory

2. open one of the files (the one with a zip extension (if any) with file-roller, which is often what happens if you double-click on an archive file in a file browser.

-o-

Let us say that you have the files in ~/Downloads

Run the following commands n a terminal window and post the output in a reply

```
cd ~/Downloads
ls -l

```
ell ess space minus ell (to show the files)

```
file-roller file-name.zip
```

Try the 'file-name.zip' shown by the previous command

---

### Post by steeldriver on 2014-06-12
What are the actual file extensions? If it's a Windows multipart archive you may have better luck with 7z/p7zip - both p7zip and p7zip-full should be available in the universe repo

---

### Post by martianexpatriate on 2014-06-12
michael@Interociter:~/Videos/Blender/Animation Toolkit$ ls -l
total 2500796

-rw-rw-r-- 1 michael michael 375398649 Jun  8 23:33 Animation%20Toolkit.tar.gz
-rw------- 1 michael michael 485919399 Jun  8 14:24 blender_anim_tk_chapter_01.zip
-rw------- 1 michael michael 474490323 Jun  8 14:22 blender_anim_tk_chapter_02.zip
-rw------- 1 michael michael  58850972 Jun  8 14:18 blender_anim_tk_chapter_03_A.zip.part
-rw------- 1 michael michael 316487324 Jun  8 14:23 blender_anim_tk_chapter_03_B.zip.part
-rw------- 1 michael michael 752732120 Jun  8 14:27 blender_anim_tk_chapter_04.zip
drwx------ 3 michael michael      4096 Jun  8 16:14 blender_anim_tk_source_files
-rw------- 1 michael michael  96890920 Jun  8 14:16 blender_anim_tk_source_files.zip
drwx------ 4 michael michael      4096 Jun  8 21:38 videos

When I attempted to open the file, archive manager comes up. When i try to extract:


7-Zip [64] 9.20  Copyright (c) 1999-2010 Igor Pavlov  2010-11-18
p7zip Version 9.20 (locale=en_US.UTF-8,Utf16=on,HugeFiles=on,8 CPUs)

Error: /home/michael/Videos/Blender/Animation Toolkit/blender_anim_tk_chapter_03_A.zip.part: Can not open file as archive

Errors: 1

---

### Post by sudodus on 2014-06-12
I don't know, but maybe you can try this command (copy and paste to get it right)
```

cat blender_anim_tk_chapter_03_A.zip.part blender_anim_tk_chapter_03_B.zip.part > blender_anim_tk_chapter_03-merged.zip
```

and then
```

file-roller blender_anim_tk_chapter_03-merged.zip
```

---

