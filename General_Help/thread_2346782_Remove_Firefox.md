---
title: "Remove Firefox"
date: 2016-12-18
forum: General Help
---

### Post by shane_faulkinbury2 on 2016-12-18
I'm trying to totally remove Firefox because I use this extension called Lastpass and it's not working.  I've tried it on both Firefox and Opera.  It works on Opera, but not on Firefox.  I know it's not Firefox because it works on my laptop, but not on my desktop.

I removed it with my terminal and for some reason it still showed as being installed in the Ubuntu Software Center so I removed it in that too.  Take a look at the screen shots so you know it was totally removed.

The problem is when I reinstall it my past extensions are still showing.  There apparently is another folder which still holds the extensions which is not removed.  Please tell me how you can do a total removal so I can have a clean install.

---

### Post by &amp;KyT$0P# on 2016-12-18
shane_faulkinbury2, before going there, are you using NoScript?

---

### Post by shane_faulkinbury2 on 2016-12-18
How do I tell?

---

### Post by deadflowr on 2016-12-18
> The problem is when I reinstall it my past extensions are still showing. There apparently is another folder which still holds the extensions which is not removed. Please tell me how you can do a total removal so I can have a clean install.
Yep.
Removing the package, or any package never removes anything from your home folder.
So you need to remove this manually, if that's your thing.

It's in the hidden folder in your home directory called .mozilla.
Your settings are kept there. (Typically in a folder ~/.mozilla/firefox/some-weird-string-like-3ed54r.default >> the default usually signifies the current profile in use.)

Sidenote, firefox allows you to create new profiles which will not include any of the settings you might have in whatever the current profile is.
Simply run:
```
firefox -ProfileManager
```
to get the profile management dialog.

---

### Post by &amp;KyT$0P# on 2016-12-18
> **shane_faulkinbury2 said:**
> How do I tell?
In Firefox, go to Tools > Add-ons Manager > Extensions, check whether you see "NoScript" listed there.

---

### Post by shane_faulkinbury2 on 2016-12-18
Well this is what I have right now.  I'll try again.

---

### Post by oldos2er on 2016-12-18
Please copy and paste text from a terminal into your posts, rather than posting a screenshot; far easier to read that way.

---

### Post by lisati on 2016-12-18
From the screenshot, it looks like you've removed firefox. You will have to delete the profile manually.

---

### Post by vasa1 on 2016-12-18
> **oldos2er said:**
> Please copy and paste text from a terminal into your posts, rather than posting a screenshot; far easier to read that way.
+1. And sometimes, terminal output may exceed one screen. Or someone may want to copy stuff and paste it in a response to you.

Don't forget to use **[noparse]```
[/noparse]** and **[noparse]
```[/noparse]** tags to enclose *terminal output*. To do so, just select the text you've pasted into your post and click on the **[SIZE=4]#[/SIZE]** icon above the text box. Your terminal output will now appear with a fixed-width font and columns will be properly aligned and spaced, just like what you see in your terminal.

---

### Post by &amp;KyT$0P# on 2016-12-18
**Move** [FONT=Courier New]~/.mozilla/firefox[/FONT] elsewhere, and delete [FONT=Courier New]~/.cache/mozilla/firefox[/FONT], and you should get a clean Firefox installation.

But do note that the reason I've been mentioning NoScript is that it's [known to break Lastpass]("https://forums.informaction.com/viewtopic.php?f=7&t=22318").  If you have an older version of NoScript (or no NoScript) on your laptop, and the newer NoScript on your desktop, that could explain it.

---

### Post by shane_faulkinbury2 on 2016-12-19
Well trying again did the job!  I need to have a little more patience and try several times before posting!  Thanks you a lot all!  :P

---

