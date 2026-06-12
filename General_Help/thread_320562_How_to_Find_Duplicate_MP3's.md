---
title: "How to Find Duplicate MP3's?"
date: 2006-12-17
forum: General Help
---

### Post by SendDerek on 2006-12-17
Hello!

I'm trying to do some "house cleaning" on my external HDD and I would like to do a search for duplicate MP3's.

I have tried to use KleenSweep, but that for some reason won't scan my external HDD.  There are no error messages, it just finishes with no results.  I know I have duplicate MP3's.

Is there a program that any of you would recommend for me?  I would like to do this the graphical way and find all duplicates in all sub-directories as well.

Thanks for any help in advance!

---

### Post by hanzomon4 on 2006-12-17
I'm sorry I only know how use cli tools for stuff like this. I would use the find command, just point it in the direction of your music folder and use the a wildcard *mp3... Here's amd example: ```
find /path/to/music/harddrive/or/folder -iname *mp3
``` 
This will give you a list of all the mp3 files "find" find's

---

### Post by SendDerek on 2006-12-17
> **hanzomon4 said:**
> I'm sorry I only know how use cli tools for stuff like this. I would use the find command, just point it in the direction of your music folder and use the a wildcard *mp3... Here's amd example: ```
find /path/to/music/harddrive/or/folder -iname *mp3
``` 
This will give you a list of all the mp3 files "find" find's

Forgive me if I'm not understanding fully, but won't that only find all my mp3's?  I want to find only duplicates.

And to clarify, I would like to be able to find duplicate songs with different file names.  

Ex:
musicfile.mp3  musicfileduplicate.mp3 are the same song, just different file names.

Thank you for your post!

---

### Post by lamego on 2006-12-17
I believe you are looking for this:
[http://ubuntu.wordpress.com/2005/10/08/find-duplicate-copies-of-files/](http://ubuntu.wordpress.com/2005/10/08/find-duplicate-copies-of-files/)

---

### Post by hanzomon4 on 2006-12-17
> **SendDerek said:**
> Forgive me if I'm not understanding fully, but won't that only find all my mp3's?  I want to find only duplicates.

And to clarify, I would like to be able to find duplicate songs with different file names.  

Ex:
musicfile.mp3  musicfileduplicate.mp3 are the same song, just different file names.

Thank you for your post!

Oh ok, sorry I don't know how to pull that one off

---

### Post by SendDerek on 2006-12-17
> **lamego said:**
> I believe you are looking for this:
[http://ubuntu.wordpress.com/2005/10/08/find-duplicate-copies-of-files/](http://ubuntu.wordpress.com/2005/10/08/find-duplicate-copies-of-files/)

Great!  Thank you for that link.

It led me to three different programs that might be able to help me out!

---

### Post by SendDerek on 2006-12-18
I tried fdupes and FSlint.  

I settled on FSlint because of the nice GUI and easy deletion tool. 

Thank you very much for the support!  This has been resolved.

---

