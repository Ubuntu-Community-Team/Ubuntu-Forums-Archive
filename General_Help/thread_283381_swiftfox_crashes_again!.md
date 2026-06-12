---
title: "swiftfox crashes again!"
date: 2006-10-24
forum: General Help
---

### Post by insub2 on 2006-10-24
swiftfox has up and closed on me a lot and i'm wondering if other's have had this issue or why it is happening.

---

### Post by Rui Pais on 2006-10-24
If it happens frequently it's usually due to some bad extension or a conflicting profile.

A plain: 

mv .mozilla/firefox .mozilla/firefox_OLD 

cure most of nasty things.

---

### Post by insub2 on 2006-10-24
ok....thanks for the warning on loosing all my bookmarks!!!

how do i get them back?

---

### Post by Rui Pais on 2006-10-25
> **insub2 said:**
> ok....thanks for the warning on loosing all my bookmarks!!!:mad: 

how do i get them back?

```
mv .mozilla/firefox .mozilla/firefox_NEW 
mv .mozilla/firefox_OLD .mozilla/firefox
```

that should put all as it was before.



If the new profile work without crashes, put the old back, and on bookmarks menu go to 'Organize bookmarks'. On the window on menu, under 'File' go for 'Export...', and save the html. 
Thats a copy of all your bookmarks.

Now you could reput the new profile back (or get again a fresh new) and redo that routine and instead of Export... now use 'Import...' to import the copy of your bookmarks.

---

### Post by insub2 on 2006-10-26
that worked beautifully!  thank you very much!


i am curious though....what does that code do/mean?

---

### Post by Rui Pais on 2006-10-26
All your firefox/swiftfox profile goes to a folder inside .mozilla/firefox/ with some bizarre name (kind of dsasd98asd7.default).

when you do:
```
mv .mozilla/firefox .mozilla/firefox_OLD 
```
removes firefox profile to a backup named firefox_OLD (you can name it what ever you like or use dates, numbers,...)

If you start ff/swiftfox it will make a new fresh one (not personalized and hopefully not broken) 

```
mv .mozilla/firefox .mozilla/firefox_NEW
```
removes your new fresh profile to a backup named firefox_NEW
 
```
mv .mozilla/firefox_OLD .mozilla/firefox
```
puts back old profile,
and so on... 
It's very simple to make and manage your profiles and backups.

btw, did the crashes stopped with a fresh profile?

---

### Post by insub2 on 2006-10-28
no
still crashes ocasionally. (though it seems to be less.)

---

