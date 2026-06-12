---
title: "[Solved] SSMTP connecting to Gmail"
date: 2016-04-01
forum: General Help
---

### Post by stormthirst on 2016-04-01
Until a short while ago (not quite sure when), SSMTP was sending the results of my cron jobs to my email. 

Here's my ssmtp.conf file:
```

#
# Config file for sSMTP sendmail
#
# The person who gets all mail for userids < 1000
# Make this empty to disable rewriting.
root=<MYEMAIL>@gmail.com

# The place where the mail goes. The actual machine name is required no
# MX records are consulted. Commonly mailhosts are named mail.domain.com
mailhub=smtp.gmail.com:587

# Where will the mail seem to come from?
#rewriteDomain=

# The full hostname
hostname=<MYEMAIL>@gmail.com

# Are users allowed to set their own From: address?
# YES - Allow the user to specify their own From: address
# NO - Use the system generated From: address
FromLineOverride=YES

UseSTARTTLS=YES
UseTLS=YES
AuthUser=<MYEMAIL ADDRESS>@gmail.com
AuthPass=<MYPASSWORD>

```

Various Google searches have yielded a few results which imply I need to add a TLS_CA_File= line, but they all reference a RedHat installation and need to add:
TLS_CA_File=/etc/pki/tls/certs/ca-bundle.crt

The only file with the same name is: /usr/share/ncat/ca-bundle.crt

My syslog says this:

```

Apr  1 22:25:20 MYHOST sSMTP[31704]: Unable to set TLS_CA_File="/usr/share/ncat/ca-bundle.crt"
Apr  1 22:25:23 MYHOST sSMTP[31704]: Creating SSL connection to host
Apr  1 22:25:23 MYHOST sSMTP[31704]: Invalid response: 501 5.5.4 HELO/EHLO argument MYEMAIL@gmail.com invalid, closing connection. g2sm376695igi.2 - gsmtp (MYEMAIL@gmail.com)
Apr  1 22:25:23 MYHOST sSMTP[31704]: SSL connection using (null)
Apr  1 22:25:23 MYHOST sSMTP[31704]: Cannot open smtp.gmail.com:587

```

I get the feeling the TLS_CA_File is where the problem is.

Has anyone else managed to get sSMTP working with Gmail? Is there an alternative to SSMTP?

---

### Post by pjrettin on 2016-04-02
I had a similar issue happen to me the past week or so - it just stopped working.

I fixed it by changing my hostname: to the following in the ssmtp.conf:

hostname=localhost

Before it was hostname:emailaddress@gmail.com

---

### Post by stormthirst on 2016-04-03
Thank you! That fixed it.

---

### Post by Argard on 2016-04-03
This fixed my problem too!
Thanks!

---

### Post by Rhys_Davies on 2016-04-15
me too. stopped working end of march. this fixed it.

---

### Post by mark103 on 2016-05-02
Thank you so much for that. I couldn't for the life of me figure out what was going wrong as my email worked before, you saved me a lot of time thanks again


> **pjrettin said:**
> I had a similar issue happen to me the past week or so - it just stopped working.

I fixed it by changing my hostname: to the following in the ssmtp.conf:

hostname=localhost

Before it was hostname:emailaddress@gmail.com

---

### Post by jaydickey on 2016-06-30
This also solved my problem.

Many thanks!

---

### Post by mayslane on 2016-07-14
Thanks solved my problem

---

### Post by rcss on 2017-02-19
> **pjrettin said:**
> I had a similar issue happen to me the past week or so - it just stopped working.

I fixed it by changing my hostname: to the following in the ssmtp.conf:

hostname=localhost

Before it was hostname:emailaddress@gmail.com

Worked
for me as well.  Have had this issue for over a year and knew not how to resolve it.  Thanks for your help.

---

