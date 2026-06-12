---
title: "Skype can't connect"
date: 2014-08-02
forum: General Help
---

### Post by Pedroski55 on 2014-08-02
Starting yesterday, Skype can't connect. That's just what it says "Skype can't connect."

I checked the Options>Advanced It was set to Port for incoming calls 0. I tried various numbers there. My girlfriend's win computer was set to 35517. But anyway, that is incoming, not outgoing. I downloaded and installed the latest version from Skype.com 

I should add, I am in China. Here, there is a thing called Tom-Skype, a Chinese offshoot of Skype, which is blessed by the authorities. Like Chinese windows, it is very invasive, installs all kinds of other bits that I neither need nor want, and pop ups everywhere.  So I use my vpn and install US Skype, which only gives your data to the NSA. Maybe China has started to block US Skype. They block gmail quite thoroughly now.

Today, I still can't connect to Skype. I don't know why. I've tried on 2 different laptops. Both the same. TomSkype on my girlfriend's win computer works  fine.

Anyone know the ip of the Skype server? I could ping it, just to see if it is reachable at all. Is this a Ubuntu 14.04 prroblem?? What other Internet telephony program can imitate skype?

---

### Post by mn_voyageur on 2014-08-02
You need to upgrade to Skype 4.3.

I was only able to upgrade to 4.3 using CLI: sudo apt-get install skype

MarkN

---

### Post by mdurham on 2014-08-02
Hi Pedroski55,
Same thing here in Australia. It doesn't accept name & password so I clicked on the "forgot password" thing and got a link to a Skype web page that asked me to log-on. I did log-on using the same username & password that it refused before. So back to the Skype app, it still won't accept the usual username & password.
Anyway don't be paranoid about being in China, I don't think it's anything to do with your vicinity. I know what it's like though, I've lived there a few times. You never seem to know what's going on.
Cheers, Mike

---

### Post by mn_voyageur on 2014-08-02
The problem is not your account.  If you go to Skype.com, you can login.

The problem is that Skype/Microsoft wants you to upgrade.

MarkN

---

### Post by mdurham on 2014-08-02
Thanks for that mn_voyageur.
Why TF doesn't it say so?

---

### Post by mn_voyageur on 2014-08-02
Don't ask.  I only use MS at work.  When I am telling MS corporate support how there licenses are issued, they are too big.  (I'm not even an IT guy)

Every day, I carry my personal laptop into work.  Kinda like an AmEx card.  I don't leave home without it!

MarkN

---

### Post by Pedroski55 on 2014-08-02
Thanks for that. I did go to skype.com and install the latest version, which is of today 4.2.0.13 So looks like this is a skype problem then.

pedro@pedro-bedro2:~$ sudo apt-get install skype
[sudo] password for pedro: 
Sorry, try again.
[sudo] password for pedro: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
skype is already the newest version.

---

### Post by sammiev on 2014-08-02
Seems ok here and have been using 4.3 for a while now.

---

### Post by mdurham on 2014-08-02
> **Pedroski55 said:**
> Thanks for that. I did go to skype.com and install the latest version, which is of today 4.2.0.13 So looks like this is a skype problem then.

Latest version is 4.3

---

### Post by Pedroski55 on 2014-08-02
Maybe not for Linux in China and/or from skype.com

---

### Post by hako1 on 2014-08-03
so, how to get version 4.3?

---

### Post by hako1 on 2014-08-03
I am using 14.04 in China. The current Skype version is 4.2.
Trying to access [www.skype.com](www.skype.com) lands me on a Chinese Skype website which does not have a Linux client.
So, I used VPN to access the international Skype.com.
There are several versions 4.3 to download, but none for 14.04.
Chose the one for 12.04, and tried to install via Software Center. Did not work because it could not uninstall Skype.bin 4.2.
Did anyone succeed, any suggestion?

---

### Post by QIII on 2014-08-03
This seems closer to asking for help in circumventing the law than it does a simple question of technology.

If that is the case, we do not support violating the law.

Closed temporarily for Staff review.

---

### Post by hako1 on 2014-08-03
no law violation here, just difficulties to upgrade.
I un-installed Skype (sudo apt-get remove skype), then installed the downloaded deb v4.3 for Ubuntu 12.04 via software center.
It works now.

Btw., on 12.04 Skype version 4.2 works currently without problems. Only on 14.04 the new version 4.3 is necessary, but not available in the repositories.

---

### Post by Pedroski55 on 2014-08-03
Fixed it! Have the newest version now, and I can login. Dunno what the problem was, but I think it was Skype, not Ubuntu.

Skype worked fine on 14.04 until a couple of days ago.

---

### Post by kmajaa on 2014-08-14
Hi there! Same problem here - in Poland (Ubuntu 13.10). I've been using skype every now and again and it always worked fine, but I haven't used it for like a month or so and tonight I wanted to use it and here I am getting the message that "Skype can't connect". I reset my password, try again - nothing changes. So I found this thread, went to skype's microsoft website and it's most certainly them when you see their message: "cannot connect? upgrade".

---

### Post by kmajaa on 2014-08-14
Yay me! I found[ this thread ]("https://answers.launchpad.net/ubuntu/+question/201516")and it helped. At least for me it works. Just replace the newer version with the version you've downloaded from skype's website, and the home/jonh/Downloads.... directory with your home/username/Downloads directory. Good luck!

---

### Post by Arief_Kurniawan on 2014-09-04
Very helpful.. just upgrade it to 4.3 and it works..

Thanx all...

---

### Post by wvonstockhausen on 2014-09-10
I'm in the US and have the same problem eventhough I have a current Skype account with funds on it. I used to open it from Linux and see my contact list right away. Did Microsoft bought Skype and do you need a Microsoft account which I don't have?

---

### Post by wvonstockhausen on 2014-09-10
Me again, downloaded 4.3  and tried to install it says: conflicts with the installed package " skype-bin:i386 "
What can I do now.

---

