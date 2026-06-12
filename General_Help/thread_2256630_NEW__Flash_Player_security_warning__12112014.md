---
title: "NEW  Flash Player security warning  12/11/2014"
date: 2014-12-13
forum: General Help
---

### Post by choochoousmc on 2014-12-13
UsingUbuntu  13.10   will likely upgrade in Jan.15  whenI get a newer  computer.
Any way  12/10/2014  all of a sdden all windows that required flash player in order to display  were deactivated.
Warning says this version is vulnerable.

So click the link to update  goes to Mozilla page,  says I am running current version.

But I also get warning to update Fire fox.

However go to software center there is not a newer version in the repository

So anybody else getting these warnings?   is there a new virus threat?

If repository doed not have newer versions of Flash or Firefox  then how do we upgrade?

---

### Post by kostkon on 2014-12-13
13.10 is [EOL]("http://www.ubuntu.com/info/release-end-of-life") so it isn't supported with security updates anymore. Supported versions of the Ubuntu Desktop (currently 12.04, 14.04, 14.10, 15.04) continue to receive security updates for Flash 11.2.

You should upgrade to 14.04 LTS (supported for 5 years) or later versions or disable your Flash since it is vulnerable in 13.10.

Same situation applies to your Firefox, it is vulnerable.

As a temporary solution you could download and use Chrome instead (comes with its own Flash, PepperFlash), hopefully it still runs fine in 13.10.

---

### Post by QIII on 2014-12-13
Hello.

The Ubuntu Forums Staff highly recommends installation of a currently supported release of Ubuntu.  Please see [this]("http://ubuntuforums.org/showthread.php?t=2229730") sticky.

If you have trouble installing a currently supported release, please start a new thread.

Thanks.

---

### Post by choochoousmc on 2014-12-13
thanks for the input, but you obviously didn't understand the question.
I know I have reached the EOL for my version, that isn't or wasn't the point. So that was moot.

And if you noticed, I also said I plan on an upgrade in Jan.

The question was  has others been getting these warnings?  (recently)   
 Was there a new virus outbreak in the past few days?

If so what have you been doing besides an immediate upgrade?

also since a newer version of flash and firefox is not in the repository, how does Ubuntu expect us to upgrade those, whether we upgrade the OS or not?

Much appreciated if you all reply to the actual question asked.  It's more helpful that way.

---

### Post by mc4man on 2014-12-13
> also since a newer version of flash and firefox is not in the repository, how does Ubuntu expect us to upgrade those, whether we upgrade the OS or not?
There will be no new versions of flash in Linux, I guess some security updates for a bit longer
( I got one recently - flashplugin-nonfree (11.2.202.425ubuntu0.14.04.1)

If you use an Eol release then Ubuntu's cares about your install are done. You can install a newer firefox yourself in some manner, ask & someone should tell you how

---

### Post by QIII on 2014-12-13
> **choochoousmc said:**
> thanks for the input, but you obviously didn't understand the question.
I know I have reached the EOL for my version, that isn't or wasn't the point. So that was moot.

And if you noticed, I also said I plan on an upgrade in Jan.

The question was  has others been getting these warnings?  (recently)   
 Was there a new virus outbreak in the past few days?

If so what have you been doing besides an immediate upgrade?

also since a newer version of flash and firefox is not in the repository, how does Ubuntu expect us to upgrade those, whether we upgrade the OS or not?

Much appreciated if you all reply to the actual question asked.  It's more helpful that way.

No.  We read and understood quite well.  The answers given were appropriate.  

You were given an answer as to why those upgrades are not available -- your release is no longer receiving updates of any kind because it has passed its EOL.  You are getting warnings from the websites you are visiting because they detect that you are using an older, insecure version of Flash.

A user gave you that answer.

You were told that the Staff would rather not see those who volunteer here spending their time here answering questions about releases that are no longer supported.

A member of the Forums Staff gave you that answer.

---

### Post by choochoousmc on 2014-12-13
> **mc4man said:**
> There will be no new versions of flash in Linux, I guess some security updates for a bit longer
( I got one recently - flashplugin-nonfree (11.2.202.425ubuntu0.14.04.1)

If you use an Eol release then Ubuntu's cares about your install are done. You can install a newer firefox yourself in some manner, ask & someone should tell you how

Once again NO.
I asked was anybody else getting these warnings.    And since you keep on insisting about the end of life.
If others have not yet upgraded   what have they been doing. Not that I care as that wasn't important.

I fully understand no new updates, but I also read elsewhere Flash may no longer be upgraded at all for Firefox.
So if that is the case, what are others doing???  the original question to the issue of is there a new virus threat?

Is UBUNTU and firefox going to collaborate on a new player that imbeds into ubintu  and firefox  or will we all be forced to change to chrome.
Whether we upgrade the OS or not.  This is a new question I'm forced to ask, because the original of what others are doing wasn't answered.

I know how to do an outsource new install.
But still the question remains.  Has others been getting the warning. Have others been told they have the newest update. Has there been a new virus outbreak in the last few days.   Those were the questions.

---

### Post by QIII on 2014-12-13
> Has others been getting the warning. Have others been told they have the  newest update. Has there been a new virus outbreak in the last few  days.   Those were the questions.

1.  Very likely, if they are using an out-dated version of Flash.

2.  Yes, if they do.  No, if they don't.

3.  Unknown and doesn't matter.  The websites are detecting that an older, insecure version of Flash is being used.

> Is UBUNTU and firefox going to collaborate on a new player that imbeds into ubintu  and firefox...

No, not for an unsupported release.  Canonical is not going to offer updates for an unsupported release.

> or will we all be forced to change to chrome

Nobody is forcing anyone to use Chrome.  Updating your installation will address your concerns.

Now, please do not belabor this or the thread may be closed.

---

### Post by kostkon on 2014-12-13
> **choochoousmc said:**
> Once again NO.
I asked was anybody else getting these warnings.    And since you keep on insisting about the end of life.
If others have not yet upgraded   what have they been doing. Not that I care as that wasn't important.

I fully understand no new updates, but I also read elsewhere Flash may no longer be upgraded at all for Firefox.
So if that is the case, what are others doing???  the original question to the issue of is there a new virus threat?

Is UBUNTU and firefox going to collaborate on a new player that imbeds into ubintu  and firefox  or will we all be forced to change to chrome.
Whether we upgrade the OS or not.  This is a new question I'm forced to ask, because the original of what others are doing wasn't answered.

I know how to do an outsource new install.
But still the question remains.  Has others been getting the warning. Have others been told they have the newest update. Has there been a new virus outbreak in the last few days.   Those were the questions.
No, we aren't getting the warnings. New vulnerabilities for Flash are appearing every so often, so we've become immune to the news, so to speak.

Flash in Ubuntu is still supported with security updates (Adobe will support Flash 11.2 until 2017).

After that, we don't know. [Ubuntu developers are still thinking about it]("http://www.phoronix.com/scan.php?page=news_item&px=MTgzODI"). Also, [Firefox now comes with its own Flash implementation, still disabled by default]("http://www.phoronix.com/scan.php?page=news_item&px=MTQ3NjY"). When it gets better, it will become the default one, I'm guessing.

Hope that clears things up a bit.

---

### Post by grahammechanical on 2014-12-13
During the recent Ubuntu Online Summit there was a discussion on this subject or something similar. I could not follow most of it. It seemed complicated and not easy for Ubuntu developers to anything about it. But here is the link

[http://summit.ubuntu.com/uos-1411/meeting/22354/adobe-flash-on-firefoxlinux-eol/](http://summit.ubuntu.com/uos-1411/meeting/22354/adobe-flash-on-firefoxlinux-eol/)

The correct solution is for web site designers stop using Adobe flash. 

Regards

---

### Post by Yellow Pasque on 2014-12-15
If you insist on running an EOL release, then you probably want to purge Ubuntu's Flash package and install/update it manually. 
1. Go here: [https://get.adobe.com/flashplayer/](https://get.adobe.com/flashplayer/)
2. Download the tar.gz and extract the libflashplayer.so
3. Close FF
4. Put the libflashplayer.so in ~/.mozilla/plugins  (note that the .mozilla is a hidden directory and you will probably need to create the plugins folder the first time you do this)
5. Start FF and double check the Flash version

Lather, rinse and repeat for every Flash security update. Expect at least one a month. [https://www.adobe.com/software/flash/about/](https://www.adobe.com/software/flash/about/)

> During the recent Ubuntu Online Summit there was a discussion on this subject or something similar. I could not follow most of it. It seemed complicated and not easy for Ubuntu developers to anything about it
That's talking about Flash for Firefox/NPAPI itself being "EOL" (not running Flash on an EOL release like the OP). Adobe will provides security updates until 2017, but eventually the axe will fall...

---

