---
title: "Evolution options"
date: 2007-10-24
forum: General Help
---

### Post by etherael on 2007-10-24
Hi All,

I'm just testing ubuntu right now side by side with a bunch of windows boxes side by side, long story short, I'm sold on the actual product, it's excellent, I have a few things that I absolutely need however before I can properly switch, and I can see short term and mid term solutions to the problems raised, any assistance or advice from anyone here on any of these things would be of great help.

Firstly, I use an exchange server package from mail2web.com, I've tried setting it up via the exchange connector in evolution however this fails to work correctly, the login phase never succeeds. I notice it says "Enter password for account" rather than "Enter password for [email]account@domain.com[/email]" So I'm not sure if it's omitting the @domain.com part from the username it tries to use to login to OWA, which would explain the authentication errors, as mail2web's exchange server setup *requires* you to login with your full email address.

 I have managed to get IMAP/SMTP access to this service so I can send and receive mail, but that leaves me without my tasks, contacts, and all items in the calendar that would otherwise be available using an exchange connection, I have however noticed that all those folders are available under the IMAP server I've configured in evolution, so is it actually possible to somehow incorporate that information into evolution using IMAP rather than the OWA protocol?

That would pretty much do it for the short term, over the longer term however I'd like to move off exchange and replace it with something linux based, I heard not long ago of a package, the name of which I cannot at the moment recall which ran serverside on linux and provided all the traditional functionality of outlook to linux clients running evolution as well as had a very slick and impressive AJAX based web interface that left owa in the dust, has anyone any real world experience with this product, and can anyone refresh my memory on the name?

Last but not least, the reason I even have an exchange server at the end of the day is just the functionality above, which I can see a way to duplicating using an entirely linux based solution, as well as push email using activesync on my HTC Hermes, which I'm not sure if it would be possible to dupe the functionality of using a server/desktop linux setup with some method of connecting my windows mobile 6 phone to a linux service somewhere for push email and contacts / tasks / calendar synchronisation. Another alternative that springs to mind is perhaps installing a handheld variant of linux on the HTC hermes, however it's been many years since I've tinkered with handheld linux and I don't know what's available in this sphere.

Thanks in advance for any available assistance.

Regards
Eric

---

### Post by lazyart on 2007-10-24
> **etherael said:**
> That would pretty much do it for the short term, over the longer term however I'd like to move off exchange and replace it with something linux based, I heard not long ago of a package, the name of which I cannot at the moment recall which ran serverside on linux and provided all the traditional functionality of outlook to linux clients running evolution as well as had a very slick and impressive AJAX based web interface that left owa in the dust, has anyone any real world experience with this product, and can anyone refresh my memory on the name?

Last but not least, the reason I even have an exchange server at the end of the day is just the functionality above, which I can see a way to duplicating using an entirely linux based solution, as well as push email using activesync on my HTC Hermes, which I'm not sure if it would be possible to dupe the functionality of using a server/desktop linux setup with some method of connecting my windows mobile 6 phone to a linux service somewhere for push email and contacts / tasks / calendar synchronisation. Another alternative that springs to mind is perhaps installing a handheld variant of linux on the HTC hermes, however it's been many years since I've tinkered with handheld linux and I don't know what's available in this sphere.

I think the package you are thinking of is Zimbra.  There is also eGroupwise, but Zimbra is pretty slick.  I'd like to set it up for myself one day.

---

### Post by etherael on 2007-10-24
> **lazyart said:**
> I think the package you are thinking of is Zimbra.  There is also eGroupwise, but Zimbra is pretty slick.  I'd like to set it up for myself one day.

Thanks, yep, that's the one, I might tinker with it today.

---

### Post by dfmalh on 2007-10-29
Hi, I have a little different question and it is regarding the SMTP setting in Evolution. At the moment I am using Thunderbird because I can's find this particular setting or option in Evolution.

First I did the setup of all my my email accounts in TB, that is an Exchange, POP and Gmail account. I have no problems sending and receiving anything. :-) 

I am using 3 different SMTP servers, one at a time, at different times :-) In TB it is not difficult to switch between them... Edit, Account Settings... At the bottom of your Default Identity you can choose any of your setup Outgoing servers (SMTP). Just click on the down arrow and a drop-down box appears with your choices... select the relevant one and send/receive your mail on all your accounts.

I it possible to do the same in Evolution? Thus far I have to remember and change every UN and PW + all the SMTP server details each time I want to use a different SMTP server for all the different accounts.

Thanks

---

### Post by Ignat on 2007-12-15
I can confirm the same problem with trying to get evolution to communicate with the exchange server at mail2web. It seems not to send the full account name in the setup dialogue. 

I then tried accessing my exchange account using thunderbird and imap. It does give me access to all my folders, including my contacts and notes. It treats notes as e-mail messages, but it does display the contents. It doesn't do quite as well with contacts.  Also, I haven't been able to get it to update folders other than the inbox. I have outlook running lots of rules filtering messages to different folders. The thunderbird/imap solution seems not to query the individual folders for changes in their contents. 

But this is still much better than the Outlook Web Access!

---

### Post by ellgor on 2007-12-16
Hi,

Try the following progs, they are much better than Evolution, Kmail-Kontact-Korganiser, all available in the repos.
They are listed as seperate packages but once installed operate as one unit keeping everything in one tidy package, hope this helps.

Regards, Ellgor.

---

### Post by cristiantm on 2007-12-22
I worked last night on making Evolution Sync with mail2web Live service work, and wrote an article explaing the workaround/hack nedded for it... 

[http://cristiantm.wordpress.com/2007/12/22/sync-wm5-wm6-with-evolution-without-activesync/](http://cristiantm.wordpress.com/2007/12/22/sync-wm5-wm6-with-evolution-without-activesync/)

---

### Post by varaonaid on 2008-01-03
> **cristiantm said:**
> I worked last night on making Evolution Sync with mail2web Live service work, and wrote an article explaing the workaround/hack nedded for it... 

[http://cristiantm.wordpress.com/2007/12/22/sync-wm5-wm6-with-evolution-without-activesync/](http://cristiantm.wordpress.com/2007/12/22/sync-wm5-wm6-with-evolution-without-activesync/)

Thank you SOOOOO much for the work figuring out the Evolution hack and for posting it!  It worked perfectly.  It's the solution I've been looking for!

---

