---
title: "Why do I have a specific document always in my /run/user/1000 folder?"
date: 2023-01-29
forum: General Help
---

### Post by Paddy Landau on 2023-01-29
I noticed by chance that there is a specific file in my [FONT=courier new]/run/user/1000[/FONT] folder. This applies even after I reboot. I first noticed it maybe a couple of weeks ago, but I thought little of it, and only today did I realise that it is persistent.

[SIZE=3]Details[/SIZE]

I have a document, let's call it [FONT=courier new]magazine.pdf[/FONT], in a folder on my disk.

However, I also have a folder containing that file here:
[FONT=courier new]/run/user/1000/doc/17a1f69b[/FONT]

I have used [FONT=courier new]diff[/FONT] to confirm that the file is identical to the original.

Now, I'm wondering how it got there and why it's persistent even across reboots?

I tried to follow the chain of mounts and got a little confused. This is what I have figured out from the [FONT=courier new]mount[/FONT] command:
```
tmpfs on /run
tmpfs on /run/user/1000
portal on /run/user/1000/doc
```
I don't know what "portal" means in this context, and searching for an answer hasn't helped me.

I'm confused, because [FONT=courier new]/run[/FONT] is a RAM disk that should be destroyed when I restart or power off (which I do at least every day).

Please would you explain what's going on?

**[SIZE=3]EDIT[/SIZE]**

[FONT=Verdana]I've just tested, and it seems that the document in my [/FONT][FONT=courier new]/run/user/1000/doc/17a1f69b[/FONT][FONT=Verdana] is not a copy, but the same document. I changed my original document on disk, and the document in [/FONT][FONT=courier new]/run/user/1000/doc/17a1f69b[/FONT][FONT=Verdana] reflected the change.[/FONT]

[FONT=Verdana]So, now, it seems that the folder holds a hard link or maybe a symbolic link to the document. But it doesn't look like one when I list it in the terminal, and the inodes for the two are different.

Also, I have flatpak installed, in case that makes a difference.[/FONT]

---

### Post by TheFu on 2023-01-29
Do you use calibre?

---

### Post by Paddy Landau on 2023-01-29
> **TheFu said:**
> Do you use calibre?
No. I hadn't even heard of it until now! I've checked, and it's not even installed on my system.

I should have mentioned that I use Ubuntu 22.04, in case it makes a difference.

EDIT: Please see my edit in the OP.

---

### Post by #&amp;thj^% on 2023-01-29
Read your edit, please check:
```
$  systemctl --user status xdg-document-portal.service
Warning: The unit file, source configuration file or drop-ins of xdg-document-p>
&#9679; xdg-document-portal.service - flatpak document portal service
     Loaded: loaded (/usr/lib/systemd/user/xdg-document-portal.service; static)
     Active: active (running) since Sun 2023-01-29 10:00:16 MST; 27min ago
   Main PID: 4233 (xdg-document-po)
      Tasks: 8 (limit: 8973)
     Memory: 1.6M
        CPU: 55ms
     CGroup: /user.slice/user-1000.slice/user@1000.service/session.slice/xdg-do>
             &#9500;&#9472;4233 /usr/libexec/xdg-document-portal
             &#9492;&#9472;4242 fusermount3 -o rw,nosuid,nodev,fsname=portal,auto_unmount,s>

Jan 29 10:00:16 me-ThinkPad-X1-Carbon-7th systemd[4014]: Starting flatpak docum>
Jan 29 10:00:16 me-ThinkPad-X1-Carbon-7th systemd[4014]: Started flatpak docume>
lines 1-14/14 (END)

```
This bug keeps on returning, first reported in 2020: see discussion: [https://github.com/flatpak/xdg-desktop-portal/issues/553](https://github.com/flatpak/xdg-desktop-portal/issues/553)
```
 ps aux | grep xdg
me          4215  0.0  0.1 475736 10372 ?        Ssl  10:00   0:00 /usr/libexec/xdg-desktop-portal
me          4233  0.0  0.0 462528  4972 ?        Ssl  10:00   0:00 /usr/libexec/xdg-document-portal
me          4236  0.0  0.0 235488  4504 ?        Ssl  10:00   0:00 /usr/libexec/xdg-permission-store
me          4245  0.0  0.7 1263904 58772 ?       Ssl  10:00   0:00 /usr/libexec/xdg-desktop-portal-gnome
me          4307  0.0  0.3 451848 24936 ?        Ssl  10:00   0:00 /usr/libexec/xdg-desktop-portal-gtk
me         29032  0.0  0.0   3508   924 ?        S    10:03   0:00 bwrap --args 41 xdg-dbus-proxy --args=44
me         29033  0.0  0.0 161744  4648 ?        Sl   10:03   0:00 xdg-dbus-proxy --args=44
me        152815  0.0  0.0  18716  4844 pts/0    S+   10:27   0:00 systemctl --user status xdg-document-portal.service
me        161341  0.0  0.0   9204  1536 pts/2    S+   10:30   0:00 grep --color=auto xdg

```

---

### Post by Paddy Landau on 2023-01-29
> **1fallen said:**
> Read your edit, please check:
```
$ systemctl --user status xdg-document-portal.service
[COLOR=#008000]&#9679;[/COLOR] xdg-document-portal.service - flatpak document portal service
     Loaded: loaded (/usr/lib/systemd/user/xdg-document-portal.service; static)
     Active: [COLOR=#008000]active (running)[/COLOR] since Sun 2023-01-29 15:19:21 GMT; 2h 28min ago
   Main PID: 2280 (xdg-document-po)
      Tasks: 9 (limit: 18532)
     Memory: 1.8M
        CPU: 112ms
     CGroup: /user.slice/user-1000.slice/user@1000.service/session.slice/xdg-document-portal.service
             &#9500;&#9472;2280 /usr/libexec/xdg-document-portal
             &#9492;&#9472;2289 fusermount3 -o rw,nosuid,nodev,fsname=portal,auto_unmount,subtype=portal -- /run/user/1000/doc

Jan 29 15:19:21 glinda systemd[2223]: Starting flatpak document portal service...
Jan 29 15:19:21 glinda systemd[2223]: Started flatpak document portal service.
```
> **1fallen said:**
> This bug keeps on returning, first reported in 2020: see discussion: [https://github.com/flatpak/xdg-desktop-portal/issues/553](https://github.com/flatpak/xdg-desktop-portal/issues/553)
I see that I have the same problem, so I've upvoted the report. But it was reported in 2020, so I don't suppose that it'll ever be fixed.
```
$ ps aux | grep xdg
paddy       2280  0.0  0.0 695096  7380 ?        Ssl  15:19   0:00 /usr/libexec/[COLOR=#ff0000]xdg[/COLOR]-document-portal
paddy       2283  0.0  0.0 244820  5236 ?        Ssl  15:19   0:00 /usr/libexec/[COLOR=#ff0000]xdg[/COLOR]-permission-store
paddy       3165  0.0  0.0 632472 14076 ?        Ssl  15:19   0:00 /usr/libexec/[COLOR=#ff0000]xdg[/COLOR]-desktop-portal
paddy       3169  0.0  0.4 1837396 75364 ?       Ssl  15:19   0:01 /usr/libexec/[COLOR=#ff0000]xdg[/COLOR]-desktop-portal-gnome
paddy       3217  0.0  0.1 351340 27244 ?        Ssl  15:19   0:00 /usr/libexec/[COLOR=#ff0000]xdg[/COLOR]-desktop-portal-gtk
paddy      29551  0.0  0.0  17868  2396 pts/0    S+   17:48   0:00 grep --color=auto [COLOR=#ff0000]xdg[/COLOR]
```

---

### Post by #&amp;thj^% on 2023-01-29
> **Paddy Landau said:**
> 
I see that I have the same problem, so I've upvoted the report. But it was reported in 2020, so I don't suppose that it'll ever be fixed.


At least You did the right thing, Thank you Paddy

---

### Post by TheFu on 2023-01-29
> **Paddy Landau said:**
> No. I hadn't even heard of it until now! I've checked, and it's not even installed on my system.

Calibre can generate PDF files from online webpages and create a "magazine" to be read offline.  It was a shot in the dark. I used it before I learned about and setup a wallabag server instead.

---

### Post by Paddy Landau on 2023-01-30
I might try deleting the folder before rebooting to see what happens.

---

### Post by ajgreeny on 2023-01-30
Maybe symbolic link or something?
If you right click the file in both folders what does**Properties** tell you, if anything?

Just a shot in the dark but it may give us a clue.

---

### Post by Paddy Landau on 2023-01-30
> **ajgreeny said:**
> Maybe symbolic link or something?
If you right click the file in both folders what does**Properties** tell you, if anything?
I already tried that. The files look as if they are not the same: Although they are identical in content and name (and as stated earlier, they are actually the same file), their inodes are different, and there are no symbolic links involved. Only the mounts as described earlier.

I have a strong suspicion that flatpak is somehow involved, but my searches in this matter have uncovered nothing. I am clueless how this might work; I think that the "portal" mount has something to do with it. My problem is that searching for "portal" in this context returns only loads of irrelevant results.

[SIZE=3]**New result**[/SIZE]

I renamed the file in [FONT=courier new]/run/user/1000/doc/17a1f69b[/FONT], and the file in the original folder on disk disappeared!
I renamed the file back again, and the file in the original folder reappeared!
I tried this a couple of times, and the results are consistent.

What in blazes is going on?

I shall try deleting the file in [FONT=courier new]/run/user/1000/doc/17a1f69b[/FONT] to see what happens (I have a backup), but I'll wait a bit longer in case someone can explain what's going on.

---

