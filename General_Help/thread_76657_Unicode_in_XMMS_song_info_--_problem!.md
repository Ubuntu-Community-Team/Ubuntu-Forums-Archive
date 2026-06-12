---
title: "Unicode in XMMS song info -- problem!"
date: 2005-10-15
forum: General Help
---

### Post by Hikaru79 on 2005-10-15
I've got a bunch of Chinese and Japanese songs whose file info is encoded in UTF-8. Nautilus reads these filenames just fine, but when I try to load them in XMMS or BMP, its malformed and the tags show up as gibberish. Here's an example attached.
Anyone know how this can be fixed? Thanks =)

---

### Post by Ferio on 2005-10-15
This is happening to me, too, but with Spanish characters (ñ, á, é, í, ó, ú, Ñ, Á, É, Í, Ó, Ú). I would appreciate any help, too.

---

### Post by gmatt on 2005-10-15
I think the developers of XMMS decided to use ASCII instead of unicode so that might explain the problem, and if it is the problem nothing short of a new version of xmms or patch or hotfix will change it. Its not that bad though :D.

ps. hehe its funny how fermat would never prove any of his theorems :P or he would prove them in the margins of his book.

---

### Post by Hikaru79 on 2005-10-15
[QUOTE=gmatt]ps. hehe its funny how fermat would never prove any of his theorems :P or he would prove them in the margins of his book.[/QUOTE]
I'm glad someone finally got my siggie ;)

It's a pity that XMMS has no Unicode support, if what you say is true :( Is there a plugin, perhaps, that rectifies this?

---

### Post by Jonathan Drain on 2005-10-15
I have the same problem, I think it's just because xmms just hasn't been programmed to support unicode characters.

---

### Post by Ferio on 2005-10-16
But it used to support them, I've been using the Spanish characters in my tags when I was in Hoary Hedgehog, but I can't use them anymore :(

---

### Post by taavi on 2005-10-16
Are you sure that your system isn't lacking right fonts or codepages (glibc). It's just a guess but take a look with dpkg-reconfigure locales.

---

### Post by Hikaru79 on 2005-10-16
[QUOTE=taavi]Are you sure that your system isn't lacking right fonts or codepages (glibc). It's just a guess but take a look with dpkg-reconfigure locales.[/QUOTE]
taavi, I'm pretty sure the right codepages are installed since both Nautilus and the terminal can render the Unicode just fine. In fact, just about everything besides XMMS and BMP has no problem with it.

---

### Post by Ferio on 2005-10-16
Yes, exactly the same for me, my main encoding charset is UTF-8, Spanish + €, and everything is fine, but XMMS and K3B (I posted about this last in another thread).

---

### Post by Tristam on 2005-10-16
I'm not sure if this is the same thing.. I'm finnish and my problems were with letters ä, ö and å. Going to the XMMS Preferences -> Fonts, and enabling "Use fontsets" helped a lot :) Now the song titles in the playlist are mostly correct.. just an idea!

---

### Post by Ferio on 2005-10-16
Well, I don't know if it has solved Hikaru79's problem, but it has solved mine! Thank you very much! :p

---

### Post by learner on 2005-10-18
hey, guys, i am having a bit of problem too, can you guys tell me what font do you use, thanks.

---

### Post by akiss on 2005-10-19
xmms has problem viewing utf8 because its gtk+ based. But since BMP based on gtk2, it should support utf8. If you dont need certain plugin only avaiable for xmms, you should use BMP instead. 

Perhaps your mp3 files id3 tags are not encoded in utf8. You might want to edit the tags (in BMP, right click on the playlist song, view track details).

Hope this helps.

---

### Post by learner on 2005-10-23
Thanks! i will try that

---

