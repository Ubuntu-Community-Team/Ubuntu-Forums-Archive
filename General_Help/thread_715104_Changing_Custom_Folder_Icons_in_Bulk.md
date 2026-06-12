---
title: "Changing Custom Folder Icons in Bulk"
date: 2008-03-04
forum: General Help
---

### Post by fireman biff on 2008-03-04
I currently have a bunch of folders each containing audio files ripped from one cd. Each folder has a JPEG file named after the name of the album, and this JPEG is used as the custom icon for the folder its in.

I would like to rename the JPEGs so that they start with a "." so that they're hidden. Is there any command(s) that can be used to rename the files and set the newly names files as the custom folder icons?

---

### Post by fireman biff on 2008-03-05
bump

---

### Post by fireman biff on 2008-03-07
I found a way to do what I wanted. I'm not sure if its the best way, but it works. I'll post it here in case anybody else is trying to do the same thing.

I started by renaming all the JPEGs to start with a dot. My music is stored in with a folder per album such as "Nirvana - Nevermind", not with a folder per artist, so if you have separate artist folders you'll need to modify the code.

```
for file in *; do cd "$file"; rename -v 's/(.*)/.$1/' *.jpg; cd ..;  done
```

I then opened a text editor (I used SciTE) and modified an xml file used by nautilus. The file is stored in "~/.nautilus/metafiles/". To figure out exactly which file to modify see [this thread]("http://ubuntuforums.org/showthread.php?p=1319473"). I used a find and replace to change:
```
custom_icon="
```
to:
```
custom_icon=".
```

Finally I restarted nautilus using:
```
nautilus -q
```

The folders were still showing the correct album covers and the JPEGs themselves were hidden.

---

