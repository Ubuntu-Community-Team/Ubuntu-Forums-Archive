---
title: "File roller asks for password with split rar archive"
date: 2007-07-06
forum: General Help
---

### Post by Sh4wn on 2007-07-06
Hi,

I'm using Ubuntu 7.04, using the nonfree unrar tool. I've downloaded a splitted rar archive. When I try to open it, click extract, it's extracts a few files, and then it asks for a password. 

But there is no password.

When I leave the password field blank, and click OK, it starts over again for the files which hasn't been extracted completey (because they're spread over multiple archives).

It's pretty annoying, because I can't extract the archive completely now.

I've also tried to 'cat' all the parts to one .rar file, but then it also asks for a password, and not all files show up.

Anyone knows how I can fix this? Thanks in advance.

---

### Post by Theimon on 2007-07-06
There are some tools on the market which will attack the rar with brute force to eventually unlock the archive. But that could take ages. So go where you got the files and ask those guys for the password. If they can't/won't supply it.....tough luck.....download the thing you want somewhere else.

---

### Post by Sh4wn on 2007-07-07
No, there's no password. That's the problem. File roller asks for a password while there's no one.

---

### Post by Theimon on 2007-07-09
Could you give me a link to where you downloaded those files? I'll give it a try then.

---

### Post by miLl3niUm on 2007-07-09
Maybe there is and the guy who posted it forgot to tell password ;)

---

### Post by ferronica on 2007-07-09
same problem here  asking for PASSWORD but there is no password :( please help :(

---

### Post by Theimon on 2007-07-10
> **miLl3niUm said:**
> Maybe there is and the guy who posted it forgot to tell password ;)

That happens quite often in certain "areas" of the internet ;) 

Or the password was mentioned in a .nfo file which the TS threw away...it could be anything, but that it needs a password to unlock the archive is evident.

---

### Post by MonsterDuc on 2007-07-12
I just encountered the same and went back to the source where I downloaded the torrent from and indeed there was a password there...

---

### Post by truxntrax on 2007-11-18
I have the same problem!  I know there isn't a requirement for a password as unrar on my Vista machine can open the archive without issue.

Did anyone fix this/ have a suggestion?

(I originally found the problem to be on my d0link 323 nas box which I have debain etch running on it,  I installed SABnzbd and it all works fine except for the unraring.  Therefore I tried to unrar the file on my ubuntu machine - still didn't work (asked for password) - but it does work on my vista machine.  So Vista proves password is not required).

Any ideas???

---

### Post by mali2297 on 2007-11-18
> **truxntrax said:**
> I have the same problem!  I know there isn't a requirement for a password as unrar on my Vista machine can open the archive without issue.

Did anyone fix this/ have a suggestion?

(I originally found the problem to be on my d0link 323 nas box which I have debain etch running on it,  I installed SABnzbd and it all works fine except for the unraring.  Therefore I tried to unrar the file on my ubuntu machine - still didn't work (asked for password) - but it does work on my vista machine.  So Vista proves password is not required).

Any ideas???

I guess you also have a split archive, say foo.rar.001, foo.rar.002 etc. If Fileroller won't extract them, try the terminal:
```

unrar e foo.rar.001

```

---

### Post by Wuzzle on 2007-11-18
I've found it was because one of the rar parts is corrupt.  Using both par2 clients in feisty indicated that they were fine.  Installed QuickPar and found that they were indeed corrupt.  Corrected with QuickPar, which in turn corrected the asking for password.:)

---

### Post by ViaD on 2007-12-30
> **Wuzzle said:**
> I've found it was because one of the rar parts is corrupt.  Using both par2 clients in feisty indicated that they were fine.  Installed QuickPar and found that they were indeed corrupt.  Corrected with QuickPar, which in turn corrected the asking for password.:)

It seems there are no options in File roller to keep extract of broken rar files. 

In command line you can use

rar e -kb foo.r00

-kb for keep broken.

---

### Post by mandzo84 on 2008-05-06
This is bug in file-roller: [http://bugzilla.gnome.org/show_bug.cgi?id=504584]("http://bugzilla.gnome.org/show_bug.cgi?id=504584")

In short, file-roller ask for password instead of missing .rar file.
You can go around this by unraring each .rar archive in command line:
  unrar e file.part03.rar

---

