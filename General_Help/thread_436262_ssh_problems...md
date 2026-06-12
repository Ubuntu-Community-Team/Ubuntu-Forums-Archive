---
title: "ssh problems.."
date: 2007-05-07
forum: General Help
---

### Post by billdotson on 2007-05-07
I have followed this guide : [URL="https://help.ubuntu.com/community/SSHHowto"]https://help.ubuntu.com/community/SSHHowto
[/URL]
to setup a pair of authorized keys so that my two PCs can ssh to each other.  However, if I do something like sudo ssh bill@IPaddress (IP address obviously being the real IP..) it asks me for the password (sudo password is what it accepts).  Then I can login that way.  I thought these authorized keys were there so that only that user could login.. now it seems I could just as easily login the other way from any other PC as long as I knew the IP..

I don't understand what is going on..

---

### Post by Nikron on 2007-05-07
> **billdotson said:**
> I have followed this guide : [URL="https://help.ubuntu.com/community/SSHHowto"]https://help.ubuntu.com/community/SSHHowto
[/URL]
to setup a pair of authorized keys so that my two PCs can ssh to each other.  However, if I do something like sudo ssh bill@IPaddress (IP address obviously being the real IP..) it asks me for the password (sudo password is what it accepts).  Then I can login that way.  I thought these authorized keys were there so that only that user could login.. now it seems I could just as easily login the other way from any other PC as long as I knew the IP..

I don't understand what is going on..

So, you want to be able for you only your computer to be able ssh to the target computer?  Or do you want only want to be able to log on using the key?

I think your problems will probably be solved by this HOWTo [https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)

---

### Post by billdotson on 2007-05-07
I want it to be so that you cannot logon to either PC via ssh without having the pair of keys on the computer that is attempting to login.  That is, having to give the passcode that goes along with the public and private key pair.  I don't want others to be able to login unless they have those keys in their ssh profile as a set of authorized keys.

---

