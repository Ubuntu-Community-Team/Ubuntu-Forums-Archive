---
title: "Idea: Ubuntu Documention Served By Apache"
date: 2007-10-18
forum: General Help
---

### Post by Guyson on 2007-10-18
I'm not entirely sure where do post this but I have a suggestion/tip that I've been doing on my desktops & servers for ages now and I think it would really help out every one, from new users to pro's.

Problem: After installing the various doc packages I'm left to find the actual docs on my own. If I'm installing on a desktop machine I'll typical use a File Manager or a webbrowser to read the docs if they are html or 'less' otherwise.  If I'm maintaining a remote machine, I can't use my webbrowser as practically and installing the docs on my local machine is nasty because of issues like versioning between different installations.

Quick Solution: Since on  all of my remote machines and most of my desktop machines have been running some form of Apache I have been creating a directory, suchs as /var/www/docs/  and creating symlinks to the various html and non-html documents that have been installed.  I'll usually create a index.html under /var/www/ that contains a list of all the documents installed locally.

Building on this solution would be to have a tool to update the symlinks and the document index when new documentation is installed.

Done right, this could address some documentation concerns raised in this thread: 
[http://ubuntuforums.org/showthread.php?t=379658](http://ubuntuforums.org/showthread.php?t=379658)

---

