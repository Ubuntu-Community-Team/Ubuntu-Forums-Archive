---
title: "Link to file, must &quot;Save As&quot;"
date: 2015-06-06
forum: General Help
---

### Post by Chris_Reeve on 2015-06-06
I have created several links to various files using:
ln -s /path/to/file ~/Desktop
When I open any of these files the option to "Save" is not available, only "Save As" and it defaults to the desktop directory. I though a link opens the original/source file? 
With Windows I could create a shortcut to a file and when using that shortcut the file would be opened and I could save it to the original location using "Save." How can I accomplish this in Ubuntu?

---

### Post by deadflowr on 2015-06-06
Yes the link should open the original location.
However you can only *Save* if you had already had permissions to do so for the original.
If you don't have write privileges for the original, then you won't get write privileges for anything that links to them.
And since you can't *Save*, the system is allowing you to create a new document with *Save as*, in a location, and with write rights, that you do have and can control.
If that makes sense.

---

### Post by SeijiSensei on 2015-06-07
> **Chris_Reeve said:**
> I have created several links to various files using:
ln -s /path/to/file ~/Desktop

I don't think that's what you want.  If you're trying to create a link in the ~/Desktop/ directory, use this method:
```

cd ~/Desktop
ln -s /path/to/filename.ext

```
Now you'll see a link in the Desktop directory that points to filename.ext.

---

### Post by Chris_Reeve on 2015-06-07
I appreciate the suggestion, although this has the same result. 

After more experimenting, I believe that it may be a bug with LibreOffice. I can link other file types and then Save them, but any linked files that I open with LibreOffice are not able to be saved.

---

### Post by Dennis N on 2015-06-07
I created a link on the Desktop exactly like yours to a LibreOffice Writer file in another directory and then opened the link. I was able to use "save",  but  the "save" option isn't available (it's grayed out) unless you first make some change to the contents. That's always been so, link or not.

---

### Post by Chris_Reeve on 2015-06-07
Dennis,
You are correct. It was not working at first, but after recreating the link and editing the file I am now able to save.

---

