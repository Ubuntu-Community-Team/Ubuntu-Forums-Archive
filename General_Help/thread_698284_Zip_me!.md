---
title: "Zip me!"
date: 2008-02-16
forum: General Help
---

### Post by Pgannon on 2008-02-16
I am brand new to Linux and need some help zipping a massive batch of files.  I have approx. 600k files that I need to compress, and they must be in the .zip format.  They also must be in folders no larger than 1.5 gigs.  Is there a utility that will allow me to limit the size of the resulting archive folder?  Or maybe a switch on the command line that will limit the folder size?  Thanks for your help.

---

### Post by SpaceTeddy on 2008-02-16
with simple zip, you cannot go about and set a mx filesize... you would need to use rar or tar for that (which is, as you say, out of question)...

with zip, the only way i know of is that you create the zip archive, and then use zipsplit to chop it up in parts... 

example
> zip -r /home.zip /home/*
zipsplit -n 1610612736 /home.zip

zipsplit does NOT create a multi archive, it just creates multiple archives which then stand on their own... also, no files packed size can be larger than 1,5Gbyte.. if they are, it is impossible to use zipsplit.

if you can, use something that acctually supports multi volume, like tar or rar.

PS:1610612736 is excatly 1,5 Gbyte - change that number to what you want the max size to be.

---

