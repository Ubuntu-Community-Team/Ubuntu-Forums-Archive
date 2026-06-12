---
title: "dpkg error when installing software"
date: 2005-10-23
forum: General Help
---

### Post by Daniloc on 2005-10-23
how to fix this
i cant to install any package

```
After unpacking 0B of additional disk space will be used.
dpkg: parse error, in file `/var/lib/dpkg/status' near line 2323 package `python-reportlab':
`Depends' field, reference to `python': version contains ` '
```

I try 100000 times and nothing what to do?
Sorry on my english please.

---

### Post by Daniloc on 2005-10-23
Please someone must know. Help me.

---

### Post by dtfinch on 2005-10-23
The last time I had a problem in /var/lib/dpkg/status that prevented me from installing or uninstalling anything, I was able to edit /var/lib/dpkg/status (sudo gedit /var/lib/dpkg/status) to manually correct the problem, since it's a plain text file. It should only be done a last resort, but you might be at the last resort stage. Make a backup first.

Mine says "Depends: python2.4-reportlab, python (<< 2.5), python (>= 2.4), python-xml" in the place in question. I can't imagine why it would ever be different.

---

### Post by Daniloc on 2005-10-23
??? 
And what i need to do? What i need to edit ?

---

### Post by dtfinch on 2005-10-23
I don't know. What does the python-reportlab section in the file look like?

If the file is simply corrupted for some reason, there should be a backup called /var/lib/dpkg/status-old, hopefully the last good copy of the file before it was damaged.

---

### Post by Daniloc on 2005-10-23
:( :( :( 
Help me pleaseeeeeeeeeeee

---

### Post by Kyral on 2005-10-23
1) I reccommend this goes to the Absolute Beginners Talk Forum

2) First get some Command Line power by reading my HOWTO in my signature (The link in the bottom of this post) and what he said SHOULD make some sense :D

---

### Post by Daniloc on 2005-10-23
My English is bad. Tell me commands or some good help.

---

### Post by Kyral on 2005-10-23
*facefault*

Summery of Terminal for Beginners

(Assuming you know how to open the Terminal)

cd = change directory
cd ~ = change to your home directory
mv <file 1> <file 2> = Move file 1 to file 2
cp <file 1> <file 2> = Copy file 1 to file 2
rm <file> = delete
cat <file> = printout the contents of a file
cat <file> | less = printout the contents of a file in such a way that it doesn't all go flying past the screen at once

---

### Post by dtfinch on 2005-10-23
Make sure the package manager / synaptic is closed first.

In the terminal:

To backup your current list of installed packages:
sudo cp /var/lib/dpkg/status /var/lib/dpkg/status-backup

Then, after making the backup, to restore the old, possibly working copy:
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status

Then see if that fixed it.
If that just makes things worse somehow, you can undo it with: sudo cp /var/lib/dpkg/status-backup /var/lib/dpkg/status

---

### Post by Psquared on 2005-10-23
Try this in a terminal:

sudo apt-get update

sudo apt-get upgrade dpkg

---

### Post by Daniloc on 2005-10-23
After unpacking 0B of additional disk space will be used.
dpkg: parse error, in file `/var/lib/dpkg/status' near line 2323 package `python-reportlab':
`Depends' field, reference to `python': version contains ` '
Always this.
My sources list is good all is good.... What, what what how someone help please. I gone crazy

---

### Post by Daniloc on 2005-10-23
[QUOTE=Psquared]Try this in a terminal:

sudo apt-get update

sudo apt-get upgrade dpkg[/QUOTE]
 Ok.. I waiting to install. WHen install be finished i give u a result in this thread. Thankls

---

