---
title: "Export list of files and folders"
date: 2013-08-25
forum: General Help
---

### Post by motorcity909 on 2013-08-25
Hi all

I should know this but...

what is the command to export a list of the sub-folders and files from a directory?

For example, my Music folder - I'd like a text list that would show Music/Artist/Album/song.mp3 for all 15000 mp3s.

I hope that makes sense!

Cheers
Dave

---

### Post by motorcity909 on 2013-08-25
Ah, got it now.

ls -R /home/myname/Music/ > filenames.txt

Cheers
Dave

---

### Post by steeldriver on 2013-08-25
You could use the 'find' command - something like

```
find "/path/to/Music folder" -iname '*.mp3'
```

If you want to results to go to a file instead of being outputted in the terminal, add a > redirect

```
find "/path/to/Music folder" -iname '*.mp3' > /path/to/outfile
```

Obviously replace the "/path/to" bits with the actual directory paths / files

---

### Post by motorcity909 on 2013-08-25
Thanks Steeldriver, your command is excellent just for filtering the list to mp3s whilst the **ls** command I mentioned lists everything, so it includes the jpgs I've got as covers.

Great stuff, many thanks.

Dave

---

### Post by Cheesemill on 2013-08-25
If you want a slightly more graphical text file you can install and use the tree command...
```
sudo apt-get install tree
tree --prune -P *.mp3 > filenames.txt
```

---

