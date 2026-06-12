---
title: "Recommendation for free SMS communication"
date: 2015-01-05
forum: General Help
---

### Post by Cool_Javelin on 2015-01-05
I have a requirement to send and receive, for free, SMS messages (not IM or email.)

I plan to send no more then 10 a day, and receive, maybe 2 a day.

I can't attach a cell phone to my computer, I have no cell service, so this needs to be totally on the internet.

Also, I am running a text based Ubuntu server, no GUI.

I would be OK with installing a small package on my server, but I think I would prefer a script based method of sending URL's to send and receive SMS's.

Thanks for your help.
Mark.

---

### Post by sandyd on 2015-01-05
> **Cool_Javelin said:**
> I have a requirement to send and receive, for free, SMS messages (not IM or email.)

I plan to send no more then 10 a day, and receive, maybe 2 a day.

I can't attach a cell phone to my computer, I have no cell service, so this needs to be totally on the internet.

Also, I am running a text based Ubuntu server, no GUI.

I would be OK with installing a small package on my server, but I think I would prefer a script based method of sending URL's to send and receive SMS's.

Thanks for your help.
Mark.
See if you are willing to comply with Twilio's trial restrictions -> [http://www.twilio.com/help/faq/twilio-basics/how-does-twilios-free-trial-work](http://www.twilio.com/help/faq/twilio-basics/how-does-twilios-free-trial-work)

Otherwise, if your willing to pay $1/mo + ~1c for each SMS, there are a few VOIP providers around that support SMS. Most of the time, received SMSes are forwarded to email, and you can send/receive from the provider's portal. Twilio allows you to create a custom handler that can support many things, including sending the messages to email.

---

### Post by Cool_Javelin on 2015-01-08
Thanks, Sandyd:

I am testing out twillo now, I think I can live with the trial policy. I am writing my own custom scripts, and might be able to deal with the extra verbiage.

I still haven't figured out how to receive an SMS on my Ubuntu 12.04 using the CLI.

Unfortunately, this is a lower priority in my life, so tests and responses to this post may take several days between updates.

Thanks. Mark.

---

### Post by dragonfly41 on 2015-01-08
Here is another (not free) service ... including API scripts to try ...

[http://www.textlocal.com/](http://www.textlocal.com/)

[http://www.textlocal.com/simple-developer-sms-api](http://www.textlocal.com/simple-developer-sms-api)

[http://api.txtlocal.com/docs/inboundmessages/getinboxes](http://api.txtlocal.com/docs/inboundmessages/getinboxes)

[http://www.textlocal.com/receiving-text-messages-online](http://www.textlocal.com/receiving-text-messages-online)

---

