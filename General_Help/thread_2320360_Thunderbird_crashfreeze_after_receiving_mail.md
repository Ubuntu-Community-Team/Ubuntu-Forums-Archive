---
title: "Thunderbird crash/freeze after receiving mail"
date: 2016-04-13
forum: General Help
---

### Post by terratronix on 2016-04-13
Hey guys,


so i set up Thunderbird with my Gmail accounts and everything worked perfectly fine.
I went ahead and added my university-email account which is pop3. I set everything up according to our sys-admins guide. I received mail and then Thunderbird froze.
I had to 'force quit' I then deleted my profile and reinstalled thunderbird. Set up only uni-mail this time and it worked. I could read all my mail with no problems.
A day later i log in and thunderbird asks me if i want to change the mail servers inbox address. It seemed right and i confirmed. TB froze again. Today i reinstalled everything again. Reset profile etc.
I made really sure the settings are correct. It still freezes. I have no clue what causes the problem. It always freezes at the same time. Works for a few seconds then freezes. Restart. The same.
All my other applications run perfectly fine, no lag, nothing. I am running 14.04 LTS and TB 38.6.0.
On windows i had the same mail accounts set up and it always worked. 
If i can supply any further information / crash reports or something, i'm glad to provide them. 
I'm not used to things not working on ubuntu so please be kind :)

Thanks in advance

---

### Post by amanchesterman on 2016-04-13
I assume you installed Thunderbird from the Software Centre, or are using the version that came pre-installed with Ubuntu?
The most common cause of Thunderbird freezing / hanging is probably antivirus scanning, but I assume you don't have that.
Another cause to look for is a misbehaving add-on. Try running Thunderbird for a day or so with all add-ons disabled.
You might also want to post in the Thunderbird support forum [https://support.mozilla.org/en-US/questions](https://support.mozilla.org/en-US/questions)
The answers in that forum sometimes touch on similar issues to yours.

---

### Post by terratronix on 2016-04-13
I will certainly try what you suggested. I will also post in Mozillas Help Forums.
Thanks for your suggestions.

I do have ClamAV installed but it isn't running according to top.
At first i used the preinstalled Thunderbird. Now i use the one from the ubuntu main repositories.

Thanks again. Have a nice day.

---

### Post by j8a on 2016-05-06
I have experienced the same problen on Xubuntu 14.04, thunderbird also remains running in the background. The only solution was to execute ps -ax | grep thunderbird to find the process and kill it from the command line before I restart thunderbird. I have no antivirus running.

---

