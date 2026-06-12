---
title: "Homedir GONE"
date: 2016-06-01
forum: General Help
---

### Post by Henry_Methorst on 2016-06-01
suddenly some of my files are not showing up in the browser. I decide to reboot and come back to a totally default home screen and home folder (all my files are gone).

When I go to /home/ and type ```
ls -la
```

I get:

```
henry@kubuntu:/home$  ls -la
total 12
drwxr-xr-x  3 root  root  4096 May  4 13:40 .
drwxr-xr-x 25 root  root  4096 May  7 04:23 ..
lrwxrwxrwx  1 root  root    44 May  4 13:34 .directory -> /etc/kubuntu-default-settings/directory-home
drwxr-xr-x 22 henry henry 4096 Jun  1 18:44 henry



```

So it looks like home has a symlink but doesn't (or wont) do anything when I unlink:

```
Sudo unlink /etc/kubuntu-default-settings/directory-home
```

rm doesn't work either! I cannot unlink or delete the symlink, and I have to assume this is the problem!!!

---

### Post by Impavidus on 2016-06-01
That unlink command should have removed the link target, not the link itself. It should have made the link invalid though. And no output means success. The same for rm, which is just unlink with a lot of options. Note that unlink isn't named like that because it can delete symlinks. It can remove everything, which from the filesystem's point of view means removing hardlinks.

But that link doesn't seem a problem to me. I've never seen it before. Something Kubuntu-specific perhaps?

Do (or did) you by any chance have a separate home partition? And I don't really get it. If your home directory (/home/username) is gone, login would normally be impossible. Is your home directory gone or is it empty?

---

### Post by Henry_Methorst on 2016-06-01
From where I sit, all my files in /home/henry are gone, and replaced with a new, totally clean (default) /home/henry.   Somehow over 300 gigs of data has just VANISHED!


I am praying it is related to this symlink, which I cannot remove!

*edit*   And no, my /home partition is on the same as / 


 sos!

---

### Post by Henry_Methorst on 2016-06-02
It is just like a new user, with the exact same name as mine was created and replaced it.

---

