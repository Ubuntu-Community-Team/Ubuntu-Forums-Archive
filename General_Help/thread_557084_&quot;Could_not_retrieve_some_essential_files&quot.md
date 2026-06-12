---
title: "&quot;Could not retrieve some essential files&quot;"
date: 2007-09-22
forum: General Help
---

### Post by trommas on 2007-09-22
I use the newest wubi (7.10 alpha from yesterday)


When I choose read-only, it downloads the iso, then it starts searching my drive (d:), and after 3 seconds give the message: "Could not retrieve some essential files"

---

### Post by ago on 2007-09-24
Make sure you run the latest wubi available on website
Run wubi from commandline passing the "--debug" argument
You will see lots of message boxes
Let me know if there is any relevant message

---

### Post by trommas on 2007-09-24
The strangest thing...

When running from my download folder. It picks up a completly different iso in that folder (it's a different application iso) and tries to set this as the ubuntu iso - this of course fails.

If I run wubi from d root, it crashes after the first couple of dialogs.

If I run it from c and choose d for install - It goes to 7z: "Error: D:\ubuntu\install\gutsy-desktop-i386.is not a supported archive" and then "could not retrive some essential files"

---

### Post by ago on 2007-09-24
> **trommas said:**
> The strangest thing...

When running from my download folder. It picks up a completly different iso in that folder (it's a different application iso) and tries to set this as the ubuntu iso - this of course fails.

If I run wubi from d root, it crashes after the first couple of dialogs.

If I run it from c and choose d for install - It goes to 7z: "Error: D:\ubuntu\install\gutsy-desktop-i386.is not a supported archive" and then "could not retrive some essential files"

Make sure the ISO is a valid file, yo may want to redownload.
You can run wubi with the --debug flag to have some more info

---

### Post by trommas on 2007-09-25
> **ago said:**
> Make sure the ISO is a valid file, yo may want to redownload.
You can run wubi with the --debug flag to have some more info

The iso seems to be fine (it mounts nicely in DT), but I'll redownload the latest.

This was all the info I got using --debug

---

### Post by ago on 2007-09-25
> **trommas said:**
> The iso seems to be fine (it mounts nicely in DT), but I'll redownload the latest.

This was all the info I got using --debug


Hmm is D:\ubuntu\install\gutsy-desktop-i386.is  or D:\ubuntu\install\gutsy-desktop-i386.is**o**?

Also, when you run the installer some files are expanded in a random tmp folder in your profile, if you look at the log messages, when it comes to 7z it should mention the folder name. If you go in there, look if there is a iso.dll in the plugins folder

---

### Post by trommas on 2007-09-25
Latest iso and wubi, both located on D: root
Output:

1. DetectCD

2. cddrive=

3. DetectIso

4. IsValidIso isopath=d: \gutsy-desktop-i386.iso

5. C: \DOCUME~1\To\LOCALS~1\Temp\nsn161.tmp\7z
  2

7-Zip -- some copyright info

Processing archive: d: \gutsy-desktop-i386.iso

Error: d: \gutsy-desktop-i386.iso is not supported archive

6. isvalid

7. nocdinfo

8. -- nothing happens (the process hangs)

The tempfolder created on c: contains a lot of files (no folders), it contains a iso.dll file.

---

### Post by ago on 2007-09-25
hmm is the md5 of the ISO correct?
Try to go to the tmp folder created, then open a dos shell and run

7z -l /path/to/iso

---

### Post by trommas on 2007-09-25
> **ago said:**
> hmm is the md5 of the ISO correct?
Try to go to the tmp folder created, then open a dos shell and run

7z -l /path/to/iso

That command wouldn't run, but I guess you meant: 7z -| d: \gutsy-desktop-i386.iso

this loads for some time, then asks me which app I want to use to open the iso file

---

### Post by ago on 2007-09-25
> **trommas said:**
> That command wouldn't run, but I guess you meant: 7z -| d: \gutsy-desktop-i386.iso

this loads for some time, then asks me which app I want to use to open the iso file

no it should be L (to list the content of the file) if memory does not fail me. Just run "7z" with no arguments for a list of commands.

---

### Post by trommas on 2007-09-25
Silly me :)

Well I got the command right now it returns the same error message wubi made in the dialog: the archive is not supported.

This is the third iso this happens to, so I don't think that's the problem, maybe it's 7z?

---

### Post by trommas on 2007-09-25
Jippi!

I downloaded the latest 7z, put it in the temp folder.. And VOILA!

:):):):):)

---

### Post by trommas on 2007-09-25
Well, that joy latest long... :( 
I rebooted into ubuntu, but half way through, it dropped out to some shell ("box"-something)

This could be a fault in the latest iso though...

---

### Post by ago on 2007-09-25
> **trommas said:**
> Well, that joy latest long... :( 
I rebooted into ubuntu, but half way through, it dropped out to some shell ("box"-something)

This could be a fault in the latest iso though...

Hmm can you try to replace 7z.exe and iso.dll using the files from the iso? 
Don't copy the full folder only those 2 files

---

### Post by ago on 2007-09-26
also try rev 309

---

