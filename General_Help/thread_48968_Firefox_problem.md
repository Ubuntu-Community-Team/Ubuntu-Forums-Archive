---
title: "Firefox problem"
date: 2005-07-14
forum: General Help
---

### Post by zarathustra on 2005-07-14
Just tried opening an XML file and got this error message:

> Error loading stylesheet: 
(null)file:///home/nick/amsn_received/MessageLog.xsl

What does it mean?

---

### Post by badrinarayan on 2005-07-14
See if [http://www.mozilla.org/projects/xslt/faq.html](http://www.mozilla.org/projects/xslt/faq.html) answers your question.
Post the file contents if it still doesn't work.

Regards
Badri

---

### Post by zarathustra on 2005-07-14
Unfortunately that's a bit over my head :oops: 

It's a chat log that I'm trying to view and I'd rather not post the contents of it...

---

### Post by badrinarayan on 2005-07-14
Ok. may be you can post the first couple (or 3) of lines. That is where a change is required

Regards
Badri

---

### Post by zarathustra on 2005-07-14
> <?xml version="1.0"?>

<?xml-stylesheet type='text/xsl' href='MessageLog.xsl'?>

<Log FirstSessionID="1" LastSessionID="1"><Message Date="7/15/2005" Time="2:47:07 AM"

Is that enough? Sorry about not being able to post all of it.

---

### Post by badrinarayan on 2005-07-14
Try changing text/xsl in second line to text/xml as the page suggest. Let me know if that works.

Regards
Badri

---

### Post by zarathustra on 2005-07-14
Same error has come up...

---

### Post by badrinarayan on 2005-07-15
bump... I am confused. I will try installing amsn and see

---

