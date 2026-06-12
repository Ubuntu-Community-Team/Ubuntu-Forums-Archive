---
title: "How can I automate renameing files from mult dirs into one dir"
date: 2021-11-03
forum: General Help
---

### Post by sofasurfer on 2021-11-03
I have 10 directories with files in them. All files in all directories are named with numbers (0001.jpg, 0002.jpg, 0003.jpg, etc). I want to put them all into one directory. Problem is that they all need to be renamed so the names to not overlap. How can I used command line to go into these directories, rename them and then move them into a new directory with all the others?

---

### Post by Holger_Gehrke on 2021-11-04
```

for i in dir1 dir2 dir3 dir4 dir5 dir6 dir7 dir8 dir9 dir10 ; do cd "$i" ; rename 's//'$(basename $i)'-/' * ; mv * absolute_target_path ; cd -; done

```

Replace "dir1" to "dir10" with the paths of your directories and "absolute_target_path" with the absolute path to your target directory. The files will be renamed by prefixing each name with the name of the directory it's in.

Holger

---

### Post by dragonfly41 on 2021-11-04
There is a package "Bulk Renamer" (which I rarely use) which can rename files in each directory.
And another I see named "KRename".
You could rename files in each directory with a prefix A_, B_, C_ .. J_.
then just push them into a common directory. 

A_0001.jpg
B_0002.jpg
....
A_0001.jpg
B_0002.jpg

Each name will be unique.

---

### Post by sofasurfer on 2021-11-07
I'm trying krename and I kind of like it...except.
I create a /Desktop/testfolder. I moved some files (from /Pictures/.../...) into it and practiced renaming them and having them moved into /finishedpics. It worked once just fine. Then I deleted them all and recreated the process with different pics. Now when I rename and move them they are renamed properly BUT!!! the photos are not the ones I renamed. They are the ones I did the fisrt time. krename is switching my photos with photos that are not even in the directories I am working with. 
I don't expect you to believe this but if you do I hope you can explain this. I have never seen this happen before.

---

### Post by dragonfly41 on 2021-11-07
I hope that you backup your source photos before any experiments with new tools.
I have not used Krename but I do use Krusader (part of the KDE family) as my main
view on my filesystem. In fact Krusader is used extensively in all workflows.
I mention Krusader since it is linked to Krename. File > Multi Rename (or Shift+F2).
Now another feature of Krusader is toolbar > UserActions.
Here you can create automation scripts for different workflows.
For example if you plan to work further on your images, using tools such as Gimp, ImageMagick, or even python scripts (OpenCV) then this opens up many routes for automation.

Or you can forego these complex tools and just use command terminal (post #2).

I cannot answer the question about wrong photos being used, but Krename is a complex tool and I would
spend time first learning/experimenting.  Certainly not on original files (you used the term "move" when I would use "copy").
 I do see an option "Overwrite existing files" and I wonder if perhaps you ticked that option. But I am guessing here.

If you continue with Krename then my suggestion is to use it within Krusader. Clarify what further processing you intend on your photos. And remember the mantra: backup, backup.

[P.S.] To depart from the opening question, and to give one example of what further very advanced image processing can be applied, I have integrated Wolframscript into Ubuntu 20.04 to explore such as this old example. There are many others.

[https://community.wolfram.com/groups/-/m/t/234016](https://community.wolfram.com/groups/-/m/t/234016)

---

