---
title: "Can't Install mplayer"
date: 2005-10-18
forum: General Help
---

### Post by outdooricon on 2005-10-18
I just tried to install mplayer but I get an error on installing one of it's dependencies, slang1. The error is the following:

```
 W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/s/slang/slang1_1.4.9dbs-8_i386.deb]("http://us.archive.ubuntu.com/ubuntu/pool/main/s/slang/slang1_1.4.9dbs-8_i386.deb")
  MD5Sum mismatch
```

Any ideas?

---

### Post by Murgle on 2005-10-18
have you updated your repositories lately?  also I ahve noticed that there have been alot of probelms with the archives today...  can you download anything else?

---

### Post by outdooricon on 2005-10-18
[QUOTE=Murgle]have you updated your repositories lately?  also I ahve noticed that there have been alot of probelms with the archives today...  can you download anything else?[/QUOTE]

I just installed breezy a couple of hours ago and have been able to install other things fine. Soon after installing I went into the sources.list and uncommented all except for the backports. The wierd thing was, the other times i've installed breezy i usually a have a massive list of updates needed right away, but this time there were only three. What kinds of issues have there been with the archives today?

---

### Post by Murgle on 2005-10-18
some people were having trouble updating their lists, I'm not too sure about the details,  did you run apt-get update or refresh in synaptic after you uncommented the universe and multiverse?  I think that there weren't many things to download is that the instilation downloads at teh very end of the install.  So you wouldn't have too many espicially if you didn't re update after you uncommented some sources.

---

### Post by outdooricon on 2005-10-18
[QUOTE=Murgle]some people were having trouble updating their lists, I'm not too sure about the details,  did you run apt-get update or refresh in synaptic after you uncommented the universe and multiverse?  I think that there weren't many things to download is that the instilation downloads at teh very end of the install.  So you wouldn't have too many espicially if you didn't re update after you uncommented some sources.[/QUOTE]

Yes, I did run the update after I changed the sources. I dunno, maybe I screwed something up by accident. Maybe I'll just reinstall Breezy and see if it happens again.

---

### Post by cytoplasm on 2005-10-18
Try removing the "us" references from the URLs in your sources.list file.  Then run `apt-get update` again and then try to installer your app.

---

### Post by Demogorgon on 2005-10-18
I must be missing something here, cause I have the universe repos uncommented and things and I see no mplayer in them, been trying to get kplayer installed for days now.

Unless someone can give me the name of a nice player that likes .bin files the way kplayer does I'll be on a neverending quest to get it compiled heh.

---

### Post by Murgle on 2005-10-18
to get mplayer you need to add multiverse onto the end of the lines with universe or make new identical lines and replace universe with multiverse

---

### Post by Demogorgon on 2005-10-18
thank you very much :-)

I've been pulling my hair out for the past couple days trying to pin down my problem. I knew I had it working fine with 5.04, but I did a clean wipe and reinstall when I got my breezy iso downloaded.

---

### Post by Murgle on 2005-10-18
glad to be of help

---

### Post by outdooricon on 2005-10-18
Well, I did a new reinstall and everything seemed to be better. Mplayer installed fine, so i guess it was just a wierd install.

---

