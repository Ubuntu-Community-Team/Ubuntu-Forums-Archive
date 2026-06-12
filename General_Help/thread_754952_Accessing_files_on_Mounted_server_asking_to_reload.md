---
title: "Accessing files on Mounted server asking to reload after saving"
date: 2008-04-14
forum: General Help
---

### Post by hawkeye0203 on 2008-04-14
I have edited my fstab to mount a server at startup so I can access it through my file structure.

I am however getting a funny event:  After editing my web pages and saving, next time I focus the document, gEdit tells me "The file blah/blah/blah.html changed on disk.  Do you want to reload the file?".  But I know this isn't happening.  I'm the only one working on them and it is instantaneous.  I edit, I save, I get this message.  It's really weird...  Can anyone help me?  Here is my fstab entry for the server:

//10.0.10.25/vulcan	/media/Vulcan		cifs	auto,user,rw,noperm,user=*username*,password=*password*,iocharset=utf8,file_mode=0777,dir_mode=0777	0

Any ideas?
Thanks in advance!

---

### Post by hawkeye0203 on 2008-04-14
bump.

sorry....  this is a huge productivity killer.

---

### Post by cdenley on 2008-04-14
Make sure your local system's time is not less than the file server's time. I think the problem is that gedit compares what the local system's time was when the file was saved to when the file was last modified according to the server's clock.

---

### Post by hawkeye0203 on 2008-04-14
cdenley,

One question for you: Why would you suggest something so simple?
Here's the answer: Because you knew what the problem was and that I hadn't thought of that!  :-D

THANK YOU SO MUCH!  It worked!

---

### Post by hawkeye0203 on 2008-04-15
Ok, so that didn't work as well as I thought it did.  I am still getting popups, but now whne I try to save instead of after saving.  Hmm...  

Anyone have any other suggestions?

---

