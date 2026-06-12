---
title: "specifying filenames correctly"
date: 2022-01-11
forum: General Help
---

### Post by pjstock on 2022-01-11
this question relates to the sound file converter SOX, but I am going to drop this here, in General Help because there is a general aspect to it.

I am trying to convert an OGG audio file to MP3. Reading up, Sox has been recommended.

at its most basic level, Sox seems pretty simple.
Sox Inputfilename Outputfilename

the instructions for instance offer this simple exampe:
sox recital.au recital.wav
 
my problem is that I have an OGG format sound file buried several levels down that I want to reference.

/home/peter/snap/audio-recorder/common/audio/SOUNDFIeL.ogg

but when I try command line I would think makes sense: sox /home/peter/snap/audio-recorder/common/audio/SOUNDFIeL.ogg /home/peter/snap/audio-recorder/common/audio/SOUNDFIeL.MP3

I get a "No Such File Or Directory"  error

which I think means I simply do not now how to reference raw file names correctly.
How would I do that? 

either to be able to type in just the short file name itself and somehow have the command know what I meant.
Or, if I have to, type in the entire PATH+filename it is expecting?

Many thanks as always.

peter

---

### Post by ActionParsnip on 2022-01-11
If you run
```

ls /home/peter/snap/audio-recorder/common/audio/*

```
What is the output please?

---

### Post by pjstock on 2022-01-11
I get:

ls: cannot access '/home/peter/snap/audio-recorder/common/audio/*': No such file or directory

---

### Post by KBar on 2022-01-11
> **pjstock said:**
> I get a "No Such File Or Directory"  error

which I think means I simply do not now how to reference raw file names correctly.

No. This means that the files don't exist. 

> How would I do that?
either to be able to type in just the short file name itself and somehow have the command know what I meant.
Or, if I have to, type in the entire PATH+filename it is expecting?


You **c**hange **d**irectory one by one, making sure that the next directory exists before changing. For more information on that, invoke ```
help cd
```

There is a concept called *working directory*. Each process has its own to be able to act upon files. The name of a working directory is stored in the **PWD** environment variable. Most processes initiated by a user have it set to their home directory. **~**, $**HOME**, */home/$**LOGNAME*** all expand to user's home directory.

Let's take a look at this directory hierarchy:
```
> pwd
/home/kbar

> ls ~/Music/Pictures/screenshots
'Screenshot from 2020-11-09 00-50-31.png'
'Screenshot from 2020-11-09 00-53-04.png'
'Screenshot from 2020-11-09 00-54-20.png'
'Screenshot from 2021-12-22 11-13-50.png'
'Screenshot from 2021-12-23 06-59-34.png'
'Screenshot from 2021-12-25 06-24-59.png'
'Screenshot from 2021-12-25 09-18-34.png'
'Screenshot from 2021-12-25 15-02-44.png'
'Screenshot from 2021-12-25 15-03-14.png'
'Screenshot from 2021-12-26 14-54-26.png'
```

If I were to manipulate these screenshots, maybe rename some of them, move a couple to another directory, I'd have two options:
[LIST=1]
[*]Do so while standing in my current working directory, which is my home directory. I would have to type full pathnames over and over. There is a powerful facility called *history expansion* provided by the **readline** library that's built into bash that eases this type of work but I won't get into that. 
[*]Change directory to *~/Music/Pictures/screenshots* and do my work on files directly inside that directory. No retyping needed. I would only type the name of the files as arguments to commands. 
[/LIST]
As you can see, second option is much more convenient and user-friendly, and less time-consuming and confusing.

In general, it is a good practice to **cd** into a subdirectory that's multiple levels deep since you can refer to parent directories with *.. *(*dot-dot*) and especially so in your home directory, since you can reference it by a single tilde character **~**. Bash treats it as a special character if left unquoted. It's expanded to the **$HOME** parameter of the current login name, i.e. its value is basically equivalent to */home/**$LOGNAME***.  For more information, read up **Tilde Expansion** in the **EXPANSION** section of **bash**'s man(ual) page.

To eliminate typos and mistakes, use _Tab_ for completion (also provided by the **readline** library).

---

### Post by HermanAB on 2022-01-12
Note that if you have funny characters in your filenames (space, dollar, tilde, dash, dot, etc) then you need to put ‘quotes’ around the whole pathname.

---

### Post by ActionParsnip on 2022-01-12
Try
```

sudo updatedb && locate -i *.ogg | grep home

```
What is the output?

---

### Post by The Cog on 2022-01-12
> I get:

ls: cannot access '/home/peter/snap/audio-recorder/common/audio/*': No such file or directory
Start with "ls /home" then "ls /home/peter" etc, expanding until you reach the name of the directory that doesn't exist. That's the name you are mis-typing somehow. You can use <tab> to complete partially typed filenames. Remember Linux is case sensitive.

---

### Post by pjstock on 2022-01-12
correction. somehow I let a lower case "a" creep in there making the path element "audio" when it should have been "Audio"
I'd forgotten (or realize now) that Linux is very case sensitive.

the ls coimmand now successfully finds the files in the directory.

ls /home/peter/snap/audio-recorder/common/Audio/*
 /home/peter/snap/audio-recorder/common/Audio/2022-01-11-14:45:35.ogg
'/home/peter/snap/audio-recorder/common/Audio/CBCtoxin.ogg'

and when I correctly enter the correct path and file name SOX seems to execute but kicks back a different error:  Input not an Ogg Vorbis audio stream

but that is a different issue than my original question.

AND I think I know the probem there now too. when I recorded this (using Sound Recorder) I did specify MP3 as the format to save it in, but somehow that .ogg tag got applied or retained. and so I thought this was an OGG file. In fact I think it is an MP3 disguised as an OGG. when I change the extension to MP3 it plays correctly.

sorted now I think. sorry to have taken  your time with something trivial.

---

### Post by TheFu on 2022-01-12
Learn to use _tab-completion_ and issues like this go away completely.  Basically, if you are typing more than a few characters for each part of a path, then you are doing it the hard way.  

Also, if your userid is peter, then ~/  is the same as /home/peter (almost always).  ~/ looks up the home directory in the password database and fills that in. The $HOME is also set based on the password DB setting.  No need to type so much for interactive commands.

However, if you are scripting stuff, using the full path is smart, since environment variables may not be set like they are for interactive sessions.

---

