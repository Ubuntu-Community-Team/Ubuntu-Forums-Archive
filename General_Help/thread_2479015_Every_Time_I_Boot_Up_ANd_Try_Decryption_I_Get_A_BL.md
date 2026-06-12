---
title: "Every Time I Boot Up ANd Try Decryption I Get A BLinking UnderScore"
date: 2022-09-12
forum: General Help
---

### Post by andy352 on 2022-09-12
Originally I would just enter my decryption code, it'd let me log in, boom.
Then it started showing me text beforehand, random errors seemed to appear in said text, then it worked without problems.
Now when I try to decrypt it says the password is successful, it brings me the wall of text and gets stuck on a blinking underscore, the wall of text is gone and a blinking underscore is the only thing.
I have left my machine on for 10 minutes on this underscore and nothing changes.
If I clickt he power button it shows me the Ubun logo without the text field then shuts down.
I am using  Ubuntu 5.15.0.46-generic
I have tried going to the Advanced options in grub and loading .43-generic, same thing happens.

I am utilising an SSD that I bought in January 2021.

---

### Post by miguel001 on 2022-09-12
The blinking line can be associated with broken, bugged, bad update, or misconfigured OS so I'm not really sure if its related to encryption or something else here.

Since the password is successful I'd expect whatever comes after such as the above is what's wrong. If its whole disk encryption then it may be a further pain for you. You probably need to find command line and fix the issue. You can try the F2 (or maybe another F key) during the blinking line and see if it shows up as it may during those times. There can be other possibilities to getting to it.

But, fixing it may well be too much for you so you can always clean install. If the drive is encrypted and you can't gain access to the files then they are forfeit if you have no backups. It is the way.

---

