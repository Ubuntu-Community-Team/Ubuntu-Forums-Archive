---
title: "Remove Inode Directory"
date: 2017-05-06
forum: General Help
---

### Post by vs-ruthless on 2017-05-06
Hi,

I noticed yesterday that I had duplicate directories within my mount directory, looking at the properties it's an Inode folder?

I added an additional 1TB hdd the day before and called it LittleTB1 this is the one that has duplicated, I also noticed that I had another inode folder as well 2441D7961B6C5CE8. 

I renamed the hdd to LTB1 hoping that would fix my issues, but has just made it worse.

Please note all three drives are additional storage drives on my media server.

```

ls -il
1201874 drwxr-xr-x 2 root root 4096 Apr 28 16:35 2441D7961B6C5CE8
1210053 drwxr-xr-x 2 root root 4096 Apr 27 16:31 LittleTB1
1201873 drwxr-xr-x 2 root root 4096 Apr 28 14:46 LIttleTB1
      5 drwxrwxrwx 1 root root 4096 May  4 09:16 LTB1
      2 drwxrwxrwx 6 root root 4096 Apr 25 22:51 Storage
      5 drwxrwxrwx 1 root root 8192 May  4 19:41 W7-Storage

```

Please can someone advise me on whether or not I should delete these directories and if so how do I remove them.

---

### Post by &amp;KyT$0P# on 2017-05-06
It doesn't look duplicated.  You have one folder named "LittleTB1" (lowercase i) and another named "LIttleTB1" (uppercase I).  The filesystem is case-sensitive.

If the directories are empty and you don't need to mount anything there, I would say yes it's likely safe to remove them.  And the safest way to do that would be to use [FONT=Courier New]rmdir -v[/FONT] from the command line.

---

### Post by vs-ruthless on 2017-05-07
All additional folder now removed.

Thank you  				 				 					 						 	[**[COLOR=#000000]halogen2[/COLOR]**]("https://ubuntuforums.org/member.php?u=2034672")

---

### Post by &amp;KyT$0P# on 2017-05-07
You're welcome. :KS

---

