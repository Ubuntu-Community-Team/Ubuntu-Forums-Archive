---
title: "Where are the gtk bookmarks files orignally set?"
date: 2014-07-03
forum: General Help
---

### Post by scott092707 on 2014-07-03
I have Lubuntu 14.04, and after getting a strange error from PCManFM when I tried to access a non-existant "standard" bookmark, I tracked down the problem to one of the two apparently identical files: 
~/.gtk-bookmarks and  ~/.config/gtk-3.0/bookmarks 
Each contains:
"
file:///home/scott/AA_Directory_Hide/Documents
file:///home/scott/AA_Directory_Hide/Music
file:///home/scott/AA_Directory_Hide/Pictures
file:///home/scott/AA_Directory_Hide/Videos
file:///home/scott/AA_Directory_Hide/Downloads
"
I have a separate partition for my data, and have modified xdg-userdirs to point at places there,
and my home directory has NO "standard" directories (Documents, etc.). (This is different from 13.10, which had the home directories, but they were empty (since I didn't use them)).

Where does the "/AA_Directory_Hide" come from?

Are these bookmark files being created at install?  (fresh install, not upgrade)

Who sets this up?   This sounds like a bug, but I don't know where to file a bug report?

Is this a Lubuntu thing, or an Ubuntu thing?

-Scott

---

### Post by vasa1 on 2014-07-04
> **scott092707 said:**
> ... This sounds like a bug, but I don't know where to file a bug report?
...
You're probably right and there was a bug on a closely related topic. If I find the time I'll post that bug link here. I seem to have volunteered for something that's hogging my free time :(

Found one: [http://ubuntuforums.org/showthread.php?t=2166355](http://ubuntuforums.org/showthread.php?t=2166355)
and this: [https://bugs.launchpad.net/thunar/+bug/1208681](https://bugs.launchpad.net/thunar/+bug/1208681) <<< please look at the various links provided in various comments.

All the best!

---

### Post by bapoumba on 2014-07-04
Just to say that I have no ~/.gtk-bookmarks.
 ~/.config/gtk-3.0/bookmarks shows the bookmarks I have created.
```
file:///home/bapoumba/Dropbox Dropbox
file:///home/bapoumba/Copy Copy
file:///storage storage

```

---

### Post by vasa1 on 2014-07-04
I have

```
file:///home/vasa1/Downloads Downloads
file:///home/vasa1/Dropbox Dropbox
file:///home/vasa1/Public Public

```

in ~/.gtk-bookmarks and I also have /home/vasa1/.config/gtk-3.0/bookmarks
```
file:///home/vasa1/Dropbox/CurrSoc CurrSoc
file:///home/vasa1/Downloads Downloads
file:///home/vasa1/Dropbox Dropbox
file:///home/vasa1/Public Public
file:///home/vasa1/Documents Documents
file:///home/vasa1/.config/openbox openbox
file:///home/vasa1/Pictures Pictures
file:///home/vasa1/.icons .icons
file:///home/vasa1/.local .local
file:///home/vasa1/.config .config

```

So I really don't know what's going on.

---

### Post by bapoumba on 2014-07-04
I'd be curious to know what was the "strange error from PCManFM" from the OP.
I notice that the OP's bookmarks ae not formated the same as ours (vasa's and mine).
file:///home/<user>/Downloads **Downloads** for ex vs file:///home/<user>/AA_Directory_Hide/Downloads : see the missing space and name ?

vasa, have you been using LXQT with your user session ? I have not, this install is pretty stock.

---

### Post by vasa1 on 2014-07-04
> **bapoumba said:**
> ...
vasa, have you been using LXQT with your user session ? I have not, this install is pretty stock.

Yes, I have been using LXQt for quite sometime but have reverted to Openbox because qt5 has introduced quite some changes that break my LXQt session. While my install isn't stock, I feel OP's bookmark problems lie elsewhere as the set-up described is quite different.

---

### Post by bapoumba on 2014-07-04
Yes, thanks, I asked because I have no ~/.gtk-bookmarks.

---

### Post by vasa1 on 2014-07-04
> **bapoumba said:**
> Yes, thanks, I asked because I have no ~/.gtk-bookmarks.
But if you look at the Launchpad bug and the links therein, I had ~/.gtk-bookmarks even in the previous version of Lubuntu (no LXQt then). I don't think ~/.gtk-bookmarks is unique or related to LXQt.

On the other hand, I just added a new bookmark using PCManFM and found that ~/.gtk-bookmarks was **not** modified whereas /home/vasa1/.config/gtk-3.0/bookmarks was!

So I really don't know where ~/.gtk-bookmarks came (or comes) from. My Lubuntu 14.04 was a clean install and not an upgrade.

---

### Post by scott092707 on 2014-07-04
--> bapoumba
The error window for PCManFM can be viewed @
"https://sourceforge.net/p/pcmanfm/bugs/869/attachment/Screenshot%20from%202014-05-10%2016%3A31%3A06.png"

BTW: "...from the OP"
"OP"?  (...probably obvious, once I hear it...)
[EDIT: Oh... I'll bet: "Original Poster" - right?]

---

### Post by bapoumba on 2014-07-04
@vasa : my most sincere apologies, I was wrong. Here is my ~/.gtk-bookmarks. Not sure how I missed it this morning, probably was not awake enough :)
```
file:///home/bapoumba/Dropbox Dropbox
file:///storage storage
file:/// Filesystem
file:///home/bapoumba/Copy Copy
```


> **scott092707 said:**
> --> bapoumba
The error window for PCManFM can be viewed @
"https://sourceforge.net/p/pcmanfm/bugs/869/attachment/Screenshot%20from%202014-05-10%2016%3A31%3A06.png"

BTW: "...from the OP"
"OP"?  (...probably obvious, once I hear it...)
[EDIT: Oh... I'll bet: "Original Poster" - right?]
Yes :)
Can you remove the bookmarks and recreate them ?

---

### Post by vasa1 on 2014-07-04
> **bapoumba said:**
> @vasa : my most sincere apologies, I was wrong. Here is my ~/.gtk-bookmarks. Not sure how I missed it this morning, probably was not awake enough :) ...
None required although I'd like to know what creates or uses ~/.gtk-bookmarks. I thought it would be PCManFM but apparently not! I haven't installed any other file manager other than the qt version of PCManFM (as part of LXQt).

Re. OP's issue, after reading through the bug cited, it looks like the dev has responded quite comprehensively. I also know that the dev of PCManFM is really, really hard at work with the qt5 version of LXQt.

---

### Post by Dennis N on 2014-07-05
Lubuntu 14.04:

No **~/.gtk-bookmarks** on this system, so it's not there by default:

```
dmn@Sydney:~$ find -maxdepth 3 -iname  "*bookmarks*"
./.config/gtk-3.0/bookmarks

```
Only the file in ~/.config/gtk-3.0/ exists, and which I did not create. It has only default folders in ~/ 

```
dmn@Sydney:~$ cat .config/gtk-3.0/bookmarks
file:///home/dmn/Documents
file:///home/dmn/Music
file:///home/dmn/Pictures
file:///home/dmn/Videos
file:///home/dmn/Downloads
```

**~/.gtk-bookmarks** must be created by some other application.

---

### Post by bapoumba on 2014-07-05
Dennis N, do I understand correctly you have not set up any additional bookmark and kept the default ones ? Would you please try to add a new bookmark ?

---

### Post by Dennis N on 2014-07-05
> **bapoumba said:**
> Dennis N, do I understand correctly you have not set up any additional bookmark and kept the default ones ? Would you please try to add a new bookmark ?

Yes to your question.

Then, I added a bookmark for another folder, and the bookmark was added to **~/.config/gtk-3.0/bookmarks** and now appears in the sidepane with the others.

---

### Post by bapoumba on 2014-07-05
Hmm, OK, thanks for the test. ~/.gtk-bookmarks is not specific to user-added bookmarks then :)

---

### Post by Dennis N on 2014-07-05
> **bapoumba said:**
> Hmm, OK, thanks for the test. ~/.gtk-bookmarks is not specific to user-added bookmarks then :)

Just to amplify my response:

I added the bookmark through PCManFM Menu > Bookmarks > Add to Bookmarks.
There is still no file **~/.gtk-bookmarks**.

---

### Post by bapoumba on 2014-07-05
> **Dennis N said:**
> Just to amplify my response:

I added the bookmark through PCManFM Menu > Bookmarks > Add to Bookmarks.
There is still no file **~/.gtk-bookmarks**.

Yes. Both vasa and I have ~/.gtk-bookmarks with user-added bookmarks. You had not, but had not added bookmarks either. The test was to see if you added one bookmark it would create the file. Apparently not, so +1 to maybe another app or action adding this file.

```
bapoumba@SonyBlue:~$ ls -l .config/gtk-3.0/bookmarks
-rw-rw-r-- 1 bapoumba bapoumba 94 avril 30 23:29 .config/gtk-3.0/bookmarks
bapoumba@SonyBlue:~$ ls -l .gtk-bookmarks
-rw------- 1 bapoumba bapoumba 114 juil.  5 16:54 .gtk-bookmarks
```

Avr 30 sounds good for my fresh install and juil. 5 16:54 for today's first boot or may be first time I opened PCManFM. Did not think to have a look at that yesterday..

---

### Post by Dennis N on 2014-07-05
> Apparently not, so +1 to maybe another app or action adding this file.

That is correct. The file was definitely not created by adding my PCManFM bookmark. Look to another application that uses bookmarks.

---

### Post by scott092707 on 2014-07-07
Hey, something really odd...

Yesterday, I was doing experimenting  with PCManFM and Nemo, seeing what happened when I removed one or both  bookmarks files, what happened when I added a bookmark or removed a  bookmark from each FM, etc.

TODAY, when I booted, I found that  EACH FM now displays MY xdg-userdirs in the sidepane/menu/etc., and that  each FM is now using the ~/.config/gtk-3.0/bookmarks file, which now  contains my xdg-userdirs info - WHICH I NEVER SET.  The file date is  today at boot.
I so far can't figure out what was installed yesterday that might have changed things.
/var/cache/apt/archives most recent date was the day before yesterday, and that contained a new linux kernal.
Could something in Linux have changed to change the bookmarks?

-Scott

---

### Post by scott092707 on 2014-07-08
Today, I booted and found that the ~/.config/gtk-3.0/bookmarks file contains the same info, but has today's boot date/time.  So, something is happening each time I boot, that sets the contents of the file to my xdg-userdirs info, and both FMs are automatically using it.  

If I had to guess, each FM had code that would show the xdg-userdirs info, and place it in ~/.config/gtk-3.0/bookmarks file and use that file, but before the new Linux version, the conditions under which it would do so were not satisfied; but now the conditions ARE satisfied, and so the code runs...

I say this, because neither PCManFM nor Nemo appeared to be among the software updates in the last couple of days, and their maintainers were at least indifferent to the concept of placing the xdg-userdirs files in the sidepanes/bookmarks (PCManFM said that (except for Desktop) "all those places are standard XDG special folders. It's just PCManFM  does not add them into sidebar due to one simple reason: the Desktop  folder is near always used while other folders may be but may be not,  it's up to user if he/she needs them or not, so only Desktop is  supported now (above of separator)"
Therefore, I think that something changed in the use of the ~/.config/gtk-3.0/bookmarks file which the FMs automatically caught. 

I will try to search for what the latest Linux kernal for Lubuntu trusty might have changed that affects xdg-user-dirs and the  ~/.config/gtk-3.0/bookmarks file.

If anyone else knows and can explain, I would appreciate it.

---

