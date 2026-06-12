---
title: "Changing Password In Thunderbird Mail"
date: 2021-10-22
forum: General Help
---

### Post by daniell59 on 2021-10-22
I would appreciate it if somebody could tell me how to change password in Thunderbird mail. I cannot seem to locate where to do so.

Thanks

---

### Post by norobro on 2021-10-22
Edit->Preferences 
Under passwords press the 'Saved Passwords' button.

To me the logical location would be under Account Settings.

HTH

---

### Post by TheFu on 2021-10-22
It should be noted that this does not change the password on the mail/imap/pop3 server. Those need to be changed on the server-side.

---

### Post by daniell59 on 2021-10-22
Thanks, but now but I am looking at the problem differently.
I cannot retrieve my email on Thunderbird. I assumed that it was a password problem. I called my provider and they assured me that it was not on their end. Now I see that they are correct. This is the strange part. I have another hard drive with windows. I also cannot retrieve the mail on Thunderbird. I can retrieve the mail on my phone as well as on my tablet. Anybody have an idea what is going on?

Thanks

---

### Post by TheFu on 2021-10-22
> **daniell59 said:**
> Thanks, but now but I am looking at the problem differently.
I cannot retrieve my email on Thunderbird. I assumed that it was a password problem. I called my provider and they assured me that it was not on their end. Now I see that they are correct. This is the strange part. I have another hard drive with windows. I also cannot retrieve the mail on Thunderbird. I can retrieve the mail on my phone as well as on my tablet. Anybody have an idea what is going on?

Thanks

That isn't really any technical data for guesses to the issue.  I happened to have an issue with an account on my email server (I've been running corporate mail servers for  ... well ... a very long time and the first thing I noticed was that Thunderbird had lost all email for that account.  I have multiple accounts and the others were all working.  I thought it was an expired password - for some accounts, I force a password change periodically.  This has absolutely nothing to do with your situation - mine was a corrupted userid on the server. I ended up grabbing all the msg files for that account and re-injecting them into a newly created account on the server.  That fixed the thunderbird access for me. You can't do that.

What you can do is
[LIST]
[*]note the EXACT, 100% correct, errors that Thunderbird is displaying. This is one of the few times that an image is useful in these forums.
[*]Show your Server connection page ... just blur out the userid/email address.  We'll need to see the IMAP/POP settings AND the SMTP settings That 2 different pages.
[*]Create a new userid on Ubuntu, login to that other account, run thunderbird and connect it to the same email address/server.  If that works, then it is an incompatible thunderbird config back in the original account.  Linux is multi-user. Time to use it that way.  If the issue persists, then it is either on the entire system or on the email provider's systems.  The fact that some other devices aren't having problems tells me it is on your computer and could be due to the thunderbird settings that have been moved forward over time.
[/LIST]
Those are just some things to try.

I would find it helpful to see a clear list for the devices, exact email program and what works and what doesn't on each for the account.
Also, the results of the 3 troubleshooting ideas above.

And, of course, please check your system logs for issues, but thunderbird probably won't write to those.  There are probably thunderbird logs somewhere in your HOME. See if you can find those.

---

### Post by Quarkrad on 2021-10-23
Just a thought (although your answer almost certainly will follow the logical path of #5).  Fire up the Evolution email client on your machine and configure that for your email account - if your problem is Thunderbird specific then your Evolution client should be working 100% ok.

---

### Post by daniell59 on 2021-10-23
Having a limited amount of knowledge, I would like to uninstall Thunderbird. What is the best of of doing this? I can then either reinstall it or try another app such as Eudora. I am open to suggestions.

Thanks

---

### Post by walts48 on 2021-10-23
> **daniell59 said:**
> Having a limited amount of knowledge, I would like to uninstall Thunderbird. What is the best of of doing this? I can then either reinstall it or try another app such as Eudora. I am open to suggestions.

Thanks

Find it in the software manager application and uninstall it.

---

### Post by TheFu on 2021-10-23
> **daniell59 said:**
> Having a limited amount of knowledge, I would like to uninstall Thunderbird. What is the best of of doing this? I can then either reinstall it or try another app such as Eudora. I am open to suggestions.

Thanks

Best?  That depends.  Use whatever package manager you normally use.
I would type
```
sudo apt remove --purge thunderbird*
```
or  to reinstall it
```
sudo apt install  --reinstall thunderbird 
```

I have 3 packages on my system related to thunderbird
```
$ dpkg -l thunder*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                      Version                           Architecture Description
+++-=========================-=================================-============-========================================>
ii  **thunderbird**               1:78.13.0+build1-0ubuntu0.20.04.2 amd64        Email, RSS and newsgroup client with int>
un  thunderbird-gnome-support <none>                            <none>       (no description available)
ii  thunderbird-locale-ru     1:78.13.0+build1-0ubuntu0.20.04.2 amd64        Russian language pack for Thunderbird

```
Most people would only have the first 2.

---

### Post by daniell59 on 2021-10-23
The ISP finally conceded that they changed some setting. They said that a technician will get back to me in several days. For what I am paying, I should not have to wait that long. I tried fixing it myself, but could not do so. In the past, whenever I put an email app in, it would automatically do the configuring. I tried to do it manually in both Thunderbird and Evolution with no success.

Thank you for listening

---

### Post by TheFu on 2021-10-23
> **daniell59 said:**
> The ISP finally conceded that they changed some setting. They said that a technician will get back to me in several days. For what I am paying, I should not have to wait that long. I tried fixing it myself, but could not do so. In the past, whenever I put an email app in, it would automatically do the configuring. I tried to do it manually in both Thunderbird and Evolution with no success.

Thank you for listening

Most ISPs have an email configuration page with detailed information about the settings.  
[LIST]
[*][https://www.att.com/support/article/email-support/KM1010523/](https://www.att.com/support/article/email-support/KM1010523/)
[*][https://www.xfinity.com/support/articles/email-client-programs-with-xfinity-email](https://www.xfinity.com/support/articles/email-client-programs-with-xfinity-email)
[*][https://www.cox.com/residential/support/email-server-settings.html](https://www.cox.com/residential/support/email-server-settings.html)
[*][https://www.spectrum.net/support/internet/email-troubleshooting/](https://www.spectrum.net/support/internet/email-troubleshooting/)
[*][https://frontier.com/helpcenter/categories/internet/email/troubleshooting-email/get-started/mail-server-settings](https://frontier.com/helpcenter/categories/internet/email/troubleshooting-email/get-started/mail-server-settings)
[/LIST]
As you can see if you scan all those links, they are all very, very, very, similar. There are standards. Most ISPs follow those standards.
Of course, gmail follows only the standards they like, but often not all of them.

There are many reasons NOT to use ISP-based email, but to use some other cloudy provider instead. The main reason is that you can change ISPs, but not have to change email addresses on hundreds of accounts. Just be certain to pick your email provider carefully.  

OTOH, I have trust issues, so I run my own email server. Almost nobody should do that. Running email servers isn't for hobbyists. Also, using free email services means that your data is being sold - they have to pay their bills somehow.  I wouldn't doubt that ISPs are doing this too.

---

### Post by T6&amp;sfpER35% on 2021-10-23
> [COLOR=#000000]I am open to suggestions.[/COLOR]
i myself tried and never liked thunderbird
i use mailspring and never have a problem
[https://snapcraft.io/mailspring](https://snapcraft.io/mailspring)

---

### Post by TheFu on 2021-10-23
> **3nd said:**
> i myself tried and never liked thunderbird
i use mailspring and never have a problem
[https://snapcraft.io/mailspring](https://snapcraft.io/mailspring)

I started using Netscape Mail in the mid-1990s. At the time, it was really the only email program that didn't suck. Thunderbird grow out of that project and added network calendaring, gpg-encryption, network address-books. Initially those were addons, but about 2-3 yrs ago, they became part of the core thunderbird.  

Thunderbird integrates nicely with calDAV and cardDAV systems ... and with Zimbra Server  or postfix/dovecot systems.  I haven't found any other tool that easily integrates calendaring and email that isn't also bloated.  MS-Exchange is the 2nd largest desktop program ever made, behind iTunes.  Evolution is 3rd, it seems.  There are a number of alternatives, but some are miscategorized as email clients.

I've played with K-9 Mail, Claws, elm, alpine, and a few others.  I dislike webmail, but love having filters and organization happen on the server-side, not tied to any client software.  I still use the standard CLI "mail" almost daily to send emails, but not for reading.  If any email is left on my systems, I consider that a misconfiguration issue. After a bad thunderbird change a few years ago, I switched to Claws for a few months, but always felt the lack of calendar support was a huge problem.  I use k-9 mail on Android.  For what it is, it works fine.  I use calendar reminders for all sorts of needs, especially periodic stuff like renewing certs or registrars.  Some reminders are 5-10 yrs from now, but still extremely important.

The one thing I wish thunderbird would provide that they don't today is a tiny xbiff tool.  I've been using gnubiff, but it gets confused and doesn't pick up the connection settings from thunderbird.  That means it is yet another location to have email credentials stored, maintained and updated. Just another hassle.

---

### Post by daniell59 on 2021-10-25
I reinstalled Ubuntu 20.04 on another computer. I then installed Thunderbird. The same problem. The server from my ISP would not accept the password. This was with two computers with Ubuntu and one with windows. This is what I don't understand. The password works on the website of the ISP. Also, I can retrieve the email on my smart phone and on an Amazon tablet. I am still waiting for the technician from the ISP to contact me. I guess I should not hold my breadth waiting.

---

### Post by TheFu on 2021-10-25
> **daniell59 said:**
> I reinstalled Ubuntu 20.04 on another computer. I then installed Thunderbird. The same problem. The server from my ISP would not accept the password. This was with two computers with Ubuntu and one with windows. This is what I don't understand. The password works on the website of the ISP. Also, I can retrieve the email on my smart phone and on an Amazon tablet. I am still waiting for the technician from the ISP to contact me. I guess I should not hold my breadth waiting.

There is good news and bad news about your results above.
Something in the thunderbird settings, which you seem to be consistent in entering, is incompatible with the ISP.
The fact that their webmail works, just means that they tested that, but not thunderbird.
Ask them for a webpage that explains how to setup thunderbird for email to connect to their system. Don't mention linux. Get the Windows instructions and follow those.  The main settings in both are identical, but I think "Edit --> Account Settings" on Linux and "Tools --> Preferences" is on Windows.I could be wrong. I haven't used Windows for email in probably 8-10 yrs.  Anyways, you'll figure it out and the ISP will actually need to have one of their people figure out the Thunderbird settings, which they should do.  There are 5 major email clients - thunderbird in one of those.

---

### Post by daniell59 on 2021-10-25
I called back the ISP. They changed my password. Again, Thunderbird could not retrieve it but the smartphone could. Up to about a week ago, Thunderbird was working perfectly on all of my computers. Something at the ISP end must have changed. They said that they were escalating the problem.

---

### Post by TheFu on 2021-10-25
> **daniell59 said:**
> I called back the ISP. They changed my password. Again, Thunderbird could not retrieve it but the smartphone could. Up to about a week ago, Thunderbird was working perfectly on all of my computers. Something at the ISP end must have changed. They said that they were escalating the problem.

Do they not have a webpage with all the required settings for email clients - similar to the example pages I posted above?

---

### Post by daniell59 on 2021-10-25
I just heard again from my ISP. I was told that they are in the process of changing over the server name and I wont be able to use the app until the work is completed.

---

### Post by TheFu on 2021-10-25
> **daniell59 said:**
> I just heard again from my ISP. I was told that they are in the process of changing over the server name and I wont be able to use the app until the work is completed.

You can check the DNS record TTL, so see how often a change might be seen.  If they were to tell you the new FQDN server name AND the IP address, then you could add that to your /etc/hosts file and have access now.  I have doubts that is related.  It could be they are trying to use techno-babble to make you go away for a day.  DNS updates for ISPs typically propagate hourly, if not much more often.  I think 5 minutes is a common TTL.  For low use, single server, websites, once a day is often sufficient. It is a judgement call.  Because I use a free DNS service that I'm grandfathered into, there is a cap on the number of queries they will allow before I'll need to pay for commercial service. I typically know  months before a DNS change will be made, so I can setup a reminder a week prior to change the TTL down to 1 hr, then 5 minutes the night before the change. I only do DNS changes on weekends - after doing something really dumb 20 yrs ago that broke all the services on a few domains for a few days before I realized it.  Internally, everything was working. Externally, not so much.

---

### Post by daniell59 on 2021-10-26
Without the help of the ISP I solved half of my problem. I can now receive email in the app but cannot send it. I changed the sever name. I called the ISP. They have to again escalate the problem. They say that they are having some problem. I don't think that I am getting competent help.

---

