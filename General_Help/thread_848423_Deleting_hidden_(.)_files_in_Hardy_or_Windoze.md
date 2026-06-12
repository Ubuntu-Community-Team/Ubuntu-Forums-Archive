---
title: "Deleting hidden (.) files in Hardy or Windoze"
date: 2008-07-03
forum: General Help
---

### Post by lewisskinner on 2008-07-03
hey guys, bear with me here.

I installed Feisty, and then upgraded to Gutsy.  However, some things weren't working quite as they ought, so when I Installed Hardy, I did a fresh install rather than an upgrade.

However, the problems were obviously in my separate /home partition, so I want to delete all the hidden Ubuntu files in there and then fresh install.  I cannot format my /home partition, as it contains all my documents and media files.

So, I either need a way to delete the files in a Linux distro (I do have Mint and gOS, so I could try to log into these to delete) or a way of showing the hidden files in Windoze Vista.

Thanks in advance all!

---

### Post by Elfy on 2008-07-03
Open nautilus - do Ctrl+H - then you can see your hidden files and can delete them.

---

### Post by jimv on 2008-07-03
Doing what I suggested in this post didn't work, so I deleted it.

---

### Post by lewisskinner on 2008-07-03
But can I delete the Ubuntu system files whilst I'm logged into Ubuntu?

---

### Post by jimv on 2008-07-03
Doing what I suggested in this post didn't work, so I deleted it.

---

### Post by lewisskinner on 2008-07-03
Sorry Jimv, I was referring to forestpixie's post.

---

### Post by jimv on 2008-07-03
In that case, yeah, you can delete pretty much anything while Linux is running.  That's why "sudo rm -rf /"is a VERY DANGEROUS command.  It will wipe out most of the contents of your harddrive even while Linux is running...including system files.

---

### Post by Elfy on 2008-07-03
Sorry ignored earlier post as I assumed you were talking about jimv's suggestion and I wasn't too sure of the answer.

But yes do what you will with the hidden configs - the only ones I guess you might want to worry about would be e-mails - they will be stored in your /home and bookmarks for your browser.

I use the seperate /home partition deal for myself - but when I do reinstall I delete all my configs except the aforementioned e-mail browser folders.

---

### Post by The Cog on 2008-07-03
How about this:

> for x in $(ls -a | grep '^\.[a-Z]') ; do  echo $x ; done
and if that only lists the directories you want to remove, change it to:

> for x in $(ls -a | grep '^\.[a-Z]') ; do  rm -rf $x ; done

---

### Post by Elfy on 2008-07-03
If it doesn't help him - I'm keeping it, after I try and work out how it does it :) - then all I have to do is rename the 2 I keep without the . and bob is my uncle.

O course after I run the echo line - I realise there are 3 - I like to keep bash_history as well :)

---

### Post by The Cog on 2008-07-03
**ls -a** lists all files including hidden ones.
**grep '^\.[a-Z]'** finds the lines that start with a dot followed by a letter a thru Z (this gets rid of . and .. which you don't want to delete)
**$(ls -a | grep '^\.[a-Z]')** creates a list of all files starting with . followed by a letter
**for x in <list> ; do echo $x ; done** sets x to be each list element in turn and echoes it.

---

### Post by Elfy on 2008-07-03
Ohhh.... I wanted to work it out for myself - now I've read it. #-o

So how do you get an output of all the packages that you have installed since the system was installed, without including packages installed as dependencies and any that were installed as a result of the system 

Now that a lot of people seem to ask for :D

---

### Post by lewisskinner on 2008-07-03
Any news on the test pal?

---

### Post by ghostdog74 on 2008-07-03
> **The Cog said:**
> How about this:
```

for x in $(ls -a | grep '^\.[a-Z]') ; do echo $x ; done

```

and if that only lists the directories you want to remove, change it to:
that's a long winded way of saying.
```

rm .*[a-zA-Z]*

```
use shell expansion

---

### Post by The Cog on 2008-07-04
Good point. I've not yet had a good look at bash pattern matching, and hadn't realised it went beyond ? and *. And I hadn't really appreciated that . doesn't mean anything special in bash like it does in regex. So it looks like
> rm -rf .[a-Z]
would be the shortest way.

---

### Post by Sinkingships7 on 2008-07-04
Uhh... If you just want to delete all of the hidden files in your home directory, then this should be all you need:

```
rm -rf .*
```
That will delete every hidden folder in your HOME directory.

EDIT: I tested this, just to be sure it works. It's safe. It will delete any hidden file and folder in your home directory (i.e., precedes with a period)

---

### Post by ghostdog74 on 2008-07-04
> **The Cog said:**
>  So it looks like
rm -rf .[a-Z]
would be the shortest way.


shell expansion is not the same as regular expression. anyway, your shortest way would only remove files like .a , .b , .c  and so on. A dot followed by 1 character.

---

### Post by bubba_169 on 2008-07-04
> **Sinkingships7 said:**
> Uhh... If you just want to delete all of the hidden files in your home directory, then this should be all you need:

```
rm -rf .*
```
That will delete every hidden folder in your HOME directory.

EDIT: I tested this, just to be sure it works. It's safe. It will delete any hidden file and folder in your home directory (i.e., precedes with a period)

Not entirely certain but I think that command can be dangerous as the directory './' can be include as well as '../' deleting a lot more than you would want, well anything you have permission to delete anyhows :confused:...

---

### Post by Sinkingships7 on 2008-07-04
> **bubba_169 said:**
> Not entirely certain but I think that command can be dangerous as the directory './' can be include as well as '../' deleting a lot more than you would want, well anything you have permission to delete anyhows :confused:...

You don't have permission to delete anything but your home directory. Without using 'sudo' with that command, it's safe.

---

### Post by lewisskinner on 2008-07-04
OK, I can delete them, but not all of them.  I'm still unable to delete my /home/.compiz or /.gconf

Since the problem I was having was mostly with Compiz fusion, I feel this may cause a problem!

---

### Post by hyper_ch on 2008-07-04
simplest way would be - IMHO -
```

sudo mv /home/USER /home/USER_old
sudo mkdir /home/USER
sudo chown USER:USER /home/USER

```
replace USER with your username.

That way you don't delete anything... you can move your files back - those that work... also config files for other programs.... just move then back what you need... when you re-login as that user then you will have clean new homefolder ;)

---

