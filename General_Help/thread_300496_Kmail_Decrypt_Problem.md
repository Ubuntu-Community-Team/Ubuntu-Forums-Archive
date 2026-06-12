---
title: "Kmail Decrypt Problem"
date: 2006-11-15
forum: General Help
---

### Post by wizzkid on 2006-11-15
Hi,

I am using Kmail 1.9.5 on Kubuntu Edgy. and kGpg 1.2.2

Email:
[email]user@domain1.com[/email] = Kmail
[email]user@domain2.com[/email] = Evolution

I tried to send email from Evolution to [email]user@domain1.com[/email] (sign and encrpt), then tried checking my kmail for new messages from [email]user@domain2.com[/email], I received email and error was

Encrypted message (decryption not possible)
Reason: Crypto plug-in "openpgp" could not decrypt the data.
Error: Bad passphrase
Encrypted data not shown.
End of encrypted message

Now, if I send email using Kmail to [email]user@domain2.com[/email] (evolution), then tried checking my evolution for new message from [email]user@domain1.com[/email], I received email and asked my a passphase, then decrypt the message. 

My only problem at this point and time is to open an encrypted message thru Kmail. It doesnt ask for a passphase to open encypted messages..


Please advice.

Thanks

---

### Post by sleepingdragon on 2007-02-26
I think everyone is having this problem! I found the only option available at the moment is to "view the source" (press V) of your encrypted message, copy the encrypted part, including the

----- BEGIN PGP MESSAGE -----

and

----- END PGP MESSAGE -----

then, make sure you have Kgpg installed. This will give you a padlock in the taskbar. Right-click it, select "Open Editor" and paste the message you copied into the small dialog window. You'll be asked for your passphrase, and all being well, the message will be decrypted. With a bit of practice, it's nothing worse than a fancy copy and paste, but it works.

I can't offer a better solution, but I'm sure someone will figure the bug out in Kmail soon enough.

[-o<

---

