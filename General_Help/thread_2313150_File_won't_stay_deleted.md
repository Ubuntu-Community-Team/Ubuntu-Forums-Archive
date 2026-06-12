---
title: "File won't stay deleted"
date: 2016-02-10
forum: General Help
---

### Post by John Jason Jordan on 2016-02-10
Some time ago I created an ISO image of a movie DVD, file size 4.6 GB. I can delete it with either Thunar or the command line, but a few hours later it reappears. Earlier today I renamed it, just to see what would happen. A few hours later there were two files, the original and the renamed file. Interestingly, if I double-click on either file it launches K3b (my default burner app), but after a bit K3b errors out saying that it can't open the file.

Xubuntu 14.04.3, up to date. File system for all drives is ext4. The drive in question is a 5 TB external USB 3.0 drive, about one year old. There have been no other drive anomalies and I have no reason to believe that there might be a problem with the disk. I have Palimpsest, but it can't do diagnostics on the drive because it is external.

I could use some suggestions!

---

### Post by Vladlenin5000 on 2016-02-10
What happens when you delete it using SHIFT+Delete?

---

### Post by ajgreeny on 2016-02-10
Strange!

What happens if you **shred** the file with command ```
shred -vzu /path/to/file
```

---

### Post by John Jason Jordan on 2016-02-10
> **Vladlenin5000 said:**
> What happens when you delete it using SHIFT+Delete?

It stays deleted! That is, I did as you suggest this morning at about 8:30, it is now noon, and it hasn't yet reappeared. Previously I always deleted it by right-clicking on it and selecting Delete in Thunar, or using rm from the command line, including using sudo, yet it always reappeared within an hour or less. I'm crossing my fingers that it stays deleted.

But I'm curious what Shift-Delete in Thunar does that ordinary deletes and deleting as root do not.

> **ajgreeny said:**
> Strange!
What happens if you **shred** the file with command ```
shred -vzu /path/to/file
```

Thanks for the suggestion. Vladlenin5000's 'shift-delete' method appears to have worked, so I didn't get to try your suggestion.

---

### Post by furtom on 2016-02-10
> **John Jason Jordan said:**
> But I'm curious what Shift-Delete in Thunar does that ordinary deletes and deleting as root do not.

I think the file size has something to do with it. You can set the space limit of the trash somewhere. Sorry, I forget how now. But in any case, I'd bet dollars to donuts the limit is exceeded by your 4.6-gig file.

To answer your question, shift+delete bypasses the trash and permanently deletes a file.

EDIT: I'm thinking... (always a dangerous proposition). Did you install Kubuntu or did you install Ubuntu and then later install KDE desktop?

SECOND EDIT: Never mind. I see you say you are running Xubuntu. I was thrown off by the K3b reference.

---

### Post by John Jason Jordan on 2016-02-10
I spoke too soon. I was away from the computer for a couple hours and when I returned the file was back. Sigh. :(

So this time I used vjgreeny's suggestion: shred -vzu /path/to/file. The command executed in four passes and the file looks gone again. We shall see.

Regarding space limit of the Trash, I'm sure I've had as much as 30-40 GB in the Trash in the past. Besides, the Shift-Delete solution that I tried before bypasses the Trash, or so I understand. And remember, the file system is ext4, which can hold a single file up to 16 TB. My largest disk is only 5 TB, so it will be a long time before I run into that limitation.

I should add that once yesterday I tried opening the file in K3b (it's an ISO of a DVD). K3b puked on it, saying that it couldn't open the file. It's as though the file really has been deleted all this time and what I'm seeing is some ghost image. But the ghost image appears in both Thunar and the command line. And the shred command attacked it with glee. So maybe it really is there.

---

### Post by lisati on 2016-02-10
How did you download the file in the first place? I'm wondering if you've got a download manager of some description active which has the mistaken notion that the download failed and needs to be restarted.

---

### Post by John Jason Jordan on 2016-02-10
> **lisati said:**
> How did you download the file in the first place? I'm wondering if you've got a download manager of some description active which has the mistaken notion that the download failed and needs to be restarted.

It is not a download The file is one I created myself from a DVD that I own, using K3b.

---

### Post by lisati on 2016-02-10
> **John Jason Jordan said:**
> It is not a download The file is one I created myself from a DVD that I own, using K3b.
My bad, I think I better re-read the whole thread!

---

### Post by furtom on 2016-02-11
> **John Jason Jordan said:**
> I spoke too soon. I was away from the computer for a couple hours and when I returned the file was back. Sigh. :(

So this time I used vjgreeny's suggestion: shred -vzu /path/to/file. The command executed in four passes and the file looks gone again. We shall see.

Regarding space limit of the Trash, I'm sure I've had as much as 30-40 GB in the Trash in the past. Besides, the Shift-Delete solution that I tried before bypasses the Trash, or so I understand. And remember, the file system is ext4, which can hold a single file up to 16 TB. My largest disk is only 5 TB, so it will be a long time before I run into that limitation.

I should add that once yesterday I tried opening the file in K3b (it's an ISO of a DVD). K3b puked on it, saying that it couldn't open the file. It's as though the file really has been deleted all this time and what I'm seeing is some ghost image. But the ghost image appears in both Thunar and the command line. And the shred command attacked it with glee. So maybe it really is there.

Very interesting. I admit, I'm stumped. I like the idea of some download manager or especially torrent replacing the file, but you say that's not possible...

Just out of curiosity, where is the file exactly?

---

### Post by steeldriver on 2016-02-11
... or some backup software that's periodically rsync'ing it from a backup somewhere?

---

### Post by HermanAB on 2016-02-11
I would wait for the Chessire cat to reappear and then use lsof to see if something is holding the file open.  An open file won't delete.  The file could also be marked as immutable and then won't delete either.  So check for that too.  Finally, use fsck on the disk.

---

### Post by matt_symes on 2016-02-11
Hi

If it keeps coming back try putting a write watch on the parent directory using auditd.

```
sudo apt-get install auditd
```

Here's an example.

There's nothing in the directory ~/temp

```
matthew-xu-16-04:/home/matthew:0 % ls temp
``` 

Add a write (**-p w**) watch (**-w**) on the directory  **/home/matthew/temp** and tag it with the keyword **file-created**. The keyword allows searching later.

```
matthew-xu-16-04:/home/matthew:0 % sudo auditctl -w /home/matthew/temp -p w -k file-created
``` 

Create a file in that directory using the touch command.

```
matthew-xu-16-04:/home/matthew:0 % touch temp/new-file
```

Use ausearch and the keyword **file-created** to get the entry for the above watch. (any write to that directory will be logged so there may be a number to trawl though)

```
matthew-xu-16-04:/home/matthew:0 % sudo ausearch -k  file-created
----
time->Fri Feb 12 02:07:52 2016
type=CONFIG_CHANGE msg=audit(1455242872.035:837): auid=4294967295 ses=4294967295 op="add_rule" key="file-created" list=4 res=1
----
time->Fri Feb 12 02:08:02 2016
type=PROCTITLE msg=audit(1455242882.135:840): proctitle=746F7563680074656D702F6E65772D66696C65
type=PATH msg=audit(1455242882.135:840): item=1 name="**temp/new-file**" inode=11665747 dev=08:02 mode=0100664 **ouid=1000 ogid=1000** rdev=00:00 nametype=CREATE
type=PATH msg=audit(1455242882.135:840): item=0 name="temp/" inode=11666416 dev=08:02 mode=040775 ouid=1000 ogid=1000 rdev=00:00 nametype=PARENT
type=CWD msg=audit(1455242882.135:840):  cwd="/home/matthew"
type=SYSCALL msg=audit(1455242882.135:840): arch=c000003e syscall=2 success=yes exit=3 a0=7ffd96fc3dfc a1=941 a2=1b6 a3=691 items=2 **ppid=2617 pid=21337** auid=4294967295 **uid=1000 gid=1000 euid=1000 suid=1000** fsuid=1000 egid=1000 sgid=1000 fsgid=1000 tty=pts9 ses=4294967295 **comm="touch" exe="/bin/touch"** key="file-created"

```

I highlighted some information that gets logged above. Scroll the code block as most of the highlighted items are to the right. 

Remove the watch with **-W**

```
matthew-xu-16-04:/home/matthew:0 % sudo auditctl -W /home/matthew/temp -p w -k file-created 
matthew-xu-16-04:/home/matthew:0 % 
```

If it gets logged there should be plenty of information for you to track down what is creating the file.

Kind regards

---

### Post by Bucky Ball on 2016-02-11
Delete the file. Empty the trash. In that order.

---

