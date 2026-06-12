---
title: "Recover Deleted Files in FAT32 fs?"
date: 2007-07-06
forum: General Help
---

### Post by stevesutt89 on 2007-07-06
Was cleaning up my music Library the other day, and i accidentally deleted almost all of my mp3 files.  They were stored on a second FAT32  filesystem, as opposed to the ext3fs that ubuntu runs off.  Is there any way of recovering these files, or do i have to start from scratch?

EDIT: Oh yes, and when i say deleted, i mean deleted. Stupid me deleted it from the garbage bin as well beofre i realised anything wasd wrong

---

### Post by stevesutt89 on 2007-07-08
Hello? Is There Anyone out there?
Do I need to post this question in another forum, or am i to take it that what i want to do is impossible

---

### Post by HermanAB on 2007-07-08
You can recover deleted files from a FAT partition, provided that you haven't written to that partition since.  There are numerous DOS utilities that can do it.  Just google for 'undelete'.  The first few pages will be paid for links.  Some ways down you should find freeware.  Then you can do the undelete using a DOS boot floppy, of which there are also free ones on the net - look for FreeDOS.

FreeDOS may have undelete all ready for you - dunno - check it out:
[http://www.freedos.org/](http://www.freedos.org/)

Cheers,

Herman

---

### Post by HermanAB on 2007-07-08
Yup, FreeDOS has it built in: [http://www.freedos.org/cgi-bin/freedos-lsm.cgi?q=f&a=base/undelete.lsm](http://www.freedos.org/cgi-bin/freedos-lsm.cgi?q=f&a=base/undelete.lsm)

---

### Post by stevesutt89 on 2007-07-08
Thanks for that HermanAB! I actualy just discvered a backup which had almost all of the music i lost on it.  Before reading this post i then went and plonked all those files back where i accidentally deleted the other ones from.  I think that comes under the heading of "writing to the partition in question" which means no undeleting for me.  Thanks for the help though, i'm sure it'll come in handy in the future as i store most of my stuff on a fat partition, and i'm likely to delete something accidentally again.

---

