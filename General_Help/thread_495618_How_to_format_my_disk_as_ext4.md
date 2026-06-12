---
title: "How to format my disk as ext4"
date: 2007-07-08
forum: General Help
---

### Post by gabeyg on 2007-07-08
Questions:
1. How to format my disk as ext 4 in newest feisty kernel (2.6.20-16) (I know this file system is experimental, so please do not say about its reliability.) with extent feature
2. How to test ext4 without formatting ext3 drive
--More question
3. When I try to port the program to other architecture or operating system, do I just have to download and compile it or is there more to that? (I only used x86, so, I'm not good at knowing other system compatibiliy.)
4. This is just a question: Is there a way to compile source code in Windows?
5. Can I use Beryl without proprietary drivers
7. Can I install Xen and make host os as DragonFlyBSD and guest as ubuntu?
8. I heard in [http://ubuntuforums.org/showthread.php?t=461378&highlight=ubuntu+ultimate&page=16]("http://ubuntuforums.org/showthread.php?t=461378&highlight=ubuntu+ultimate&page=16") that ubuntu ultimate source code is based on the bash script (sh file). How can I compile it.
9. How to make source code into .deb
10. --This if you know it please help me but not important question: Does DragonFlyBSD has Linux compatibility mode?
11. what is major difference between Hybrid and Monolithic kernel?
Thanks.

---

### Post by Loffe_ on 2007-07-08
Those where many questions.

3. Porting a program to a different architecture should only need a recompile( as long as you have all dependencies installed). Porting to another os usually requires more work.
4. Of course you can compile source code on windows. That's how windows programs are compiled. Or do you want to compile Linux programs on Windows? Never tried myself...
5. Depends totally on your graphic card. Beryl needs 3d drivers and if you are lucky you can go open source. 
Note: Beryl is not getting any more updates. The Compiz and Beryl communities have merged. If you think you want beryl, it is really Compiz-Fusion you are looking for.
8. Bash script are script and don't need to be compiled. To execute it make sure it's executable and run it like this.
```

$ chmod +x myscript.sh
$ ./mysqcript.sh

```
11. [http://en.wikipedia.org/wiki/Hybrid_kernel](http://en.wikipedia.org/wiki/Hybrid_kernel) and [http://en.wikipedia.org/wiki/Monolithic_kernel](http://en.wikipedia.org/wiki/Monolithic_kernel)

---

