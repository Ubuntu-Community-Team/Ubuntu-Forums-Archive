---
title: "GTKpod issues"
date: 2005-08-26
forum: General Help
---

### Post by kevinat0r on 2005-08-26
So I just bought an iPod shuffle, and I went to sync with the iPod with gtkpod. I pressed sync, it told me this...
OK to create the following directories?
/media/ipod/Calendars
/media/ipod/Contacts
/media/ipod/iPod_Control
/media/ipod/iPod_Control/Music
/media/ipod/iPod_Control/iTunes
/media/ipod/iPod_Control/Music/F00
...
/media/ipod/iPod_Control/Music/F19

I press OK.

I get the following error
iPod directory structure must be present before synching to the iPod can be performed.

How do I create the iPod directory?

---

### Post by ACK!! on 2005-08-26
[QUOTE=kevinat0r]So I just bought an iPod shuffle, and I went to sync with the iPod with gtkpod. I pressed sync, it told me this...
OK to create the following directories?
/media/ipod/Calendars
/media/ipod/Contacts
/media/ipod/iPod_Control
/media/ipod/iPod_Control/Music
/media/ipod/iPod_Control/iTunes
/media/ipod/iPod_Control/Music/F00
...
/media/ipod/iPod_Control/Music/F19

I press OK.

I get the following error
iPod directory structure must be present before synching to the iPod can be performed.

How do I create the iPod directory?[/QUOTE]

I read the following remark on this error from another Fedora focused forum and I quote:

It seems Fedora automounts the Ipod to /media/ipod instead of gtkpod's 
default path of /mnt/ipod. After changing that, I think I was able to 
upload some mp3s to the shuffle.

Try that.

---

### Post by kevinat0r on 2005-08-27
I got the directories made, how do I put the iTunes.db file on the iPod? gtkpod is giving me error messages about that.

---

### Post by rdwtux on 2005-08-27
You should setup the ipod first in windows.. format it, let it create the filesystem, etc.  then plug it into linux.

---

