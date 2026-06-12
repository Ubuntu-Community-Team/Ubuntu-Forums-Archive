---
title: "Libreoffice 4.0.3.3 on 12.04: Writer closes when I copy something ..."
date: 2013-05-28
forum: General Help
---

### Post by Bucky Ball on 2013-05-28
Hi all,

Bit desperate here. Got a ton of stuff due tomorrow night using Libreoffice Writer and everytime I copy something it crashes, closes, disappears. This is a potential nightmare. I did notice an update happen for it over the last while so maybe that is at the bottom of things because it was fine about a week ago. I have, naturally, had a search around for a fix, reset the user profile, switched Java and experimental features on and off and still nothing.

Urgent to fix this so all and any ideas welcome ... tnx in advance. ;)

PS: I thought it might have something to do with copying the whole twenty nine page document, which wasn't a problem before but trying anything at this point, but have found that copying any text causes Libreoffice to close, even a word or sentence. Crash happens if using CTL+C or Edit>Copy. 

PPS: I even restarted the machine out of desperation knowing it probably would make no diff!

* Update: When I launch LO in a terminal and replicate the copy close/crash, I get this error message:

```
WARNING: gnome-keyring:: couldn't connect to: /tmp/keyring-2Rfpvo/pkcs11: No such file or directory
```

Eek. I might have to leap into Win to get this work done ...

---

### Post by Bucky Ball on 2013-05-28
Just to add a peculiarity. I can open all files fine in Openoffice in Win7, and copy and paste fine, but when I try to open the document I was working on in Ubuntu it says it is locked and would I like to open a read-only copy or a copy. When I check in the folder, sure enough, there is a locked copy of the file there. So I deleted and file opened fine, copy and pasted fine. Thought that might fix so back to Ubuntu, same problem. Back to Win so I can get some work done, the locked file has appeared again! What's with that? 

So, not sure if this is causing the error. I'm just going to now check if the locked file is showing up in Ubuntu and delete it and try again to find out. Wish me luck ... I don't have time for this! But I find it is at times like this something inevitably breaks, when you least need it to.

PS: Another peculiarity; I have seven title pages at the beginning of the document, no headers or footer or page numbers. Page numbering starts with page one on actual page eight, if you follow. Or at least it should. In Ubuntu the numbering has for no reason I can fathom skipped a page and now starts with one on what should be numbered page two and page one has no number, just a blue block where one should be. 

The strangest part is when I open the doc in Win the page numbering is fine! File is .odt BTW. That is the stuff of another thread but no idea about what happened there. Didn't even notice when it actually happened, just noticed it on a print out which is when things started getting pear-shaped so might be connected. (One of the reasons this seemed to kick off was that I noticed the numbers were wrong so rather than wading through fixing it I was attempting to copy the copy from the mis-numbered document to an old version where the numbering is correct and the copy thing started happening, and probably the locked file.)

* Update: Back in Ubuntu (/home sweet /home). Further development is yes, there is a locked file there. I delete, unlocked file opens fine, I copy text, LO closes leaving a new locked file. I'm starting to lean toward this self-spawning locked file anomaly being related to the cause of the issue as it was fine before.

---

### Post by Bucky Ball on 2013-05-28
And an update on all that; na, that wasn't the problem. I managed to disassociate the locked file by deleting it, opening the file and closing it. All worked fine and the locked file disappeared. Which is when I noticed that when I open the same file, copy text and crash LO, then the locked file remains until I delete it.

---

### Post by Bucky Ball on 2013-05-28
All happening and I may have found the root to my problem. The partition the file is on is now not mounting. It is showing up in the file manager and I can click on it but nothing happens. It doesn't change from the directory the file manager is displaying. Right click to mount and I can even do that but it doesn't mount. Right click again and 'Mount' is the only thing available. 

The odd thing is this partition is still working fine in Win. I am aware that Win is sometimes not so fussy when it comes to disk errors. Who knows what's happening? I'll go back and have another check in the morning but in the meantime, to bed ...

* Another anomaly before I go; Gparted tells me the partition is mounted! File manager not. Hmm. There is only one HDD in this laptop, incidentally, so it is odd, but not unheard of, that this partition dies and not the whole drive. Also, it is an NTFS partition which is shared between Win and Ubuntu.

---

### Post by Bucky Ball on 2013-05-29
I'm starting to wonder if the LO update requires OpenJDK. It doesn't appear in the list when I Tools>Options>Java>Tick 'Use Java'. Sun and two Oracle ones do. Tried 'em all and no different.

I also uninstalled LO, installed OO, which didn't close when I copied the whole document but didn't allow me to use macros and a bunch of other things because they required Java. Problem was it was ticked for Java but there was no Java options in the list for me to select and OO to use. So back to LO. No different. Same copy=crash/close. 

So if anyone has any ideas how to get the Java selections to appear in OO or any idea about the original predicament, feel free ...

* Update: Something of a breakthrough and a clue. The document I'm having trouble with has quite a few inserted pictures. When I copy/paste a text only document all seems fine. This narrows it down a little. BTW I can access the partition the file is on now no problems.

* Update to the update: Yep, that's it. Opened the dodgy document, copied a huge slab of text only, no pics, copy/paste no issue. So LO is having a problem copying graphics. But no, that's not it either. I just went through the whole 28 page document and copy/pasted all graphics to a new file. No issue. It's only when I try and copy the whole document ... all graphics are .png so there's no odd one out, at least haven't found one.

* Nailed it. When I try and copy a .png and text at the same time, crash/close. One or the other, fine. Weird. No fix though.

---

### Post by Bucky Ball on 2013-05-29
After babbling to myself for the last twelve hours, I'd like to wrap this up succinctly.

* Fixed the numbering issue, which was the reason I tried to copy the whole document in the first place;
* Not sure the document itself is corrupted as opens and copies fine in Openoffice in both Xubuntu and Win 7;
* Can copy text or graphics but not both at once; cause the crash/closure of LO.

This issue isn't solved and I can replicate it easy enough, but for now I'm going to avoid copying the whole document and get on with it. ;)

---

