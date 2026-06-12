---
title: "libqt-mt.so.3 problem"
date: 2008-01-27
forum: General Help
---

### Post by lebiathan on 2008-01-27
Last night, I tried using Opera but it didn't seem to do anything. So I open a command line, type "opera" (without the quotes, of course) hit enter and get the following message:

```
/usr/lib/opera/9.25-20071214.6/opera: symbol lookup error: /usr/lib/libqt-mt.so.3: undefined symbol: 
```

So I google using firefox (hopefully it ran ok) but came up with no good solution. Problem is, I didn't do any changes as far as I can recall since my last boot-up, when opera was working just fine. I saw a few other threads around ubuntuforums saying they had a problem with "libqt-mt.so.3" library, but what was said there didn't actually help a lot.

So I try an *ls* on the file and get the following:
```
lebiathan@lebi-laptop:~$ ls /usr/lib/libqt-mt.so.3
lrwxrwxrwx 1 root root 26 2008-01-26 19:49 /usr/lib/libqt-mt.so.3 -> /usr/lib/libqt-mt.so.3.3.7
```

The file /usr/lib/libqt-mt.so.3.3.7 exists and an ls on it gives me
```
lebiathan@lebi-laptop:~$ ls /usr/lib/libqt-mt.so.3.3.7
-rw-r--r-- 1 root root 8434140 2007-10-30 19:29 /usr/lib/libqt-mt.so.3.3.7
```

I tried reinstalling opera, with and without backing-up the .opera/ folder, but nothing came out of it. Problem persists. Now, the worst part is that when I try opening Amarok (Kaffeine too) and MySQL-navigator, I get the **exact** same error! Hopefully, I don't get the error with all of the apps I'm running.

For all it matters, I installed the Qt library some days ago, version 4.3 (latest one), from the Trolltech site (i wanted to use it for programming). I downloaded the .tar.gz file (for C/C++) to a local folder (full path was: /home/lebiathan/MyFiles/Programs/Qt ), and untar it. I type the ./configure command that their INSTALL.txt file says and everything's ok. What I do recall doing some time yesterday or the day before is that I moved the folder where Qt4.3 was untarred to another directory (sth like: /home/lebiathan/MyFiles/Programming/Qt). I'm not sure if this has caused so much trouble, but I thought I should mention it just in case.

I read about [this]("http://ubuntuforums.org/showpost.php?p=1167982&postcount=62") thread, I download i386 libqt, but when I try to install it I get a "You got a newer version installed" message. I don't know if that refers to Qt4.3 or a newer 3.x version, but If I have a newer version installed, shouldn't that make Opera (and all the other apps) work ok (except if incompatibility issues are at hand)? 

//edit: I forgot to mention. I'm using Ubuntu 7.10 (Gutsy) on a x86 laptop (HP Pavillion).

Any suggestions are more than welcome!

Thank you very much,
George

---

