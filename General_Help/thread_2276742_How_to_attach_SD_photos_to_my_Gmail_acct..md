---
title: "How to attach SD photos to my Gmail acct.?"
date: 2015-05-04
forum: General Help
---

### Post by bob120 on 2015-05-04
Applies to : Xubuntu 15.04

I attempted Thunderbird, wants my Gmail acct password(?). Why do I need a 3rd party involved?

What software do I need to install to upload images on my SD cards to my Gmail acct?
Is there instructions on how to install for your recommended install?

---

### Post by bapoumba on 2015-05-04
*Thread moved to **General Help**.*

How do you set up the email account ? Whichever maail provider you use, you will have to tell any email client your password.

For your second question, not sure I understand. Are you looking for an app that uploads to your google photos ? Other than using the web interface, maybe fspot would do it, but I have not tried.
[http://f-spot.org/Features](http://f-spot.org/Features)

---

### Post by ajgreeny on 2015-05-04
Are you thinking of picasa, which used to be available as a google application for photo management.
Or is you query about something completely different, as your comment about gmail does not make a great deal of sense; of course gmail will ask for your password if you have not already saved it in the setup of the account.

I you really do want picasa and this has nothing to do with gmail, you will have to get it from [http://picasa.en.softonic.com/](http://picasa.en.softonic.com/) as mentioned in the thread at [http://ubuntuforums.org/showthread.php?t=2273431](http://ubuntuforums.org/showthread.php?t=2273431)

Note that you will have to run it in wine, but it certainly used to run in wine very well when I last looked at the possibility of using it.

---

### Post by bob120 on 2015-05-05
Thanks for both responses.
I don't understand "email client".
One opens Gmail, then write info to send, select SD card numbers, attach photos and send.
Doesn't work, Xubuntu 14.04 comes with Thunderbird apparently for this, why?
Then Thunderbird wants my Gmail acct password, to me this is 3rd party intrusion.

Reviews said Thunderbird has unfixed bugs, did not look why, just don't want non-updated software.
If an "email client" is needed for attaching Gmail photos from SD cards what are my options? Is there instruction on how to do this?
Is there a different method without needing a Client?

---

### Post by ajgreeny on 2015-05-05
> **bob120 said:**
> I don't understand "email client".
One opens Gmail

Thunderbird is an "email client" just like a lot of other applications available in Windows, Macs and Linux.
You speak as if gmail is a dedicated application, which it isn't in Linux, but I presume from what you say that you are going to the gmail.com website in a web-browser, and either entering your gmail password, or have already let the browser save the password; how is that different from TBird doing the same?

As to your attachment problem, I have no idea if it is possible as I have always attached photos that are on my hard disk rather than on an SD card or an attached camera.  However I am about to try that and see if it works.

EDIT:
It works fine sending a photo direct from my SD card using TBird.  You must, however make sure that the SD card is still attached and mounted when you send or I don't think it will work.

Does that help in any way?

---

### Post by bob120 on 2015-05-05
AJgreeny,
Yes that solves my problem. I did not understant that Thunderbird is an application. Do a Gmail search on google and see the 3rd parties that want your signin info. See what page the actual signin is on. Appears I'm hacked too as Gmail always loads the security check page and shows, a few cities around me accessing my acct. , changing password does not help. But thats a different topic, security next on my list. tHank you.

---

### Post by bapoumba on 2015-05-05
What do you call the security check ? have you enabled the two steps authentication ?
I also find account login location not that reliable. It shows locations close by, but not the real one. I've always assumed this was coming from my internet provider that was not giving out accurate location (which is quite fine by me) and not that my account was compromised.

---

### Post by bob120 on 2015-05-06
Thunderbird fails on reinstall of Xubuntu 15.04. It will not recognize my Gmail password. I would dump Gmail except my Kijiji account needs this one. If you register a new address then a program catches this from keywords, then no doubt ones  address is checked too. Immediate loss of privileges.

I search the internet, no success.
Can't find a search for Ubuntu software center to look for a option besides Thunderbird, why is that?

Can anyone suggest a program compatible to 15.04?

bapoumba, Reply : I have Gmail signin page bookmarked, Name and pass automates to my chosen acct normally. Lately is redirects to a security page with a bunch of features including acct activity. Near the top, right one can select acct access and get into that acct.
I have reinstalled Xubuntu 14.10 and 15.04 repeatedly over other software not installing. I have changed my password, multiple times, now that fails too. Accepts the new password, but results in either  it does then it don't work. 

I do not use my phone number for internet reason.

I can understand Bell DLS 100MPS service using other locations nearby, as I've had input emails from the locations, Google will recognise the ip chain, why then the security checkup REQUEST from Google unless there is a reason?

Google and Kijiji are not easy to contact or get results let alone a reply. I looked for solution following the popups, waste of time.

---

### Post by bapoumba on 2015-05-06
If you reinstall, and do not keep your /home, writing over everything, it is normal that your personal settings are lost and you have to give them again.
When logging into gmail from a web browser, I get a security check from time to time. I review the info and click "OK looks good" (or some similar wording), it is part of google procedures now.

---

### Post by bob120 on 2015-05-07
Google is blocking Thunderbird, "does not use modern security standards". On a page called "allowing less secure apps to access your account". I don't want to decrease my Gmail security settings.

What other options are available without fees?

How do you search in "Ubuntu software center"?

EDIT: The security feature page : [www.google.com/settings/security/lesssecureapps](www.google.com/settings/security/lesssecureapps)

---

### Post by bapoumba on 2015-05-07
May be this : [http://googlesystem.blogspot.fr/2014/07/more-secure-gmail-authentication.html](http://googlesystem.blogspot.fr/2014/07/more-secure-gmail-authentication.html)
I set up the 2 steps verification right after it was set up by Google and have no problem with any email client I use. Google does not offer regular account login/password by default anymore and you have to revert to the old setting in your Google account to be able to use it now. So this is on you, your own choice, to log in with what Google calls "less secure" processes (their wording).

---

### Post by ajgreeny on 2015-05-07
> **bapoumba said:**
> May be this : [http://googlesystem.blogspot.fr/2014/07/more-secure-gmail-authentication.html](http://googlesystem.blogspot.fr/2014/07/more-secure-gmail-authentication.html)
I set up the 2 steps verification right after it was set up by Google and have no problem with any email client I use. Google does not offer regular account login/password by default anymore and you have to revert to the old setting in your Google account to be able to use it now. So this is on you, your own choice, to log in with what Google calls "less secure" processes (their wording).
What that linked information page specifically **does not say** is what email  clients, other than a few google and android ones, are using the  two-step Open Authentication google now are recommending.

I am still confused about this, and I am still using Thunderbird, but to do so I have to take that extra step that google recommend should not be taken, and allow a less secure application to access gmail, ie Thunderbird.
How did you manage to do this, as you say you already have, and also, can I ask what email client you use?

I believe this change has been handled appallingly by gmail over the past few months, and as I say above, I am a bit confused over the whole chabge that they have made; like a lot of others I suspect!

---

### Post by bapoumba on 2015-05-07
I use Sylpheed on ubuntu. Just set up TB with my gmail account to check. Gave the email address and the app password and was in right away. No problem.

---

### Post by bob120 on 2015-05-07
EDIT: I found Sylpheed in Ubuntu software center and many more to look at. Thanks for the info.

---

### Post by bob120 on 2015-05-07
Same problem as Thunderbird, Gmail blocks due to security. Google would not have this added security layer for no reason. 
I should be looking at a Gmail forum to get compatible application. I'll post what I find out.

---

### Post by bob120 on 2015-05-07
ajgreeny, So the issue is the email clients need to upgrade to match current security?

As I am advertising on Kijiji, opening unknown emails, it would be foolish to drop to a lower Gmail security setting. I'm a senior downgrading my items, not a business.

Any ideas?

---

### Post by bapoumba on 2015-05-08
Well, the only point is see is you move your gmail account to the "2 step verification" security level.
[https://support.google.com/accounts/answer/180744?hl=en](https://support.google.com/accounts/answer/180744?hl=en)
[https://www.google.com/landing/2step/](https://www.google.com/landing/2step/)

---

### Post by bob120 on 2015-05-08
The 2 step verification will not solve the issue as the problem is discussed in associated pages to:
[www.google.com/settings/security/lesssecureapp](www.google.com/settings/security/lesssecureapp)

The problem is identified. 
A solution is needed : the name of an email client that will work with Gmail security and Xubuntu 15.xx. It appears the EC's need upgrading.
I have this question posted on a Google forum too, asking for an app that will work.

---

### Post by raptir on 2015-05-08
In order to add your Gmail account that has 2-step verification enabled to an e-mail client on your desktop/laptop you will need to use an [application specific password]("https://support.google.com/accounts/answer/185833?hl=en"). I am not aware of any e-mail clients apart from mobile Gmail that support 2 factor authentication.

---

### Post by bob120 on 2015-05-08
raptir, I am aware of that, 2 step is not the issue, it is not needed for an email client with Gmail (There may be exceptions).

Go to the link I posted immediately above, that is the problem. The solution question, please read the rest of my last post. 

The topic is about Thunderbird not working WITH the CURRENT Google / Gmail security, NOT bypassing the security setting link posted above.

---

### Post by bapoumba on 2015-05-08
The above url gives me a 404.

---

### Post by bob120 on 2015-05-08
Search Google "less secure apps" "account settings".

On a Google forum a responder though it is not so important to set to "less secure". I'll do that for Thunderbird. 

Also suggested to look for email clients that use "Oauth". Does that apply to Linux? Is there apps?

---

### Post by bob120 on 2015-05-11
What a sick joke "Xubuntu is user friendly".

---

### Post by bapoumba on 2015-05-12
That behavior is on the Google side of things, not TB or any OS. I could set up my Google account in TB without any problem, but I use their 2 steps verification setup and gave an app specific password as required. Same for Sylpheed on Ubuntu, Opera Mail on the Macs, phone app on the phone etc.

---

### Post by bob120 on 2015-05-13
Very frustrating. I'll try with a different email service as both clients won't work. Sylpeed indicates an email was sent, never arrived, it was not a Gmail acct, just sent using the installed Gmail acct.

Any direction on email acct's that work but does not need a phone number? 

I'll try Bell.ca as they already know my number and are very selective of who they sell it too!

---

