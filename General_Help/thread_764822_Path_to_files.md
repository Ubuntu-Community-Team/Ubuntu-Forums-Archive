---
title: "Path to files"
date: 2008-04-24
forum: General Help
---

### Post by gilloz on 2008-04-24
Can someone give me the paths to locate the Bookmarks for Firefox file and the Address Book for Thunderbird?  Thanks

---

### Post by marufaberlin on 2008-04-24
Think you can set them in chrome. They're variable.

---

### Post by forrestcupp on 2008-04-24
Firefox = ~/.mozilla/firefox/**some_random_letters**.default/

Thunderbird = ~/.mozilla-thunderbird/**some_random_letters**.default/

It's different on everyone's computer.

---

### Post by gilloz on 2008-04-24
Thanks for the replies, but dummy me does not how to look for ~/.mozilla.  I need the complete path.  Sorry.

---

### Post by Monicker on 2008-04-24
> **gilloz said:**
> Thanks for the replies, but dummy me does not how to look for ~/.mozilla.  I need the complete path.  Sorry.

~/ is just a shortcut for your home directory.

The complete path would be /home/username/.mozilla

---

### Post by gilloz on 2008-04-24
Thanks, that did the trick.  I will make a note of that so I won't ask again.  Learn something everyday.

---

### Post by forrestcupp on 2008-04-26
Also, the reason we put ~ in our instructions is because we don't know your username.  Using the ~ in a terminal will actually get you to your /home directory no matter what your user name is.
```
cd ~/.mozilla
```
will change to the .mozilla directory in your /home directory without needing to know what your user name is.

But it's good you asked.  If you want to use your file browser instead of the terminal, I guess it *would* help to know what ~ means.

---

