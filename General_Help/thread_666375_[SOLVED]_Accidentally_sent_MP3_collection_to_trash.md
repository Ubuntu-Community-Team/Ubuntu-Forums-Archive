---
title: "[SOLVED] Accidentally sent MP3 collection to trash"
date: 2008-01-13
forum: General Help
---

### Post by ~LoKe on 2008-01-13
Rhythmbox sucks.

Anyways, now that I've got most of my music in the trash (about 2000 files), all files, no folders, how do I...restore them to where they used to be?  I can't be bothered to put them all in their respective folders... -_-

---

### Post by lluisanunez on 2008-01-13
That happened to me once. I don't think there is a way for the Trash to "restore" to original folders. I solved it with Gtkpod. Maybe there are other programs to do so, but that's what I had.
1. Copy all the files from the Trash to another folder
2. Open Gtkpod, select "Local" and "add directories"
3. Once all the files are loaded, select them all, right click and "copy tracks to filesystem". Give another new folder for example Music. 
4. See that the "file format" is something like %a/%A/%t.mp3. This generates a folder per artist, with a folder per album, etc.,

---

### Post by ~LoKe on 2008-01-13
Oohh, I'll give that a shot.  Thanks!

---

### Post by kleo skywalker on 2008-01-13
Does a restore option actually exist? Whenever I put something in the Trash accidentally, I have to cut-paste it back where it belonged.

---

### Post by steeleyuk on 2008-01-13
Not yet. There is some work to do that but it'll come with the new changes to GNOME. Don't expect it straight away though.

---

### Post by ~LoKe on 2008-01-13
> **kleo skywalker said:**
> Does a restore option actually exist? Whenever I put something in the Trash accidentally, I have to cut-paste it back where it belonged.

Something that Windows has but Ubuntu does not (AFAIK).  Never had the need for it, but after systematically deleting 2000 mp3 files, I took a look. ;)

---

### Post by erpo on 2008-01-13
If you're not uptight about organizing your mp3 collection, just store them all in 1 folder. Almost all music managers/players will work just as well no matter whether your mp3s are sorted into folders.

If you are uptight about organizing your mp3 collection, you can use a program called Easytag to rename/move files based on their artist/album/whatever data.

---

### Post by ~LoKe on 2008-01-13
> **erpo said:**
> If you're not uptight about organizing your mp3 collection, just store them all in 1 folder. Almost all music managers/players will work just as well no matter whether your mp3s are sorted into folders.

If you are uptight about organizing your mp3 collection, you can use a program called Easytag to rename/move files based on their artist/album/whatever data.

I check my home folder every night for files that aren't properly organized. :lolflag:

---

### Post by steeleyuk on 2008-01-13
Depending on how big your collection is, opening folders with 1000's of files in can get quite slow. Its usually a good idea to group them into album name, artist name or something.

---

### Post by ~LoKe on 2008-01-13
> **steeleyuk said:**
> Depending on how big your collection is, opening folders with 1000's of files in can get quite slow. Its usually a good idea to group them into album name, artist name or something.

That's basically how I had it.

```
Music -> Artist1 -> Album1 -> Track1.mp3
                    Album2 -> Track1.mp3
                    Album3 -> Track1.mp3
         Artist2 -> Album1 -> Track1.mp3
                    Album2 -> Track1.mp3
...
etc
```

---

### Post by lluisanunez on 2008-01-13
That's the way Gtkpod will put them in, it reads artist amd album from the tags in every track

---

### Post by ~LoKe on 2008-01-13
lluisanunez's suggestion worked.  Thanks a lot!

---

