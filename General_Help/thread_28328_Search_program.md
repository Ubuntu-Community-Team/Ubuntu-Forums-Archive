---
title: "Search program"
date: 2005-04-19
forum: General Help
---

### Post by eXidos on 2005-04-19
alright im still new to linux, but the other distro's come with a "search for.." program i cant seem to find one installed, what program do i install from synaptic if there is one?

---

### Post by andvaranaut on 2005-04-19
What's wrong with Places > Find files? ;)

However, my personal favourite is slocate, which you must use from the command prompt.

Hope this helps, andvaranaut

---

### Post by bored2k on 2005-04-19
[QUOTE=andvaranaut]What's wrong with Places > Find files? ;)

However, my personal favourite is slocate, which you must use from the command prompt.

Hope this helps, andvaranaut[/QUOTE]
 I second that, locate owns Beagle, Mac's Spotlight or whatever ;).

---

### Post by bk452 on 2005-04-21
[QUOTE=andvaranaut]What's wrong with Places > Find files? ;)

However, my personal favourite is slocate, which you must use from the command prompt.

Hope this helps, andvaranaut[/QUOTE]

This sounds like exactly what I need.  Can you point me to a reference on using it?  Hopefully one that a newbie can decipher.

---

### Post by bored2k on 2005-04-21
[QUOTE=bk452]This sounds like exactly what I need.  Can you point me to a reference on using it?  Hopefully one that a newbie can decipher.[/QUOTE]
 From command prompt just type
locate whatever

And it will find that file, wherever it is in seconds.
It doesn't really search your computer, it uses an index file wich automatically updates, so if you need to find something that you recently changed [like, 2 or 3 minutes before], type sudo updatedb to update the index  then use locate.

---

### Post by bk452 on 2005-04-21
[QUOTE=bored2k]From command prompt just type
locate whatever

And it will find that file, wherever it is in seconds.
It doesn't really search your computer, it uses an index file wich automatically updates, so if you need to find something that you recently changed [like, 2 or 3 minutes before], type sudo updatedb to update the index  then use locate.[/QUOTE]

Wow.  I got it to work!! Thanks !!

---

### Post by bored2k on 2005-04-21
[QUOTE=bk452]Wow.  I got it to work!! Thanks !![/QUOTE]
 Remember: If you make a lot of changes and want to search for something right away, do sudo updatedb first ;).

---

### Post by bk452 on 2005-04-21
[QUOTE=bored2k]Remember: If you make a lot of changes and want to search for something right away, do sudo updatedb first ;).[/QUOTE]

I'll have to do that every AM.  Thanks for the info.  How do I search for the contents of a file? I do a lot of research and a lot of my files are pdfs and htmls.

---

