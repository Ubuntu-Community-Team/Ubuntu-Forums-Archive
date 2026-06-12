---
title: "[ubuntu] Recursive command to remove dirs &amp; files"
date: 2014-02-27
forum: General Help
---

### Post by bc.haynes on 2014-02-27
I have a file system that I need to remove part of it. I got into it, and there are myriad folders and files. I tried
```
sudo rmdir -R <foldername>
```
and evidently the **-R** has been dropped from **rmdir** (I guess it is too dangerous for some to use).

How can I remove the current folder and all child folders and files without having to spend all night **cd**.ing and **rmdir**.ing and **rm**.ing files?

A response will save me several hours work.

Thanks   -   Ben

---

### Post by lisati on 2014-02-27
*Thread moved to **General Help**.*

Forum Feedback and Help is for reporting technical problems with the website here (i.e. broken features), or ask questions pertaining to forum features.

---

### Post by bc.haynes on 2014-02-27
Thank you lisati I was going to ask y'all to move it to General because I realised it was in the wrong place. You moved it without my asking. Thank you, Ben

---

### Post by steeldriver on 2014-02-27
The *rmdir *command only removes *empty *directories - to remove non-empty dirs you need to use rm

```
sudo rm -rf <foldername>
```

[COLOR=#ff0000]**BE ABSOLUTELY SURE YOU TYPE THE FOLDERNAME CORRECTLY - THERE IS NO UNDO**[/COLOR]. Be especially careful if the foldername contains special characters or spaces.

---

### Post by bc.haynes on 2014-02-27
Thank you, **steeldriver**, that's twice you have saved me some time & toil.

Thanks for the heads-up warning.

---

### Post by papibe on 2014-02-27
EDIT: sorry late response.

Hi bc.haynes.

**[COLOR="#FF0000"]WARNING[/COLOR]**: there's no comeback if this you ran this on the wrong directory:
```
rm -rf foldername
```
-r for recursive
-f for force, no questions asked.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by bc.haynes on 2014-02-27
This is how it went"
```
sent 138.91K bytes  received 12.73K bytes  101.10K bytes/sec
total size is 172.13M  speedup is 1135.08 (DRY RUN)
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1070) [sender=3.0.9]

```
Code 23 is "Partial transfer due to error"
```
rsync -vaxzPXhn /Source/ /Destination
```
Was what I used.

What did I do wrong?

---

### Post by papibe on 2014-02-27
Were you able to remove recursively the directory you wanted to delete?

How the 'rsync' command is related to your original concern? If it's not, opening another thread for that specific problem would get more attention to it.

Regards.

---

### Post by bc.haynes on 2014-02-27
I did a -vv (very verbose) Dry Run and got this:
```
total: matches=0  hash_hits=0  false_alarms=0 data=0

sent 135.68K bytes  received 12.83K bytes  99.00K bytes/sec
total size is 171.68M  speedup is 1156.05 (DRY RUN)
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1070) [sender=3.0.9]
ben@MissionControl:~$ 

```
I removed an old rsnapshoy dir & all children. Then I used the /snapshot directory to store rsync info on a USB pendrive.

---

### Post by bc.haynes on 2014-02-27
@ **papibe** - I shall do as you suggest and start a new thread about this.

---

### Post by Dennis N on 2014-02-27
> **bc.haynes said:**
> I have a file system that I need to remove part of it. I got into it, and there are myriad folders and files. 
How can I remove the current folder and all child folders and files without having to spend all night **cd**.ing and **rmdir**.ing and **rm**.ing files?
Thanks   -   Ben
Seems to me the file manager would take care of this if you just delete the folder in question. All the contents (subfolders and files) go with it - the recursive removal is implied. You could run it as root if you need to.

---

