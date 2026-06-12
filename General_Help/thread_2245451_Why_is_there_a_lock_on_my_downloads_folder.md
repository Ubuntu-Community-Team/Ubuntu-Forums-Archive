---
title: "Why is there a lock on my downloads folder?"
date: 2014-09-23
forum: General Help
---

### Post by andreadixon825 on 2014-09-23
Hi, I just installed xubuntu 14.04 and I have notest that it has a lock on my downloads folder, how can I get ride of that lock, because everything I download comes up with an error. Please help me thanks so much. :)

---

### Post by Michael_McKenney on 2014-09-23
Assign your user rights to the folder to read, write, and execute.

---

### Post by coffeecat on 2014-09-23
A lock on the folder would suggest an ownership or permissions problem which is very odd for a new installation. Post the output of this terminal command so that we can see what the ownership and permissions are on all of your home folders, not just the Downloads folder:

```
ls -l ~
```

---

### Post by andreadixon825 on 2014-09-23
Here is the list from terminal
```
total 36
drwxr-xr-x 2 andrew andrew 4096 Sep 23 13:22 Desktop
drwxr-xr-x 2 andrew andrew 4096 Sep 23 10:05 Documents
dr-xr-xr-x 7 andrew andrew 4096 Mar 23  2014 Downloads
drwxr-xr-x 2 andrew andrew 4096 Sep 23 10:05 Music
drwxr-xr-x 2 andrew andrew 4096 Sep 23 10:05 Pictures
drwxr-xr-x 2 andrew andrew 4096 Sep 23 10:05 Public
drwxr-xr-x 2 andrew andrew 4096 Sep 23 10:05 Templates
drwxrwxr-x 7 andrew andrew 4096 Sep 23 13:23 tmp
drwxr-xr-x 2 andrew andrew 4096 Sep 23 10:05 Videos

```

---

### Post by coffeecat on 2014-09-23
Somehow, your Downloads folder has acquired 555 permissions, which means you can't write to it. To fix this, run this command:

```
chmod 755 ~/Downloads
```

But that still leaves the mystery as to why your Downloads folder has inappropriate permissions. Were you doing anything with permissions?

**Edit:** by the way, I've changed the quote tags to code tags in your last post. You need to use code tags for terminal output in order to retain formatting.

---

### Post by andreadixon825 on 2014-09-23
&#65279;Hi, thanks for that fixes it worked, about the permission, I did not touch anything of that at all,  All I did was install a clean installation today on a new computer I built. Ya I have know Idol how that happed, It was an old dvd I had from mouths ago, could that be it? anyways thanks :)

---

### Post by coffeecat on 2014-09-23
The other odd thing is that although the folder dates for the other home folders all show that you installed the system today, your Downloads folder is dated March 23rd. Offhand I cannot think how that could happen. Anyway, I'm glad it's fixed.

---

