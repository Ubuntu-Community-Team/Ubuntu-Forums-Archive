---
title: "Umlauts broken in mail forwards but not in mailbox itself"
date: 2023-01-07
forum: General Help
---

### Post by ufreier on 2023-01-07
[FONT=verdana]Dear Community,

I don't even know if my problem is relied to Postfix or Dovecot but I would be glad for any hint to solve it.

Setup:

Ubuntu 22.04, Postfix 3.6.4, Dovecot 2.3.19.1

I set up a domain's mailbox and therein a mail forward to another mail address that is hosted local on the same server, so I receive each mail to this mail address twice, once in the mailbox itself and also in the mailbox of the forward. Spam and virus protection are disabled on both mailboxes.

Issue:

In general this setup works as expected but there are mails from a foreign web application or middleware that do not contain any content-type or other information about charset and if those mails **go directly into the mailbox** German umlauts are correctly displayed (and if the mail file is opened on the server in vi it shows right coding e.g. "Stra<DF>e" for "Straße") but in the **forwarded mails** (to a mail address on the same server) the umlauts are broken (e.g. "Stra&#65533;e"). So it seems that on forwarding the mail body has been altered and that shouldn't be IMO. All locales on the server are en_US.UTF-8.
Using exactly the same setup on a Ubuntu 14.04, Postfix 2.11.0, Dovecot 2.2.18 the problem does not persist, the forwarded mails are identical to the mails in the mailbox - the problem arose first during migration from the old to the new server. Unfortunately I have to parse the contents of the affected mails to a database (therefore preserving the umlauts is mandatory) and I can't influence their bodies or headers in any way.

I'll appreciate any hint where I can search for further advice!

Many thanks, Uwe[/FONT]

---

### Post by TheFu on 2023-01-07
Basic email, is 7-bit ASCII.  Basically, the US-ASCII character set.  MIME has added the ability for additional attachments to be added which support more characters.  The SMTP standard **requires** the 7-bit version be transmitted and the MIME attachments are optional.  This is how fancy emails with UTF-8 encoding are supported.

So, check that both are being sent and that the client is not set to use "plain text" or "text" as the option.  In thunderbird, there is "Simple HTML" and "Original HTML" as options.  The Original HTML is a security problem, since external links like image bugs allow tracing.  Simple HTML will/should show the expect characters.

At one company, I was getting empty email messages because the sender's email server (MS-Exchange) was improperly configured and I only used 7-bit ASCII as a way to limit security problems.

I did find that dovecot needed specific settings to support UTF8, but the messages around that were from 2019 going back to 2016.  In the end, they said that all the software in the email path needed to be compliant and configured to support utf8 for that to work as expected.

That's my best guess.  But I haven't used dovecot since 2008-ish.  Nothing against it, we just love enterprise features offered by some other, much more bloated, software. ;(

BTW, ESM support for 14.04 ended 4 yrs ago. Nobody should be using it for anything in 2023 ... or 2020.

---

### Post by ufreier on 2023-01-08
Thanks a lot for your answer but I don't have any control over the affected mails, I must process them as they are. Further more there is no mail client involved, the mails are read directly from the file system by the parser and therefore I guess the problem is not a wrong interpretation but different depictions of umlauts in both mail files, the one that lies under the mailbox and the one that lies under the mailbox of the address it was forwarded to.

---

### Post by Impavidus on 2023-01-08
DF stands for ß in both Latin-1 and Unicode, that's correct, but in UTF-8 this is actually encoded as C3 9F. So it looks like in your file, as you inspect it with vi, it's actually encoded as 8-bit Latin-1 (or something similar), not as UTF-8. Recent versions of vi can also guess encoding and convert, so it displays correctly. My vim displays both "Stra<C3><9F>e" and "Stra<DF>e" as "Straße", but in the latter case tells me that the encoding has been converted. Dumping it to the terminal with cat gives an encoding error in the latter case.

The encoding isn't explicitly indicated, so the e-mail program you use has to guess. It correctly sees that it isn't valid UTF-8 and then guesses correctly that it's 8-bit Latin-1. When forwarding, the message gets explicidly marked as UTF-8, so the e-mail program now detects an encoding error and shows a question mark in a box. At least, that's my guess. Maybe you can check it by inspecting the headers.

I'm not familiar with Dovecot or Postfix. It looks like you have to configure your forwarder not to add encoding information to the header if it isn't there already without properly guessing the used encoding. If the forwarder can't guess the encoding, then the tool you use to parse the mails must guess it. Then this parser has to convert the encoding if necessary.

---

### Post by TheFu on 2023-01-08
> **ufreier said:**
> Thanks a lot for your answer but I don't have any control over the affected mails, I must process them as they are. Further more there is no mail client involved, the mails are read directly from the file system by the parser and therefore I guess the problem is not a wrong interpretation but different depictions of umlauts in both mail files, the one that lies under the mailbox and the one that lies under the mailbox of the address it was forwarded to.

You should contact the source of the emails if they are a partner company or just start bouncing them as "malformed" for anyone else. At least that way the users on the other side would be able to contact their email admin to get it fixed.

---

### Post by ufreier on 2023-01-11
@TheFu
I'm more scared that they'll make it worse on trying to make it better (or right). Especially because the import of their mails is running perfectly on the existing system so I won't change it.

@Impavidus 
The hint with Latin/Unicode of the mail that seems to be okay is interessant, I didn't notice that it's not UTF-8. Obviously encoding was changed anywhere between saving, forwarding the mail and saving it again (it all happens on the same server). The MTA does not add any header information concerning encoding while forwarding, just like the original the forwarded mail does not contain one. 

Thanks to all, I have to investigate further.

---

