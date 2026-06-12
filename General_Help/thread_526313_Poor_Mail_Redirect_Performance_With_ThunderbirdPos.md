---
title: "Poor Mail Redirect Performance With Thunderbird/Postfix"
date: 2007-08-15
forum: General Help
---

### Post by Mojosdad on 2007-08-15
Does anyone have experience of redirect large amounts of mail via Thunderbird and the MailRedirect extension. I am using a local Postfix server since I continually reach my ISP limit on sent mail.

The mail appears to redirect OK but is is so slow! i.e. one mail every 20 seconds or so. I've done a similar thing in Windows using free MailEnable server and the redirected mail just flies out of Thunderbird.

I realise that the mail probably won't get delivered quicker in Windows, but it does hit the local server mail queue much faster meaning I can shutdown knowing that next boot the mail will try to send in the background.

Any suggestions -  I think my Postfix config is almost default apart from the location of the SASL auth and my local domain address.

---

