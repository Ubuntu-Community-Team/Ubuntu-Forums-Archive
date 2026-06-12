---
title: "Cannot print pdf files"
date: 2007-06-12
forum: General Help
---

### Post by Mel_K on 2007-06-12
Since upgrading to 7.04, I can no longer print pdf files.  I have no problem printing other file types.  I have a Brother HL2040 and have been printing with it in Ubuntu for over a year.

I have checked System>Admin>Printing and it says that HL2040 is ready.  I have watched this while trying to print and the job does not even get to the queue.

In the printer set-up, the printer command is /usr/bin/lp.  
I have checked the documents' permissions and have changed all to read and write. None of this makes a difference.  

In the past, printing pdf files has never been perfect. In multi page documents, there would be one blank page printed in between the first and second page of the actual document.

What should I try? 
Thanks.

---

### Post by Patrick K on 2007-06-12
If printing works for everything but PDF files, it sounds like evince has a problem. You could install Acrobat Reader. I had to to print in landscape. It's in the repos.

---

### Post by Mel_K on 2007-06-12
Thanks, 
I have evince, xpdf and acrobat and none can print pdf files.

---

### Post by Patrick K on 2007-06-12
Having never had this problem, I don't have any ideas. I guess you have gone through the preferences pages for each app. Although it sounds like a more universal problem than just the apps. 

Personally, I use Edgy for most everything. I find it works better for me than Feisty.

---

