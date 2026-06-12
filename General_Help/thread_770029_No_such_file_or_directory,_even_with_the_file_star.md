---
title: "No such file or directory, even with the file staring me in the face"
date: 2008-04-27
forum: General Help
---

### Post by Waelwulf on 2008-04-27
```
sudo /home/tao/Desktop/ubuntu-8.04-eeetweak-eeepc701.sh
``` yields me the error message "sudo: unable to execute /home/tao/Desktop/ubu.sh: No such file or directory"

The file is staring me in the face and I know I have the right path, why?

---

### Post by amingv on 2008-04-27
Did you write the path/filename correctly? I know you said you did, but I'm tempted to ask again since the path you provide and the one in the error message do not match.

You can try this:
1. Try to tab-complete the path, to reduce error likelyhood.
2. Drag and drop the file into the terminal;  that will produce the exact path.

---

### Post by Waelwulf on 2008-04-27
Oh yes, I'm sorry, I did provide two different filenames but that was only a typo, I am most certainly providing the correct path.

I did the drag and drop method, still the same error message.

---

### Post by mali2297 on 2008-04-27
You must either make the script executable or run it with sh,
```

sudo sh /home/tao/Desktop/ubuntu-8.04-eeetweak-eeepc701.sh

```

---

### Post by Iowan on 2008-04-27
Perhaps not the case... but sometimes "local" files need a "dot" to execute.```
sudo sh ./home/tao/Desktop/ubuntu-8.04-eeetweak-eeepc701.sh
``` or one of the other permutations.

---

