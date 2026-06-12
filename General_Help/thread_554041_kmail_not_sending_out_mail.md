---
title: "kmail not sending out mail"
date: 2007-09-18
forum: General Help
---

### Post by nikef on 2007-09-18
kmail will not send any emails

i have made sure the settings are ok,but still unable to send
it gets mail ok           :confused:
any1 have any ideas ,as i like to use kmail instead of evo,and thunderbird

---

### Post by treb0r on 2007-09-18
Are you sure your settings are correct?

Are you using sendmail or an external mail relay?

---

### Post by nikef on 2007-09-19
I have tried both ,sendmail looks as though it gets sent from my pc,but does not go to where it supposed to,with my external it just goes straight to out box
:confused:
thanks  for replying

---

### Post by BetterAndBetter on 2007-09-19
I am using kubuntu DVD Gutsy Gibbon dated 9/10/2007.

I have set KMail up exactly the same as it is on another computer.  Gutsy KMail is able to read email messages into my system but it is not able to send email out.  Well I actually got it to send two (2) message out once.  But I don't know what magic caused that to happen.

---

### Post by BetterAndBetter on 2007-09-19
I should have added that the system is current as of this date from the following sequence:

apt-get update
apt-get -ud upgrade
apt-get -u upgrade

---

### Post by nikef on 2007-09-20
> **BetterAndBetter said:**
> I am using kubuntu DVD Gutsy Gibbon dated 9/10/2007.

I have set KMail up exactly the same as it is on another computer.  Gutsy KMail is able to read email messages into my system but it is not able to send email out.  Well I actually got it to send two (2) message out once.  But I don't know what magic caused that to happen.

yeah i have been able to send a couple,and receive them ,i am having to use thunderbird
thunderbird  is ok,but i do prefer kmail 

does any1 else have any ideas as its such as shame, not being able to use kmail :confused:

---

### Post by linedeen on 2007-11-02
My kmail also will recieve but not send.

 I did a telnet to port 25 of mailserver , did work,
Servername sendername etc seems to be correct. 

When trying sending withe kmail, the led of cablemodem does not blink.

My system is kubuntu feisty, up to date except last to upgrades. Al;s i hmust confess to using automaticsm what seem to be very dangerous.

Still all help is welcome, be it solutions or directions in wich to look
i don't know if it is relevant, but kmail was not a present option in my KDE-menu. I put it there.

---

### Post by True Rage on 2007-11-10
Hi
Same problem here. Kmail doesn't send emails out. Bloody hell.
I have been using kmail for years, now upgraded to Gutsy Gibbon and doesn't work anymore.
I think it is just a bug in the last release, so we'll have to wait until it's fixed!
I tried this: uninstalled kmail with Adept. Went to the debian site and downloaded the stable package of kmail, which was a previous one and i hoped it would work. Clicked on it and chose "install package". Everithing seemed to work fine, but then, the command kmail wouldn't start anything...
So now I just can't use kmail anymore... :(
Any ideas?!
Any suggestion for another good email client?
Bye

---

### Post by True Rage on 2007-11-10
I tried another thing.
Downloaded the kmail package of Kubuntu 7.04. It gets open with GDebi package installer. Same problem as before. I click "install package", something seems to happen, no error messages, but the package doesn't actually get installed, cause at the kmail command it says "couldn't find "kmail" executable". This didn't happen in the 7.04!
Annoying... New versions bring along new problems! Shouldn't it be that they fix the old bugs and keep the working features?!

Byez byez!

---

### Post by jonesvb on 2007-11-13
Hi!

I just realised, that my Kmail on gutsy doesnt send anymore either!

Has somebody found a solution?

Greetings from Hamburg

Jones

---

### Post by nikef on 2008-01-24
:):):):):):):):

Hey i just tryed my kmail and its working  :guitar:

---

### Post by atentik on 2008-03-25
How did you get it to work?

---

### Post by ACGarland on 2008-04-30
I was using kmail fine for a couple of days. Then I did some network configuration work (setting up ad-hoc wireless) and when I went back to my normal wired networking everyting works fine (routing, internet access) except that kmail default 'send' no longer sends.

As others with this problem have observed on other threads, 'send via' where you select the specific sending account still works ok.  But this is very annoying because automatic 'send now' no longer works.

All the SMTP settings are correct (unchanged from before) and work fine when you manually select that sending account.  So there appears to be something where kmail ends up confused and won't automatically use the default account unless you manually select it each time.  Ugh. :-(

---

### Post by ACGarland on 2008-04-30
Saw a post about a person having problems due to interactions with the kdewallet:

[http://ubuntuforums.org/showthread.php?t=488733](http://ubuntuforums.org/showthread.php?t=488733)

So I closed kontact, opened the kdewallet, deleted all the kmail passwords, and restarted kontact.

Then, I provided the passwords again for the sending and receiving accounts in kmail. After doing this, kmail resumed sending using 'send now' with the default sending account like it used to and the problem appears to be fixed! :-)

---

### Post by kioftes on 2008-07-23
In my case it was also needed to erase the .index files at the $HOME/.kde/share/apps/kmail/mail/  directory...

---

