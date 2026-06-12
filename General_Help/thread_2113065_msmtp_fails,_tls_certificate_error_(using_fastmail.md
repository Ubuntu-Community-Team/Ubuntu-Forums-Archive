---
title: "msmtp fails, tls certificate error (using fastmail)"
date: 2013-02-06
forum: General Help
---

### Post by DiogenesNJ on 2013-02-06
Hi, all.

I run a homebrew mailing list for the board game of Go, using a bunch of Python scripts driving the "mail" system command.

The environment is old Ubuntu -- 8.04 LTS.  I use msmtp as the mailing program.

In September 2012, everything worked. Now I get the error "certificate hasn't got a known issuer."

Here are the relevant lines from the .msmtprc file:

 tls on
tls_trust_file /usr/share/ca-certificates/mozilla/DigiCertHighAssuranceCA-3.crt
tls_starttls off]

This is the correct file, according to the fastmail documentation.

Has anyone else seen this?  Can anyone tell me how to obtain/install the correct root and user certificates, or point me to an FM to R?

Thanks in advance.  Sorry for the repeat posting, if this is one; I tried before and couldn't fing the post, so I'm trying again.

---

