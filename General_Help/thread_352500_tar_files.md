---
title: "tar files?"
date: 2007-02-03
forum: General Help
---

### Post by LinuxforHumans on 2007-02-03
Okay, I know this is a miserable question but I've followed other tutorials and for some reason none of them work.

I just downloaded a file (4715-Darlue.tar)
Now it's on my dektop.

I tried the following:

```
$ tar xvzf 4715-Darlue.tar.
```

And I got the following error:

```
tar: 4715-Darlue.tar: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
```

How do I use compile/use this file?

---

### Post by Ramses de Norre on 2007-02-03
There is a '.' too much in your filename and you shouldn't use the z flag, that's for zipped tar archives only.

So use this: **tar xvf 4715-Darlue.tar**

---

### Post by LinuxforHumans on 2007-02-03
The I get this:
```

tar: 4715-Darlue.tar: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
```

---

### Post by Ramses de Norre on 2007-02-03
Then you've got the file name wrong.. Are you in the right directory and such? That's the only possible error I can think of.

---

### Post by LinuxforHumans on 2007-02-03
How do you change directory/determine which you're in?

---

### Post by mcglnx on 2007-02-03
Did you try without the 'x'?

To change dir: cd
To know the current one: pwd
To have the current promt location on the terminal header, add the following on your ~/.bashrc (if you are using bash shell)
        PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME}: ${PWD}\007"'

---

### Post by FenrisAbraxas on 2007-02-03
> **LinuxforHumans said:**
> Okay, I know this is a miserable question but I've followed other tutorials and for some reason none of them work.

I just downloaded a file (4715-Darlue.tar)
Now it's on my dektop.

I tried the following:

```
$ tar xvzf 4715-Darlue.tar.
```

And I got the following error:

```
tar: 4715-Darlue.tar: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
```

How do I use compile/use this file?

Have you tried:

```

$cd /the/dir/of/your/file
$tar -xvzf YourFile #with a minus tar -options 

```

You can also read the manual:
```

$man tar

```

---

### Post by Topsiho on 2007-02-03
You say the tar-file is on your desktop.
Then, wherever you are (in whatever directory I mean :)) do

cd (enter)  {this changes you to your home directory)
cd Desktop  (enter) {this changes you to your Desktop directory}

to be sure do

ls  (enter)   {this gives you a list of the files and subdirectories in the Desktop directory}

If you find the tar-file in this list you can do:

tar xvf filename  (enter)

x means: extract (retrieve from the tar (tape archive)), v means: verbose, f means: file, filename is the name of the file to be tar-ed. The z-option means to (un)zip the file, this is not necessary here as it is a tar file and not a tar.gz one (a tarball such a file is called).

Good luck,

Topsiho

---

### Post by LostShootingStar on 2007-02-03
you should also use tab completion to make sure your getting the file name exactly right.

---

### Post by LinuxforHumans on 2007-02-03
Thanks for all the help!

um..now, how do I add the new themes I downloaded to emerald theme manager?

---

### Post by LostShootingStar on 2007-02-03
open the emerald theme manager. click import, select the .emerald file you want. you can probably drag and drop too..

---

### Post by FenrisAbraxas on 2007-02-03
what i meant is that AFAIK the arguments are given with a - sign (tar is the name of the program and -xfzv are the arguments!) so you HAVE to use like this :
```

$ tar                  -xvzf

```

---

### Post by Ramses de Norre on 2007-02-03
Tar works without a dash for its options too, this is the old way of specifying options and most commands haven't got this anymore but tar does, just like ps aef and ps -aef both work (but there is a change of functionality with the ps command).

---

### Post by FenrisAbraxas on 2007-02-03
> **Ramses de Norre said:**
> Tar works without a dash for its options too, this is the old way of specifying options and most commands haven't got this anymore but tar does, just like ps aef and ps -aef both work (but there is a change of functionality with the ps command).

Anyway, i pointed to the manual page as well :P anyway! if you can't find the app in synaptic you can get it in .deb packages! try it out (and also some compressors/desomnpressors with gUI).

Adios amigos!

---

