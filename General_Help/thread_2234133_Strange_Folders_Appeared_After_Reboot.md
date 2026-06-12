---
title: "Strange Folders Appeared After Reboot"
date: 2014-07-12
forum: General Help
---

### Post by danbuz on 2014-07-12
Hi there,

Today after I rebooted my syystem I noticed strange folders in my home folder. I tried to delete them after I accessed thunar as root, but no success. The process of deleting is lasting forever, and nothing happens. When I try to see the size of the folders, also "calculates" the size forever (I canceled the process after 30 minutes). What could cause this. Searched for solution on the web and found nothing. 

Here is a screenshot:

 [ATTACH=CONFIG]254676[/ATTACH]

Thanks in advance guys..

---

### Post by Bucky Ball on 2014-07-12
*Thread moved to **General Help**.*

I'm guessing the new ones are the two with non-sensical names?

---

### Post by ajgreeny on 2014-07-12
How did you start thunar as root?

What does ```
**ls -l**
``` from a terminal tell you about those folders?

---

### Post by sandyd on 2014-07-12
> **ajgreeny said:**
> How did you start thunar as root?

What does ```
**ls -l**
``` from a terminal tell you about those folders?

Dont do that, if there are millions of files in the folder (which is what it looks like), ls will try to fetch the metadata for all those files which will take forever.

Instead, post the output of
```

ls -1Uf *foldername* > filelist
wc -l filelist

```
which will show how many files are actually in there. (-2 for current/parent directories)

---

### Post by danbuz on 2014-07-13
> **sandyd said:**
> Dont do that, if there are millions of files in the folder (which is what it looks like), ls will try to fetch the metadata for all those files which will take forever.

Instead, post the output of
```

ls -1Uf *foldername* > filelist
wc -l filelist

```
which will show how many files are actually in there. (-2 for current/parent directories)

Cannot load information for over 15 minutes... Just "thinking"..

---

### Post by sandyd on 2014-07-13
Hmm, it could be that there are a lot of files or possibly disk corruption as you indicated this was after a reboot. Have you checked the smart Data on the drive? Are you using any encryption of your home folder or your entire system?

---

### Post by danbuz on 2014-07-13
> **sandyd said:**
> Hmm, it could be that there are a lot of files or possibly disk corruption as you indicated this was after a reboot. Have you checked the smart Data on the drive? Are you using any encryption of your home folder or your entire system?


No encryption at all.. I noticed it after reboot because I didn't turn off my machine for at least 3 days (wasn't at home), so it could be something before that..

---

### Post by ajgreeny on 2014-07-13
> **sandyd said:**
> Dont do that, if there are millions of files in the folder (which is what it looks like), ls will try to fetch the metadata for all those files which will take forever.

Instead, post the output of
```

ls -1Uf *foldername* > filelist
wc -l filelist

```
which will show how many files are actually in there. (-2 for current/parent directories)
Why do you think there are so many files in the /home folder of the OP?  I did not mean to run that command from a root terminal, merely from the user's terminal, and without the -a option for ls that ls -l command will only show the folders and files in /home, certainly not millions.

---

### Post by Habitual on 2014-07-13
> **danbuz said:**
> it could be something before that..Have you used, or do you use Bleachbit?

---

### Post by danbuz on 2014-07-13
> **Habitual said:**
> Have you used, or do you use Bleachbit?

yes!?

---

### Post by sandyd on 2014-07-13
> **danbuz said:**
> yes!?

[http://askubuntu.com/questions/427647/strange-folder-in-my-home-folder-after-a-failed-run-of-bleachbit](http://askubuntu.com/questions/427647/strange-folder-in-my-home-folder-after-a-failed-run-of-bleachbit)

---

### Post by danbuz on 2014-07-14
> **sandyd said:**
> [http://askubuntu.com/questions/427647/strange-folder-in-my-home-folder-after-a-failed-run-of-bleachbit](http://askubuntu.com/questions/427647/strange-folder-in-my-home-folder-after-a-failed-run-of-bleachbit)

In my case [FONT=Ubuntu Mono]rm -r foldername* DOES NOT WORK . I left the computer for over 2 hours and nothing happened.
[/FONT]

---

