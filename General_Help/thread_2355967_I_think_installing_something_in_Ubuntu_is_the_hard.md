---
title: "I think installing something in Ubuntu is the hardest thing ever."
date: 2017-03-18
forum: General Help
---

### Post by one-9-archmage on 2017-03-18
First you go into "Software"

Second you choose the package that you want.

Third you are asked for your email and password of your Single-Sign-One-Account. You insert them and got the message "incorrect email or password".

Forth you recheck them and notice that they are correct and try it again and got the message "incorrect email or password".

Fifth you recheck them and notice that they are correct and try it again and got the message "incorrect email or password".

Sixth you recheck them and notice that they are correct and try it again and got the message "incorrect email or password".

Seventh you recheck them and notice that they are correct and try it again and got the message "incorrect email or password".

Eight you recheck them and notice that they are correct and try it again and got the message "incorrect email or password".

Ninth you recheck them and notice that they are correct and try it again and got the message "incorrect email or password".

Ten you recheck them and notice that they are correct and try it again and got the message "incorrect email or password".

Eleventh you install Windows

Twelfth you just install the requested program with a double click.

Could someone tell me why it is so hard to install something and why it keep asking me to reinsert my correct email and password?

---

### Post by howefield on 2017-03-18
What package are you trying to install and which version of Ubuntu ?

At one time snap packages required an SSO account to install but that is no longer the case, I'd ask if you're system is currently up to date ?

---

### Post by Keith_Helms on 2017-03-18
First I go into Synaptic

Second I search for the package name

Third I check Mark for Installation

Fourth I click on Apply

---

### Post by one-9-archmage on 2017-03-18
It's 16.10 with the latest patches. I'm trying to get VLC.

I did now reset my password. Enter the new password and still in software I got the response. "incorrect email or password"

---

### Post by howefield on 2017-03-18
So it is the snap package that you want ?

There are two VLC packages in the software centre, firstly the traditional deb package which is probably what you would be best with and secondly the snap package of the current daily state of VLC.

Software is the first thing I uninstall so working from memory you should be able to expand on the details tab for the package and be clear on which package is which. The version details for the snap package should refer to "daily" and the other won't.

Alternatively, using the terminal with..

```
sudo apt install vlc
```

should sort it out nice and easy.

---

### Post by one-9-archmage on 2017-03-19
I ended reinstalling Ubuntu. Now it is accepting my email and password. And yes, it was the SNAP-version.

Thank you everybody, that tries to help.

---

