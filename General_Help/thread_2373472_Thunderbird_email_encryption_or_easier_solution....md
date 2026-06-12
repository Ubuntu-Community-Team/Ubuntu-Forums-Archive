---
title: "Thunderbird email encryption or easier solution..."
date: 2017-10-06
forum: General Help
---

### Post by 1jarwolf on 2017-10-06
Hello everyone, sorry if this is a duplicate post but I have Ubuntu and I wanted an email service that is free that encrypts and decrypts emails. I know that Ubuntu has Thunderbird already installed however after watching this video [https://www.youtube.com/watch?v=0cJ418PhJ_A](https://www.youtube.com/watch?v=0cJ418PhJ_A) well...I gave up. Way too many steps and I can't seem to get it right. So I am now asking for a possible easier solution or free email service that auto encrypts and decrypts...

---

### Post by slickymaster on 2017-10-06
I use [https://protonmail.com/](https://protonmail.com/)

---

### Post by Nosphky on 2017-10-06
Hi, 1jarwolf - use the Thunderbird Enigmail plugin. This is based on gnupg which is already installed in Ubuntu operating systems (at least in all the ones I've used). Download enigmail from :
[https://www.enigmail.net/index.php](https://www.enigmail.net/index.php)

There is also lots of help documentation on that website plus a users mailing list where the members are generous in their help.
Enigmail user discussion list <enigmail-users@enigmail.net>

You can generate your key pair via the enigmail gui.

hth

---

### Post by joye2 on 2017-10-06
> **slickymaster said:**
> I use [https://protonmail.com/](https://protonmail.com/)
Protonmail is the best choice in that case, its easy to use and easily to install, I have found the great [Email Encryption Guide]("https://www.beencrypted.com/how-to-encrypt-email/") hope that helps :)

---

### Post by SeijiSensei on 2017-10-06
Remember that you alone cannot effect encryption of your messages.  All your correspondents must support whatever technology you choose.

---

### Post by kurt18947 on 2017-10-06
I guess it depends on how 'strong' you want but 7zip seems reasonably strong, cross platform and is readily available. I'm no expert on this stuff but did do some searching. From what I gathered, password protected encrypted .zip files are pretty easy to crack, password protected .7z files less so. I added 7zip-full from the repositories and can access it via Nautilus/Nemo.

---

### Post by Rick St. George on 2017-10-06
PLEASE NOTE:

It doesn't have to be Thunderbird and Enigmail. The person on the other end needs a mail client that can handle OpenPGP encrypted emails. The following link lists a number of email clients that have OpenPGP support: [http://openpgp.org/software/](http://openpgp.org/software/)

Peace,
Rick

---

### Post by SeijiSensei on 2017-10-06
> **Rick St. George said:**
> It doesn't have to be Thunderbird and Enigmail. The person on the other end needs a mail client that can handle OpenPGP encrypted emails. The following link lists a number of email clients that have OpenPGP support: [http://openpgp.org/software/](http://openpgp.org/software/)
Both correspondents also have to have [private/public keypairs]("https://www.gnupg.org/faq/gnupg-faq.html#define_key") with the latter published.  Just having the software is not enough.  I'm sure you knew that, but the thread starter may not.

---

### Post by 1jarwolf on 2017-10-07
Thank you everyone for the support! I think I will go with the protonmail as it's already configured and whatnot. I just couldn't wrap my head around how to manually do it. Though I do like the Thunderbird as I don't have to open up a internet browser. Thanks though guys!!

---

### Post by kurt18947 on 2017-10-11
One caution though, I had Lavabit running in Thunderbird. One day it wouldn't connect and I found it had been shut down and the servers wiped overnight. If I hadn't had copies of the Lavabit emails, I'd have been in for some work. Proton mail's servers are in Switzerland which I assume makes a recurrence of the Lavabit story unlikely.

---

