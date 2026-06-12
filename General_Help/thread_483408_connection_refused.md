---
title: "connection refused"
date: 2007-06-24
forum: General Help
---

### Post by spamalot on 2007-06-24
hi everyone!

lately i have been getting the problems below with update manager as well as synaptic package manager. i am also unable to establish a connection with a news server using thunderbird. problem persists after stopping firewall via firestarter. any help would be appreciated. thanks.



W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en/language-pack-en_7.04+20070601_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en/language-pack-en_7.04+20070601_all.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-en/language-pack-gnome-en_7.04+20070601_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-en/language-pack-gnome-en_7.04+20070601_all.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gnome-app-install/app-install-data_0.3.31_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gnome-app-install/app-install-data_0.3.31_all.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gnome-app-install/gnome-app-install_0.3.31_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gnome-app-install/gnome-app-install_0.3.31_all.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

---

### Post by yabbadabbadont on 2007-06-24
That appears to indicate that you are using a local proxy.  Disable it and see if it works then.

---

### Post by spamalot on 2007-06-25
thank you for the hint.

i removed anon altogether. unfortunately it hasn't solved my problem. which settings should i look into to see what might be causing this problem?

---

### Post by spamalot on 2007-06-25
correction: update manager works after disabling local proxy. problem with thunderbird/newsgroup probably unrelated.

---

