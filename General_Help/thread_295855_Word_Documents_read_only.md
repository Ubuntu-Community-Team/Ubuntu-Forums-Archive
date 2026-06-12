---
title: "Word Documents read only?"
date: 2006-11-08
forum: General Help
---

### Post by Mooseus on 2006-11-08
Hey everyone, 

I opened some Word documents I have with Open Office's Writer but It won't let me edit the text because it's read-only. How do I change that so I can edit it?

Thanks in advance

---

### Post by whitewizardcoder on 2006-11-08
How are you accessing these documents?  If it is from your hard drive, right click on the file, click "properties", and then click on the "permissions" tab.  Make sure "Owner" reads as your username and that you have read and write access.  If you are not the owner of the document, open up a terminal, navigate to the folder where the document is and do:
```
sudo chown <username> <filename>
```
Then, go back to the "permissions" dialog and make sure you have read and write access.

If you are trying to access the document from an email attachment, you must save this document on your hard drive first to make it writeable.

Hope this helps...

-WhiteWizardCoder

---

### Post by professor_chaos on 2006-11-08
Where (physically) is the file?

.... remember, NTFS file systems are not writable out of the box. So if your *.doc is on your windows partition, and it's NTFS, you won't be able to write to it (easily).

---

