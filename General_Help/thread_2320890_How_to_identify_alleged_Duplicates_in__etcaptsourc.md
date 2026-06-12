---
title: "How to identify alleged Duplicates in  /etc/apt/sources.list"
date: 2016-04-18
forum: General Help
---

### Post by Eanruig on 2016-04-18
Since the only foolish question is the unasked one, here is my query - others may decide if it is foolish or not.

```
uname -a

Linux hanraoi-ME051 3.19.0-58-generic #64~14.04.1-Ubuntu SMP Fri Mar 18 19:05:42 UTC 2016 i686 i686 i686 GNU/Linux
```

(I note that uname doesn't seem to know that I'm running Lubuntu.)

The output of 

```
sudo apt-get update
```

reports, in part,

```
W:  Duplicate sources.list entry http://security.ubuntu.com/ubuntu/  trusty-security/main i386 Packages  (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_main_binary-i386_Packages)
W:  Duplicate sources.list entry http://security.ubuntu.com/ubuntu/  trusty-security/restricted i386 Packages  (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_restricted_binary-i386_Packages)
W:  Duplicate sources.list entry http://security.ubuntu.com/ubuntu/  trusty-security/universe i386 Packages  (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_universe_binary-i386_Packages)
W:  Duplicate sources.list entry http://security.ubuntu.com/ubuntu/  trusty-security/multiverse i386 Packages  (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_multiverse_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
```

The  suggestion "You may want to run apt-get update to correct these  problems" prompts me to reply, "Really? I got this listing when I ran  apt-get-update," and I am irked.

Next, I found in several posts in Ubuntu Forums that I can probably get rid of these "problems" (if problems they are) by editing sources.list. That makes sense, because the report specifically says "Duplicate sources.list entry...", so I back it up, and start editing.

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
sudo leafpad /etc/apt/sources.list
```

One of the "Duplicate" entries above is 

"http://security.ubuntu.com/ubuntu/ trusty-security/main i386 Packages"

I search for that string with the editor, and get, "Search String not found".
Annoyance comes.

I remove " Packages" from the search string, and search again - and get  my friend "Search String not found". 
Increment annoyance.

I remove " i386" from the search string, and search again - and get my friend "Search String not found". 
Increment annoyance.

I remove "/main", search again, and I find it! 
Relief ensues, but not  for long. 
There is only one match in sources.list, and I thought there was a  duplicate here.
Where is it hiding? 
Increment annoyance.

I see several possibilities - there may be others. 
(1) "sudo apt-get update" is lying, or 
(2) it  doesn't know what a duplicate is, or 
(3) its report format is (unnecessarily? deliberately?) obscure, or 
(4) I don't recognize a duplicate when  I see it.

I'm not about to change something without knowing what I'm doing.

So: How do I identify duplicates in sources.list?

---

### Post by Bucky Ball on 2016-04-18
You've identified one. Put a hash (#) in front of it (this means you don't delete the line, it is ignored so you can remove the hash later if you want the line to be used), save the file and try an update. You'll need to open the file in Leafpad as root to change.

```
gksudo leafpad /etc/apt/sources.list
```

Looks like you have the multiverse and universe i386 repos duplicated. 

```
lsb_release -a
```

... should show you you are running Lubuntu.

---

### Post by Eanruig on 2016-04-18
As suggested, I commented out the one line I found, and re-ran the update.

All the "Duplicate" entries vanished.

I take it that means I had four entries in sources.list which were duplicated by a single fifth entry.

Remove the common enemy, and all is well.

Thanks, Bucky Ball!

---

