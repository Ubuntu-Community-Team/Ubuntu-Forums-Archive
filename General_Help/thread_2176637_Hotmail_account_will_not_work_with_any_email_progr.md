---
title: "Hotmail account will not work with any email program"
date: 2013-09-25
forum: General Help
---

### Post by adam17 on 2013-09-25
Hi,

I am very new to Ubuntu but am loving it so far. I have however run into problems using Evolution mail & Thunderbird. 

No matter what pop or smtp servers I try I get the same response could not connect to pop3.live.com ect Connection refused.

This is driving me crazy! I have set my windows live account to enable pop access and allow pop apps, but still no progress. I have even used the server address listed on the live.com website with no luck.

Is there something I am missing? Does anyone else have a similar problem?

Thanks in advance.

Adam

---

### Post by Isamu715 on 2013-09-25
Is your password longer than 16 characters? If so, try changing it to something 16 characters or less.

---

### Post by Azdour on 2013-09-25
You might also want to double check that Evolution or Thunderbird is using the correct port numbers and security:

[http://answers.microsoft.com/en-us/windowslive/forum/mail-sync/are-there-pop3-settings-for-outlookcom/8515bbdb-14bd-487b-86c1-bea3edf6a24f](http://answers.microsoft.com/en-us/windowslive/forum/mail-sync/are-there-pop3-settings-for-outlookcom/8515bbdb-14bd-487b-86c1-bea3edf6a24f)

---

### Post by adam17 on 2013-09-26
Password is 8 characters long with a mix of upper and lower case letters, I have used the suggested ports on the Hotmail web page & the settings in Azdour's link.

Thank you for the responses but still no luck with it working.

---

### Post by adam17 on 2013-09-26
Also on another note, Evolution has not asked me for my mail password?! This could be causing the problem. I am using Evolution 3.2.3 on Ubuntu 12.04 LTS I haven't seen any box to enter a password in the setup ( I assumed it would ask when sending and receiving)

---

### Post by Topsiho on 2013-09-26
Maybe you do not use the correct user name for the connection.

It's already quite a while ago that I struggled with this same problem, even when I still used Windows (and that is a very long time ago), and it is not connected to what operating system you use, or what mail client.
Problem is that some providers use the part before the @ as user name, and other providers the full email address. And maybe there are other strategies they use.

You may try this, see the documentation of your providers, or see what you use in Windows, if you still use Windows.

Topsiho

---

### Post by adam17 on 2013-09-26
Have tried using without the full email address and username but still the same :( I have also tried in Thunderbird to get my hotmail mail but with the same results. I also installed Thunderbird in Windows and had the same outcome. This feels like it may be an issue with the pop server at hotmail / microsoft perhaps.

---

### Post by dcstar on 2013-09-26
> **Azdour said:**
> You might also want to double check that Evolution or Thunderbird is using the correct port numbers and security:

[http://answers.microsoft.com/en-us/windowslive/forum/mail-sync/are-there-pop3-settings-for-outlookcom/8515bbdb-14bd-487b-86c1-bea3edf6a24f](http://answers.microsoft.com/en-us/windowslive/forum/mail-sync/are-there-pop3-settings-for-outlookcom/8515bbdb-14bd-487b-86c1-bea3edf6a24f)

Exactly, you must use SSL and port 995 to access the mail server.

If you are not following these instructions **exactly** then you are wasting everybody's time.

---

### Post by adam17 on 2013-09-26
I have input all of these settings exactly into both Thunderbird and Evolution. Thunderbird just hangs on connecting to pop3.live.com Evolution says connection refused.

---

### Post by Azdour on 2013-09-26
Have you set up a firewall to block all ports on your computer except ones you specifically open?

When you set up the pop3 account in Thunderbird, when it asked for your password did you ask it to save it?  Could it be that you entered in the password wrong - now no matter what settings you use it is using the wrong password?

If you think it is the wrong password: go to Edit | Preferences - click on Security and then on the Passwords tab.  Now click on the Saved Password and remove the ones associated with your hotmail account and try again to connect.  It should ask for your password again.

Failing that could you take a screenshot of the pop3 account settings in Thunderbird and post them here to see if we can spot anything?

---

### Post by Topsiho on 2013-09-26
Hi,

I can't log in into my Hotmail account, as I forgot my password for it aeons ago.
However, in my evolution email client I use port 110, and for SSL I (have to, my provider is not top class, Thunderbird says I have to speak to them :) ) use: No security.
I never had (so far) to alter these from email account to email account, but who knows :(

You are NOT wasting my time ....

Topsiho

---

### Post by Topsiho on 2013-09-26
I can kick myself, but as far as I know the title of your thread states this well: your hotmail account does not work with any email program :)

You have to access Hotmail from your ==> browser <== client, such as Firefox.

I (almost) never use WEBmail, such as Gmail and Hotmail, so I was not sharp enough to give you a correct reply earlier, sorry for that ...

Topsiho

---

### Post by adam17 on 2013-09-26
Cracked it! 

Thank you everyone for all your suggestions. It looks like it was blocked ports on my network. I was trying to access my mail on my work network and I suspect that the ports are blocked as it seems to work at home.

Thanks

---

### Post by Azdour on 2013-09-26
Excellent,  glad you found a solution.  Any chance you can now mark this thread as solved? Top right under Thread Tools.

---

### Post by adam17 on 2013-10-02
Hi, 

Thanks for all the responses to the above, I have managed to solve the mystery. The problem was I was attempting to access my mail on my work network and it seems that they have blocked these ports. Working from home I am now able to send and Receive emails. The only way to send and receive emails on my work network would be to enable Thunderbird to access a http mail server. Does anyonw know if there is a pluggin for this or if it is possible? 

Thanks

---

### Post by Isamu715 on 2013-10-02
I suggest you mark this thread as solved and start a new one with that questions as it's no longer related to the thread subject.

---

### Post by adam17 on 2013-10-03
Ok, will do  thanks.

---

