---
title: "Chromium Icedtea Java"
date: 2013-02-06
forum: General Help
---

### Post by american.swan on 2013-02-06
1. Install Ubuntu64 yet again. Piece of cake. Joy. Wonderful.
2. Use Chromium. Great. Sing praises to the open source community for all it's greatness.
2a. Libre works well enough. Cool. 
3. Go to peaceful chatroom online. Must install plugin.
4. Now what?  Search Google. See WAY TOO MANY options on Google. Which is correct? Click one at random maybe the first one. Answers vary. I try installing JDK from Software Center. 
5. Another source says don't install JDK from Software Center.
6. Uninstall JDK
7. Click another link on google. Install Ice Tea is the "simple solution" 
8. Response on forum says there are security errors and not to install Java or Icetea at present time or some such thing.
9. (maybe I should install Windows AGAIN)
10. Always wanted to install from source code with that fancy ./configue; make/ make install so I continue on my quest.
11. Find Icetea tarbal.  (Even cutting edge build)
12. Quickly and painlessly open it.
13. ./configure
14. File doesn't exist. Command unknown. Is Ubuntu trash?
15. Of course not. Ubuntu is great. Oh, open INSTALL file. It says to run ./configue and it should work. IT ISN'T THERE MORONS.
16. (considering Windows 7)
17. More Google searching. Oh, some programs don't use ./configue.
18. Maybe there's a perl file or some other file I am supposed to run.
19. Oh, there's a README file. 
20. Open readme file. Says run ./autogen.sh.  Great.
21. Maybe we're going to get this done in the next few minutes.
22. ./autogen.sh Unknown command. You don't have permission!!!
23. Permission?  Oh, great. Chmod
24. ./autogen.sh You don't have permission. WHAT? 
25. GUI!!  Change permissions in the GUI.  Check box. DANGER!! 
26. WHAT?  IT AUTOMATICALLY unchecks the box.
27. CURSE THE DAY UBUNTU WAS BORN
28. CURSE EVERY PROGRAMMER WHO THOUGHT UP THIS NONSENSE.
29. Who's the fool who thought this ./configue was wise.
30. GO to UBUNTUFORUMS to complain loudly and curse some more.
31. PLANS to destroy UBUNTU with Windows 7 if I don't get a good explanation.

---

### Post by Stonecold1995 on 2013-02-07
Are you sure configure isn't there?

[[IMG]http://www.pictureshack.us/thumbs/25278_configure_is_there.png[/IMG]](http://www.pictureshack.us/images/25278_configure_is_there.png)

It should only be download from the official source: [http://icedtea.wildebeest.org/download/source/](http://icedtea.wildebeest.org/download/source/)

---

### Post by american.swan on 2013-02-07
I will see if I can find the place I downloaded it from.

---

### Post by american.swan on 2013-02-07
I was here.

[http://icedtea.classpath.org/wiki/IcedTea-Web#Plugin]("http://icedtea.classpath.org/wiki/IcedTea-Web#Plugin")

I guess I was in the wrong place.

I will delete what I downloaded and use your link.

---

### Post by american.swan on 2013-02-07
what is "atool"?  Thanks.

---

### Post by american.swan on 2013-02-07
New question. My download doesn't have "green" executable like yours. Why? I have to set them executable manually. How do I know which ones should be executable on any given download?  Thanks.

---

### Post by american.swan on 2013-02-07
I'm doing "sudo chmod -x ...." and it's REFUSING to be "green"/ executable. Seriously angry again.

---

### Post by american.swan on 2013-02-07
anyways....ignoring chmod...I was able to make configure "green".

I ran configure and it tells me a couple things.

One...I can't compile ecj natively. Maybe I don't have to.
Two...missing JDK home directory.  I will attempt to install JDK now from aptitude( for some reason i don't fancy apt-get even though it's fine)

---

### Post by american.swan on 2013-02-07
aptitude says openjdk-7 is installed.

---

### Post by american.swan on 2013-02-07
I'm searching google...can't find a solution to JDK home directory not found.  I tried an ln option, but it failed on my machine.

---

### Post by american.swan on 2013-02-07
[http://forums.gentoo.org/viewtopic-t-893726.html](http://forums.gentoo.org/viewtopic-t-893726.html)  

Found this, but it doesn't help me.

---

### Post by Stonecold1995 on 2013-02-08
> **american.swan said:**
> what is "atool"?  Thanks.
atool is a package which automatically runs the correct extraction program based on the filetype.  So if you run "atool -x somefile.tar.bz2" it will automatically run it through bzip2 and tar.  If you run "atool -x somefile.rar" it will run it through rar, etc.  That way you don't have to remember the correct command for each utility (for example, you have to use "bzip2 -d somefile.bz2" to extract it, but with rar you have to use something like "rar x somefile.rar", etc).

> **american.swan said:**
> New question. My download doesn't have "green" executable like yours. Why? I have to set them executable manually. How do I know which ones should be executable on any given download?  Thanks.
Post the output of the command "alias".  It should have the line "alias ls='ls --color=auto'".

> **american.swan said:**
> I'm doing "sudo chmod -x ...." and it's REFUSING to be "green"/ executable. Seriously angry again.
Well there's your problem!  First of all, you don't need to use sudo (I think it might mess up permissions as well), and second of all, running "chmod **-**x" REMOVES executable permissions.  You want to run "chmod **+**x" instead, if the file isn't already executable.


As for your other posts, you seem to be confusing Java and web Java.  If you have Java installed, all that allows you to do is run Java program's you've *downloaded*, by running "java -jar program.jar".  If you want it to run on Chromium, you'll need web java as a plugin instead.

And protip: You can edit your posts if you have more information.  There's no need to post multiple times in a row.

---

