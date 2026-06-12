---
title: "Find (and delete/move) ALL files matching string recursively"
date: 2008-04-04
forum: General Help
---

### Post by Hoza on 2008-04-04
Heya folks,

I've been searching for a solution and I'm not really figuring out what to search for so I decided to finally post on the Ubu boards.  I'm very happily runing 7.10 with my old XP install sitting very dormant on the hard drive -- yay!  I'm stoked, to say the least.

I do a lot of Web development and get a ton of files from collaborators working on Mac boxes.  They regularly send me big batches of files that have the immensely annoying "two-of-everything" files, where there's the actual file and then the (directory listing?) file that starts with "._" like "._banner.jpg" along with the "banner.jpg" file.

I've done the brute-force method for a while in WinXP where I went through and deleted all those annoying files, but my experience with Linux (sporadic) over the years tells me there's likely a quick single-line command that would allow me to locate and delete/move/whatever all those suckers in one swoop.  This needs to be recursive from a particular directory with many subdir's if possible.

Anyone know one of the ways this could be done?

Example: Select all the files beginning with "._" and delete them in this tree:
  ./dir/sub1/file1.txt
  ./dir/sub1/._file1.txt
  ./dir/sub1/file2.txt
  ./dir/sub1/._file2.txt
  ./dir/sub2/file.txt
  ./dir/sub2/._file.txt
  ./dir/sub2/subsub/file.txt
  ./dir/sub2/subsub/._file.txt
  (... etc, ad infinitum)

Thanks for any help... I've got dozens of directories with hundreds of files (and their duplicates) to sort out.

Thanks!

---

### Post by Hoza on 2008-04-04
(Have I really been a member here since mid-2006 and this is my first post??!?  Wow.  I'm the definition of a lurker, apparently.  Goes to show you, though, that these boards rock since I've always found my answers before having to post!)

...and yes, this post is just to get another bean.  Shameful, I know.  :P
:popcorn:

---

### Post by bodhi.zazen on 2008-04-04
use find

[http://www.hccfl.edu/pollock/Unix/FindCmd.htm](http://www.hccfl.edu/pollock/Unix/FindCmd.htm)

---

### Post by Hoza on 2008-04-04
> **bodhi.zazen said:**
> use find

[http://www.hccfl.edu/pollock/Unix/FindCmd.htm](http://www.hccfl.edu/pollock/Unix/FindCmd.htm)
Terrific, thanks!  I can see some tinkering with find is overdue.  :)  

Here are the commands I'm using that seem to be doing the trick: (Those reading this later, please do your own research & tests -- don't hold me accountable if something goes wrong for you!)

Test output of the find command string from current directory:
```
find . -name '._*'
```

Make a backup of the find results and confirm what find... found -- because I'm nervous/cautious/paranoid:
```
sudo find . -name '._*' -exec tar -Pvrf ~hoza/old_mac_files.tar {} +
```

Do the burly delete job:
```
sudo find . -name '._*' -exec /bin/rm -f '{}' +
```

Wow... awesome.  Thanks!!  All those directories are nice and tidy now.  :biggrin:

---

