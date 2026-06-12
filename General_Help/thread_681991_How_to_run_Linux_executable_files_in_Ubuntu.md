---
title: "How to run Linux executable files in Ubuntu?"
date: 2008-01-29
forum: General Help
---

### Post by UK-Wobbie on 2008-01-29
Do any one know how to run Linux executable files in Ubuntu?
I have got a executable file from some site and on the site it says, That it's Linux!
But when i click on the file it will not open or do anything, And when i look at the file info on it, It says it's executable :confused:

The site what i am looking at is this 
[http://handbrake.fr/?article=download](http://handbrake.fr/?article=download)

It's a tool made for Windows,Linux,MacOS..
It will yet you put DVD's in to MP4 files for your PSP or Phone.

Thanks :)

---

### Post by chris200x9 on 2008-01-29
yea run then in terminal to /the/path/HandBrakeCLI --help

edit: or put it in /bin so you can just go HandBrakeCLI instead of having to put in the path :)

edit2: probably a better idea to create a bin folder in your home then type export PATH=$PATH:~/bin and store HandBrakeCLI there and this will let you not have to type the path either.

---

### Post by UK-Wobbie on 2008-01-29
> **chris200x9 said:**
> yea run then in terminal to /the/path/HandBrakeCLI --help

edit: or put it in /bin so you can just go HandBrakeCLI instead of having to put in the path :)

Thanks :)

---

### Post by UK-Wobbie on 2008-01-29
I am having a go on what you are saying, but it sounds a bit to hard :lolflag:
What do i do 1st :confused:

Thanks for your help

---

### Post by chris200x9 on 2008-01-29
you could put it in the /bin directory and not need a path...it's what I do but I think a better idea I should probably do is create a bin folder in your home and put handbrake in there then put in the command (I have not done the latter I just read it on a website so I assume it will work like it should)

---

### Post by chris200x9 on 2008-01-29
also read [http://trac.handbrake.fr/wiki/CLIGuide](http://trac.handbrake.fr/wiki/CLIGuide) for how to operate it

---

### Post by UK-Wobbie on 2008-01-29
> **chris200x9 said:**
> you could put it in the /bin directory and not need a path...it's what I do but I think a better idea I should probably do is create a bin folder in your home and put handbrake in there then put in the command (I have not done the latter I just read it on a website so I assume it will work like it should)
Ok :lolflag: I made a folder in my home and named it bin :)
Put in the file handbrake, But what is the command?

Thanks :)

---

### Post by jrothwell97 on 2008-01-29
As I understand it, first you should double click on the file to untar it.

The open the terminal (I believe it is under Applications/System Tools).

You will be presented with a terminal in your home directory. Go to the folder (presumably on the Desktop?) in which you untarred the file. This is done using the command

```
cd
```

For example, if it was on the Desktop, then you would type

```
cd Desktop
```

Check you're in the right folder by listing the files using this command:

```
ls
```

It helps to remember these commands, they will come in very useful later.

If you can see the file, then you need to run this command to get it to work:

```
./HandBrakeCLI -i source -o destination
```

If that doesn't work, you may need to enable execution permissions on the file. This can be done in the terminal using chmod, but you might find it easier to use the properties window for the executable.

I hope this answers your question.

---

### Post by taurus on 2008-01-29
```
mv filename ~/bin
```
Then, you need to edit ~/.bashrc and put ~/bin in your path so you can run it anywhere, without including the whole path.

```
gedit ~/.bashrc
```
and add these two lines to the end of it.

```
PATH=$PATH:~/bin
export PATH
```
Save it and run

```
source ~/.bashrc
```

---

### Post by chris200x9 on 2008-01-29
> **UK-Wobbie said:**
> Ok :lolflag: I made a folder in my home and named it bin :)
Put in the file handbrake, But what is the command?

Thanks :)

```
 export PATH=$PATH:~/bin 
```


also as the other guy said make sure it's untared and has executable permision I'm going to assume it's untared.....but for the permission highlight it hit file or edit I forget which go to properties then make sure the has executable permission (or something) box is checked...if it is cool...if its not check it :)

---

### Post by UK-Wobbie on 2008-01-29
> **jrothwell97 said:**
> As I understand it, first you should double click on the file to untar it.

The open the terminal (I believe it is under Applications/System Tools).

You will be presented with a terminal in your home directory. Go to the folder (presumably on the Desktop?) in which you untarred the file. This is done using the command

```
cd
```

For example, if it was on the Desktop, then you would type

```
cd Desktop
```

Check you're in the right folder by listing the files using this command:

```
ls
```

It helps to remember these commands, they will come in very useful later.

If you can see the file, then you need to run this command to get it to work:

```
./HandBrakeCLI -i source -o destination
```

If that doesn't work, you may need to enable execution permissions on the file. This can be done in the terminal using chmod, but you might find it easier to use the properties window for the executable.

I hope this answers your question.

Hey thanks for all your help you two :)
I have done all of this,
But right at the end of it on the install!
I get this..
--------------------------------------------------------------------------------------------------
Output format couldn't be guessed from file name, using default.
HandBrake 0.9.1 (2007100800) - [http://handbrake.m0k.org/](http://handbrake.m0k.org/)
2 CPUs detected
Opening source...
ERROR: dvd: DVDOpen failed (source)No title found.
HandBrake has exited.
--------------------------------------------------------------------------------------------------

I do not know what to do :lolflag:

Thanks

---

### Post by taurus on 2008-01-29
Change permissions from a terminal with, assuming you are in the directory where the file is.

```
chmod 755 filename
```

---

### Post by UK-Wobbie on 2008-01-29
> **taurus said:**
> Change permissions from a terminal with, assuming you are in the directory where the file is.

```
chmod 755 filename
```

Hey thanks for your help :)

Is it like this? 
If i say i have the file on the desktop?

chmod 755 /home/user/Desktop/HandBrakeCLI

I am still like all new to this stuff :lolflag:

---

### Post by chris200x9 on 2008-01-29
did you select an inpiut

i.e ```
 -i /media/cdrom0 
```

then title 

i.e ```
 -t 1 
```

then an output

i.e ```
 -o ~/Videos/_something_.mp4 
```


note the .mp4 extension is vital because unless you specify a container format it uses the extension to *guess*

I doubt it chmod since by your output it looks like it started running

I hope this solves it for you because I gtg sorry

---

### Post by UK-Wobbie on 2008-01-29
> **chris200x9 said:**
> did you select an inpiut

i.e ```
 -i /media/cdrom0 
```

then title 

i.e ```
 -t 1 
```

then an output

i.e ```
 -o ~/movies/_something_.mp4 
```


note the .mp4 extension is vital because unless you specify a container format it uses the extension to *guess*

:lolflag: I do not know what i am doing, I am still on the installing i say.

I put in "cd"
Then "cd Desktop" To show that it's on the desktop :lolflag:
Then "ls" To show the files on the desktop!
Then "./HandBrakeCLI -i source -o destination" to install!

It sounds way to hard :lolflag: I may not do it.

Thanks for all your help you guys or girls lol  :mrgreen:

---

### Post by chris200x9 on 2008-01-29
First off sorry for my absence, secondly don't get discouraged, thirdly this is a cli app so there is no "installing", fourthly I'm stupid and don't know why I didn't recommend this before [http://sourceforge.net/project/downloading.php?groupname=rippedwire&filename=handbrakegtk_1.0.1_i386.deb&use_mirror=osdn](http://sourceforge.net/project/downloading.php?groupname=rippedwire&filename=handbrakegtk_1.0.1_i386.deb&use_mirror=osdn)

only thing queing up doesn't keep your settings :)

---

### Post by UK-Wobbie on 2008-01-29
> **chris200x9 said:**
> First off sorry for my absence, secondly don't get discouraged, thirdly this is a cli app so there is no "installing", fourthly I'm stupid and don't know why I didn't recommend this before [http://sourceforge.net/project/downloading.php?groupname=rippedwire&filename=handbrakegtk_1.0.1_i386.deb&use_mirror=osdn](http://sourceforge.net/project/downloading.php?groupname=rippedwire&filename=handbrakegtk_1.0.1_i386.deb&use_mirror=osdn)

only thing queing up doesn't keep your settings :)

Hey chris200x9,

Thanks for everything your a star :biggrin:
That .deb file made things so easy :lolflag:

Thanks ;)

---

