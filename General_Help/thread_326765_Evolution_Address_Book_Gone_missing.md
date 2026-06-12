---
title: "Evolution Address Book Gone missing"
date: 2006-12-28
forum: General Help
---

### Post by Stephen Shellard on 2006-12-28
I have been running a series of address books in evolution, but this morning one of them unaccountably dissapeared.  I think I was trying to delete an address book entry, but appear to have delted the entire address book.  No warning that anything this radical was about to happen was given.   

Having made various attempts to locate the missing file, I then attempted to recreate the address book, using the same name,  Initally this seemed fine, until I attempted to make a first entry in the new book.  An error message was returned saying that a file could not be accessed, but giving a path name and suggesting I check the existence of the file in question.  

In fact the file does exist.  It was located in the  .evolution\addressbook\localfolder\1167299063.4940.0@zoostorm  (zoostorm being the name of my computer).  It is a 12KB file called addressbook.db

I am thinking, this is the file I thought I had deleted, but have tried to open it with various applications including a text editor which returns the following:  gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.

Have I run into some kind of bug?  Is my address book retrievable or must I start manual entry all over again?  Help welcome.

Stephen

---

### Post by bapoumba on 2006-12-29
Well, all I got in my .evolution/addressbook/* are .xml or .db files :/

---

### Post by Stephen Shellard on 2006-12-30
Well, thank you for this reply, though in all honesty, I don't really understand it's relevance.  The file I mentioned was a .db file, not inconsistent with your own experience as far as I can tell.  Please bear in mind that, in Ubuntu terms I am a mere one cupper and should perhaps not have strayed from the Absolute Beginners forum.  

I have now, having got over the initial shock of losing it, recreated my address book from scratch, but would still be interested in answer to my original questions:  Have I run into some kind of bug? Is my address book retrievable?

As a complete aside:  Why does everyone post to forums under obscure pseudonyms:  I seem to be the only person in the Ubuntu community revealing their real name.  Do I run some kind of security risk by so doing, or am I simply culturally marginal?

---

### Post by bapoumba on 2006-12-30
> **Stephen Shellard said:**
> 
In fact the file does exist.  It was located in the  .evolution\addressbook\localfolder\1167299063.4940.0@zoostorm  (zoostorm being the name of my computer).  It is a 12KB file called addressbook.db
Sorry, I read that part too quickly (just the first part) :/
Anyway, a 12KB file is too small, it was corrupted one way or another. This file, with the other ones, is saved when I backup my evolution settings. Could be a good idea for you to keep a backup of .evolution, so that if anything happens, at least you do not loose everything. (I just make a tar.gz file that I copy in a safe place).

Not sure this is a bug, unless you can reproduce it. I tried removing contacts, went smoothly ;)

Cheers and Happy Holidays.

---

### Post by Stephen Shellard on 2006-12-30
Sound advice. Thank you.

---

