---
title: "Regaining my disk space"
date: 2007-03-23
forum: General Help
---

### Post by SirPaPa on 2007-03-23
Hello, I've recently ripped a couple of my dvd's using [COLOR="Red"]RipIt4Me[/COLOR] under [COLOR="Red"]wine[/COLOR] but I have lost disk space and would like to regain it. 
I've deleted the folder containing the dvd title and the .iso image under [COLOR="Red"]Wine[/COLOR] before but did not gain any space.
 How do I go about this please.  Thank you kindly for any suggestions.



Here are screenshots :

---

### Post by jimbob on 2007-03-23
Why can't you just go into your file manager (Nautilus?) and move those *.iso's to trash and then empty the trash?

If not open a terminal and just zap them with the rm command.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by SirPaPa on 2007-03-23
> **jimbob said:**
> Why can't you just go into your file manager (Nautilus?) and move those *.iso's to trash and then empty the trash?

If not open a terminal and just zap them with the rm command.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

Thank you for quick reply. I have highlighted and pressed delete and emptied the trash folder but have not regained space in the home folder.

---

### Post by jimbob on 2007-03-23
Post the output of df -h and fdisk -l

Find out if they are still there - open a root terminal and enter:

cd /
find . -name  *.iso  
 
and see what turns up.

I have never used wine so am not familiar with how it works.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by SirPaPa on 2007-03-23
> **jimbob said:**
> Post the output of df -h and fdisk -l

Find out if they are still there - open a root terminal and enter:

cd /
find . -name  *.iso  
 
and see what turns up.

I have never used wine so am not familiar with how it works.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

Here is the output of df -h. I have the .iso files that I mentioned.
 I just want to remove them after I burn them and regain my disk space.
 
Would the command " sudo aptitude --purge remove /.wine/ drive_c/DVD_VIDEO " work without destroying [COLOR="Red"]Wine[/COLOR] setup? Anyone?

---

### Post by hikaricore on 2007-03-23
> **SirPaPa said:**
> Here is the output of df -h. I have the .iso files that I mentioned.
 I just want to remove them after I burn them and regain my disk space.
 
Would the command " sudo aptitude --purge remove /.wine/ drive_c/DVD_VIDEO " work without destroying [COLOR="Red"]Wine[/COLOR] setup? Anyone?

You don't use aptitude to remove files or directories, just packages.

If you want to remove the whole directory and all files in it, just use:

```
rm -R ~/.wine/drive_c/DVD_VIDEO
```

---

### Post by SirPaPa on 2007-03-23
> **hikaricore said:**
> You don't use aptitude to remove files or directories, just packages.

If you want to remove the whole directory and all files in it, just use:

```
rm -R ~/.wine/drive_c/DVD_VIDEO
```

Thank you [COLOR="Red"]hikaricore[/COLOR]. Do you mean that it will remove the " [COLOR="Red"]DVD_VIDEO[/COLOR] " part of the whole command without destroying my [COLOR="Red"]Wine[/COLOR] configuratios?

---

### Post by jimbob on 2007-03-24
> Thank you hikaricore. Do you mean that it will remove the " DVD_VIDEO " part of the whole command without destroying my Wine configuratios?
Reply With Quote

Yes, that will remove DVD_VIDEO and everything under it.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

