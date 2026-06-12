---
title: "Need help with internal dialup modem @ aol isp setup."
date: 2007-02-17
forum: General Help
---

### Post by Carolee on 2007-02-17
Hello Everyone,   I am new to the Linux/Ubuntu Community and I need your help. I recently installed Ubuntu on my upstairs computer as a stand alone OS; But, I am having trouble with the modem setup (as well as with my aol connection/setup). I contacted aol tech. support and was directed to this web site in an attempt to aquire info. as to my problem. I do not have access to broadband/cable service in the rural area where I live, and sattalite service is an act of airway/space robbery; So, I am currently stuck with my aol dialup service. I need to know if there is a way to use/setup my aol account with/through Ubuntu: I also would like to know exactly how to setup my modem/ISP account in the same. Are there any other dialup Ubuntu users out there; If so, what ISP provider are you able to successfully use? Please advise: Thanks.  Carolee

---

### Post by tragicglee on 2007-02-18
Can't help with the modem but once you've got that squared away, look into using Penggy to connect to AOL. It's in the repositories, so you can install with Synaptic or apt-get but you'll need to enable Universe, if it's not turned on. I used it ~3 years ago when I was using another distro, and also stuck with AOL.

Once it's installed, your going to have to edit (what I *believe* is) penggy.conf, in /etc - from what I recall, it's really straightforward, and you just need to supply your username, your password (it may ask you to put that in another file, i forget) and some of your local AOL connection #s. It will dial out, connect you to the AOL servers and allow you to access the 'net like you were using a real ISP. You can check your mail on the website, and IM with GAIM.

(AOL actually released at *least* one version for Linux way back when, but that was pretty shortlived, and I never managed to get my hands on the install)

---

### Post by Carolee on 2007-02-18
tragicglee,   Hello: Thanks for the information, I'll see if I can locate the program you mentioned and give it a try. It is a slight pain living in a dialup world; But, as I stated I would feel as though I am being robbed at gunpoint with every $70.00 + payment to the sattalite service Gods. Hopefully one day someone will come along who will decide to lower the fees in order to better match/compete with the cable services. Besides the fact that sattalite service fees are twice as high as cable services, they are in many ways inferior to cable/broadband; So, wheres the bang for the buck? Anyway, again Thanks for the information.  Carolee

---

### Post by akshaysrinivasan on 2007-02-18
You are going to have a tough time getting that modem working  first.

---

### Post by Carolee on 2007-02-18
akshaysrinivasan,  Hello. Yes you are correct it does appear that it will/might be quite a task in accomplishing my goal. It would be nice if Ubuntu came with a manual of sorts: And, perhaps was a little more straight forward in its commands line. I am quite tired of windows, but it is setup to be a little easier on the not so savy computer user. Perhaps someone will come up with an easier to use program/setup for these Linux based OS's: In the meantime Thanks for your input.  Carolee

---

### Post by AngelX on 2007-02-18
Carolee,

Check out this page to help you set your modem... I found it quite usefull.

[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

AngelX

---

### Post by Carolee on 2007-02-18
AngelX,  Thanks for the information; But, the link that you provided for me simply looped me back to my Unbuntu forum personnal messages page (?): Am I missing something? Please advise. Thanks Again.   Carolee

---

### Post by AngelX on 2007-02-21
UPS! this is the right one....

[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)


Try this link also... it gives you a list of all dialup documentation on the ubuntu help site.

[https://help.ubuntu.com/community/?action=fullsearch&context=180&value=dialup&titlesearch=Titles](https://help.ubuntu.com/community/?action=fullsearch&context=180&value=dialup&titlesearch=Titles)

---

