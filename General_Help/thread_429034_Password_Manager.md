---
title: "Password Manager?"
date: 2007-04-30
forum: General Help
---

### Post by Dimension7 on 2007-04-30
Hello!  'Just want to know what password manager does Ubuntu users use?
Any recommendation?

---

### Post by threegremlins on 2007-04-30
Eh? Be glad to help if you could you rephrase the question a bit more clearly?

---

### Post by Dimension7 on 2007-04-30
Oops, sorry.  Password manager, as in password keeper, or password wallet, or password vault, or any program that stores password so I only have to memorize 1 password for the program.

---

### Post by threegremlins on 2007-05-01
Okay I got it now, unfortunately I don't use password managers, I have this uncanny nack of remembering long strings of letters and numbers. You'll have to open up Synaptic and do a search for Password Managers, try out a few and select the one most suited for your style. Everybody has a favorite but it might not be yours.

---

### Post by NilsE on 2007-05-01
The one that is in the synaptic package repository is decent.

On Windows I use Password Corral which I like but have not checked to see if there is a Linux version.

---

### Post by girard on 2007-07-02
I was looking for the same thing. I use Keepass in windows and I found this:

[http://keepassx.sourceforge.net/downloads/](http://keepassx.sourceforge.net/downloads/)

but I'm not quite sure if the deb version would work as it says x86 only. not sure what that means so i decided to do a little more searching. 

Keepass works well in windows so i'm really hoping i could use this with ubuntu. plus all my data can be migrated easily. 

anyone care to check out the link and tell if we could install this in ubuntu. i have 6.10.

---

### Post by Dimension7 on 2007-07-02
Now I'm using MyPasswordSafe, from the Synaptic Package repository.
I like it because it is compatible with Password Safe, which is what I'm using under Windows.
Now whichever OS I boot I still get to access one password database.



Read for more info on MyPasswordSafe...
[http://www.semanticgap.com/myps/](http://www.semanticgap.com/myps/)

---

### Post by BlackAnthrax on 2007-07-02
This is what you do.

sudo apt-get install keepassx

I like it a lot.

also, look into this:

[http://portableapps.com/news/2007-04-16_-_keepass_portable_1.07](http://portableapps.com/news/2007-04-16_-_keepass_portable_1.07)

You could place the portable version on a flashdrive/etc

it works fine with wine

that way if you go to a friends house/etc/ you can just use it instead of having to worry about syncing/etc.

just use the portable version if you think you would travel and need it to be up to date.

---

### Post by Dimension7 on 2007-07-13
Thanks girard and BlackAnthrax, now I'm a KeePass convert.

I still get to use one password database for Ubuntu, Windows and now PocketPC.

---

### Post by sefs on 2007-07-13
KeePassX is nice, but how can I generate a Keyfile for it.

---

### Post by FSHero on 2007-07-16
Hi all,

I've been using Password Safe in Windows, and Password Gorilla in Knoppix 5.1.1 so far.

I was thinking about migrating to KeepassX, but I cannot import my .psafe3 database. Apparently the Windows version can import it, but I want to use Windows as little as possible now... :) )

Otherwise, I could manually type in each and every entry from Password Gorilla into KeepassX... but that would take *ages*.

Should I just use KeePass in Windows, as a one-off, to import my database? (Perhaps use Wine?) Or should I continue to use Password Gorilla? How's MyPasswordSafe?

(The reason I want to switch is: there is no Autotype in Password Gorilla. Plus, KeePassX looks a little more polished ;) )

---

### Post by FSHero on 2007-07-16
I'm going to install MyPasswordSafe now, through apt-get. (Not in Add/Remove in Kubuntu :( )

---

### Post by FSHero on 2007-07-16
Sorry to keep bugging everyone...

I'm using Kubuntu Feisty Fawn, and haven't added anything new to my /etc/apt/sources.list. The version of MyPasswordSafe that apt-get installed is old -- it can't open .psafe3 files.

How do I install the newer version (e.g. 20061216)? I have a feeling I need to add something to my /etc/apt/sources.list, but I'm not sure what, and I'm not sure what to do after this.

---

### Post by Dimension7 on 2007-07-16
MyPasswordSafe, as far sa I know, can only support up to version 2.0 of Password Safe for Windows.

To export your Password Safe files (Windows version), use Export To, Plain Text (tab separated)...
Then from Keepass (Windows) or KeepassX (Linux), create a new file save it, then import using PwSafe v2 TXT File...

'Hope it helps.

---

### Post by strabes on 2007-07-16
kubuntu comes with kwallet out of the box

---

### Post by FSHero on 2007-07-17
Dimension 7:

Thank you thank you thank you!
It worked: in Wine, I used Password Safe 3.* to export to text file, then in Wine I used KeePass 1.07 to import PasswordSafe v2 text file.

All the username and passwords have been imported successfully. Only problem is: My URLs have been imported as "Notes", and my Notes have been lost! :P Never mind; the main parts are still working!

I didn't see any "Import PwSafe v2 Text File" in KeePassX. This KeePassX was installed using Add/Remove in Kubunu. The version is 0.2.2. Of course, it doesn't really matter: KeePass (Windows version, in Wine) worked okay.

BTW, is there any way of permanently 'shredding' (i.e. deleting) the text file output of Password Safe?

---

### Post by rahul_bhise on 2007-07-20
i too was a user of keepass in windows xp. and am happy to see a some what same application in ubuntu. the keepassx could read my database.ked.ked and also pwsafe.key.
so no import/export problems.
in keepassx in extra>setting>other tab change browser command from kfmclient openURL %1 to firefox %1 then select the keepassx entry and ctrl+u will open the url  ctrl+b will copy the user name then ctrl+v at appropriate place then ctrl+c to copy password and past it with ctrl+v where it is needed.
i think no autotype feature is avalable

---

### Post by n.aggel on 2007-07-29
> **Dimension7 said:**
> Now I'm using MyPasswordSafe, from the Synaptic Package repository.
I like it because it is compatible with Password Safe, which is what I'm using under Windows.
Now whichever OS I boot I still get to access one password database.

Read for more info on MyPasswordSafe...
[http://www.semanticgap.com/myps/](http://www.semanticgap.com/myps/)


> **Dimension7 said:**
> Thanks girard and BlackAnthrax, now I'm a KeePass convert.

I still get to use one password database for Ubuntu, Windows and now PocketPC.

I am using password safe with windows, and password gorilla with ubuntu. This enables me to have a single database {meaning one format-- psafe3}, and everything works fine!!!

---

