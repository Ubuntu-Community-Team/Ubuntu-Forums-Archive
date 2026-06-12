---
title: "Postfix outgoing email throttling"
date: 2014-07-25
forum: General Help
---

### Post by bzlom on 2014-07-25
Hello guys, 

we have a local Postfix server that uses Amazon SES (SMTP service) to deliver emails. I would like to limit the number of emails that are being sent on a per hour basis. 
The thing is I have the following configuration in /etc/postfix/main.cf and it doesn't work:
anvil_rate_time_unit = 1h      
smtpd_client_message_rate_limit = 2
smtpd_client_connection_rate_limit = 2

Above I wanted to send a maximum number of 2 emails per hour with a maximum of 2 maximum connections per client. 

I restarted postfix afterwards. No error/warnings logs in the /var/log/mail.log - Postfix continues to send emails without throttling anything. 

Does this method work - or should I try something like [FONT=Arial]postfwd or policyd?[/FONT]

---

### Post by lisati on 2014-07-25
It has been a while since I've run a postfix installation, but I believe that the parameters you mention are for *incoming* emails. The [default_destination_rate_delay]("http://www.postfix.org/postconf.5.html#default_destination_rate_delay")  parameter might not be quite what you want, but is a step in the right direction.

---

### Post by bzlom on 2014-07-25
Fair enough. I haven't specified that my Postfix server acts as a relay between a web application and Amazon SMTP service (SES). So even parameters for incoming emails would work here I presume - but they just don't work. That's what I'm trying to figure out - I have checked on different forums and apparently these solution should work but it doesn't for me. 
When I check the actual options with postconf I see that the values **[COLOR=#000000]anvil_rate_time_unit = 1h , [/COLOR][COLOR=#000000]smtpd_client_message_rate_limit = 2, [/COLOR]**[COLOR=#000000]**smtpd_client_connection_rate_limit = 2**[/COLOR] are being applied but don't have an effect.[COLOR=#000000][/COLOR]

---

### Post by SeijiSensei on 2014-07-25
In sendmail it's possible to tell the server to queue all outbound messages rather than delivering them immediately.  In this arrangement you run a cron job that processes the queue routinely, like one per hour.  I suspect Postfix has an equivalent configuration, but my knowledge of that program is a pretty limited.

---

### Post by lisati on 2014-07-25
> **bzlom said:**
> Fair enough. I haven't specified that my Postfix server acts as a relay between a web application and Amazon SMTP service (SES). So even parameters for incoming emails would work here I presume - but they just don't work. That's what I'm trying to figure out - I have checked on different forums and apparently these solution should work but it doesn't for me. 
When I check the actual options with postconf I see that the values **[COLOR=#000000]anvil_rate_time_unit = 1h , [/COLOR][COLOR=#000000]smtpd_client_message_rate_limit = 2, [/COLOR]**[COLOR=#000000]**smtpd_client_connection_rate_limit = 2**[/COLOR] are being applied but don't have an effect.[COLOR=#000000][/COLOR]

The parameters you have looked at are for when postfix is RECEIVING mail, not for when it is SENDING mail.

---

