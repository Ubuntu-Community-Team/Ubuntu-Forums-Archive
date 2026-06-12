---
title: "Question about renaming files w. Nautilus"
date: 2007-06-11
forum: General Help
---

### Post by _sAm_ on 2007-06-11
A bit strange question from me regarding nautilus;

I have a lot of files that I want to rename; all the files have long names and I want to remove only a part of it that all the files have.         Example; lise_lalala_jamendo.mp3 
Is it possible to get nautilus to remove only the “jamendo” part from a lot of files?

---

### Post by ThinkBuntu on 2007-06-11
Look into the shell "mv" command. I'm certain there's a way to batch-rename files while still preserving their filenames or extensions.

---

### Post by _sAm_ on 2007-06-11
Thanks
I have been reading the man page, but it didnt make me any smarter... Any one else know how to use the man command for some files in a folder? 

[http://www.research.att.com/~gsf/man/man1/mv.html](http://www.research.att.com/~gsf/man/man1/mv.html)

---

### Post by Brucevdk on 2007-06-13
I was looking around as to whether Nautilus supports renaming files based on patterns and came across this thread. As far as I can tell Nautilus does not have such functionality, but not to leave you hanging here's a solution to your problem using some common commands.

First off here's an example of a directory containing some files as you described:
```

-rw-r--r-- 1 bruce bruce 0 2007-06-13 21:25 bar_jamendo.ogg
-rw-r--r-- 1 bruce bruce 0 2007-06-13 21:25 cake_jamendo.ogg
-rw-r--r-- 1 bruce bruce 0 2007-06-13 21:25 foobar_jamendo.ogg
-rw-r--r-- 1 bruce bruce 0 2007-06-13 21:25 foo_jamendo.ogg
-rw-r--r-- 1 bruce bruce 0 2007-06-13 21:25 pie_jamendo.ogg
-rw-r--r-- 1 bruce bruce 0 2007-06-13 21:26 yoghurt_jamendo.ogg

```

To remove the jamendo part we can use the *rename* command, which supports regular expressions:
```

rename "s/jamendo//" *.ogg

```

Where *s/jamendo/foobar/ * would have meant substitute *jamendo* with *foobar*, or in the above case with absolutely *nothing*.

We could also have used variable substitution:
```

for file in *.ogg; do mv "$file" "${file/jamendo/}"; done

```

The important bit here is *${file/jamendo/}*, which means in variable *file* replace *jamendo* with nothing. We could also have said replace *jamendo* with *foobar* by using *${file/jamendo/foobar}*.

But with the loop and all, that's just too much to remember when you can just use rename :)

My own solution before reading [this article about renaming at Debian Administration]("http://www.debian-administration.org/articles/150") would have involved using *sed*:
```

for file in `ls`;  do mv "$file" `echo "$file" | sed "s/jamendo//"; done

```

I must warn you that these might be the most efficient or most elegant solutions, if somebody who has more experience using the command line can offer another example I say go right ahead. They all work though and you'll end up with the following:
```

-rw-r--r-- 1 bruce bruce 0 2007-06-13 21:25 bar_.ogg
-rw-r--r-- 1 bruce bruce 0 2007-06-13 21:25 cake_.ogg
-rw-r--r-- 1 bruce bruce 0 2007-06-13 21:25 foobar_.ogg
-rw-r--r-- 1 bruce bruce 0 2007-06-13 21:25 foo_.ogg
-rw-r--r-- 1 bruce bruce 0 2007-06-13 21:25 pie_.ogg
-rw-r--r-- 1 bruce bruce 0 2007-06-13 21:26 yoghurt_.ogg

```

Good luck.

---

### Post by stchman on 2007-06-13
> **_sAm_ said:**
> A bit strange question from me regarding nautilus;

I have a lot of files that I want to rename; all the files have long names and I want to remove only a part of it that all the files have.         Example; lise_lalala_jamendo.mp3 
Is it possible to get nautilus to remove only the &#8220;jamendo&#8221; part from a lot of files?

Yes, highlight the files and press F2 and you will be able to add or delete to the file name.  Just like Explorer.

---

### Post by _sAm_ on 2007-06-17
Thanks stchman for your suggestion, but I have a lot of files so manually change them via F2 would take too long time. But I will remember the shortcut F2, nice one.

Brucevdk; Just want to say that your suggestion is perfect, and the very good explanation you gave is highly appreciated. This is just what I was looking for, and it will save me a lot of time! Normally I fear the terminal, but this shows me how great it can be even for a noob like me! Thank you for your time.

---

### Post by Brucevdk on 2007-06-17
No problem glad you liked it :)

UPDATE: actually what you read below isn't such a good idea when we could just use call Thunar's extension from within Nautilus, [see this post]("http://ubuntuforums.org/showpost.php?p=2906846&postcount=10"). I'll just leave it here for historic references :)

You could also sorta integrate this functionality into Nautilus through the context menu using nautilus-actions and zenity for popping up a dialog. I actually hacked up a little shell script in a few seconds which does this, but it only works if you're renaming files in the current directory. I thought I'd share it anyways since you might find it useful. See the screenshot I've attached for a preview of how it works.

If you want to use it. Just *apt-get* both packages as displayed below and execute *nautilus-actions-config* to import the file I've included in the attachments, make sure to modify the path to the location of the shell script.

```
sudo apt-get install nautilus-actions zenity
```

---

### Post by _sAm_ on 2007-06-19
Hi again

I just wanted to say that I have found a solution _with_ GUI. I am more then fine whit the solution above, but gonna post the the gui solution here if others might search for the same. 

The browser for xfce called Thunar can rename files in many different ways, like based up on tags(music tags), change what you want to what you want(as I asked for), and so on.
I installed it from Synaptic, here is the homepage;  [http://thunar.xfce.org/index.html](http://thunar.xfce.org/index.html)

Thanks again Brucevdk, I will try it - perhaps I learn something:D

---

### Post by Brucevdk on 2007-06-19
I just installed Thundar and I must admit that sure is a pretty slick extension, the preview feature is really handy and so is the ability to rename using music tags.

---

### Post by Brucevdk on 2007-06-24
You know what (I don't know why I didn't think of this any sooner), forget about the whole Zenity dialog thing I previously posted. Lets just use Nautilus actions to call this Thunar extension, I attached the exported config from nautilus-actions-config. I tried it out and it works as long as you stick to renaming files in the same folder.

Label: Bulk Rename
Tooltip: Rename files/directories using Thunar's Bulk Rename functionality
Icon: /usr/share/icons/hicolor/48x48/apps/Thunar.png
Path: /usr/bin/Thunar --bulk-rename
Parameters: %M

---

### Post by mdurham on 2007-06-24
> You know what (I don't know why I didn't think of this any sooner), forget about the whole Zenity dialog thing I previously posted. Lets just use Nautilus actions to call this Thunar extension, I attached the exported config from nautilus-actions-config. I tried it out and it works as long as you stick to renaming files in the same folder.

Thanks Brucevdk, that's brilliant!

---

