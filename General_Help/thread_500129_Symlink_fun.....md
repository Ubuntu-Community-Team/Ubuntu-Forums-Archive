---
title: "Symlink fun...."
date: 2007-07-13
forum: General Help
---

### Post by volksman on 2007-07-13
Hey All!

I have two drives I use to store media on.  Both have similar file structures.  I mount these drives to a central location (IE mythbox).  I would like to "merge" the structures using symlinks, but aside from manually creating each link I'm not sure how to accomplish this.

Here is an example of the structures:

drive1

```
/TV/
   /Show1
      /Season 1
         Episode 1.avi
         Episode 2.avi
   /Show2
      /Season 1
        Episode 1.avi
```


Drive 2

```
/TV/
    /Show2
       /Season 2
          Episode 1.avi
```



So if I symlink at the /TV level I get a "duplicate" directory error on Show2.  The only way I can make it work is to symlink in the /TV/Show2/ directory so that Season 2 shows up.

If anyone has any hints on better ways of doing this I'm all ears.  My problem is as I download things one drive fills up and the next season I use a new drive etc....Moving stuff around is an option but a tedious one...I may end up writing a script if no one can help that would look at each directory and create a merged FS but that is also a lot of work if bash already provides an answer.

Any help is appreciated.

Thanks!

---

### Post by kidders on 2007-07-14
Hi there,

If you think about it, you'll probably see that "blending" two directory trees together easily is impossible. For instance, in your example, what if both tree structures contained  a "TV/Show1/Season 1/Episode 1.avi"? You see, the fact that you probably won't do that is irrelevant ... the theoretical possibility still exists.

If being able to see all your stuff in one unified directory structure is really that important to you, I would suggest something like the following...
[LIST]
[*]Suppose plugging in/out a USB hard disk or something triggered a script execution.
[*]Imagine the script was hard-wired to scan newly attached directory structures for directories called something special you had reserved for the purpose (eg ".movies").
[*]The script could execute a series of "mkdir -p ..." and "ln -s ..." commands, to symlink all your AVI files into your home directory someplace.[/LIST]Personally though, I would prefer to write a web page in PHP or something ... it'd be a lot less messy.

---

### Post by volksman on 2007-07-16
Hey Kidders!

Yeah I know exactly what you mean about duplication or conflict management.  

It looks like I will have to revert to the old shell script idea as you say about making the sym links for me on each file in the directory.

I can't go the web page route cause this is all so that MythTV sees my library of media in a unified manner rather than having to hunt for the file across multiple drives/FS structures.

Thanks for the help though!

---

