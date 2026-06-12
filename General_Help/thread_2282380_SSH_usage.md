---
title: "SSH usage"
date: 2015-06-13
forum: General Help
---

### Post by papakota on 2015-06-13
Hello!
                              I want to run web server on Ubuntu 14.04  desktop. Do I need SSH at all? I always have direct physical access to  the server. No one else is in business.

---

### Post by papibe on 2015-06-13
Hi papakota.

Not really, but here are some thoughts:

If you are going to develop, patch and update your server, all while sitting down in front of it, not really. If that's not the case, you need a way to upload/transfer your changes. ssh/sftp is great for that.

Does the server have other clients than yourself? Like room mates, or family members. When they need help, are they going to wait for you to come physically in front the server? Can they solve their problems by themselves when you are away?

Having said all that, you don't "really" need it. Start without it, and then you can install it if you think it makes things easy.

Regards.

P.S.: BTW, I personally even ssh into my home server which is in the other room :p

---

### Post by QIII on 2015-06-13
Web server exposed externally?.  I would say absolutely no to the desktop.  Every service that runs on the server is an attack surface and a Desktop runs a host of services -- even if you are the only one with physical access.

Like papibe, I administer my home servers over SSH from my primary desktop machine.

---

### Post by sandyd on 2015-06-13
It depends really.

If you might want to update files remotely one day instead of having to access the server, I suggest using SSH. Unless your using FTPS, FTP is not secure at all. If your hosting files, then you might consider simply making the server pull from a private git repo every few minutes. Then commits to the git repo will be automatically added. Might be easier and more efficient than SSH or FTP if you are updating files.

If you are considering enabling SSH, make sure you restrict logins to SSH keys, and disable password logins.

That being said, I suggest not running the desktop Ubuntu variant, but instead the server edition. The server edition is much lighter, and comes with only essential services installed, making it less of a security risk. If you have to have Ubuntu desktop installed, running the webserver in docker may provide a bit more security.

---

### Post by papakota on 2015-06-14
Thank you all for your replies!

---

