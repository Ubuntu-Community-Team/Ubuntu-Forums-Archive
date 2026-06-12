---
title: "How to convert a SAVED .eml file as a .pdf?"
date: 2016-12-05
forum: General Help
---

### Post by Wadcutter on 2016-12-05
How do I convert a SAVED .eml Thunderbird file to .pdf?
I know I can directly print a Thunderbird email to pdf (or even print it on paper). But once I save the T-Bird email to an .eml file somewhere else on my computer, it is no longer possible to turn it into a .pdf file. I can view it again in what appears to be it’s original email form, but attempting to preview it or print it just turns up a mostly blank page with “about:blank” at the top and the date and time at the bottom. No message between top and bottom. I guess I don't understand how I can see what appears to be the original email, but the ink or .pdf printer can't see it.

I'm using Ubuntu 14.04 and the pdf printer is installed--I use it all the time on other kinds of files to save them (and paper).

---

### Post by Wadcutter on 2017-01-25
Here is what I discovered after some research (I've also posted this at the Thunderbird forum on email problems): the best workaround for this issue for me (using Ubuntu 14.04  and Thunderbird 45.5.1) seems to be to simply open the .eml file with Libre Office Writer and then print with CUPS-pdf printer. I also found that opening with a text editor like Gedit (native to Ubuntu) or Notepad worked pretty much the same. I can also open the .eml file in Thunderbird and then go to &#8220;Message&#8221; on the toolbar and then&#8220;Edit As New Message&#8221; to get the email, but when I print it, I only get the body of the message and nothing else (like From: To:, Subject, Time, etc).


More study revealed that Thunderbird messages saved as .eml files are actually MHTML format (short for MIME HTML). To then convert them to.pdf one needs a printer that is capable of doing that. Apparently there is a shareware pdf printer called &#8220;novapdf&#8221; that will create .pdf from MHTML in various versions of Windows, but not in Linux distros. Trying to find the Linux equivalent of &#8220;novapdf&#8221; might be an exercise in futility. For me, the workaround above will be just fine and equals SOLVED.

---

