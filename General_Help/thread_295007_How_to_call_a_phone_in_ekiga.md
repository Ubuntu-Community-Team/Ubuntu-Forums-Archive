---
title: "How to call a phone in ekiga?"
date: 2006-11-07
forum: General Help
---

### Post by Shay Stephens on 2006-11-07
I setup Ekiga and have an account.  I have tried the [email]500@ekiga.net[/email] test and it worked fine.  I also started an account with diamondcard.us and put 10 bucks in it and have had the account verified.  And it is enabled in ekiga.

So now, I want to call my friend at 123-456-7890.  I live in the united states, so the country code is 01, which I believe would make the whole sip:
sip:011234567890

And it looks like I have to put a 00 in front of all that according to a help file I read.  So the whole thing now looks like:
sip:00011234567890

When I enter that, a diamondcard.us domain gets added and the leading 00 gets removed like this:
sip:018453420569@eugw.ast.diamondcard.us

It then beeps a few times, but then invariably I get this error:
User not found

It doesn't matter what phone number I use, my own, a friend, a cell phone, etc.  I always get the user not found error.  Anyone have any idea what I am doing wrong?

---

### Post by dentaku65 on 2006-11-07
mmm, I did not use ekiga but you can try with ++ instead 00 so:

sip:++011234567890

Like in gizmo I supposed...

---

### Post by Bigbluecat on 2006-11-07
I would think that you have to drop the first 0.

It will be using international dial as there is no way of determining location on the internet.

00 is a very common internationl access code. This should be followed by the country code:

USA is 1
UK is 44

So a US number would be 00 1 area code number
UK would be 00 44 area code number

You can ususally also substitute + instead of 00

+1 area code number

---

### Post by Shay Stephens on 2006-11-07
Thank you for the suggestion.  I tried it, but it would not place the call and said there was an abnormal call termination.  So the ++ looks like it is not an ekiga recognized thing.

Thanks anyway :D

---

### Post by Shay Stephens on 2006-11-07
Bingo!!!  That was the it.  I had to drop the leading 0 in the country code.  So my working sip looks like this:
00<country code with no leading 0><area code><phone number>
sip:0011234567890

Thank you so much!

> **Bigbluecat said:**
> I would think that you have to drop the first 0.

It will be using international dial as there is no way of determining location on the internet.

00 is a very common internationl access code. This should be followed by the country code:

USA is 1
UK is 44

So a US number would be 00 1 area code number
UK would be 00 44 area code number


---

### Post by Bigbluecat on 2006-11-07
Happy calling.

You will probably find that a single + will work in place of 00 as well.

---

### Post by Shay Stephens on 2006-11-07
> **Bigbluecat said:**
> Happy calling.

You will probably find that a single + will work in place of 00 as well.

I tried that, and got the error of "abnormal call termination".  So it looks like the only way it works so far for me is to put 001 in front of the phone number so it looks like this:
sip:[COLOR="Red"]001[/COLOR][COLOR="Blue"]123[/COLOR][COLOR="SeaGreen"]456[/COLOR]7890

I called my sister and parents already and it works great :D

A big thank you to everyone who replied and helped me out 8)

---

