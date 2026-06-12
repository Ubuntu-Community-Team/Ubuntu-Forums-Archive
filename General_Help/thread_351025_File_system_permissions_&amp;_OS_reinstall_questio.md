---
title: "File system permissions &amp; OS reinstall question"
date: 2007-02-01
forum: General Help
---

### Post by FooSoft on 2007-02-01
I'm kind of a newbie when it comes to how file ownership and such is implemented, so I figured I'd ask this before I reinstalled Ubuntu (as opposed to risking locking myself out of my own data). 

Basically I have a drive that's full of files which were created by my account, foosoft. Now let's say that I format, and create a user foosoft, will I still have ownership of these files? I'm thinking it's based on some UID scheme, so would I need to write down my user ID and force it on the foosoft user after my reinstall (is this possible?)

Btw, the file system in question is Ext3

---

### Post by chriscando on 2007-02-01
I do this all the time. Works just like you want it to. When you installed ubuntu you probably made 3 partitions right (/ , /home, and a swap)? When you reinstall you have the option to keep your /home (which will have /home/foosoft) and only format root (/). Then during installation just keep the same username and when the system boots up you will have your same home directory.

Worst case scenerio, you would have to create another account like foosoft2 and copy all the files from the first to the second one. This isnt as clean cause you would have to use root to copy the files and then change all the permissions back. Ive had to do this when I wanted to change my username.

Just make sure you dont format /home

---

### Post by FooSoft on 2007-02-01
Thanks for the reply. My data is on a physically separate disk. However if it works with /home on a separate partition (which is a really good idea btw) I don't see why it wouldn't work with the data being on a different drive entirely :)

---

### Post by chriscando on 2007-02-01
Yea, it shouldnt make a difference.
I really like the system of having /home on a different partiton too. I have tried out other distros and kept my /home intact. Its works out great since the home directory keeps all your settings for different programs so when you install another os you still have your settings/preferences from before.

---

