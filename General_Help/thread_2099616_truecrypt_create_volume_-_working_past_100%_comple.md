---
title: "truecrypt: create volume - working past 100% complete"
date: 2012-12-30
forum: General Help
---

### Post by svaens on 2012-12-30
Hi all, 

I setup the creation of a large truecrypt volume, selected filesystem type ext3, and let it run.

Once it got to 100% (some hours later) , 
as I was monitoring its progress, I wanted then to start working on the drive, however, while it had reached 100%, the gui still seemed like it was working (though the disk light was no longer flashing).

Assuming it was just a gui problem (mistakenly, I believe) 
I clicked the cancel button... realizing only later that another window had opened up requesting the password..... 
But I was tired ..... and didn't realize what was happening.... continued to cancel and close the application.
 
I Reopened, and attempting to open the new truecrypt volume resulted in the following message:

mount: you must specify the filesystem type

So, now, I am suspecting I did indeed interrupt something. 

However, I then found an ubuntuforums thread, in which the poster had the same problem (for other reasons). I followed the advice given there, and ran something like:

mke2fs -j -m o /dev/loop0

This ran successfully, and I was then after able to open the truecrypt volume. 

My question is:

I interrupting the process in the way I did, and creating the filesystem in the way I did, 
Have I undermined the security truecrypt provides to that drive ... somehow created a vulnerability? 

thanks!

---

### Post by svaens on 2013-01-02
bump...
additionally .... does anyone know if the time required to change the password on a truecrypt volume depends much on the size of the volume? 
i.e., is a large volume going to cause truecrypt to apparently hang for hours ? 

thanks again.

---

### Post by Calinou on 2013-01-02
> Have I undermined the security truecrypt provides to that drive ... somehow created a vulnerability?

This seems unlikely (although I have never tried -- I don't use disk encryption on any of my computers). Maybe try changing the passphrase (it shouldn't take too much time). Remember that if you need to keep your computer on for a long time, do it in the night, the electricity will be cheaper. :D

---

### Post by akshay.bhardwaj on 2013-01-02
When a volume is encrypted volume header is created which is encrypted your password/keyfile and using this volume header the encryption key is generated using which the entire volume (i.e. your drive) is encrypted. Hence on changing your password doesn't re-encrypts entire hard disk rather re-encrypts the volume header. So changing password should be quick! 

For details refer to: [http://www.truecrypt.org/docs/?s=changing-passwords-and-keyfiles](http://www.truecrypt.org/docs/?s=changing-passwords-and-keyfiles)

---

