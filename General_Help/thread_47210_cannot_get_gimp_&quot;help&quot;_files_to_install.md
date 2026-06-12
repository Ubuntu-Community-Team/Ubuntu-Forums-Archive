---
title: "cannot get gimp &quot;help&quot; files to install"
date: 2005-07-07
forum: General Help
---

### Post by GMachine_24 on 2005-07-07
Hi: I was starting to play around with The Gimp a bit ago and a little box told me if I hit F1 I could get help at any point during my Gimp adventure. So I hit the F1 key and got this message:

[B]The GIMP help files are not installed. Please make sure gimp-help-en is installed, or the appropriate gimp-help package for your language.

Could not open '/usr/share/gimp/2.0/help/en/gimp-help.xml' for reading: No such file or directory

Please check your installation.[/B] 

So, I searched and found out that help files are not loaded with The Gimp but I found a place to d/l them and so I typed did an apt-get install and this is what turned up:

[B]
The following NEW packages will be installed:
  gimp-help-common gimp-help-en
0 upgraded, 2 newly installed, 0 to remove and 1 not upgraded.
Need to get 456kB/6588kB of archives.
After unpacking 11.1MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main gimp-help-en 2+0.6-2 [456kB]
Fetched 456kB in 3s (144kB/s)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gimp-help/gimp-help-en_2+0.6-2_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gimp-help/gimp-help-en_2+0.6-2_all.deb)  MD5Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?[/B]

I ran apt-get update with and without --fix-missing but I still cannot get the "help" files to run. I know I got a 'failed to fetch' message ... but don't know what to do to fix it. Thanks in advance.

---

### Post by GMachine_24 on 2005-07-07
Well, from what I have learned, apparently you can only install the 'help' files if you're using a developer version because they are the only ones with this file: "gimp-2.0.pc" in them. You can still install the help files but they don't go to the proper directory for The Gimp to find them when you press F1 and I'm trying to work out whether a symbolic link will do the trick. If anyone knows, please advise.

Thanks.

---

### Post by polo_step on 2005-07-08
I can't get it either:

This error came up on both tries:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gimp-help/gimp-help-en_2+0.6-2_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gimp-help/gimp-help-en_2+0.6-2_all.deb)
  MD5Sum mismatch

---

### Post by jeremy on 2005-07-08
maybe try one of the other repo's, eg;
[http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hoary/main

---

### Post by GMachine_24 on 2005-07-08
Thank you for your reply. I inserted the line you suggested, with slight editing to meet the proper format (I think), then tried to install the help files again and this is what I got:

[B]root@ubuntu:/home/erikm # apt-get install gimp-help
Reading package lists... Done
Building dependency tree... Done
Note, selecting gimp-help-zh-cn instead of gimp-help
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gimp-help-zh-cn: Depends: gimp-help-common (= 2+0.6-2) but it is not installable
E: Broken packages[/B]

So..... should I file a bug report or is there something else I should try? Thanks.

GMachine

---

### Post by jeremy on 2005-07-09
Sorry that didn't work, yes, it seems like time for a bug report.

---

### Post by GMachine_24 on 2005-07-09
Sat. July 9, 5:14 PM EST I filed a bug report so let's see if the problem is addressed. Thanks again to everyone for replies, suggestions, etc.

GMachine

---

### Post by GMachine_24 on 2005-07-09
The problem downloading The Gimp help files has been FIXED. Thank you!!

---

### Post by savage on 2005-07-12
I'm having this same problem if it's fixed how do I make it work on my system?

---

### Post by GMachine_24 on 2005-07-12
You need to give us some more information - what commands have you used and what error message(s) have you received?

---

