---
title: "Changes in the way cron sends email between 18.04 and 20.04"
date: 2022-11-28
forum: General Help
---

### Post by erlingmoeller on 2022-11-28
Hi

We are using a docker container based on 18.04 to run cron jobs. It sends output of the jobs as email. However after upgrading our base image from 18.04 to 20.04 sending emails does not work anymore. Did sendmail command line interface change or did the way cron sends emails change?

We use a custom made email sender that drops in and replaces sendmail.

-Erling

---

### Post by ActionParsnip on 2022-11-28
What command are you using to send emails?
Can you check connection to the email server with:
```

timeout 5 bash -c "</dev/tcp/mailservername/25" && echo "connection success" || echo "connection failed"

```
Does it connect OK?

---

### Post by erlingmoeller on 2022-11-28
> **ActionParsnip said:**
> What command are you using to send emails?
Does it connect OK?
We use a custom made sendmail replacement that we put into /usr/sbin/sendmail
This works fine in ubuntu 18.04. We just get our programs help message in the logs leading me to think that the sendmail command changed flags between 1804 and 2004.

---

### Post by TheFu on 2022-11-28
> **erlingmoeller said:**
> We use a custom made sendmail replacement that we put into /usr/sbin/sendmail
This works fine in ubuntu 18.04. We just get our programs help message in the logs leading me to think that the sendmail command changed flags between 1804 and 2004.

Does the real sendmail work still?  If not, then perhaps you have a bug.  If so, then the bug is in the custom code.
I haven't used sendmail since the mid-1990s. We switched to postfix and never looked back.  postfix has a sendmail compatible interface and it definitely works without any changes on every Ubuntu Server LTS from 10.04 through 22.04.  All my systems provide system summary reports daily via cron emails.

---

### Post by erlingmoeller on 2022-11-30
The bugs was in our custom code, cron had changed the order of command line flags to the sendmail command. Which is fine for sendmail, but not to our custom code.

---

### Post by TheFu on 2022-11-30
> **erlingmoeller said:**
> The bugs was in our custom code, cron had changed the order of command line flags to the sendmail command. Which is fine for sendmail, but not to our custom code.

Please use the "Thread Tools" link at the top of the page and mark this thread as SOLVED to help the community out and save time for everyone else.

---

