---
title: "Update Error Message"
date: 2007-03-29
forum: General Help
---

### Post by JimS on 2007-03-29
...
Using Dapper on a 2 year old Toshiba notebook.

Every so often I see a little red icon in my panel and I know I have software updates available.  
So I click on it, sign in, and update.  
After that is done and before I close,
I click on "Check".  
It cycles thru my system and starts to say that I have a bunch more files to update/install.  
But then a Message pops up entitled "Warning".

W: GPG error: [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release: 
The following signatures couldn't be verified because the public key is not available: 
NO_PUBKEY CC919A31E23C5FC3

Anyother problem, that may not be related, is when at a Web Cast the picture
seems good, but the audio is vvveeerrrryyyy sssslllloooowwww.  
Not so on my Windoz box when sound is good.  
I resently installed Flash9 so I could get the Web Cast.

What do you think I should do now about the Warning?
...

---

### Post by zvacet on 2007-03-29
gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
 gpg --export --armor KEY | sudo apt-key add -


so in your case 

gpg --keyserver hkp://subkeys.pgp.net --recv-keys CC919A31E23C5FC3
 gpg --export --armor  CC919A31E23C5FC3  | sudo apt-key add -

---

### Post by JimS on 2007-03-29
...
Thanks
I ran your 2 lines thru terminal and hopefully all is okay
the next time I'm sent an update.
...
JimS
Prostate Cancer Survivor
...

---

### Post by dannyboy79 on 2007-03-29
you don't have to wait for an update, you can just run

sudo aptitude update && sudo aptitude upgrade

and it'll parse automatix's repository for updates and if the gpg key is correct then you will be good to go otherwise here is a link for exact instructions for using automatix's repo's and how to add their gpg key. just follow the instructions for your version (dapper). [http://www.getautomatix.com/wiki/index.php?title=Installation#Ubuntu_6.06_.28Dapper_386.29](http://www.getautomatix.com/wiki/index.php?title=Installation#Ubuntu_6.06_.28Dapper_386.29)

---

### Post by JimS on 2007-04-14
...
Issue resolved.

Will be ugrading from Dapper soon.
Probably when Fiesty has passed out of beta
later this month, I think. But I'll need to first create
a seperate home partition.  PsychoCats should
be a good guide.

Many thanks,

JimS
[email]workfromhome@pobox.com[/email]
...

---

