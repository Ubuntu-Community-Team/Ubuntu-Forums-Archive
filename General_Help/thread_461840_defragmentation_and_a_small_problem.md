---
title: "defragmentation and a small problem"
date: 2007-06-02
forum: General Help
---

### Post by BastiH on 2007-06-02
Hi,

congratulations for this software! It works really great on my Amilo Notebook (Centrino Pentium M).

I have two questions:

First: can I do a normal defragmentation with windows? Will this affect the Ubuntu/Wubi installation in any way?

Second: when I boot Ubuntu the normal Ubuntu load screen appears. Then it removes and I see a black screen with many status messages. Most of them returns an Ok but one shows a red Fail message. I am not able to read which operations fails I think its something with the virtual discs and "file not found". The screen disappears very quick and Ubuntu starts. Is there any possibility to see a log file or pause the boot sequence so I can read what fails?

Thank you very much and please forgive my bad englisch.
Bastian

EDIT I use the test 3 release and mit Host OS ist Windows XP Media Center Edition (so it is XP Pro)

---

### Post by minhmeoke on 2007-06-04
As far as I know, defragmentation in Windows should not affect Wubi, but I have not tried it yet...

As for the "file not found" error, this is might be a problem with mounting the extra.virtual.disk swap partition. It is not a critical problem, but it might reduce Wubi's performance, since it will not be able to use virtual RAM (on your hard drive), only physical RAM. See this post for more info: [http://ubuntuforums.org/showthread.php?t=460457&highlight=virtual.disk.extra]("http://ubuntuforums.org/showthread.php?t=460457&highlight=virtual.disk.extra")

Log files are stored in /var/log
See this post on how to view them: [http://ubuntuforums.org/showpost.php?p=2780570&postcount=6]("http://ubuntuforums.org/showpost.php?p=2780570&postcount=6")

In any case, please report your findings here on the forum. Thanks.

---

### Post by ago on 2007-06-04
extra.virtual.disk does not affect performance and you can safely ignore the error. It is an extra disk to expand disk capacity later on if needed. So at boot we look for it and if there is none an error is raised.

---

### Post by msobel on 2007-06-07
running xp when I try to defragment my disk, i get one file 

21              5.86 GB         \wubi\disks\home.virtual.disk

which won't defragment.  it's big enough so that in theory I should defrag every time.     Can I erase it or what ?

Will it be automatically recreated ?

---

### Post by Computer Guru on 2007-06-07
I believe that this *is* the Wubi intstall itself - you don't want to delete that!

What program are you using to Defrag? DiskKeeper and the Windows Defrag program aren't very good, I recommend PerfectDisk, it's awesome.

---

### Post by msobel on 2007-06-07
I am using native xp defrag

---

### Post by ecology2007 on 2007-06-07
21 fragments for such a file is not problematic at all. That makes an average size of 250 Mb per fragment. It won't hurt the performance in any way.

---

### Post by Computer Guru on 2007-06-07
If only someone would port Reiser4 to Windows - no more defrag :D

---

### Post by Joshiii-Kun on 2007-06-07
You could also use [JkDefrag]("http://www.kessels.com/JkDefrag/"). It works like a charm ^_^

---

