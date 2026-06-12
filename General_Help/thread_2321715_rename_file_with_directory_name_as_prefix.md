---
title: "rename file with directory name as prefix"
date: 2016-04-24
forum: General Help
---

### Post by DM2016 on 2016-04-24
I've been searching for a way to rename all files within all subdirectories with each subdirectory name as prefix to the new filename.  I then want to get rid of the directory structure and have them all in one directory.  

I don't mind doing it in a terminal, although I am new to this.  

I've got close...
```
for f in * ; do cp -r "$f" "/backups/tempRenamedPhotos/2011_December_$f" ; done

```
... but the recursive aspect is not working, and it keeps the directory structure.  Any tips gratefully received.

---

### Post by steeldriver on 2016-04-24
Something like this maybe? Given a directory structure like

```

$ tree dir
dir
&#9500;&#9472;&#9472; dir1
&#9474;   &#9500;&#9472;&#9472; filea
&#9474;   &#9500;&#9472;&#9472; fileb
&#9474;   &#9492;&#9472;&#9472; filec
&#9492;&#9472;&#9472; dir2
    &#9500;&#9472;&#9472; filed
    &#9500;&#9472;&#9472; filee
    &#9492;&#9472;&#9472; filef

```

then

```

$ mkdir newdir

$ find dir -type f -exec bash -c 'for f; do cp -v "$f" newdir/"${f//\//_}"; done' bash {} +
‘dir/dir2/filed’ -> ‘newdir/dir_dir2_filed’
‘dir/dir2/filef’ -> ‘newdir/dir_dir2_filef’
‘dir/dir2/filee’ -> ‘newdir/dir_dir2_filee’
‘dir/dir1/fileb’ -> ‘newdir/dir_dir1_fileb’
‘dir/dir1/filec’ -> ‘newdir/dir_dir1_filec’
‘dir/dir1/filea’ -> ‘newdir/dir_dir1_filea’

```

Result
```

$ tree newdir
newdir
&#9500;&#9472;&#9472; dir_dir1_filea
&#9500;&#9472;&#9472; dir_dir1_fileb
&#9500;&#9472;&#9472; dir_dir1_filec
&#9500;&#9472;&#9472; dir_dir2_filed
&#9500;&#9472;&#9472; dir_dir2_filee
&#9492;&#9472;&#9472; dir_dir2_filef

```

---

