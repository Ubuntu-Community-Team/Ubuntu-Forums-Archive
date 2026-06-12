---
title: "Thunderbird will not delete emails"
date: 2014-03-24
forum: General Help
---

### Post by polt on 2014-03-24
Hello Ubuntu Masters!

Thunderbird is driving me mad lately.  Here is the problem:

I have Thunderbird version 24.4.0 and Ubuntu 13.10.

I have several email accounts, some POPs, some IMAPs, that I've loaded into Thunderbird and they've always all worked fine.  Recently I added a new POP email account and, come to find, I can not delete any emails no matter how hard I try.  You ask: Does using the "Delete" key work?  No! Does clicking the right button and selecting "Delete" work?  Indeed not! Well then, moving them physically into the trash should certainly do the trick.  But it doesn't!  :confused: These emails are just sitting here staring at me mockingly, in spite of my stellar efforts to the contrary.

I've looked at the error messages that come up after an attempted delete, and these are they:

```

Timestamp: 14-03-24 06:47:45 PM
Warning: Unknown property 'mso-line-height-rule'.  Declaration dropped.
Source File: mailbox:///REDACTED/Inbox?number=0
Line: 0, Column: 145
Source Code:
font-family:arial, sans-serif;font-size:11px;line-height:20px;margin:10px 0 10px 0;padding:0;color:#1279D1;text-align:center;mso-line-height-rule: exactly;

```

```

Timestamp: 14-03-24 06:47:45 PM
Warning: Unknown property 'mso-line-height-rule'.  Declaration dropped.
Source File: mailbox:///REDACTED/Inbox?number=0
Line: 0, Column: 33
Source Code:
height:20px; mso-line-height-rule:exactly;

```

+ 3 more just like them, all to do with this mso-line-height.  I'm not positive they are the source of the problem, those are just the ones that appear when I attempt a deletion.

I'm literally up the wall! (figuratively).

Dash it!  These emails really want to live!  Can anyone help me?

---

### Post by gifford on 2014-03-25
Are these all of your emails or just in the new POP account you added?

---

### Post by polt on 2014-03-25
These are just from my new account.  I finally gave up on this problem and just removed the bloody account and then added it back.  It now seems to be working fine.  Another point of interest:  Before removing that account, I was able to drag the emails into one of my local folders and then delete them from there.  I figured that out right before deciding to delete the whole account.

---

