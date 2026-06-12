---
title: "Firefox - opening symlinks to local files"
date: 2018-09-01
forum: General Help
---

### Post by palipeaublasee on 2018-09-01
This is on Xubuntu 16.04, Firefox 61.0.1

I am baffled by a particular Firefox behaviour with respect to opening html files via symlinks.

I have a bunch of html files, among other types, in (2) two fairly deep tree structure (filesystems), with several symlinks, spread out within the same two structures, pointing to those html files.  Whether the symlinks are relative or absolute doesn't seem to affect the outcome.

**Most of my symlinks cannot be opened by Firefox, either by using the menu's "Open File" (Ctrl+O), or by sliding the symlink, in my File Manager, onto the firefox main viewing area.**

Frankly I do not know when it started.  A few days, weeks, I'm not sure.  In fact there is a slight chance that it's always been that way but I failed to notice. I've had this setup:

    home: ext4    
    storage: ntfs

for a long time, this has not changed so it can't be part of the cause..., unless the mozilla people changed something.


Firefox's "Web Console" shows absolutely nothing when an unsuccessful attempt is made at opening a link to a file.  Nothing happens except for a little black dot that moves back and forth on the tab's heading, showing that something is happening.  Nothing happens (more than 5 min) until I close the tab.  I have done this many times with many different symlinks.

As far as I can tell the symlinks that **can** be opened are all in my /home directory, pointing to html files that live on the same volume/filesystem.  Firefox opened some test files & symlinks I created, both relative and absolute links.

Those that cannot be opened are all either on the ntfs volume or point to a file that is, and what surprises me very much is that even the **symlinks on that volume that point to files on that same volume also fail to open**.  Surprised because I would have perhaps blamed a cross-system problem.  It's not:

    home-file-link     ->     home-file        = OK
    store-file-link     ->     home-file        = fail
    home-file-link     ->     store-file        = fail
    store-file-link     ->     store-file        = fail


The other aspect of this situation which puzzles me is that all these symlinks that cannot be opened by Firefox **-can-** be by double clicking on them in the file manager, or still in file manager by right clicking on the symlink and selecting Open With > select browser (Firefox).  Also they can be opened by invoking [FONT=courier new]$ firefox /path/symlink[/FONT] without problem or error message in the terminal.

Is the failure to open those links directly from within Firefox or by sliding the file in the file manager normal (by design) ?

Why the discrepancy between that behaviour and the successful opening of those same links using double clicking or "Open File" (Ctrl+O) in the file manager ?


Thanks.

---

### Post by HermanAB on 2018-09-01
Hmm, I have three ideas for you: 
1. You should launch firefox from a terminal, to see the error messages returned when it tries to follow the links.

2. Symlinks are horrid things.  When you delete the file, broken symlinks remain on disk.  It is generally better to use hard links.  A hard link is an additional directory entry pointing to the same file and are managed automatically.   The actual file will only be deleted once the last hard link is deleted.  So you can think of hard links as smart links, while the others are soft in the head links.  

3. You can also deduplicate your system with a program called - wait for it - drum roll -  'hardlink', which on my systems save gigabytes of space.

---

### Post by Holger_Gehrke on 2018-09-01
@HermanAB: Yes, symbolic links are not so great, but if you're linking across filesystems - as is the case here - they are the only game in town.

@[COLOR=#000000]palipeaublasee: I tried to reproduce the error but couldn't. Symlinks from my $HOME (internal SATA, ext4) to html files on ntfs (external USB2) opened just fine in Firefox either through the file open dialog or by drag'n'drop. But my system is not Ubuntu 16.04, it's XUbuntu 18.04. [COLOR=#000000]Firefox i[/COLOR]s the same version . So the problem might be due to any of the differences between our two systems. HermanAB's idea of looking for errors in the terminal is a very good one.

Holger
[/COLOR]

---

### Post by Impavidus on 2018-09-01
Have you verified that the problem only happens with symlinks, so you can open the files on your storage partition in firefox directly?

---

### Post by palipeaublasee on 2018-09-01
@Impavidus - yes, never any problem opening the files themselves in either /home or /storage.

---

### Post by palipeaublasee on 2018-09-01
Thank you for your replies.

The symlinks are opened normally using:  [FONT=courier new]**$ firefox /path/symlink**[/FONT]
so there's nothing from the terminal.

Hard links cannot jump filesystems, as Holger_Gehrke points out, but also you can't hard link to directories and many of my links are.

-----

I've done some reading and done tests with hard links.  I use them in very specific settings only.  The relation between two files is what I want to understand and use efficiently in general.  In practice this relation is more difficult to find than with symbolic links, so far for me anyway. [FONT=courier new]**$ ls**[/FONT] and [FONT=courier new]**$ find**[/FONT] can show you how many other files are linked to it/inode for each file listed, but from there it seems laborious.  There is a utility called "[FONT=courier new]**symlinks**[/FONT]" that lets you quickly find symlinks recursively, what they point to, and their state (relative, absolute, dangling,  etc.).  Along with various [FONT=courier new]**$ ls**[/FONT] options and simple bash stuff I get around ok.  I'm trying to find a good balance for me between GUI and CLI opreations, but I am apparently slow and going back and forth is not the best.  Practice, practice, practice.

As it is I use the file manager more than most people. These links help me to find my way around faster and stay in a better mood.  I write a lot on different subjects and in my own projects, so I can't have several copies of notes, or activities I document and update regularly.  I'm still learning how to use them, and learning the management cost.  I'ts mainly for my own documents management, but also for the general organisation of my system-partitions-backups-scripts etc.  I use Thunar as a file manager, the default in Xubuntu I think.  Maybe other file managers have options related to displaying hard links info, I don't know.

---

### Post by palipeaublasee on 2018-09-01
@HermanAB

I can't find the site for the 'hardlink' program you mention in 3.

It looks like a backup scheme.  If that's what it is, then I don't need that.  I'm already working on a general backup solution using a series of **rsync** commands in a script.  I've figured out for the most part how to handle links in my backups, and all is well.  I do lots of testing as I go about it, and so far all is good.

Right now I'm just curious about this strange behaviour, wondering if it's normal or not.  Learning to use a Unix like os also is sort of a hobby for me, besides being my main work environment.

---

