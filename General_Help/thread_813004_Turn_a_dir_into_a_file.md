---
title: "Turn a dir into a file?"
date: 2008-05-30
forum: General Help
---

### Post by 289Shelby on 2008-05-30
Is it possible to turn a directory into a file? I had a dir which contained some images and have just recently noticed that the directory and all the images within it have now become a single file, and as such the images are no longer viewable. I tend to use the 'mv' and 'cp' commands for manipulating files.

Can anyone suggest what I have done wrong here, and more to the point, is it possible to get those images back? Perhaps by turning the file back into a directory?

Thanks

---

### Post by ibuclaw on 2008-05-30
What is the size of the file?

[EDIT]
type into the terminal:
```
cd ~/ && find -type f -iname "*.**jpg**" 2>/dev/null
```
Change the suffix with that of what your pictures where saved as, and perhaps you'll find them...

Regards
Iain

---

### Post by latna on 2008-05-30
Do you think it's an tar archive or a zip file? What does this command give you? Of course replace filename with the actual name of your file.

```
file filename
```

---

### Post by 289Shelby on 2008-05-30
> 
```
file filename
```

This seems weird to me. The result of the above gives:

Microsoft ASF.

I'm not too sure what this means.

---

### Post by 289Shelby on 2008-05-30
> **tinivole said:**
> What is the size of the file?

71MB

> 
[EDIT]
type into the terminal:
```
cd ~/ && find -type f -iname "*.**jpg**" 2>/dev/null
```
Change the suffix with that of what your pictures where saved as, and perhaps you'll find them...


No joy. It lists the jpgs in all other directories but not the one that's a file.

---

### Post by TheFuzzy0ne on 2008-05-30
I'm not undermining your intelligence, but for the sake of clarity, please could you post the output of "ls -la" on the directory/file in question, or rather the directory it resides within? Thanks.

---

### Post by KingTermite on 2008-05-30
I know in Windows you can copy (using wild cards) files and if the destination doesn't specify a directory correctly, it will just jam them all together like one big file.

I suspect that may be what happened....Not sure how you can recover it though. It's not like it uses tar when it does that.

---

### Post by bingoUV on 2008-05-30
If I remember correctly, ASF is a video format by microsoft. Try playing it in your video player. mplayer used to play ASF without trouble. Maybe some program converted your images into one single movie.

---

### Post by 289Shelby on 2008-05-30
> **TheFuzzy0ne said:**
> I'm not undermining your intelligence,

Not at all:-)

>  but for the sake of clarity, please could you post the output of "ls -la" on the directory/file in question, or rather the directory it resides within? Thanks.

This is the 'file'

[email]pat@xeon:~/.imag[/email]es$ ls -la atk
-rw-r--r-- 1 pat pat 73772122 2008-04-29 16:58 atk

This is the dir it's within.

drwxr-xr-x  88 pat pat   315392 2008-05-30 09:55 .
drwxr-sr-x 115 pat pat    20480 2008-05-30 08:58 ..

---

### Post by TheFuzzy0ne on 2008-05-30
The only thing I can suggest (and I am no expert), is to open the console and type:

```

sudo touch /forcefsck

```

which will do a file system check on your next reboot. Reboot, and go and put the kettle on (I take mine with no sugar, thanks). I should take a few minutes depending on the speed of your system, but it may pick up on it if there is corruption in your filesystem, and hopefully fix it.

---

### Post by 289Shelby on 2008-05-30
> **KingTermite said:**
> I know in Windows you can copy (using wild cards) files and if the destination doesn't specify a directory correctly, it will just jam them all together like one big file.

I suspect that may be what happened....Not sure how you can recover it though. It's not like it uses tar when it does that.

That could well be what has happened if I wasn't concentrating on what I was doing at the time. Oh well, if they're gone they're gone. I was as much curious as to what I'd done as much as anything else.

---

### Post by 289Shelby on 2008-05-30
> **bingoUV said:**
> If I remember correctly, ASF is a video format by microsoft. Try playing it in your video player. mplayer used to play ASF without trouble. Maybe some program converted your images into one single movie.

I tried mplayer and smplayer and the file doesn't show up even when asked to list 'all files'

---

### Post by TheFuzzy0ne on 2008-05-30
I was under the impression that you needed to concatenate using a double right-cheverons ">>" (to append). If that is the case, I believe it's unlikely that this has happened. That is, of course, unless Linux can do this without the double right-cheverons.

---

### Post by bingoUV on 2008-05-30
> **289Shelby said:**
> I tried mplayer and smplayer and the file doesn't show up even when asked to list 'all files'

it won't show up. Just play it with mplayer on command line
```

mplayer <filename>

```

---

### Post by ibuclaw on 2008-05-30
You could always read the last, say, 100 or 200 commands that you used in the terminal...
```
tail -n 200 ~/.bash_history | less
```
And have a scoop for any commands that seems to be something that you didn't want to do.
(Use the **Up** and **Down** keys to navigate through the text, and the **Q** key to exit)

Regards
Iain

---

### Post by latna on 2008-05-30
Let us know the details if you get this sorted out. I'm kind of curious now. ;)

---

### Post by 289Shelby on 2008-05-30
> **bingoUV said:**
> it won't show up. Just play it with mplayer on command line
```

mplayer <filename>

```

That works. It is a video, I could have sworn that it was a dir containing images. Perhaps I can put it down to old age.

I apologise to everyone who replied for leading them on a wild goose chase.

Many thanks to you all for your help.

---

### Post by 289Shelby on 2008-05-30
> **tinivole said:**
> You could always read the last, say, 100 or 200 commands that you used in the terminal...
```
tail -n 200 ~/.bash_history | less
```
And have a scoop for any commands that seems to be something that you didn't want to do.


I couldn't find anything that looked obvious but then I don't really know when it happened, I only noticed it recently.

Thanks

---

### Post by 289Shelby on 2008-05-30
> **latna said:**
> Let us know the details if you get this sorted out. I'm kind of curious now. ;)

A bit of an anti-climax I'm afraid. See my reply to bingoUV.

Time to get a brain transplant I think:-)

---

### Post by 289Shelby on 2008-05-30
> **TheFuzzy0ne said:**
> The only thing I can suggest (and I am no expert), is to open the console and type:

```

sudo touch /forcefsck

```

which will do a file system check on your next reboot. Reboot, and go and put the kettle on (I take mine with no sugar, thanks).


:-)

> 
 I should take a few minutes depending on the speed of your system, but it may pick up on it if there is corruption in your filesystem, and hopefully fix it.

Thanks for the suggestion, I'll try that. I can't reboot immediately because I'm running some monitoring software but as soon as that is done I'll give it a try.

Thanks

---

### Post by ibuclaw on 2008-05-30
> **289Shelby said:**
> A bit of an anti-climax I'm afraid. See my reply to bingoUV.

Time to get a brain transplant I think:-)

What **you** need is some [**Ubuntu Wine**]("http://www.kwv.co.za/brands/view/32"). That'll fix-up that brain of yours...
Hmm...Yummy Goodness!!!

Iain

---

### Post by 289Shelby on 2008-05-31
Definitely like your idea better:-)

---

