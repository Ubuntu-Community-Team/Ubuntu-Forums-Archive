---
title: "update manager error message"
date: 2008-01-13
forum: General Help
---

### Post by RonMecca on 2008-01-13
When I try to update in update I get this error message 
W: GPG error: [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3FF0DB166A7476EA
Any Ideas?

---

### Post by Washer on 2008-01-13
```

wget http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg -O- | sudo apt-key add -
sudo apt-get update
```

(i think)

---

### Post by RonMecca on 2008-01-13
I tried it and no luck

---

### Post by Washer on 2008-01-13
I think you need to try it a couple times

---

### Post by RonMecca on 2008-01-13
I tried a few more times something seemed to update and now I get this message

[http://ubuntu.beryl-project.org/dists/feisty/main/binary-i386/Packages.gz:](http://ubuntu.beryl-project.org/dists/feisty/main/binary-i386/Packages.gz:) 404 Not Found [IP: 88.191.250.18 80]

---

### Post by Casual Fan on 2008-01-13
The : on the end of that URL is what's giving you the 404 error.

If you enter that URL in your browser and delete the : you will be able to download a gzip file.

Other than that, I'm of no help.

---

### Post by RonMecca on 2008-01-13
Thanks for the replys I just cant figure this out I hope I can get this resolved so I can keep my Ubuntu updated.

---

### Post by Washer on 2008-01-13
ok just do it manually. Save [this]("http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg") file on your desktop or w/e then go to Add/remove->preferences->authentication->import

---

### Post by Washer on 2008-01-13
It's just a warning, i think. Your ubuntu should still be downloading the updates anyway.

---

### Post by RonMecca on 2008-01-15
Thanks for your help washer, can anyone confirm this or is there a way to fix this issue

---

