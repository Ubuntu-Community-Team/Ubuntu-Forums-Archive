---
title: "Thunderbird audio notify no longer works"
date: 2007-08-05
forum: General Help
---

### Post by wilberfan on 2007-08-05
I posted a "me too" response to a similar thread in the Beginners forum, but there have been no responses yet.   Desperation is motivating me to try again here...

Beginning with Thunderbird 2.0.0.5 I lost my audio notify when new mail comes in.  All I get is a system beep now.  

I used the Ubuntuzilla script to install 2.0.0.5--as well as to install 2.0.0.6 just now.   Still no audio with new mail.

This IS a 64-bit Feisty install--but previous versions of TBird have worked fine, so I don't think that's a factor...?

Any advice?

---

### Post by nanotube on 2007-08-05
> **wilberfan said:**
> I posted a "me too" response to a similar thread in the Beginners forum, but there have been no responses yet.   Desperation is motivating me to try again here...

Beginning with Thunderbird 2.0.0.5 I lost my audio notify when new mail comes in.  All I get is a system beep now.  

I used the Ubuntuzilla script to install 2.0.0.5--as well as to install 2.0.0.6 just now.   Still no audio with new mail.

This IS a 64-bit Feisty install--but previous versions of TBird have worked fine, so I don't think that's a factor...?

Any advice?

previous versions worked fine - do you mean ones from the repository, or older ones also installed with ubuntuzilla?

---

### Post by wilberfan on 2007-08-05
> **nanotube said:**
> previous versions worked fine - do you mean ones from the repository, or older ones also installed with ubuntuzilla?

Well, the one in the repo is 1.5 or something, right?   It wasn't that version.  I think it must have been 2.0--but now that you bring it up, I can't swear where that one came from--possibly from[ this thread]("http://ubuntuforums.org/showpost.php?p=2604962&postcount=90")?

Wish I could be more specific...

---

### Post by nanotube on 2007-08-05
hmm.. well, this is just kind of a stab in the dark, but do you have all the packages recommended for installation in here? : 
[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla#.5BThunderbird.2C_Firefox.5D_What_you_need_to_run_Firefox_and_Thunderbird_on_64-bit_system](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla#.5BThunderbird.2C_Firefox.5D_What_you_need_to_run_Firefox_and_Thunderbird_on_64-bit_system)

particularly, maybe lib32asound is missing?

---

### Post by wilberfan on 2007-08-06
> **nanotube said:**
> hmm.. well, this is just kind of a stab in the dark, but do you have all the packages recommended for installation in here? : 
[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla#.5BThunderbird.2C_Firefox.5D_What_you_need_to_run_Firefox_and_Thunderbird_on_64-bit_system](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla#.5BThunderbird.2C_Firefox.5D_What_you_need_to_run_Firefox_and_Thunderbird_on_64-bit_system)

particularly, maybe lib32asound is missing?

Dark stabs are appreciated.   

All of those packages appear to be already loaded...

:confused:

---

### Post by tomstrong on 2007-11-21
Hello There,

Since the original post was almost 4 months ago, my post will probably not be much help, however.....

I had the same problem (Kubuntu 7.10). After trying every tip I could find, I started looking for .wav files to use. When I found the included system waves (either for Ubuntu or for the KDE), and selected one. everything worked great. I believe they are in *usr/share/sounds*.

If one is trying to use a custom sound, it might help to move that file to t*he usr/share/sounds* folder.

I am a linux novice, but I am relentless when it come figuring things out. After all, who can deny that human civilization was built by trial and error?

Tom Weeks

---

