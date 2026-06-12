---
title: "Firefox extensions not installing within Ubuntu"
date: 2007-05-06
forum: General Help
---

### Post by Robbyx on 2007-05-06
I am using a dual boot system. From within Ubuntu- linux I am unable to install any extensions.

My profile is on an ntfs drive that has read write access for linux.

The firefox error log shows 

No chrome package registered for chrome://adblock/skin/adblock-icon.png .

I would very much like some help debugging this problem. Has anyone solved it?

---

### Post by MoLE on 2007-05-12
Can you clarify your setup at all?  Are you using the same profile for firefox in both Windows and Ubuntu?  If you're doing this to keep your browser settings synchronised, you might want to consider something like google browser sync or foxmarks.

Using an ntfs drive as a shared drive in both Win and Ubuntu is potentially risky still, and I suspect you may be having difficulties with permissions on the directories you are accessing.

---

### Post by Robbyx on 2007-05-16
> Can you clarify your setup at all? Are you using the same profile for firefox in both Windows and Ubuntu? If you're doing this to keep your browser settings synchronised, you might want to consider something like google browser sync or foxmarks.


I am able to see the book marks in windows and ubunu. They seem to be correct in both. The problem arises because of the extensions. I have so far failed to add any new ones in Ubuntu. In Ubuntu none of the extensions are working. I created a new logical drive on my serial drive. I can see it in Windows but not Ubuntu. I intended to relocate the profile's data  to the new drive, but can do so because I can not see it in ubuntu.

It has been suggested that I should not use the same profile for linux and Windows but I do not know how to share the bookmarks but not the extensions. Do you know?

> I suspect you may be having difficulties with permissions on the directories you are accessing.

I think so as well but looking at the owner of the linux directory  /home/robin/.mozilla/firefox

I find that I am the owner with full permission to change the files, etc.

There is a plugins directory below .mozilla but that only has a few plugins in it.

Robin

---

### Post by MoLE on 2007-05-17
> **Robbyx said:**
> 
It has been suggested that I should not use the same profile for linux and Windows but I do not know how to share the bookmarks but not the extensions. Do you know?


I work around this problem by using the [google browser sync ]("http://www.google.com/tools/firefox/browsersync/") extension, installed independently on both systems.  I choose just to synchronise my bookmarks, nothing else.  A fresh install of firefox would be prudent before pursuing this solution.

---

### Post by Robbyx on 2007-05-17
It looks as if I have to go down your route. Thanks for your suggestion.

Robin

---

