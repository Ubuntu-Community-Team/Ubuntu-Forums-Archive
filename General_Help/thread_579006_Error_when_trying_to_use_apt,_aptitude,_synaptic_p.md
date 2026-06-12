---
title: "Error when trying to use apt, aptitude, synaptic package manager"
date: 2007-10-17
forum: General Help
---

### Post by rrcn on 2007-10-17
I can no longer use any of the update methods, I installed tor and proxy and then they all quit working.  After uninstalling these last two the problem remains, here are the error messages. . .

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main vim-runtime 1:7.0-164+1ubuntu7.2
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main vim-runtime 1:7.0-164+1ubuntu7.2
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main vim 1:7.0-164+1ubuntu7.2
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main vim-runtime 1:7.0-164+1ubuntu7.2
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main vim 1:7.0-164+1ubuntu7.2
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main vim 1:7.0-164+1ubuntu7.2
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
E: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/v/vim/vim-runtime_7.0-164+1ubuntu7.2_all.deb:](http://archive.ubuntu.com/ubuntu/pool/main/v/vim/vim-runtime_7.0-164+1ubuntu7.2_all.deb:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

this was for aptitude, the others give a different port #.  

Any ideas?

---

### Post by Pumalite on 2007-10-17
Make sure your connection is OK. Have you tried the Internet?.

---

### Post by rrcn on 2007-10-18
yep, email & browsers work fine.  This morning I even had an update that downloaded and installed for Opera, but no luck with the other three.

---

