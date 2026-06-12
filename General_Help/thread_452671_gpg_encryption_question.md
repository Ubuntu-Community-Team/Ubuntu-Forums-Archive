---
title: "gpg encryption question"
date: 2007-05-23
forum: General Help
---

### Post by darkworld on 2007-05-23
Ive backed up my mobile phone data onto a linux ext3 usb flash key. Phone numbers etc. It occurred to me if I lost my usb flash then the finder would have all my phone files. I searched for a simple encryption solution. I know nothing about encryption.

Found command

> gpg -c filename

Seems simple, tested it on a .php file, encrypted and back again, fine. I assume you can do this to any file type? pictures? passwords?

However the main question is, what does this warning imply? Occured when I was unencrypting file. Am I doing something wrong?

> gpg: WARNING: message was not integrity protected

Sorry this is new ground for me???

---

### Post by kuja on 2007-05-23
Yes, you can do this with any filetype. You're not doing anything wrong as far as I can see, the warning can probably be safely ignored.

---

### Post by darkworld on 2007-05-23
cheers! :D

---

### Post by fanatik on 2007-05-24
well you used symmetrical password encryption, and I suspect that why it warned you... you can suppress this warning using the --no-mdc-warning option.

I'd suggest creating some gpg keys and encrypting that way. A good series of tutorials can be found here:

[http://www.hackinglinuxexposed.com/articles/](http://www.hackinglinuxexposed.com/articles/)

also read man gpg for more info

---

### Post by darkworld on 2007-05-24
Thanks for that Fanatik

---

### Post by kuja on 2007-05-24
Downside of course being if you lose your private key, you're up the river, that is, you won't be able to decrypt the files without it, at all, period. So be sure to back up your keys somewhere secure also  just in case.

---

