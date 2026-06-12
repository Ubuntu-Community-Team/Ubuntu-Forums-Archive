---
title: "rsync from local folder to sftp"
date: 2013-01-16
forum: General Help
---

### Post by element on 2013-01-16
Can I rsync a local folder to sftp?

something like this?

rsync -az --progress --size-only /home/localfolder/* sftp://test:test@serverIP/testfolder/

I also want to pull as well.  Has anyone done this?

---

### Post by lol on 2013-01-17
Well, I cannot really answer the specific question you are asking but it looks like unison would be the right tool to do what you would like to achieve. With the added benefit that unison can handle deleted files (it does a true two-way synchronization), unlike rsync.
Did you consider it already?

---

### Post by papibe on 2013-01-17
Hi element.

I'm afraid rsync can't use 'sftp://' as an url.

However, if you have sftp access it means you have ssh access isn't? You may want to use directly rsync over ssh. For instance:
```
rsync -az --progress --size-only /home/localfolder/* user@serverIP:/path/to/testfolder/
```
If you don't use ssh keys, you'll be ask to provide the user's password right after the command.

Does that help?
Let us know how it goes.
Regards.

---

