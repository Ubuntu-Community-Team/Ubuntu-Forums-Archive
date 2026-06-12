---
title: "Where to put files?"
date: 2006-12-30
forum: General Help
---

### Post by taekwondodogoof on 2006-12-30
Hi,
      When you are using commands in terminal that require files, where do you put them?

---

### Post by 23meg on 2006-12-30
You mean in the command string? It depends on the command, but usually command options come first and name of the file to be acted upon comes after. You can check the manual page of the command for the exact notation.

---

### Post by taekwondodogoof on 2006-12-30
I'm sorry if I wasn't clear in my question, I'll put an example, I'm trying to use command ```
cat moviefilename.avi.001 >> moviefilename.avi.002
``` to combine videos. Where do I put the files? It says it cannot find them

---

### Post by ~LoKe on 2006-12-30
You have to be in the directory where you have the .avi files.

Type this in the terminal:
```
locate *.avi.001
```
Or whatever your video is called.

It'll print out a location, like this:
> /home/name/videos/moviefilename.avi.001
If that were the case, you'd type..
```
cd /home/name/videos
```
then
```
cat moviefilename.avi.001 >> moviefilename.avi.002
```

---

### Post by 23meg on 2006-12-30
Or you can use an absolute path, like */home/name/videos/moviefile1.avi *for each filename.

---

### Post by taekwondodogoof on 2006-12-30
Ok, thanks, is there anywhere I can move the files so that I don't need an adress? Does it automatically look for it in a folder?

---

### Post by ~LoKe on 2006-12-30
> **taekwondodogoof said:**
> Ok, thanks, is there anywhere I can move the files so that I don't need an adress? Does it automatically look for it in a folder?

```
mv /home/name/videos/*avi* ~/
```

---

