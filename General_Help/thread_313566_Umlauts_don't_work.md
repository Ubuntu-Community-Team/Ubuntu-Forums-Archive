---
title: "Umlauts don't work"
date: 2006-12-06
forum: General Help
---

### Post by Flavian on 2006-12-06
Hi guys, I got a problem, when I took a look at my old folders I moved from my windows machine to the ubuntu box I encountered that the German Umlauts such as "äöü" were gone. They are simply not there anymore...
I have to say that my keyboard language is "GERMAN" But the system language is "english" (I did that on purpouse because I wanted to use english more, to practice it while using ubuntu ;) )
Anyhow another problem is that some apps just show weird rows of endless "????????????" in the place of umlauts. That is for example in Evolution's contacts or in the GAIM Contact list. If someone would have the last name: "Wörister" for example it would show up that way in Gaim: "WÃ¶rister"
Or it would show up that way in the evolution contact list: "W???????????????????????rister" which is REALLY annoying...

echo $LANG shows the following
> en_GB.UTF-8 shouldn't that be German? And if so, how can I change it (without losing the english interface and so forth...

Thanks for any help
Flo

---

### Post by wylfing on 2006-12-06
I am not an expert at this subject, and I don't even have useful suggestions, but I might have some ideas for why you are experiencing these problems.

Part of the issue might be that Windows isn't using UTF-8. Even looking at web pages in Linux sometimes results in odd characters being displayed, because the page has Windows-encoded characters pasted directly into the HTML, and the author didn't bother specifying the encoding. There may not be any good way around this problem other than retyping things.

The $LANG variable is based on your locale, not keyboard settings.

---

### Post by geraldf on 2006-12-06
Use ASCII-characters for filenames and directory names. You save a lot of trouble.

---

### Post by annda on 2006-12-06
i've had the same problem whie trying to move some german, polish and croatian named files via terminal. the names were seen as invalid because of windows-specific character encoding. i finally managed to copy them using gui.

however, i suppose your best bet will be to correct those contact entries manually. it's safest to use standard ASCII (latin) characters - for compatibility across systems - but even if you use umlauts, they will be read correctly (at least under linux).

---

### Post by gostal on 2006-12-09
I don't agree that the umlauts are necessarily correctly read. Heres my experience. I have an electronic identity certificate issued by my bank which uses a windows program to export the certificate once created. The certificate was exported to a NTFS partition using a name containing an umlaut, ö to be precise. Using this certificate requires a browser an a loaded java applet. I have not been able to get this certificate to work using Ubuntu, neither originals nor copies, and my interpretation is that it is due to buggy character encoding/byte interpretation. The reason is that if I mount the NTFS volume using utf8 the ö looks fine as it also does if I make a copy of the certificate to the Ubuntu home directory. If I use iso8859-1 it does not. If I on the other hand use Arch linux it is the other way around. NTFS has to be mounted using iso8859-1 for the ö to look right. Furthermore there are no problems using the certificate in Arch. Both originals and copies work regardless whether the copies have ben made using winXP or Arch. So there must be a bug lurking in basic file operations. The contents of the copies are OK at least so far as an MD5SUM can guarantee it but the names don't work the way they should. Also the original certificate on the NTFS volume works in Arch regardless if I mount using utf8 or iso8859-1. I use swedish locale settings.

If there is another possible interpretation I'm all ears.

---

### Post by Strider42 on 2007-03-22
If you're using an English keyboard see this thread here for how to get umlauts working.

[http://www.ubuntuforums.org/showthread.php?t=365726&highlight=umlaut]("http://www.ubuntuforums.org/showthread.php?t=365726&highlight=umlaut")

---

