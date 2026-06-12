---
title: "Postfix Problem Emailing Myself (mutt)"
date: 2007-04-20
forum: General Help
---

### Post by DonnieP on 2007-04-20
I installed mutt which depends on postfix in Synaptic.  While I doubt I really need postfix (just to send smtp) I installed it since that's how Ubuntu packaged mutt.  All works fine except when I try to email myself.  I've set things up to use my mac.com email account and sending email to anyone but myself works fine.  And I can successfully email myself at the mac.com address using other clients.

---

### Post by DonnieP on 2007-04-26
I finally figured this out after much googling and mashing of postfix's main.cf.  In short, I had to set up smtp.mac.com as relayhost and also in the transport file.  This article is particularly helpful:

[http://souptonuts.sourceforge.net/postfix_tutorial.html]("http://souptonuts.sourceforge.net/postfix_tutorial.html")

---

### Post by andrew.46 on 2007-07-02
Hi.

 I dodged around postfix in my own setup:

[http://people.aapt.net.au/~adjlstrong/mutt.html](http://people.aapt.net.au/~adjlstrong/mutt.html)

              Andrew

---

### Post by DonnieP on 2007-07-02
Andrew's guide is excellent.  I agree with him about the simplicity of avoiding postfix, however I will say - now that I understand the concept - that postfix is really not that hard.  And I have had several occasions to appreciate the log file you get with postfix.  As Andrew says about ssmtp, "The only annoyance with this program is that it will not create a logfile which would useful during testing but this shortcoming does not tempt me to try Exim or Postfix."

In my own setup I didn't bother with fetchmail because my mail is imap and I access it from several different commputers and my iPhone.  Actually I don't see much point in using fetchmail with mutt *unless* you're going to do local spam filtering.

---

### Post by andrew.46 on 2007-07-05
Hi,

 I read your post with great interest:

> **DonnieP said:**
> In my own setup I didn't bother with fetchmail because my mail is imap and I access it from several different commputers and my iPhone.  Actually I don't see much point in using fetchmail with mutt *unless* you're going to do local spam filtering.

BTW thanks for the compliments on my setup guide! I am a little jealous that you can use IMAP, it sounds like a very satisfying way to read your mail! Plus if you compiled your own copy you could enable header-caching, not sure if the repository version enables this or not.

            Andrew

 PS Strictly speaking Fetchmail does not *filter*, a program such as Procmail would normally do that.

---

### Post by DonnieP on 2007-07-05
The repository version does have header caching compiled in.

---

