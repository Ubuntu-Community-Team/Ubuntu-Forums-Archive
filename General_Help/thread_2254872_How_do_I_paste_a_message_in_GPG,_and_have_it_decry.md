---
title: "How do I paste a message in GPG, and have it decrypt it and display to console?"
date: 2014-11-30
forum: General Help
---

### Post by HeroCC on 2014-11-30
Hello!
I am trying to use GPG, and I want to paste a PGP encrypted message. I use ```
sudo gpg -d
``` and paste the message, and it asks me for my password, which I enter, then press Enter. Then it just doesn't do anything. No text, no thing, I can push keys, type letters and it appears, but it doesn't do anything until I CTRL+C Out. I want it to print the message to me, but now it does nothing. If I specify a file to take it from, it decrypts just fine.
Any help would be appreciated, thanks!

---

### Post by Lars Noodén on 2014-11-30
You don't need, or even want, sudo in this case unless you are using root's keyring and not your own.  So just run gpg -d and when you get to the end of your message, press ctrl-D

---

### Post by HeroCC on 2015-01-13
Sorry for the old reply, but when I just do gpg -d, I get this. (I would have replied earlier, but it didn't email me when someone replied)
[http://pastebin.com/Y4PDh3T7](http://pastebin.com/Y4PDh3T7)

---

### Post by Lars Noodén on 2015-01-14
```

gpg: failed to create temporary file `/home/me/.gnupg/.#lk0x2498130.me-desktop.8330': Permission denied
gpg: keyblock resource `/home/me/.gnupg/secring.gpg': general error
gpg: failed to create temporary file `/home/me/.gnupg/.#lk0x24981d0.me-desktop.8330': Permission denied
gpg: keyblock resource `/home/me/.gnupg/pubring.gpg': general error
gpg: Go ahead and type your message ...

```

That looks to be fallout from having used sudo earlier.  When you run gpg for the first time, it sets up some files.  If you did that using sudo than it set them up as some other user, probably root.  Try changing the ownerships back to your own account.  

```

sudo chown -R me:me /home/me/.gnupg/

```

---

### Post by HeroCC on 2015-01-17
OK, I ran the command and now I don't get the error, and the Control + D works, thanks!

---

