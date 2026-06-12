---
title: "How ti Instal an Earlier Version of libsvn-java"
date: 2016-11-11
forum: General Help
---

### Post by artist-wavenet on 2016-11-11
I installed the latest version of Eclipse Neon. When I attempted to create a PHP project I got this error:

Failed to load JavaHL Library.
These are the errors that were encountered:
no libsvnjavahl-1 in java.library.path
no svnjavahl-1 in java.library.path
no svnjavahl in java.library.path
java.library.path = /usr/java/packages/lib/amd64:/usr/lib/x86_64-linux-gnu/jni:/lib/x86_64-linux-gnu:/usr/lib/x86_64-linux-gnu:/usr/lib/jni:/lib:/usr/lib

So I attempted to install JavaHL follow the instructions at:
[http://subclipse.tigris.org/wiki/JavaHL](http://subclipse.tigris.org/wiki/JavaHL)

In Eclipse: Help => Installation Details I see I have Subclipse version 1.10.13. According that web page I need to install SVN/JavaHL version 1.8.x. When I follow the directions farther down that page and execute the command:

sudo apt-get install libsvn-java

what is installed is version 1.9.3-2ubuntu1. How can I install version 1.8.x?

I attempted to install Subclipse version 1.12.x by pasting the URL:

		[http://subclipse.tigris.org/update_1.12.x](http://subclipse.tigris.org/update_1.12.x) 

In Eclipse: Help => Install New Software => Work with field, after removing both Subclipse and SVNKit. But the versions  it was going to install was still Subclipse 1.10.13 and SVNKit Library 1.8.12.

---

