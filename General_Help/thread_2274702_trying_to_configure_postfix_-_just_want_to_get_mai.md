---
title: "trying to configure postfix - just want to get mail from programs locally"
date: 2015-04-21
forum: General Help
---

### Post by a-you on 2015-04-21
I've been trying to configure postfix so that for example rkhunter can email me if it detects something odd. I have been running:

```
dpkg-reconfigure postfix
```

and trying every conceivable variation on the items it asks for but unfortunately I don't really understand some of the terms. I've searched and read many tutorials, guides, etc but they all seem to be about trying to configure postfix to send to an external account. I don't need that. Just being able to receive emails from locally installed programs is all I'm after.

Many thanks in advance for any advice!!!

---

### Post by matt_symes on 2015-04-21
Hi
> 
I've searched and read many tutorials, guides, etc but they all seem to  be about trying to configure postfix to send to an external account. I  don't need that. Just being able to receive emails from locally  installed programs is all I'm after.

I'm no postfix expert so i won't be able to help too much. I'm confused by the above quote though and maybe some clarification will help someone get the ball rolling for you.

Where do you want the mail delivered to ? 

Do you want the mail sent to the local mailbox of the system administrator (your account) on the machine running rkhunter ?

Do you want the e-mail sent to an external service such as gmail ?

I understand you want to get rkhunter's email but where do you want it sent to so you can retrieve it.

Can you clarify this please.

Kind regards

---

### Post by a-you on 2015-04-22
Thanks matt for your comment.

All I'm trying to do is to have mail from programs on this laptop delivered to a folder on this same machine, not to the greater interwebs. No configuration I tried worked; the mail was at least being delivered (before postfix had apparently not been configured at all) but it was going to an mbox in /var/mail for "nobody."

I think I may have answered my own question though. But if you or anybody else that knows postfix would please comment I'd much appreciate it; I'd like to be sure I didn't break anything (THANKS in advance). What I did was:

I ran```
dpkg-reconfigure postfix
```again. This time when it asked for "system mail name" I entered localhost.localdomain. Then when it asked for "root and postmaster mail recipient" I enterred my user name. For all other questions I left the default answers except when it asked me to specify "mailbox size limit (bytes)" I changed it from the default of 0 to 51200000 which it also said was the "upstream default."

Then I edited /etc/aliases by adding these two lines:
root: my_user_name
operator: my_user_name
above the line that says "# ---SmartList Begin"

Then I did:
```
newaliases
```

Then I tested it by changing /etc/rkhunter.conf.local to send to [EMAIL="root@localhost.locald"]root@localhost.locald[/EMAIL]omain and rkhunter sent its report to an mbox created with my user name in /var/mail.

But like I say, I'd appreciate it if somebody more expert in this would comment, in case that was not the way to do it. Thanks again.

---

### Post by matt_symes on 2015-04-22
Hi

That's pretty much what i have done on this laptop and on some of my other servers for local mail delivery, so if it's wrong then we're both doing it wrong :p

BTW: I configured it on this laptop for the packages* apt-listchanges *and* tripwire*.

You may want to mark this thread as [SOLVED] or wait a while to see if someone can comment on the postfix configuration and then mark it so.

Kind regards

---

### Post by a-you on 2015-04-23
"so if it's wrong then we're both doing it wrong" <--haha, nice.

Maybe I'll leave it "unsolved" for just a few days more in case somebody wants to comment, then whether they do or not I'll mark it "solved."

Thanks again for your comments. Btw I like the quotes you have at the bottom of your posts :-).

---

