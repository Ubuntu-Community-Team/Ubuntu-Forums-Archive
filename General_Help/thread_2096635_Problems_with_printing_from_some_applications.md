---
title: "Problems with printing from some applications"
date: 2012-12-20
forum: General Help
---

### Post by rthorpe on 2012-12-20
I'm running Xubuntu 12.04. Recently I've been having problems with printing. I've found that some applications can print correctly. Those I've tried that work are Abiword and the command-line lp program. Some though don't print correctly, this includes Evince and GIMP. I think this may be related to the recent security problems with CUPS because I get a "keyring" warning whenever I successfully print.

I have a long PDF document to print out. The only way I've found to do it is by converting each page to a PNG with GIMP then printing out that page using the lp command.

Has anyone else had this problem?

---

### Post by irv on 2012-12-20
Now that you mention this, Yes I have been having problems also. I can print from most of the apps, but I have problems printing PDF's and anything from the Internet via a browser. I needed to print a return shipping label the other day, I finely did a screen capture of the label and pasted it into a LibreOffice Writer Document and printed it out that way. I have a HP Printer.
Here is my printer properties. 
[ATTACH]228930[/ATTACH]

---

### Post by rthorpe on 2012-12-21
I'm using a Canon MP272 printer.

I don't think the problem is printer related, otherwise all applications would be having problems. I think it's something about how apps are dealing with CUPS or gnome-printing. I know little about those, so I can't look into it.

A couple of days ago there was a security problem found with CUPS which allowed code to escalate privileges. There was a fix to solve that, I think that may have caused the problem.

---

### Post by irv on 2012-12-21
I am thinking the problem is more with CUPS also. I am using an older version on my server and I do not have any problem printing from there. Of course I am using an older version of Ubuntu also so I can't be for sure it is CUPS.

---

