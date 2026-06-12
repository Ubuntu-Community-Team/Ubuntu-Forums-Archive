---
title: "Postfix &amp; Greylisting"
date: 2007-11-30
forum: General Help
---

### Post by pot_roast on 2007-11-30
See the log section here:

Nov 30 19:34:43 heap postfix/smtpd[27141]: NOQUEUE: reject: RCPT from unknown[201.240.117.167]: 450 4.7.1 <7080105@pbp.net>: Recipient address rejected: Greylisted for 18 seconds (see [http://isg.ee.ethz.ch/tools/postgrey/help/pbp.net.html);](http://isg.ee.ethz.ch/tools/postgrey/help/pbp.net.html);) from=<illegalsn246@woodwisedesign.com> to=<7080105@pbp.net> proto=ESMTP helo=<client-201.240.117.167.speedy.net.pe>
Nov 30 19:34:43 heap postfix/smtpd[27141]: NOQUEUE: reject: RCPT from unknown[201.240.117.167]: 450 4.7.1 <7040801@pbp.net>: Recipient address rejected: Greylisted for 18 seconds (see [http://isg.ee.ethz.ch/tools/postgrey/help/pbp.net.html);](http://isg.ee.ethz.ch/tools/postgrey/help/pbp.net.html);) from=<illegalsn246@woodwisedesign.com> to=<7040801@pbp.net> proto=ESMTP helo=<client-201.240.117.167.speedy.net.pe>
Nov 30 19:34:43 heap postfix/smtpd[27141]: NOQUEUE: reject: RCPT from unknown[201.240.117.167]: 450 4.7.1 <7040901@pbp.net>: Recipient address rejected: Greylisted for 18 seconds (see [http://isg.ee.ethz.ch/tools/postgrey/help/pbp.net.html);](http://isg.ee.ethz.ch/tools/postgrey/help/pbp.net.html);) from=<illegalsn246@woodwisedesign.com> to=<7040901@pbp.net> proto=ESMTP helo=<client-201.240.117.167.speedy.net.pe>

--
Postfix is greylisting things for addresses that do not exist on my system. This is the first box that I've used greylisting on. With the previous server, I had Postfix to use a relay_recipient_maps file and that file contained a list of valid email addresses. Anything else was rejected.

While postfix is still rejecting the addresses that are invalid, Postgrey is also getting involved. I'd like to have Postfix just reject the invalid addresses right off the bat before Postgrey gets involved.

In main.cf:
relay_recipient_maps = hash:/etc/postfix/valid_emails

smtpd_recipient_restrictions = 
	reject_unauth_pipelining, 
	permit_mynetworks, 		
	permit_sasl_authenticated, 
	reject_non_fqdn_recipient,
	reject_unauth_destination, 
	check_policy_service inet:127.0.0.1:60000,
	check_recipient_access hash:/etc/postfix/recipient_checks,
   	check_sender_access hash:/etc/postfix/sender_access,
   	check_client_access hash:/etc/postfix/banned_servers,
	permit

--

I really don't want to sign up for the Postfix-users mailing list just to ask one question, and I have already searched Google for this issue to no avail.

---

### Post by HermanAB on 2007-11-30
Move the policy server thing down so it is below the blacklist things.

Cheers,

Herman

---

### Post by HermanAB on 2007-11-30
BTW, you should appreciate that I didn't tell you to use Citadel instead of Postfix.  So don't look at this link: [http://www.citadel.org](http://www.citadel.org)

and then I won't remind you that Citadel can install in about 20 minutes using their Easy Install script either...
;)

---

### Post by pot_roast on 2007-11-30
> **HermanAB said:**
> BTW, you should appreciate that I didn't tell you to use Citadel instead of Postfix.  So don't look at this link: [http://www.citadel.org](http://www.citadel.org)

and then I won't remind you that Citadel can install in about 20 minutes using their Easy Install script either...
;)

Good, because "X sucks, use Y" types of answers don't help anybody at all. :-)

Also, the valid_emails check is above the postgrey entries in main.cf, so moving them isn't going to do anything.

---

