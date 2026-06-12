---
title: "Odd gnome response to &quot;ln -s&quot;"
date: 2016-10-27
forum: General Help
---

### Post by Jeff_Rockel on 2016-10-27
I am trying to use "ln -s" to create Desktop links in gnome to access Libre documents. Let's say I have a spreadsheet named "Journal Web Blog.ods" and I want a symbolic link named "JWB" on the Desktop. I tried the following to accomplish the command in one line:

ln -s 'Journal Web Blog.ods' ~/Desktop/JWB

However, this created an object that when opened yields the message "The link "JWB" is broken. This link cannot be used because its target "Journal Web Blog.ods" doesn't exist." A look at the properties indicates Type: Link (broken) (inode/symlink)

What I thought I needed to do was execute two commands:

ln -s 'Journal Web Blog.ods' ./JWB
cp JWB ~/Desktop/

However, this copy is not a symbolic link, it is a full spreadsheet document (as indicated by the Properties). A link created under Ubuntu 14.04 on the Desktop shows Type: Link to OpenDocumentSpreadsheet

What does gnome want to create a symbolic link?
BTW... I am unable to use Files (Nautilus) because it does not provide a right-click Make Link command any more in Ubuntu 16.04.

---

### Post by WedgeHG on 2016-10-27
To see why this isn't working, use the command:

```

ls -l ~/Desktop/JWB

```

You'll see that the JWB link on the desktop points to the file 'Journal Web Blog.ods' ... also on the desktop. It doesn't have a correct path to the real file since your original file isn't actually on the desktop.

You can fix this two ways:

1. Include a full path to the file when you're making the link. For example, if your file is in your home directory you could do

```
ln -s "$HOME/Journal Web Blog.ods" ~/Desktop/JWS
```

2. Use a relative path for the link **relative to the link**. Again, assuming that your file is in your home directory, you could do this:

```
ln -s '../Journal Web Blog.ods' ~/Desktop/JWS
```

This works because the real file is in the parent directory of Desktop.

---

### Post by deadflowr on 2016-10-27
> BTW... I am unable to use Files (Nautilus) because it does not provide a right-click Make Link command any more in Ubuntu 16.04.
Yes it does.

Post the results of:
```
dpkg -l | grep nautilus | awk '{print $1,$2}'
```
to see whether or not something isn't installed properly.

I know it exists in 16.04 and up, because I inadvertently make links all the time.

---

### Post by Jeff_Rockel on 2016-10-28
Thank you WedgeHG & deadflower. [I have never come up with a good user name/handle for myself :-(]

First suggestion works great (of course). I am a convert from Windows to Linux and trying very hard to get into the right mindset. (I'm old enough to have used DOS so it's not completely new.) I now understand the need to provide the full path when generating the link. 'ln' does not make assumptions regarding the current command location as other commands might. Likewise, if I use ```
./source ~/Desktop/JWB
``` it won't work because the link becomes ```
./source
``` which doesn't exist. Got it!

Regarding nautilus:
 
```
[FONT=courier new]jeff@Zeus:~$ dpkg -l | grep nautilus | awk '{print $1,$2}'[/FONT]
[FONT=courier new]ii libnautilus-extension1a[/FONT]
[FONT=courier new]ii nautilus[/FONT]
[FONT=courier new]ii nautilus-data[/FONT]
[FONT=courier new]ii nautilus-dropbox[/FONT]
[FONT=courier new]ii nautilus-sendto[/FONT]
[FONT=courier new]ii nautilus-share[/FONT]
[FONT=courier new]jeff@Zeus:~$[/FONT]
```

Perhaps another clue, my Files GUI has the Close/Maximize/Minimize controls in the upper right. They were always in the upper left per standard Ubuntu. (Only Chrome has Windows like controls.)
If necessary please help me understand how I can do a clean install of the latest nautilus app.
Again, thanks.

---

### Post by deadflowr on 2016-10-28
Mea culpa.
I see that nautilus in 16.10 does not have make link.
Nautilus in 16.04 is version 3.14 (versionized as 3.18is3.14, comically)
16.10 jumps all the way to 3.20.
So somewhere between the two, make link was pulled, or hidden somewhere(?).

Newer nautilus' for 16.04 are available through gnome ppa's, did you by chance add one?
Or is it 16.10, and somehow you mistakened it as 16.04?

Perhaps look at
```
apt-cache policy nautilus
```

---

### Post by CantankRus on 2016-10-28
In 16.10 there is no right click "make link" item but it is still available via menu > edit 
or ctrl+m.
In regards to nautilus having buttons on the right, I had the same thing in 16.04.
Without knowing I had updated to the nautilus version 1:3.18.5-0ubuntu1~xenial1 which was in the budgie-remix ppa.
Just purged ppa and now....
```
**[COLOR="#006400"]glen@Xenial:~$[/COLOR] apt policy nautilus**
nautilus:
  Installed: 1:3.18.4.is.3.14.3-0ubuntu5
  Candidate: 1:3.18.4.is.3.14.3-0ubuntu5
  Version table:
 *** 1:3.18.4.is.3.14.3-0ubuntu5 500
        500 [http://ftp.iinet.net.au/pub/ubuntu](http://ftp.iinet.net.au/pub/ubuntu) xenial-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     1:3.18.4.is.3.14.3-0ubuntu4 500
        500 [http://ftp.iinet.net.au/pub/ubuntu](http://ftp.iinet.net.au/pub/ubuntu) xenial/main amd64 Packages
```

---

### Post by Jeff_Rockel on 2016-10-31
Thank you all. Here is my policy output. I see significant differences probably due to my gnome update.
```
jeff@Zeus:~$ apt-cache policy nautilus
nautilus:
  Installed: 1:3.18.5-0ubuntu1~xenial1
  Candidate: 1:3.18.5-0ubuntu1~xenial1
  Version table:
 *** 1:3.18.5-0ubuntu1~xenial1 500
        500 http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu xenial/main amd64 Packages
        100 /var/lib/dpkg/status
     1:3.18.4.is.3.14.3-0ubuntu5 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
     1:3.18.4.is.3.14.3-0ubuntu4 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
```

Also, I ONLY have a Files menu in the menu bar. No Edit menu. And Ctrl-m has no effect.

So, can you suggest how I bring a good nautilus back into my environment? Preferably an older version that has the right click "Make link". I haven't treaded into these waters yet.

---

### Post by mcduck on 2016-10-31
I haven't upgraded to 16.10, but maybe the old drag&drop with middle mouse button still works? That should give yo a popup menu asking if you want to copy, move or link the file...

---

