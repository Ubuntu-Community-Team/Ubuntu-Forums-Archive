---
title: "Lost Pictures?"
date: 2008-01-03
forum: General Help
---

### Post by crazytiredguy on 2008-01-03
Hello all, thanks for the help in advance.  I posted previously with some Ubuntu problems that everyone was very helpful in resolving.  Today's problems are about a different computer.  My wife has a Dell Inspiron 8600 that was running Windows XP Pro.  She had several pictures of our newborn son on there.  She told me she backed them up to our other computer before loaning it out to her brother.  She missed a file she'd placed elsewhere and her brother thought he'd be helpful and put Gutsy on her laptop without calling us or asking.  Now we've lost our only copies of several pictures of our infant son (1st bath, 1st day alive etc.) and I was hoping there was some way.  He formatted our entire harddrive using ext3.  I hoped it would wind up in the lost + found folder but it is empty now (though it says something about having 6 gigs of free space or something).  Is there anything that can be done?

---

### Post by sonofusion82 on 2008-01-03
try google for file/disk recovery tool.
i have accidentally formatted my USB flash drive before too. PC inspector data recovery [http://www.pcinspector.de/Sites/file_recovery/info.htm?language=1](http://www.pcinspector.de/Sites/file_recovery/info.htm?language=1) seems to work well for me but you may need to try with different options available to see which works well.
first thing is don't touch that hard disk.. booting into gutsy may risk more files being unrecoverable... remove it and place it in another PC or boot from another drive and try to run various recovery tool to see how much you can recover.
if you have the cash and those pictures are too important to you, you can perhaps send it to those profesional data recovery services.
good luck.

---

### Post by crazytiredguy on 2008-01-04
Thank you.  I'm new to Linux and I have no idea what to do.  I've downloaded the program called testdisk (it looks like my best bet of recovering pictures) but from there I'm really struggling even after reading the instructions given.  Is it possible to tell me the code I need to type and where?  I know in terminal, but looking at the instructions that came with the program it looks like at some point I need to change away from the terminal but I don't know where to go from there.  Thanks.

---

### Post by bodhi.zazen on 2008-01-04
[http://www.linux.com/articles/56588](http://www.linux.com/articles/56588)

---

### Post by crazytiredguy on 2008-01-04
Thanks for the link.  Whenever I try to open the executable using Wine nothing happens, it just sits there.  I've downloaded and extracted the files.  Anything else to do?

---

### Post by bodhi.zazen on 2008-01-04
testdisk is in the ubuntu repos, you do not need wine :

```
sudo apt-get install testdisk
```

---

### Post by crazytiredguy on 2008-01-04
Thanks.  How do I run it from here?

---

### Post by bodhi.zazen on 2008-01-04
Sorry, you will want to try photorec

You understand you may not be able to recover the files as they may well have been over written ?

You should not be running the computer from the hard drive, you should work from a live CD.

Installing testdisk also installs photorec

The link I gave you gives step-by-step directions

what step are you on ?

---

### Post by crazytiredguy on 2008-01-04
Actually, I got it running last night (after about 2 hours of frustration) and then it ran for about 4 hours.  I was able to recover 90% of my .jpg files, so I can't complain too much.  Thanks again for all the help.

---

