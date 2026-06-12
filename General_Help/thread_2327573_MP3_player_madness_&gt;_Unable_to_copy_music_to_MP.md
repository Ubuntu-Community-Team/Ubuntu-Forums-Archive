---
title: "MP3 player madness &gt; Unable to copy music to MP3 player"
date: 2016-06-12
forum: General Help
---

### Post by GeordieJedi on 2016-06-12
Hi there.

I'm having some trouble copying some music (MP3s) to an MP3 player.

My friend has 2x no-named-brand and
1x Samsung (yp-u2 zb /xsa) model MP3 players.

I'm trying to copy his music to his MP3 players (as hes not very technically minded).

However I'm really struggling, I'm not able to copy any of his music accross any of
the MP3 players.

I'm getting a few different error messages.

I was suspecting a permissions problem, but it seems that it may be even more obsucre.


Troubleshooting steps.

01. (Trying to copy using the GUI). 
Fails, error message = access denied. Could not write to '/media/30A3-239E/'

02. (Trying some mount commands)

2.1. 
```
df
```
results=
```
/dev/sdc1
```


2.2.
```
ls -l /mnt/device/sdc1
```
results =
```
ls: cannot access /mnt/device/sdc1: No such file or directory
```

```
 = ls -l /media/shared
```
result =
```
ls: cannot access /media/shared: No such file or directory
```

03. Now the bizarre thing is, when I plug in the MP3 players, they seem to be recognised
as I will get a prompt from KDE/dolphin asking me what I want to do with the device.
I can then mount the device, look around its dirs and see music already there.

But If I try to copy or move any music accross to the MP3 player, I will get the error
messages from point 1 (as I was just trying to use the GUI for convenience).


04. For the sake of compltededness, I have also tried to do the same using Windows 7
but get the same/similar results, and I'm unable to copy his music accross to his
MP3 player devices.


Any help or advice would be greatly appreciated

Useful information =
OS = Ubuntu 12.04
Kernel =3.2.0-104-generic-pae-(i686)
DE = KDE version = 4.8.5

MP3 players File System = VFAT
Samsung (yp-u2 zb /xsa) file system = VFAT

---

### Post by X-RED_Tech on 2016-06-12
> **GeordieJedi said:**
>  I have also tried to do the same using Windows 7
but get the same/similar results, and I'm unable to copy his music accross to his
MP3 player devices.

So it has nothing to do with Ubuntu specifically, it's the players flash memory being somehow locked and possibly requiring some proprietary software, or corrupt (mounted as read-only).
No name mp3 players usually behave like any other USB mass storage devices -and- what they usually don't have is a sophisticated software/firmware 'locking' mechanism nor require proprietary software.

First things first, backup (if needed). You can do that simply by copying the contents as you can read those drives.
I would suggest checking their settings menus anyway. Look for access, permitions, etc. And look for "format" and try that. Perhaps it's all it needs.

---

### Post by ajgreeny on 2016-06-12
With the mp3 player attached and mounted so you can see the files, show us the output of command **mount**

---

