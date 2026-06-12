---
title: "Notification on Phone"
date: 2022-09-13
forum: General Help
---

### Post by meetdilip on 2022-09-13
I use a custom Python script in 22.04 to get notifications for low battery and battery full. Wondering what is the best way to get the notification on my Android mobile phone. The first idea that occurred to me was to make Thunderbird send an email to a set email ID along with the status notification display. Would be nice to know if there are any better, reliable methods to achieve this task. Thanks.

Normally, both the smart phone and laptop are under the same WiFi network.

---

### Post by kostkon on 2022-09-13
There's [Gotify]("https://gotify.net/"), or even [Apprise]("https://github.com/caronc/apprise"), which supports *almost all of the most popular notification services* (sic.)

---

### Post by TheFu on 2022-09-13
You could post a private notification to one of your social media accounts ... or setup a new 'bot' account just for this purpose.
I think that's the way the kids would do it today.

What I do is send an email.  I'm old and use email for communications.  My phone will see the email and "bing" with the notification, unless I'm away from a network. All my Linux systems can send emails anywhere ... eventually.  Most only send to my internal email server, since many notifications contain sensitive information that I'd never send to an external email account.

---

### Post by meetdilip on 2022-09-17
Thanks for the replies. Is there anything that already exists that I can use?

I see that in 22.04, Upower can be used to send low and full battery notifications

[https://askubuntu.com/questions/1411483/battery-full-indicator-22-04](https://askubuntu.com/questions/1411483/battery-full-indicator-22-04)

Is there any simple method to use this? 

I am no expert. Any help would be great.

Edit 1:

Or is it as simple as installing Notify on 22.04 and corresponding Android app on the phone?

---

### Post by meetdilip on 2022-09-17
Gotify Web UI is successfully running on my laptop and I have installed the Android app.

But when I type the WebUI address with the port no in Android app to CHECK URL, it says

Request to 'http://127.0.0.1:85 /version' failed with status code 0

Not sure how to link the low battery and full battery notifications to it.

---

### Post by meetdilip on 2022-09-17
I used this command with proper token and message and received a desktop notification. 

Now my attempt is to make battery notifications linked to Gotify and have them delivered on my Android phone with Gotify app

curl "https://push.example.de/message?token=<apptoken>" -F "title=my title" -F "message=my message" -F "priority=5"

---

### Post by meetdilip on 2022-09-17
Worked on it a bit and now I am able to successfully send battery notifications that are registered in the Gotify WebUI. Notifications are displayed on PC through Gotify but it is still not reaching the Android app.

---

### Post by meetdilip on 2022-09-17
Working great now. I used the internal IP instead of the 127.0.0.1:85

Thanks :)

---

