---
title: "Request forTips on enrolling Google Titan security key in Ubuntu 20.04 desktop and Go"
date: 2023-05-17
forum: General Help
---

### Post by dragonfly41 on 2023-05-17
I have Dell desktop, Ubuntu 20.04.  Adding Google Titan security key.

Because cloud accounts now insist on 2FA (my test case is Heroku) I am in a position where I have a paid account with Heroku but I cannot enroll a Google Titan key which I recently purchased. So I am stuck.  I cannot sign into in Heroku support with my shiny new Titan security key.

I'm hoping that a Ubuntu user with Google Titan Key in use for 2FA can spot where I am going wrong in my security key enrollment workflow.

I purchased Google Titan security keyUSB-A/NFC security key. I chose USB A because I only have A and B ports.

I can plug into a USB port hub.

=======================================

I had to dig deeper to find that I had to register key in Google account, Security.

[https://www.howtogeek.com/365045/how-to-set-up-and-use-the-google-titan-key-bundle/](https://www.howtogeek.com/365045/how-to-set-up-and-use-the-google-titan-key-bundle/)


Found the answer here. Added security key to Google account. Then security key recognised by Heroku.


[https://myaccount.google.com/security](https://myaccount.google.com/security)

A bit confusing, since the reference to Bluetooth but I used direct port connection.

---

