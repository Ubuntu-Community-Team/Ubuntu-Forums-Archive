---
title: "Decrypting an encrypted home partition from outside of Ubuntu"
date: 2013-06-29
forum: General Help
---

### Post by zesterer on 2013-06-29
Hi there,

I recently screwed up my Ubuntu install - very badly. There were a massive number of problems with it, and I had installed too much to try to retrieve it. I just want a clean install. So I've done that, but I have a problem. My files are still on the original partition, and they are in an encrypted home folder.
I've tried looking at the readme text file, but I don't think its working.

My question is - how can I get back my files without booting the original Ubuntu (it cant even boot up to a terminal tty!)

Please do NOT try to help me fix my system - I've screwed it up very badly this time, and I don't want it back to be honest. I just want a fresh install with all of my original files.

Any ideas? Any tools to decrypt and existing ubuntu home folder?

Thanks very to anybody who answers,

Barry Smith (Zesterer)

[COLOR=#ff0000][B]EDIT: Sorry, solved it myself. For anyone interested, just do this command when booting up a live CD:
[/B][/COLOR][COLOR=#2f4f4f]**sudo ecryptfs-recover-private**[/COLOR][COLOR=#ff0000][B]
And then enter your original passphrase![/B][/COLOR]

---

### Post by Cheesemill on 2013-06-29
This may be some help...
[http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/](http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/)

---

### Post by Cheesemill on 2013-06-29
This may be some help...
[http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/](http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/)

If this doesn't work then a quick Google for 'encrypted home ubuntu' brings up several pages describing how to recover your home directory.

---

### Post by zesterer on 2013-06-29
Thanks for the replies everyone! I literally just found that answer right as you said it! I think I was probably searching the wrong thing in previous google searches. I've ammended the topic prefix and put and edit on the first post. Thanks again for helping Cheesmill!

- Barry Smith (Zesterer)

---

