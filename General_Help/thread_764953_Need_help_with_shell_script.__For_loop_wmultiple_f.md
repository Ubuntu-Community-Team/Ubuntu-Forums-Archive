---
title: "Need help with shell script.  For loop w/multiple file types."
date: 2008-04-24
forum: General Help
---

### Post by papafreebird on 2008-04-24
Hello.

I am needing help with shell scripting.  I have searched the net but have not found exactly what I am looking for.  I am wanting to write a shell script with a for loop with mutiple file types.  In windows would go about it like this.

```

for %%a in ("*.avi","*.mp4","*mpg","*.d2v") do 

```

Now I know in bash for a single file type loop I do this
```

for i in *.avi ; do 

```

What I would like to know is how to write a shell script that would accomplish the same thing as my first batch file for windows?

Any suggestions will be appreciated.
Much Thanks!

---

### Post by justleen on 2008-04-24
```
for files in `find . -name "*.mp3" -o -name "*.avi"`; do
```
the -o is OR in this case

---

### Post by papafreebird on 2008-04-24
Wow that was fast.  

Okay.  Much thanks for that.

> So long and thaks for all the fish!

---

