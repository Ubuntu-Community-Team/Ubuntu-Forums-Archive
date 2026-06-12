---
title: "Copy command fails &quot;Directory omitted&quot;"
date: 2007-05-23
forum: General Help
---

### Post by Pichu0102 on 2007-05-23
First of all, I first burned the CD on a Mac from school, and it complained there about not having admin privileges and some files may have failed to copy due to this. However, it burned correctly and the locked files did not copy.
When trying to drag and drop the files from a CD rom into my home directory, Nautilus silently crashes (or is unexpectedly closing the windows).
When trying from the command line, it sends this back:
```
pichu0102@pichu0102-laptop2:~$ cp /cdrom/* /home/pichu0102/memories/danielservercp: omitting directory `/cdrom/daniel'
cp: omitting directory `/cdrom/desktop'
cp: omitting directory `/cdrom/documents'
cp: omitting directory `/cdrom/library'
cp: omitting directory `/cdrom/movies'
cp: omitting directory `/cdrom/music'
cp: omitting directory `/cdrom/pictures'
cp: omitting directory `/cdrom/portable firefox os x'
cp: omitting directory `/cdrom/public'
cp: omitting directory `/cdrom/sites'
cp: omitting directory `/cdrom/untitled folder'
cp: omitting directory `/cdrom/untitled folder 2'
pichu0102@pichu0102-laptop2:~$ sudo cp /cdrom/* /home/pichu0102/memories/danielserver
cp: omitting directory `/cdrom/daniel'
cp: omitting directory `/cdrom/desktop'
cp: omitting directory `/cdrom/documents'
cp: omitting directory `/cdrom/library'
cp: omitting directory `/cdrom/movies'
cp: omitting directory `/cdrom/music'
cp: omitting directory `/cdrom/pictures'
cp: omitting directory `/cdrom/portable firefox os x'
cp: omitting directory `/cdrom/public'
cp: omitting directory `/cdrom/sites'
cp: omitting directory `/cdrom/untitled folder'
cp: omitting directory `/cdrom/untitled folder 2'

```

Even as root it is not letting it work.

---

### Post by bashologist on 2007-05-23
cp -r /cdrom/* /home/pichu0102/memories/danielservercp/

---

### Post by earobinson on 2007-05-23
> **bashologist said:**
> cp -r /cdrom/* /home/pichu0102/memories/danielservercp/
yup thats how to do it. ```
man cp
``` for more info

---

### Post by Pichu0102 on 2007-05-23
> **bashologist said:**
> cp -r /cdrom/* /home/pichu0102/memories/danielservercp/

This worked; thanks!
However, while opening nautilus as root, I found a debug file that nautilus dropped in the root folder. I thought it might help in something, so I clipped out the parts that seem to be pointing out that something went wrong.

```
0x8187150 2007/05/23 15:28:00.7784 (USER): rename file old="file:///home/pichu0102/memories/untitled%20folder", new="metzger_daniel"
0x8187150 2007/05/23 15:28:00.7787 (USER): selection changed in window 0x81e2188
0x8187150 2007/05/23 15:28:01.4310 (USER): selection changed in window 0x81e2188
	file:///home/pichu0102/memories/metzger_daniel
0x8187150 2007/05/23 15:28:01.5631 (USER): fm_directory_view_activate_files window=0x81e2188
	file:///home/pichu0102/memories/metzger_daniel
0x8187150 2007/05/23 15:28:01.5635 (USER): directory view open_location window=0x81e2188: file:///home/pichu0102/memories/metzger_daniel
0x8187150 2007/05/23 15:28:01.5635 (USER): window 0x81e2188 open location: old="file:///home/pichu0102/memories", new="file:///home/pichu0102/memories/metzger_daniel"
0x8187150 2007/05/23 15:28:01.5635 (USER): finished loading window 0x81e2188: file:///home/pichu0102/memories
0x8187150 2007/05/23 15:28:01.6790 (USER): change view of window 0x81e2188: "file:///home/pichu0102/memories/metzger_daniel" to "OAFIID:Nautilus_File_Manager_Icon_View"
0x8187150 2007/05/23 15:28:01.7844 (USER): finished loading window 0x81e2188: file:///home/pichu0102/memories/metzger_daniel
0x8187150 2007/05/23 15:28:02.9240 (USER): copy the following URIs to "file:///home/pichu0102/memories/metzger_daniel":
	file:///cdrom/daniel
	file:///cdrom/desktop
	file:///cdrom/documents
	file:///cdrom/library
	file:///cdrom/movies
	file:///cdrom/music
	file:///cdrom/pictures
	file:///cdrom/portable%20firefox%20os%20x
	file:///cdrom/public
	file:///cdrom/sites
	file:///cdrom/untitled%20folder
	file:///cdrom/untitled%20folder%202
	file:///cdrom/documents.zip
	file:///cdrom/picture%201.png
	file:///cdrom/picture%201%20copy.jpg
	file:///cdrom/squid.ppt
	file:///cdrom/the%20cake%20is%20the%20world.mp3
	file:///cdrom/the%20demon%20likes%20pingpong.mp3
0x8766930 2007/05/23 15:28:20.4871 (GLog): file file-method.c: line 2244 (do_create_symbolic_link): assertion failed: (target_reference != NULL)
0x8766930 2007/05/23 15:28:20.4872 (USER): debug log dumped due to signal 6
===== END RING BUFFER =====
```

---

### Post by bashologist on 2007-05-23
It seems to be a bug in Nautilus. Everything should be ok.
[http://www.google.com/search?hl=en&q=USER%29%3A+debug+log+dumped+due+to+signal+6&btnG=Google+Search&meta=](http://www.google.com/search?hl=en&q=USER%29%3A+debug+log+dumped+due+to+signal+6&btnG=Google+Search&meta=)

---

