---
title: "Empathy Facebook Issue in 12.10"
date: 2013-02-23
forum: General Help
---

### Post by prashant7526 on 2013-02-23
I have 2 issue with empathy and facebook:

When you configure facebook correctly in Empathy and everything start to work after then sometime these problem come:

1.  while working if you get disconnected from your Internet any how, Empathy start to
     giving message of Facebook account authorization which is very hard to resolve
     after trying many time.
                In this case :  First i go to facebook and remove UBUNTU app from my 
                                         facebook and login again after from Empathy repeating this 
                                         process many times,
                                         I get connect to facebook. (Which i think still is an issue)

2.   But today i am facing another new Issue i.e., when i got disconnected from Internet 
       my Facebook as usual again asking for authorization but this time, when i clicked on 
      Authorize it is not opening page in the BOX of empathy instead it is opening some
      Link in Firefox browser:

                 [https://www.facebook.com/login.php?skip_api_login=1&next=https%3A%2F%2Fwww.facebook.com%2Fdialog%2Foauth%3Fclient_id%3D302061903208115%26redirect_uri%3Dhttps%253A%252F%252Fwww.facebook.com%252Fconnect%252Flogin_success.html%26display%3Dpopup%26type%3Duser_agent%26scope%3Dpublish_stream%252Cread_stream%252Cstatus_update%252Cuser_photos%252Cfriends_photos%252Cxmpp_login%26from_login%3D1&cancel_uri=https%3A%2F%2Fwww.facebook.com%2Fconnect%2Flogin_success.html&display=popup&api_key=302061903208115](https://www.facebook.com/login.php?skip_api_login=1&next=https%3A%2F%2Fwww.facebook.com%2Fdialog%2Foauth%3Fclient_id%3D302061903208115%26redirect_uri%3Dhttps%253A%252F%252Fwww.facebook.com%252Fconnect%252Flogin_success.html%26display%3Dpopup%26type%3Duser_agent%26scope%3Dpublish_stream%252Cread_stream%252Cstatus_update%252Cuser_photos%252Cfriends_photos%252Cxmpp_login%26from_login%3D1&cancel_uri=https%3A%2F%2Fwww.facebook.com%2Fconnect%2Flogin_success.html&display=popup&api_key=302061903208115)

       Now what is this new problem i don't understand. Please Advise and also i request Ubuntu Community and Canonical to report this issue to Empathy.

If anyone having solution for this please advice me.

---

### Post by titagula on 2013-02-23
I was having this issue as well, but rather than find a proper solution, I just stopped using Empathy. Not so much help as it is a form of surrender, but it did stop the problem...

---

### Post by prashant7526 on 2013-02-23
This is not a proper way... I understand your problem. But I want solution because these are the big bugs can also effect the impression of ubuntu.....

Please anyone here who can help!!!

---

### Post by prashant7526 on 2013-02-23
Can anyone Help me?

---

### Post by prashant7526 on 2013-02-24
There is same bug reported on launchpad :

[https://bugs.launchpad.net/signon-ui/+bug/1132296](https://bugs.launchpad.net/signon-ui/+bug/1132296)

but no solution. Anyone can you please work on it? And please advice what to do to fix this?

---

### Post by prashant7526 on 2013-02-24
> **titagula said:**
> I was having this issue as well, but rather than find a proper solution, I just stopped using Empathy. Not so much help as it is a form of surrender, but it did stop the problem...

Do you want to say it got fixed automatically later on?

---

### Post by fritz269 on 2013-02-24
I am having the same issue but instead, it brings up chrome, lets me log in and says success..but nothing happens. the account is not added.

---

### Post by prashant7526 on 2013-02-24
> **fritz269 said:**
> I am having the same issue but instead, it brings up chrome, lets me log in and says success..but nothing happens. the account is not added.

Is it happening from yesterday or from before ? Because [https://bugs.launchpad.net/signon-ui/+bug/1132296](https://bugs.launchpad.net/signon-ui/+bug/1132296) <- this also reported 18 hrs ago.

---

### Post by prashant7526 on 2013-02-24
Is it happening from yesterday or from before ? Because [https://bugs.launchpad.net/signon-ui/+bug/1132296](https://bugs.launchpad.net/signon-ui/+bug/1132296) <- this also reported 18 hrs ago.

---

### Post by anantinfosys on 2013-02-25
Another one that reports the same, though via gwibber reference.

[https://bugs.launchpad.net/ubuntu/+source/gwibber/+bug/1131263](https://bugs.launchpad.net/ubuntu/+source/gwibber/+bug/1131263)

This is indeed a showstopper.

Does anyone know of any other application/applet/screenlet/desklet/indicator that allows a user to see Facebook notifications right on the desktop without having to go to the website?

Or in case if a workaround has been found? 

A bug of this enormity can render Ubuntu 12.10 a dead meal if not fixed in an appropriate timeframe.

---

### Post by anantinfosys on 2013-02-25
It has been asked here as well, so can be followed for further updates on the issue.

[http://askubuntu.com/questions/259528/online-accounts-in-12-10-facebook-not-working](http://askubuntu.com/questions/259528/online-accounts-in-12-10-facebook-not-working)

---

### Post by anantinfosys on 2013-02-25
Basically, Facebook seems to have changed their authentication procedure very recently, and are redirecting to http instead of https (though this is invisible to the user), and Ubuntu developers do not support http in that module for security reasons. 

Either Facebook or Ubuntu developers will need to modify one line of code in either.

Darn, and the user is bugged till then.

---

### Post by prashant7526 on 2013-02-26
Is this prob. got resolved or have to live with this.... Waiting for an update anyone else also facing same?

---

### Post by anantinfosys on 2013-02-26
The problem has not been resolved as yet.

I am following the bug on launchpad, and a notification would pop up as soon as a workaround is found or a fix is released.

Its a very simple one to resolve for the Ubuntu developers, since they just need to add http to the allowed authentication schemes for Facebook webapp, which most of them would have done on their systems, but at the expense of system security, so they are not releasing the fix.

---

### Post by Wobbo on 2013-02-26
I have exactly the same problem. Indeed these problems really need to be fixed otherwise the bugs wil be a negative impression of Ubuntu.

---

### Post by anantinfosys on 2013-02-26
A Facebook developer says fix is ready and will be pushed out soon.
So lets be hopeful.

---

### Post by fritz269 on 2013-02-26
For now, I have been able to log in using Emesene. Make sure you log in using [email]username@chat.facebook.com[/email] for it to work. Not the best solution but a temporary fix

---

### Post by brockolicosmique on 2013-02-26
> **anantinfosys said:**
> A Facebook developer says fix is ready and will be pushed out soon.
So lets be hopeful.

I tried adding my Facebook account using Online Accounts again and this time the login info popped up in the settings window instead of launching a browser. It is now back to normal.

JF

---

### Post by fritz269 on 2013-02-26
Yes, I tried it after I read your post. It's working again. Nice...All my chat accounts are now on empathy

---

### Post by anantinfosys on 2013-02-26
Thanks guys for keeping us updated whilst it was night time our end of the world. 
Would wake up now and check in a jiffy.

Cheers to Ubuntu and its users!

---

### Post by anantinfosys on 2013-02-27
I am still not completely satisfied.

Facebook chat is now working properly using Empathy, and via Online accounts with the fix.

But I am still not seeing Facebook notifications on desktop (not the usual chat messages or the complete feed, but the notifications about likes, dislikes, comments on my posts).

Can anyone let me know how is that configured?

---

### Post by unheeding on 2013-02-27
> **anantinfosys said:**
> I am still not completely satisfied.

Facebook chat is now working properly using Empathy, and via Online accounts with the fix.

But I am still not seeing Facebook notifications on desktop (not the usual chat messages or the complete feed, but the notifications about likes, dislikes, comments on my posts).

Can anyone let me know how is that configured?


I think gwibber is the application that you need to set up.  It seems stuck on "refreshing" for me.   I'm not sure, since I don't use it.

---

### Post by anantinfosys on 2013-02-27
Gwibber is already set up my end.
But that is for browsing the entire feed.
And its quite buggy.

I am looking only for Facebook notifications right on the desktop.

---

### Post by wepai on 2013-02-27
hello, facebook works now, but I have a problem with my account live.fr

empathy can not connect to live.fr and it puts a message:
"no reason was given"

---

### Post by anantinfosys on 2013-02-27
> **wepai said:**
> hello, facebook works now, but I have a problem with my account live.fr

empathy can not connect to live.fr and it puts a message:
"no reason was given"

Start a new thread for your issue, before a moderator does it, since its not connected.

And in case you are sure its a bug, you can register a bug at launchpad.net, but do make it entirely sure its not a configuration issue at your end. So ask for a little help in a new thread before logging a bug.

---

### Post by prashant7526 on 2013-02-27
It's awsome, It started working.... the FACEBOOK wow!!!

---

### Post by stevebag on 2013-03-08
I resolved this problem by going to Facebook App settings and removing the Ubuntu app.  Then when I added the Facebook account via online accounts it reauthorized Ubuntu on Facebook and now it is working.

---

### Post by anantinfosys on 2013-03-09
> **stevebag said:**
> I resolved this problem by going to Facebook App settings and removing the Ubuntu app.  Then when I added the Facebook account via online accounts it reauthorized Ubuntu on Facebook and now it is working.

This issue was resolved by Facebook developers a week ago, and you do not need to remove the Ubuntu app from Facebook app settings any more. In case you still need to do that to be able to add Facebook to online accounts, please log a bug at launchpad.net.

---

