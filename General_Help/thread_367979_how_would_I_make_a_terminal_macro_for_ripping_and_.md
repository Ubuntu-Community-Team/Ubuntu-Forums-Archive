---
title: "how would I make a terminal macro for ripping and converting DVDs (home-made ones)?"
date: 2007-02-22
forum: General Help
---

### Post by billdotson on 2007-02-22
I know a little bit about the DOS shell and how you can make .bat files to automate tasks.
I have also heard of scripting to automate tasks in Linux kernel OS's.  

I have downloaded an installed vobcopy, transcode, dvd+-rw tools, mjpeg tools, dvd author, subtitle ripper.  I know the commands to rip the movie off of the DVD and convert it into .mpg format.  

vobcopy 
tcextract -i INPUT.vob -t vob -x mpeg2 > movie.m2v   (input being the name of the file)
tcextract -i INPUT.vob -t vob -x ac3 -a 0 > movie.ac3   (input being the name of the file)
mplex -f 8 -o "movie%d.mpg" movie.m2v movie.ac3

Can I just create a script so that when I type vob it will automatically rip and transcode the video?

---

### Post by geirha on 2007-02-22
Edit a new file in ~/bin/ with some easy editor like nano:

```

mkdir ~/bin # in case it doesn't exist
nano ~/bin/vob 

```
with this content
```

#!/bin/bash

vobcopy -t movie
tcextract -i movie.vob -t vob -x mpeg2 > movie.m2v
tcextract -i movie.vob -t vob -x ac3 -a 0 > movie.ac3
mplex -f 8 -o "movie%d.mpg" movie.m2v movie.ac3

```
Then make it runnable:
```
chmod +x ~/bin/vob
```

Now you can run it by typing vob (granted that ~/bin is in your path variable, type "echo $PATH" to check), and if I interpret the commands correctly, it will create movie.vob, movie.m2v, movie.ac3, movie1.mpg and movie2.mpg ... in the directory you're in, so you'll need a bit of space there (perhaps an idea to remove files with "rm -f filename" when the files aren't needed anymore)

The syntax for bash-scripts is documented in bash's manpage, you can read it by typing "man bash"

---

### Post by billdotson on 2007-02-22
wait :  why do you have "-t movie" after vobcopy in the script?? 

 vobcopy
tcextract -i INPUT.vob -t vob -x mpeg2 > movie.m2v (input being the name of the file)
tcextract -i INPUT.vob -t vob -x ac3 -a 0 > movie.ac3 (input being the name of the file)
mplex -f 8 -o "movie%d.mpg" movie.m2v movie.ac3

vobcopy -t movie
tcextract -i movie.vob -t vob -x mpeg2 > movie.m2v
tcextract -i movie.vob -t vob -x ac3 -a 0 > movie.ac3
mplex -f 8 -o "movie%d.mpg" movie.m2v movie.ac3

---

### Post by billdotson on 2007-02-22
I still wonder why you d put "-t movie" after vobcopy but I am assuming that is making the title movie.  I did all of that you said and then typed "vob" in the terminal and it said command not found.  I did the echo $PATH and this is the output:  /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games

---

### Post by geirha on 2007-02-23
ok, the path problem, when I type: cat .bash_profile
it prints out this bit at the end:
```

# set PATH so it includes user's private bin if it exists
if [ -d ~/bin ] ; then
    PATH=~/bin:"${PATH}"
fi

```
if it's not there, edit .bash_profile and add it. The change will take effect the next time you login, or you can type "bash --login" in the terminal window to make it work in that terminal. The above code will change the PATH to include your ~/bin dir, but only if it exists.

You could of course just type the whole path instead, like "~/bin/vob", to run your vob-script

As for the -t parameter, the vobcopy manpage says this:
```

       -t, --name NAME
              you can give the file a name if you don&#8217;t like the one from dvd.
              -t hallo will result in hallo.vob. (stdout or "-" are deprecated
              now)  If you want to give it names like "Huh I like this movie",
              do it in quotation marks.

```
so the resulting file should be called movie.vob instead of something random(?).vob I haven't tried vobcopy before, so I wouldn't really know.

---

