---
title: "evolution vs thunderbird"
date: 2008-04-03
forum: General Help
---

### Post by curtk69 on 2008-04-03
hi there
i usually use thunderbird cuz it works and it seems simple to use but i recently discovered evolution with my new gutsy install.

evolution seems to have alot of extra features that i like.
so i would like to keep using it BUT  it keeps giving error windows saying it  had problems /errors fetching mail..
this happens quite frequently but every time i test the system by sending an email from another source it works and so does out going mail. 

SO WHATS THE PROBLEM?

 i have went thru all the setting 3 times looking for anything to change but it all seems good

---

### Post by sekinto on 2008-04-03
What e-mail service do you use (Gmail, Hotmail, et cetera)?

---

### Post by curtk69 on 2008-04-03
i use the  provincial gov sasktel.net adress i was given

---

### Post by nick_h on 2008-04-04
> i would like to keep using it BUT it keeps giving error windows saying it had problems /errors fetching mail..
What exactly do the error messages say?

---

### Post by curtk69 on 2008-04-05
/errors fetching mail

something about erro fetching mail.

hasnt happened in last 2 days so i cant remember exactly

---

### Post by nick_h on 2008-04-05
I suggest you type the error message into Google or launchpad.  I did a quick search and found [bug #27014](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/27014).  Without the exact error message it is hard to search.

---

### Post by curtk69 on 2008-04-06
heres the two errors i see right now after having left my evolution open all day.

Evolution Error
Error while fetching mail
unable to connect to pop server mail.sasktel.net
error sending password; connection reset by peer 
                                                                  OK



ENETER PASSWORD FOR [email]curtk@sasktel.net[/email]
 
unable to connect to pop server mail.sasktel.net
error sending password; err[sys/temp] service
temporarily unavailable

please eneter the pop password for curtk on host
mail.sasktel.net

password box here

 check; remember this password

                                           CANCEL     OK





thats what the 2 error windows look like
any ideas?

---

### Post by nick_h on 2008-04-06
Have a look at [this](http://tools.ietf.org/html/draft-gellens-pop-err-01) link.  It describes POP error codes.  In particular read section 5:
> SYS/TEMP indicates a problem which is likely to be temporary in
nature, and therefore there is no need to alarm the user, unless the
failure persists.  Examples might include a central resource which
is currently locked or otherwise temporarily unavailable,
insufficient free disk or memory, etc.
Have you checked disk space and memory?

---

### Post by curtk69 on 2008-04-07
heres another error i just got after using it 15 min ago and leaving evolution open

evolution erro
Error while fetching mail
host hookup failed; mail.sasktel.net; name or service not known
OK

---

### Post by curtk69 on 2008-04-07
I Have A Gig  Of Memory And 500 Gigs Of Space

---

### Post by curtk69 on 2008-04-07
I Checked That Link And Found No Help

---

### Post by Boyohazard on 2008-04-07
Sounds to me like a problem with your mail provider. Have you got the same account setup in Thunderbird? Any problems with that?

---

### Post by curtk69 on 2008-04-07
yes i can use thunderbird flawlessly with this same account

---

### Post by nick_h on 2008-04-07
> Error while fetching mail
host hookup failed; mail.sasktel.net; name or service not known
A similar question was asked [here](https://answers.launchpad.net/ubuntu/+source/evolution/+question/7328).

As Boyohazard suggested, it seems likely to be a problem with your mail provider.

---

