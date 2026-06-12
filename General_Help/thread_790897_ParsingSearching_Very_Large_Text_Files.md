---
title: "Parsing/Searching Very Large Text Files"
date: 2008-05-11
forum: General Help
---

### Post by TroyDowling on 2008-05-11
Hey guys,

Basically, I have a couple massive log files from a program I wrote that went ballistic. Each of these logs are about 700MB large! Opening them in text editor just freezes (obviously) as they're humongous; nano also fails for some reason as it makes it look like an empty file. My questions are:

1) What is the command to read a text file INTO the console? I would like to be able to 'grep' it.

2) Is there a command that can just display the last line in the file?

3) If I created a ramdisk and loaded the file over to that, would it open better in Gedit?

Thanks a lot guys.
Troy.

---

### Post by sekinto on 2008-05-11
Try "cat [file]".

---

### Post by tacutu on 2008-05-11
for the very last line of the file:
```
 tail -n 1 <filename>
```

---

### Post by TroyDowling on 2008-05-11
No, it didn't do anything. I tried that earlier with the -A flag as well, but to no avail...

---

### Post by olejorgen on 2008-05-11
```

$ man tail
$ man head
$ cat log | grep

```
I don't think it would help to load the file in a ramdisk.

You could also try other editors, maybe vim or emacs will do the trick.

---

### Post by TroyDowling on 2008-05-11
I think I figured it out guys. My program prints lines in a while loop. This loop went infinite on me which is how I got the crazy large files. When I made the logs, I just piped the output of my console to a text file using the '>' operator. I'm not sure if this is true, but could the files be "full of nothing"? Nano seems to agree that the files are large but empty... This would explain 'tail', 'head' and 'cat' having no effect. Thanks for the help so far guys; I'm still learning the UNIX ropes.

---

### Post by TroyDowling on 2008-05-11
Forgive the double post. I just recreated the event and everything went like it should have in the first place-- except from getting the huge logs in the first place of course :). Thanks for the help guys, these forums are truly noob-forgiving.

Troy.

---

