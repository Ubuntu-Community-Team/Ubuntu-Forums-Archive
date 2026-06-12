---
title: "What to do about Dropbox dropping support warning?"
date: 2018-10-25
forum: General Help
---

### Post by Vadi on 2018-10-25
I'm using an encrypted LUKS filesystem and Dropbox is dropping support for it shortly. What are my options while still staying secure?

---

### Post by HermanAB on 2018-10-25
You are using Dropbox and you are worried about security? ;)

Anyway, I can't see how the file system is any concern of Dropbox.  It should not matter which file system you are using.

---

### Post by ajgreeny on 2018-10-25
Have a look through the thread at [https://ubuntuforums.org/showthread.php?t=2398409&highlight=dropbox](https://ubuntuforums.org/showthread.php?t=2398409&highlight=dropbox)

It may give you some further ideas, though any cloud/remote storage of my own files away fro my total control always gives me concerns, and I don't ever use it for anything important.

---

### Post by Vadi on 2018-10-25
Not the answer I'm looking for - work uses Dropbox, and I use Ubuntu at work.

---

### Post by nozombian on 2018-10-25
Dropbox sucks, but it is used in businesses, so I will have to deal with it too. You can workaround with loopback file with ext4 and mount it where you have your dropbox files. Someone already figured that out here: [https://metabubble.net/linux/how-to-keep-using-dropbox-even-if-you-dont-use-unencrypted-ext4-workaround/](https://metabubble.net/linux/how-to-keep-using-dropbox-even-if-you-dont-use-unencrypted-ext4-workaround/)

---

### Post by Vadi on 2018-10-25
Thanks a ton!

Sorry for being unclear before - yes, I'd like to remain on Dropbox.

---

### Post by sp40140 on 2018-10-25
Another option is Tonido.
Makes your computer a cloud. It has apps for iOS and Android as well.
Check it out.
Free for home use. Set-up is straight fwd.
[https://www.tonido.com/](https://www.tonido.com/)

---

### Post by nozombian on 2018-10-26
I don't want to get too far from topic, but with all respect, paying $4.20 what for? For hosting it myself? There are other free self hosted cloud solutions like syncthing (which  I'm using) or owncloud. But it stil requieres the other party to have  the client too.

Even dropbox is free when you are not space hungry and with ecryptfs is quite secure, but as it looks you should have their crypted originals on ext4. I hope this will continue to work, unless they say "if we are unable to read your whatever, we will ban you".

---

