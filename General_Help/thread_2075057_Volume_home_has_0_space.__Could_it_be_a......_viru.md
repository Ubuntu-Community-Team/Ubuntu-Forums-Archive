---
title: "Volume /home has 0 space.  Could it be a...... virus?!"
date: 2012-10-22
forum: General Help
---

### Post by Ifaistos on 2012-10-22
Hello everyone !

I am buffled!  My volume /home should be almost empty... yet it started saying that I have less and less space.

Only yesterday I erased files and made 5 gigs of space available.
Now it has 0 space again, without me downloading or writing on the HD anything at all!!

However I am using the system monitor bar, and I can see that there is a LOT of writing on the HD all the time!  Something is getting downloaded and something is getting written on the HD from time to time..

I have no idea as to how to react to that, or how to test it, or how to make it stop.

Any ideas anyone?

Thanks everyone in advance :-)


edit : to help you out guys..  I used iotop, and I saw that the prime candidate for the i/o writes on the HD is thunderbird!  It is constantly writing smt on the HD!  I have no idea what causes that or how to stop it.  (other than closing Thunderbird... which I need).

btw.. now that my /home has 0 space, I cannot open and see my e-mails.  I can receive but cant' see! :(
Anyone?

edit2 : I disabled all addons on Thunderbird.  It still writes smt on the HD.  Added the properties of the home folder.  Some files are unreadable?  Something is going on here...

---

### Post by ~LoKe on 2012-10-23
Edit -> Preferences -> Advanced
Uncheck "**Enable Global Search and Indexer**"

Click "**Network & Disk Space**"
Under "**Disk Space**" be sure to set the value to 1024 or less.  Then press "Clear Now".

---

### Post by rg4w on 2012-10-23
You may need to turn off indexing in FF.  I've found on a couple of my systems that once my mail db gets big enough the index maintenance for it becomes a nightmare of disk thrashing.

---

### Post by Ifaistos on 2012-10-23
@ Loke

Thank you for your answer :-)
I did what you said.  I set to 512 MB. Pressed clear now.
Thunderbird is still accessing the HD :(
And my /home is getting smaller.
I deleted a big chunk of about 25 gigs, so I created a whole lota space.. but the problem persists.
Any more ideas?

@rg4w

Thank you for your answer.
What is FF?  and how do I turn indexing off?

---

### Post by ~LoKe on 2012-10-23
> **Ifaistos said:**
> @ Loke

Thank you for your answer :-)
I did what you said.  I set to 512 MB. Pressed clear now.
Thunderbird is still accessing the HD :(
And my /home is getting smaller.
I deleted a big chunk of about 25 gigs, so I created a whole lota space.. but the problem persists.
Any more ideas?

@rg4w

Thank you for your answer.
What is FF?  and how do I turn indexing off?
Did you disable Indexing in the same window?

---

### Post by Ifaistos on 2012-10-23
Please check if what I did is correct.

Thank you :-)

---

### Post by ~LoKe on 2012-10-23
Yeah, that should be fine.  Try:
```
sudo killall thunderbird && thunderbird &
```

---

### Post by Ifaistos on 2012-10-23
I forgot to tell you that I rebooted after I did that.

Shouldn't that be the equivalent of killall?

Anyway I did the killall...

I restarted thunderbird and.. thunderbird is still on the top of my iotop list in writing accesses to my HD. :(

I am attaching two picts of the thunderbird and home folder.
I cleared 25 gigs an hour ago, and now its down to 22 gigs.

This thing is eating my HD space with incredible speed !!

---

### Post by sandyd on 2012-10-23
Hmm
I think that thunderbird is downloading ALL your email.

so maybe...

go to Edit -> Account Settings -> Synchronization & Storage

set "Synchronize Most recent" and "Don't Download Messages Larger Than"

to one day

---

### Post by silencej on 2012-10-23
NO USE!

I also suffered from this problem and I am with Ubuntu 12.04, thunderbird 16.0.1.

I deleted my TB profile and now the dir .thunderbird comes to 4GB from only 23M in the beginning. I've tried all disk limiting options in Thunderbird but got nothing improved.

I am very upset about this. And even angry that there is no easy way to submit a bug report. For those who has same problems, I would suggest: use web-based gmail instead, or submit a bug report to Thunderbird -- for sake of us!!!


> **sandyd said:**
> Hmm
I think that thunderbird is downloading ALL your email.

so maybe...

go to Edit -> Account Settings -> Synchronization & Storage

set "Synchronize Most recent" and "Don't Download Messages Larger Than"

to one day

---

### Post by Ifaistos on 2012-10-23
@sandyd

I think you are right!  There is a lot of downloading and saving on HD that is going on.  When I close down TB it stops!

What I don't understand is why?!  I haven't upgraded TB, I haven't upgraded Ubuntu to the new version, so why on earth has it decided to re-download all my e-mail and save it again...

I have a lot of e-mails that I am checking here.  There are two major ones, and a few other less used ones.
I did what you said, but the downloading still goes on.

@silencej

I am sorry to hear that.  What do you think caused that?!
It would be very difficult for me to use web based e-mail.  I am using calendar and provider for google.  I am using searching on my contacts and many more on my TB.

So web based mail, would be a very temporary solution.
Could you please inform me if you have found smt new about this?
Do you know what caused this?

Thanks

in the meanwhile... any more ideas?

---

### Post by Ifaistos on 2012-10-23
bump :-)

---

### Post by Ifaistos on 2012-10-23
bumpity bump :-)

---

### Post by oldos2er on 2012-10-23
Please don't bump your post more than once every 24 hours. Thanks.

---

### Post by awr on 2012-10-23
Bumping too much is rude, please refrain from doing so more than once in 24hours.

As sandyd mentioned, Thunderbird is likely download all emails from your email account.  Depending on who you have email setup through, and the settings on that account and in Thunderbird, this could be years worth and many GBs.

Thunderbird will download ALL the mail stored in your account unless you tell it otherwise (change the settings as sandyd specified).  If you have GBs of messages then it will try to download all of it.  If it is a new install of Thunderbird then it has no way of knowing that you have already read it and will download it all.

There are a few ways to prevent this, but will depend on what system your email provider uses.  If you are unfamiliar with mail servers and how they work try the following link, particularly the sections on SMTP, POP, and IMAP.  [http://whatismyipaddress.com/mail-server](http://whatismyipaddress.com/mail-server)

---

### Post by Ifaistos on 2012-10-24
@oldos2er and @awr

Will do. Thanks for letting me know.  To my own defense : I've been writing in forums for quite some time and it seems that there is no set time limit for bumping.  Some forums don't allow it at all, some tolerate it, some are very lenient and some even encourage it...  I just didn't know what was the proper etiquette in these forums.

@awr

It seems that we have established beyond any doubt that TB is causing that.  I also noticed that when I launch TB it does start to download staff from my imap gmail accounts.  I just don't understand why!  As I mentioned above, it is not a new installation.  Why did it decide to d/l now?

Is there a way to stop downloading from gmail?  The important folder is a folder that gmail has created and I certainly don't mind if I don't have anything from it on my HD.

Should I allow it to download everything and stat erasing the e-mails from my local folders?

---

### Post by sandyd on 2012-10-25
Is there any way you can 

a) Delete the thunderbird profile
b) Readd the accounts while making sure the options I mentioned earlier are checked

I think that since the operation to download all your emails has already commenced, it ignores the settings because it just resumes the download operation each time you start up thunderbird.


Thanks for testing!

---

### Post by Ifaistos on 2012-10-25
Hey Sandyd :-)

I am bit reluctant to do what you told me.
The way I "managed" the situation, is to let it do what it wants.  It downloaded a lot of GB, and now it has stopped.

I have no idea why it behaved the way it behaved out of the blue.

I have cleared a big chunk of my home folder and the empty space is now stable...

So I am afraid to mess with it right now...

Thank you for your help though.. I do appreciate it :-)

---

### Post by el cameleon on 2012-10-26
Hi gents,


This issue is certainly related to a regression introduced in TB16 and which impact some IMAP servers (like dovecot).
  [Bug 803843 - IMAP mailfiles keep growing to gigabyte size]("https://bugzilla.mozilla.org/show_bug.cgi?id=803843")

---

### Post by Ifaistos on 2012-10-26
@el cameleon

Hola !  Thank you for your link.  It seems that I am not the only one with this problem.  I guess the problem will be taken care of eventually by TB itself.
I will keep an eye on the bug link and see what happens.

Do you know of any other way to find out if the bug was eventually solved?

Thanks for the help :-)

---

### Post by el cameleon on 2012-10-26
> **Ifaistos said:**
> Do you know of any other way to find out if the bug was eventually solved?
No better way than looking at the bug itself ;-)

I hope a fix will soon be available in Thunderbird 17 beta, maybe in a few days.

---

### Post by Ifaistos on 2012-10-27
I will mark this as solved since I think we found the source of the problem, although the solution is not there yet.

Thanks everyone :-)

---

### Post by silencej on 2012-10-29
> **Ifaistos said:**
> I will mark this as solved since I think we found the source of the problem, although the solution is not there yet.

Thanks everyone :-)

I know it! I know it!

I know it's the bug from TB! So I transfered to web based Gmail and Calendar. I tried to file a bug report to Mozilla, but found it more inconvenient than post a complaint here in Ubuntu forum... :guitar:

Cheers for the emerged bug report and await for fix.

---

### Post by Ifaistos on 2012-10-29
Let's hope so !!

I just upgraded to 12.10, and TB started downloading again.
My home folder has gone down by almost another 6 Gigs !!!

This is ridiculous !!

---

### Post by Ifaistos on 2012-10-30
I just downloaded the update for the bug fixes for TB.
So it seems that I stumbled upon a major bug, that thousands of people had.

The problems were fixed and the related Bugs in launchpad are : 

[https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/1072362](https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/1072362)
[https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/1068921](https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/1068921)

So all you have to do is just update TB.

My question is this : 

This bug fix, will also work retroactively and fix the problems the previous TB version created?
Will it restore to it normal size the Huge mailboxes, and restore the space in our HD?

Does anyone know?

If not, what are the steps we need to take, in order the remedy the problem?

Can anyone point to a link with the solution?

Thank you all :)

---

