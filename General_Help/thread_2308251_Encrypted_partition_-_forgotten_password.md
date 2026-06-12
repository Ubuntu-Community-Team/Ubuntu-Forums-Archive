---
title: "Encrypted partition - forgotten password"
date: 2016-01-01
forum: General Help
---

### Post by Jacek_Polaczek on 2016-01-01
Hello everyone and Happy New Year.

My new year didn't start well :-( . I've lost the card with password which is necessary to encrypt the partition (I use Ubuntu 14.04)...

I know the password length, first 3 letters and last 3 or 4 letters.

Do you have any ideas how can I recover it?

Do you know any programs which I can use (on LiveCD)?

---

### Post by ian-weisser on 2016-01-01
You cannot recover it, sorry.
There is no encryption recovery method or application. That's due to the nature of encryption - there simply are no mathematical shortcuts for a recovery method or application to use.
Without the password, your data is gone forever.

I would try real hard to find that card.
Or, since you know six or seven characters of the password, start trying methodically to solve the rest.

---

### Post by Jacek_Polaczek on 2016-01-01
It's impossible to find the card, I left it in the restaurant and the waitress doesn't know about it. I've been there already 3 times, they think that I'm crazy :-)

Really it's impossible :( ?
I know most signs, 
For example -> XXXxxxXXXX , I know only uppercase letters, so there's not a lot of combinations, but I don't want to do it manually. I tried a lot of times but I can't remind 3 characters ...

---

### Post by ian-weisser on 2016-01-01
Well, that example has only about 17,000 possible solutions. You can likely script a solution to try each solution methodically.
However, since I don't use encryption, I'll leave the advice on how to do so up to another community member more familiar with that end of the system.

---

### Post by dragonfly41 on 2016-01-02
I do not have the need to encrypt my Ubuntu OS.   But your experience led me to research further what approach I might take in similar circumstances.

Here are a few of articles I found in a quick search.

[http://resources.infosecinstitute.com/popular-tools-for-brute-force-attacks/](http://resources.infosecinstitute.com/popular-tools-for-brute-force-attacks/)

[http://www.cybercrimetech.com/2014/08/how-to-brute-forcing-password-cracking.html](http://www.cybercrimetech.com/2014/08/how-to-brute-forcing-password-cracking.html)

[https://alvinabad.wordpress.com/2012/09/22/how-to-recover-a-luks-encrypted-disk/](https://alvinabad.wordpress.com/2012/09/22/how-to-recover-a-luks-encrypted-disk/)


From my reading it seems that you need to get to a point (from Live CD) where you are brute force attacking cryptsetup?

In this [http://www.cybercrimetech.com/2014/08/how-to-brute-forcing-password-cracking.html](http://www.cybercrimetech.com/2014/08/how-to-brute-forcing-password-cracking.html)  the author writes

> 
[COLOR=#666666]Regardless of some challenges, cryptsetup does have some useful options, such as -T which controls how many times it will ask for a password before giving up. And also the option [/COLOR]*--test-passphrase*[COLOR=#666666], which will see if the password worked without actually opening the device. So right now we have the following command to open the LUKS device:[/COLOR][COLOR=#666666]

cryptsetup luksOpen $1 x --test-passphrase -T1
[/COLOR]

Since you have a head start by remembering part of the password (start and end strings) perhaps you could you write a python script to loop through concatenating strings into a passphrase

known start string . bruteforce attack string . known end string

where middle string is limited to xxx?

This approach might give you a start.

---

