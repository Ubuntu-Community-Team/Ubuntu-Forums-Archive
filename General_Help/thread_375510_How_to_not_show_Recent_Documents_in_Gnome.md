---
title: "How to not show Recent Documents in Gnome"
date: 2007-03-03
forum: General Help
---

### Post by fakie_flip on 2007-03-03
Here are directions in Ubuntu under System>Help>System Documentation.

```
Hide Recent Documents in the Places menu

To hide Recent Documents from the Places menu, open a terminal and run the command:

chmod 400 ~/.recently-used

To show the menu again, run the command:

chmod 600 ~/.recently-used
```

It does not work. I even tried making the file owned by root and have chmod 000 permissions. I found out that the ~/.recently-used file is not the file that stores the history because I deleted it, and my recent documents still showed in Places>Recent Documents.

---

### Post by tbodine on 2007-03-03
I did that and my Recent Documents menu faded so I can't go into the actual menu, I think that's what it's supposed to do..

---

### Post by fakie_flip on 2007-03-04
After you open some more files, they will show in "Recent Documents" again.

---

### Post by Septicaemia on 2007-07-01
Same thing happening here, is there real fix available?

---

### Post by Brucevdk on 2007-07-01
> **Septicaemia said:**
> Same thing happening here, is there real fix available?

I looked a little bit into it. The XML file in which the recent document history seems to be stored is *.recently-used.xbel*, Changing the permissions (or even changing the owner to root) doesn't prevent anything because for some reason the permissions/owner are set back to the user no matter what you try. 

There's no real fix available (though I presume there will be shortly), the workaround as described in bug report #87472 at Launchpad is to remove the file and create a directory instead.
```

rm ~/.recently-used.xbel
mkdir ~/.recently-used.xbel

```

Here are the relevant bug reports:
[LIST]
[*][Bug 305325 &#8211; request to add option to disable 'Recent Documents' lists.]("http://bugzilla.gnome.org/show_bug.cgi?id=305325")
[*][Using chmod 400 ~/.recently-used does not work for the .xbel file]("https://bugs.launchpad.net/ubuntu/+source/ubuntu-docs/+bug/87472")
[/LIST]

Turns out this was already discussed in other threads:
[LIST]
[*][Keeping recent documents cleared in Edgy]("http://ubuntuforums.org/showthread.php?t=293018") ([the post]("http://ubuntuforums.org/showpost.php?p=2710865&postcount=17") of the person who thought up of the workaround)
[*][HOW-TO: Enable and Disable the Recent Documents Menu in Gnome]("http://ubuntuforums.org/showthread.php?t=91154")
[/LIST]

---

### Post by ElliottMarlow on 2007-07-27
> **Brucevdk said:**
>  There's no real fix available (though I presume there will be shortly), the workaround as described in bug report #87472 at Launchpad is to remove the file and create a directory instead.
```

rm ~/.recently-used.xbel
mkdir ~/.recently-used.xbel

```


Worked for me.

---

### Post by nowshining on 2007-09-26
rm and mkdir worked for me also - it's greyed out. :) and I have Gutsy will all updates - the other way didn't work at all. :P

---

### Post by /etc/init.d/ on 2007-09-26
The ~/.recently-used.xbel didn't exist pre-Edgy, in Dapper there was just ~/.recently-used.  Unfortunately, just about every app that isn't GTK (and even some that are) will have their own history files.  Best bet is to go through each application directory (the dirs starting with a period) and set any history file to read-only.

---

### Post by retrow on 2007-11-15
```

rm ~/.recently-used.xbel
mkdir ~/.recently-used.xbel

``` Nice fix! Removing .recently-used.xbel and replacing it with a directory worked in Gutsy too.

---

### Post by dolphinsonar on 2007-12-31
Thanks that did it for me!

```

rm ~/.recently-used.xbel
mkdir ~/.recently-used.xbel

```

---

### Post by Belerophon on 2008-02-10
Creating that directory worked for me too! Thanks :)

I'm new to Linux, but I find it odd that "something" in my system could change in that way my file permissions:
- while trying to disable recent docs, I changed the owner of the .xbel file to *root*, with only read permissions. Next thing I see after opening some document, is that the file had completely changed, the owner was me again and it had write permissions!?
How did something owned by the *root* could be changed in that way?...
The problem is solved, but I still would like to understand this...

Thanks.

---

### Post by Brucevdk on 2008-06-19
> **Belerophon said:**
> How did something owned by the *root* could be changed in that way?...
The problem is solved, but I still would like to understand this...

I was just browsing through my post history and noticed your message (above), even though it might be a little late I thought I'd answer your question (publicly just in case anybody else is wondering the same). 

> To delete a file requires both write (to modify the directory itself) and execute (to stat() the file's inode) on a directory.  *Note a user needs no permissions on a file nor be the file's owner to delete it!* 

Emphasis mine. I couldn't manage to use *lsof* to monitor .recently-used.xbel to find out which process deletes the file (perhaps related to [Bug #192734](https://bugs.launchpad.net/ubuntu/+source/lsof/+bug/192734)) but here's the output from *inotifywatch*:

```

$ inotifywatch .recently-used.xbel 
Establishing watches...
Finished establishing watches, now collecting statistics.
total  delete_self  filename
2      1            .recently-used.xbel

```

---

