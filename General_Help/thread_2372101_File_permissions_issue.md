---
title: "File permissions issue?"
date: 2017-09-21
forum: General Help
---

### Post by adamb1973 on 2017-09-21
I am having issues reading some of my data DVDs.  They come from a music subscription company.  When I put the DVD in, it shows what is in the attached image.  Each of these items should be directories (folders).

Any help that can be offered is much appreciated.

Thank you.

---

### Post by TheFu on 2017-09-21
Post the output **of ls -al {path/to/dvd}** - I can't tell anything from that screen shot. Please use "code tags" so things line up correctly.  They are accessed via Adv Reply (#).

---

### Post by adamb1973 on 2017-09-23
borntrager@borntrager-U52F:/media/borntrager$ ls -al M186
```
ls: cannot access 'M186/.': Permission denied
ls: cannot access 'M186/..': Permission denied
ls: cannot access 'M186/AIRPLAY CHARTS': Permission denied
ls: cannot access 'M186/BONUS VIDEO! CHECK THIS OUT!': Permission denied
ls: cannot access 'M186/C561': Permission denied
ls: cannot access 'M186/C562': Permission denied
ls: cannot access 'M186/C563': Permission denied
ls: cannot access 'M186/C564': Permission denied
ls: cannot access 'M186/MP BONUS TRACKS AND DATABASE FILES': Permission denied
ls: cannot access 'M186/MUSIC LISTS': Permission denied
ls: cannot access 'M186/RR160': Permission denied
ls: cannot access 'M186/RL151': Permission denied
ls: cannot access 'M186/RJ93': Permission denied
ls: cannot access 'M186/RH150': Permission denied
ls: cannot access 'M186/RC150': Permission denied
ls: cannot access 'M186/RA150': Permission denied
ls: cannot access 'M186/T1322': Permission denied
ls: cannot access 'M186/T1323': Permission denied
ls: cannot access 'M186/T1324': Permission denied
ls: cannot access 'M186/T1325': Permission denied
total 0
d????????? ? ? ? ?            ? .
d????????? ? ? ? ?            ? ..
?????????? ? ? ? ?            ? AIRPLAY CHARTS
?????????? ? ? ? ?            ? BONUS VIDEO! CHECK THIS OUT!
?????????? ? ? ? ?            ? C561
?????????? ? ? ? ?            ? C562
?????????? ? ? ? ?            ? C563
?????????? ? ? ? ?            ? C564
?????????? ? ? ? ?            ? MP BONUS TRACKS AND DATABASE FILES
?????????? ? ? ? ?            ? MUSIC LISTS
?????????? ? ? ? ?            ? RA150
?????????? ? ? ? ?            ? RC150
?????????? ? ? ? ?            ? RH150
?????????? ? ? ? ?            ? RJ93
?????????? ? ? ? ?            ? RL151
?????????? ? ? ? ?            ? RR160
?????????? ? ? ? ?            ? T1322
?????????? ? ? ? ?            ? T1323
?????????? ? ? ? ?            ? T1324
?????????? ? ? ? ?            ? T1325
```


Is this an issue with the DVD.  I get these discs monthly and I have problems with some discs, others work fine. Is this an issue with the way the disc is created?

Thanks.

---

### Post by deadflowr on 2017-09-23
Try the ls -al command with sudo
```
sudo ls -al path-to-file
```

(when you reply, click on either the Reply to Thread button or the Go Advanced Button and click on the # symbol in the toolbar to insert the output into code tags, please)

---

### Post by adamb1973 on 2017-09-29
```
adam@adam-X750JA:/media/adam$ sudo ls -al M192/total 64
dr--r--r--  20 adam adam 1084 Dec 22  2015 .
drwxr-x---+  3 root root 4096 Sep 29 16:58 ..
dr--r--r--   2 adam adam  176 Dec 22  2015 AIRPLAY CHARTS
dr--r--r--   2 adam adam  580 Dec 21  2015 BONUS VIDEO! CHECK THIS OUT!
dr--r--r--   2 adam adam 2224 Dec  3  2015 C587
dr--r--r--   2 adam adam 2484 Dec  9  2015 C588
dr--r--r--   2 adam adam 2384 Dec 17  2015 C589
dr--r--r--   2 adam adam 2332 Dec 21  2015 C590
dr--r--r--   3 adam adam 3064 Dec 22  2015 MP BONUS TRACKS AND DATABASE FILES
dr--r--r--   2 adam adam  860 Dec 21  2015 MUSIC LISTS
dr--r--r--   2 adam adam 1948 Dec 21  2015 RA153
dr--r--r--   2 adam adam 1892 Dec 21  2015 RC153
dr--r--r--   2 adam adam 2248 Dec 15  2015 RH153
dr--r--r--   2 adam adam 1680 Dec 17  2015 RJ96
dr--r--r--   2 adam adam 2420 Dec 21  2015 RL157
dr--r--r--   2 adam adam 1756 Dec 15  2015 RR166
dr--r--r--   2 adam adam 2152 Dec  3  2015 T1348
dr--r--r--   2 adam adam 2168 Dec  9  2015 T1349
dr--r--r--   2 adam adam 2352 Dec 15  2015 T1350
dr--r--r--   2 adam adam 2528 Dec 17  2015 T1351


This is what I get if I use SUDO.  I can launch Nautilus using the Sudo command too and then I have access to the files, not really convenient though.

Thank you.

```

---

### Post by TheFu on 2017-09-29
Wrong permissions.  It would be smart to learn them.  A directory without execute permissions cannot be entered.  Search for "ubuntu permissions" to get to the tutorial on this vital information.

sudo nautilus is a mistake.  DO NOT RUN NAUTILUS using sudo.  It causes issues that you are not able to resolve.

If the file system is NTFS, then you need to control the permissions during the mount.
If it is a Unix file system, then you can chmod -R +x on the directory and everything below will get those permissions.  If you need help with any of these things, ask. But we'll need accurate data about the type of file system used to be of any help.  Linux isn't like Windows, there are over 20 different file systems that it could be.

---

### Post by yetimon_64 on 2017-09-29
> I can launch Nautilus using the Sudo command too and then I have access ...
Be aware using nautilus with sudo can cause problems with your user account and can at times even lock you out of logging into your user account if the ~/.ICEauthority or ~/.Xauthority files become corrupted from doing so.

If you continue to use sudo with graphical applications, especially nautilus, I would suggest you use the "-H" switch with sudo, for example ...
```
sudo -H nautilus
```
... this will prevent log in problems with your user account by forcing the use of roots home environment and not your users home environment as straight sudo with no -H switch uses.

Some info from "man sudo" for you to read ...

> ```
     -H, --set-home
                 Request that the security policy set the HOME environment variable to the home
                 directory specified by the target user's password database entry.  Depending on the
                 policy, this may be the default behavior.

```

**Edit:** I agree with TheFu that learning about permissions and setting them correctly is better than using sudo and nautilus even with the -H switch. 
Using the -H switch will only prevent the more serious side effects of using sudo and nautilus but it is not the best way of doing what you need, learning to set permissions correctly is a much better idea.

---

### Post by adamb1973 on 2017-09-30
Thank you.  The files in question are on a "read only" DVD.  Can you adjust permissions on a disc like that?

---

### Post by ajgreeny on 2017-09-30
> **adamb1973 said:**
> Thank you.  The files in question are on a "read only" DVD.  Can you adjust permissions on a disc like that?
No you can't; you may have to copy them to your hard-disk and then you should be able to do so.

---

### Post by TheFu on 2017-09-30
> **adamb1973 said:**
> Thank you.  The files in question are on a "read only" DVD.  Can you adjust permissions on a disc like that?

You should be able to override permissions that aren't 'write' at mount time, but it depends on the file system used when the disk was burned.  I think the disk was burned incorrectly, since a directory without execute permissions is pretty useless.

---

