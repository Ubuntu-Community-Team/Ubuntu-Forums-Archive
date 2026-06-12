---
title: "Jboss"
date: 2008-05-29
forum: General Help
---

### Post by anderskitson on 2008-05-29
[FONT="Arial"]I am trying to install jboss from source, and it keeps failing. I have build-essential installed. I navigate to the build folder and type > sh build.sh
It gives me this output at the end.

> BUILD FAILED
/usr/local/jboss-4.2.2.GA-src/connector/build.xml:200: Compile failed; see the compiler error output for details.
Now I went to the file build.xml line 200, I am assuming thats what the 200 stands for, this is what was there
>  failonerror="${javac.fail.onerror}">
I am not sure where to find the compiler error output, or what to do to get this to install properly? Any help would be great.
[/FONT]

---

### Post by olivesandtrees on 2008-07-30
Any specific reason you are trying to build JBoss from source?

Why not just decompress the JBoss .tar.gz that you need to the directory of your choice and host Java apps to your heart's content.

---

