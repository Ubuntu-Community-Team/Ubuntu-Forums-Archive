---
title: "Quick command line permissions question"
date: 2008-01-25
forum: General Help
---

### Post by Paqman on 2008-01-25
This isn't specifically an Ubuntu question. I've got a NAS that I mount shares from, and the permissions of one of the shares have got screwed up.

I can SSH into the box quite easily, and have figured out that I need to chmod the mp3s back to 766 for Windows to be happy with them. Trouble is the directories themselves need execute permissions.

So how do I reset all the diretories to 777 and the files within them to 766 from the command line?

---

### Post by ynef on 2008-01-25
Use the "find" command -- you can tell it to first give you the directories only (and apply some command to them, in your case chmod) and then do the same but for the files in those directories. See the manual page, or search around on the Internet for more information.

---

### Post by Paqman on 2008-01-25
So if I chmod-ed the whole lot to 766 then picked out the directories with something like:

```

find . -type d -exec chmod 777

```

I should be onto a winner? Would the find command there pull out all the directories under the one I was in?

---

### Post by gvartser on 2008-01-25
Yes it will with some mods.

```
find . -type d -exec chmod 777 {} \;
```

/g

---

### Post by Paqman on 2008-01-25
Thanks for that! I'll throw you command at the NAS when I get home tonight.

Is it just me, or does the find command have really weird syntax?

---

### Post by Paqman on 2008-01-25
Ok, i've tried this command and got the following output:

> 
BusyBox v1.01 (2007.07.26-19:12+0000) multi-call binary

Usage: find [PATH...] [EXPRESSION]

Search for files in a directory hierarchy.  The default PATH is
the current directory; default EXPRESSION is '-print'

EXPRESSION may consist of:
        -follow         Dereference symbolic links.
        -name PATTERN   File name (leading directories removed) matches PATTERN.
        -print          Print (default and assumed).

        -type X         Filetype matches X (where X is one of: f,d,l,b,c,...)
        -perm PERMS     Permissions match any of (+NNN); all of (-NNN);
                        or exactly (NNN)
        -mtime TIME     Modified time is greater than (+N); less than (-N);
                        or exactly (N) days


When I try the simple find command (find . -type d) it lists the directories correctly. The error output above doesn't mention the -exec, so i'm wondering if this box won't accept that as a parameter?

Is there another way of achieving the same result? Something with grep?

---

