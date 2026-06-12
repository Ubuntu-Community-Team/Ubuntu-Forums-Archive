---
title: "How to encrypt a file after any change"
date: 2015-04-17
forum: General Help
---

### Post by enricobe on 2015-04-17
Hello,
I would like to know if there's a way to encrypt a file everytime that I make a change on it. I want to use it for the cloud. 

Because of my bad English, I try to be more clear:

1. I save all my ENCRYPTED documents in my "Dropbox" folder
2. I want to open a file and I double click on it.
3. A program should decrypt the file (asking for the passphrase) and open it
4. When I save & close the file, the program should encrypt it and save it to the folder

In this way I can use the files like they were not encrypted, but they are actually encryped. I don't know if it is possibile, but it's really time expensive select every file, decrypt it via CLI or Seahorse, modify it, re-encrypt it and save the file into the folder. I need to modify some files very often and I would like to do it easily :)

---

### Post by mcduck on 2015-04-17
Take a look at EncFS, which allows you to create encrypted folders with real-time file-based encryption just like you want. Really handy for storing files in cloud...

I recommend using Gnome EncFS Manager, it gives you nice UI for creating & mounting the encrypted folders.

[http://www.webupd8.org/2013/05/gnome-encfs-manager-cryptkeeper.html]("http://www.webupd8.org/2013/05/gnome-encfs-manager-cryptkeeper.html")

---

### Post by enricobe on 2015-04-18
> **mcduck said:**
> Take a look at EncFS, which allows you to create encrypted folders with real-time file-based encryption just like you want. Really handy for storing files in cloud...

I recommend using Gnome EncFS Manager, it gives you nice UI for creating & mounting the encrypted folders.

[http://www.webupd8.org/2013/05/gnome-encfs-manager-cryptkeeper.html](http://www.webupd8.org/2013/05/gnome-encfs-manager-cryptkeeper.html)

Sorry for the double post, but I wanted you get the notification :) 
The EncFS looks perfect for what I want to do, I'm doing some tests.
I'm also looking if it can be used with my GPG key and on Windows. 

Do you know if it's possible to use it on Windows? I often switch from Xubuntu and Windows and I would like to be able to use my files on both systems :)

---

### Post by mcduck on 2015-04-18
Sure, there are couple of tools for Windows that allow you to access EncFS drives. I'm using [EncFSMP]("http://encfsmp.sourceforge.net/") myself, but [Safe]("http://www.getsafe.org") looks pretty good as well.

---

### Post by enricobe on 2015-04-19
> **mcduck said:**
> Sure, there are couple of tools for Windows that allow you to access EncFS drives. I'm using [EncFSMP]("http://encfsmp.sourceforge.net/") myself, but [Safe]("http://www.getsafe.org") looks pretty good as well.
Thank you again ;) 
At the end of Safe's About Page, we can read: "Extra Special thanks to [Dropbox]("http://dropbox.com/") for being an awesome employer and giving me the space and time to develop Safe independently.". We should suppose that Dropbox's files are already encrypted with Safe?

---

### Post by mcduck on 2015-04-19
Encryption is kind of pointless if you aren't the one holding the keys... ;)

Besides, if they do encryption, it only happens *after* you've transferred all the files over the network. (They do use SSL for transfers but that's nowhere near the same level of security as you'd get by encrypting the files properly *before* sending them anywhere)

---

### Post by enricobe on 2015-04-19
> **mcduck said:**
> Encryption is kind of pointless if you aren't the one holding the keys... ;)

Yes, you're right :) 
I'm not so worried that Drobox or Microsoft "read" my data, I just want that the "malicious hackers" can't do it. I'm trying to understand how to manage these encrypted data with my Windows Phone... At the moment I think it's not possible but I'm really considering to use EncFS anyway. Thanks for your tips :)

---

### Post by mcduck on 2015-04-19
It's just that if Dropbox (or Microsoft, Gogole or someone else) is the one holding the keys, them getting hacked could mean the hackers get both the data and the keys. And also you can't really choose (or even know) if the encryption and the handling of the keys is done as well as you'd like. ANd of course there' s still the issue of unsecure data transfer between you and the cloud servers.

Sadly, I'm not aware of any EncFS implementation for Windows Phone. For Android there's [Cryptonite]("https://play.google.com/store/apps/details?id=csh.cryptonite").

---

### Post by enricobe on 2015-04-19
> **mcduck said:**
> Dropbox (or Microsoft, Gogole or someone else)

I'm already considering Google as a "malicious hacker" :lolflag:

I also don't know any implementation of EncFS on WP and I think that the OS doesn't allow this type of encryption. Anyway, I've found Boxcryptor for iOS that could work on my iPad, but I need to do more tests :) 
The cloud is SO useful, but it also looks so insecure...

---

