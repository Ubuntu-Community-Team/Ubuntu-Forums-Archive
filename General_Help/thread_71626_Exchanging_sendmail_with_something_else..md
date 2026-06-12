---
title: "Exchanging sendmail with something else."
date: 2005-10-03
forum: General Help
---

### Post by Juzz on 2005-10-03
Hi,
This is not excactly related to ubuntu, but I have a question regarding my main server at home.
It is running SuSE (from waaay back before Ubuntu appeared) and it is running sendmail...
Is it possible for me to exchange sendmail with another MTA without loosing the mails on the accounts on my server?
I would really like to implement antivirus scanning on the mails, but with amavis and Norman sendmail locks up - I think that it is because sendmail is running as root with the need for root permissions on the mailqueue dirs - but amavis is run as vscan without root permissions.
Will a change of MTA solve this - or can I solve it by getting the system to run sendmail as another user instead of root?
I have tried browsing the settings in Yast, but it doesn't mention anything about running sendmail as a specific user (though for other services you can setup the user to runas in Yast).
Hope some of you bright ppl can help :cool: 
Cheers
Juzz

---

