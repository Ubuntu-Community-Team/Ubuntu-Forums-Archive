---
title: "Help with compiling files??"
date: 2015-10-20
forum: General Help
---

### Post by McTaveesh on 2015-10-20
So I'm trying to compile some things with Ubuntu and I keep getting the same error.. Ex: "ThinkPad-T420:~/usr/local/src$ tar -xjvf gnupg-2.0.20.tar.bz2 tar (child): gnupg-2.0.20.tar.bz2: Cannot open: No such file or directory tar (child): Error is not recoverable: exiting now tar: Child returned status 2 tar: Error is not recoverable: exiting now " But I'm in the directory and that's where the package is located so... ? Sorry I'm new this.

---

### Post by TheFu on 2015-10-21
Welcome to the forums.

Why not just install gpgv2 package? It is v2.0.22 on a 14.04 system.

Downloading source code to install is the last resort on ubuntu systems unless you are a developer and need to build the programs yourself for some reason.

When you are new, it is best to only install programs through the package manager. Even downloading .deb files and manually installing those is about choice 5 because it often has unwanted side effects.

Also, it would help us if you used more whitespace in your posts and used "code tags" for terminal inputs and outputs. If you decide you still want to do this we can help, but you'll need to understand userid file and directory permissions. For example, it is doubtful that your userid can write any files to /usr/local/. That area requires root.

---

