---
title: "Preserving Dell Media Direct with Ubuntu"
date: 2006-12-19
forum: General Help
---

### Post by SmallShoes on 2006-12-19
So I've read a few other threads but haven't really found an answer yet. I have a Dell Inspiron E1505 with Windows XP Media Center Edition. There's a MediaDirect button on these laptops which allows you to skip the complete boot of the OS and load a Media Center where you can watch DVD's etc.  

Now many may think it's not worth all that much but I'd like to try to keep it. I've installed Ubuntu once already and when GRUB overwrites the MBR the button doesn't work anymore. Actually it totally crashed my system - I had to restore the XP MBR and then repartition my drive back to how I had it when I took the notebook out of the box - back to square one. 
I'm trying to figure out if I can avoid having GRUB overwrite the MBR because apparently that's how the MediaDirect button works.
(see this thread: [http://www.notebookforums.com/thread159964.html]("http://www.notebookforums.com/thread159964.html"))

I know one person was trying to create a GRUB entry for the MediaCenter partition but had no luck. (see this thread: [http://ubuntuforums.org/showthread.php?p=1544946]("http://ubuntuforums.org/showthread.php?p=1544946")) 

I know people rave about how great GRUB is but I don't really mind having it on the same partition as my Ubuntu install so I can preserve the original MBR and have the MediaCenter button still work (hopefully).  So how do I do an install of Ubuntu with GRUB on the same partition? And after that how do I boot into Ubuntu if GRUB is on the same partition? 

And as if that wasn't enough one more question - This ([http://www.goodells.net/dellrestore/mediadirect.htm]("http://www.goodells.net/dellrestore/mediadirect.htm")  )and other sites say that the MediaDirect partition is around 2 gigs and the Dell Restore is about 3.7 gigs. However, [this]("http://ubuntuforums.org/showthread.php?p=1544946") thread says the MediaDirect partition is around 4 gigs. Any way for me to tell which partition is which? I'd like to avoid reinstalling with the MediaCenter disk (lord knows what that'll do to my MBR). 
Too many questions?
Help?

---

### Post by ndpete on 2007-01-04
I haven't tried this yet but i think this article could help you:

 [How do I dual boot Windows and Linux from NTLoader?]("http://www.windowsitpro.com/Article/ArticleID/15683/15683.html?Ad=1")

---

### Post by golem3 on 2007-01-21
BUMP.

I really want to know how to preserve MediaDirect. Please help.

---

### Post by houstonbofh on 2007-01-21
> **golem3 said:**
> BUMP.

I really want to know how to preserve MediaDirect. Please help.

If you install Ubuntu as posted about in "How do I dual boot Windows and Linux from NTLoader?" you will not touch the MBR, and load from the NT loader.  This means your Media stuff will be intact.

---

### Post by golem3 on 2007-01-28
> **houstonbofh said:**
> If you install Ubuntu as posted about in "How do I dual boot Windows and Linux from NTLoader?" you will not touch the MBR, and load from the NT loader.  This means your Media stuff will be intact.

But will Media Direct be able to read material from an EXT3 partition, namely the Ubuntu primary disc?

---

### Post by houstonbofh on 2007-01-30
> **golem3 said:**
> But will Media Direct be able to read material from an EXT3 partition, namely the Ubuntu primary disc?
You would have to ask Dell, but I seriously doubt it.  I am sorry but I can't help with Media Direct support. :)

---

