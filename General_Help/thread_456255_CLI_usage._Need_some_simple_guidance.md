---
title: "CLI usage. Need some simple guidance"
date: 2007-05-27
forum: General Help
---

### Post by eentonig on 2007-05-27
I've done it before. But for the heck of it. I can't remember how I did it.

I feel so stupid now.

I have a folderstructure with pictures in it, and out of those, I want to find the RAW images (all with DNG extension) and move them to a seperate folder.

I know there is a one commandline way of achieving this. I just can't remember how to combine the results of my "ls -R | grep DNG" with a "mv".

---

### Post by dolphin_oracle on 2007-05-27
can't you just

$mv *.dng destinationfolder/

**edit** never mind, I see you are copying from a whole structure.  sorry.

---

### Post by stylishpants on 2007-05-27
One way is this:

```
find . -type f -name \*.DNG -exec mv {} /path/to/destination \;
```

---

### Post by eentonig on 2007-05-28
Thanks!

Not how I did it. But it got the job done.

Now I just have to make sure I don't forget how I did it.

---

### Post by Nikron on 2007-05-28
> **eentonig said:**
> Thanks!

Not how I did it. But it got the job done.

Now I just have to make sure I don't forget how I did it.

You could always just make it a function in your .bashrc

---

### Post by eentonig on 2007-05-28
I already made a little script out of it. 

Now I just need to extent it, to allow user input to change starting folder, destination folder and regular expression to match (or just match the file extension)

---

