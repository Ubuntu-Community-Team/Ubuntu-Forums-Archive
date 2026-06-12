---
title: "Can't encrypt file"
date: 2016-02-20
forum: General Help
---

### Post by ScorpioTiger on 2016-02-20
Hi,

Been trying to encrypt backups before uploading to cloud storage. I've tried the following plus a few different varients, but everytime, the result is an empty file. It takes maybe 30 seconds to run and there are no errors, just an empty file.

openssl smime -encrypt -binary -aes-256-cbc -in backup/dump.tgz -out backup/dump.tgz.dat -outform DER public-key.pem

Thanks

---

### Post by gordintoronto on 2016-02-21
[http://stackoverflow.com/questions/16056135/how-to-use-openssl-to-encrypt-decrypt-files](http://stackoverflow.com/questions/16056135/how-to-use-openssl-to-encrypt-decrypt-files)

---

