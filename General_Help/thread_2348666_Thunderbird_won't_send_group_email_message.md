---
title: "Thunderbird won't send group email message"
date: 2017-01-06
forum: General Help
---

### Post by Ralph L on 2017-01-06
I am having trouble sending a message to a group email list using Thunderbird.  The message contains a .5 MB jpeg photo.  Whenever, I try to send, I get the message:
```
The size of the message you are trying to send exceeds a temporary size limit of the server. The message was not sent; 
try to reduce the message size or wait some time and try again. The server responded:  4.1.1 <jrdune@gmail.com> requested action aborted: try again later - POL503.
``` Note that the message blamed the problem on <jrdune@gmail.com>, so I deleted <jrdune@gmail.com> from the group list and it stalled on another address.  This went on until I had deleted about 5 of the addresses in the list and then the email was sent.  This site [https://forums.xfinity.com/t5/Email-Web-Browsing/Size-of-message-exceeds-temporary-size-limits/td-p/913167](https://forums.xfinity.com/t5/Email-Web-Browsing/Size-of-message-exceeds-temporary-size-limits/td-p/913167) says the problem is ```
Thunderbird and Comcast are on different pages regarding error messages. The full error message from the server is "452 4.1.1 ... temporary failure". 
TB sees the "452" part and interprets it as an error about size limits. The actual problem is that there is a DNS problem with the domain part of the email address. 
Comcast won't accept email to (or from) email domains that are currently undeliverable. Comcast can't get a DNS answer about whether or not it's a valid email domain, 
so it responds with that 452 error code, which is a temporary error that essentially means "try again later".
``` I don't have Comcast but rather Mediacom as my email provider and I use the email system they provide--mchsi.com.  It seems possible that Mediacom has the same problem as Comcast. When googling this problem, I found that is happens rather commonly, and that it always seems to involve a problematic address in the group list.  Moreover, using an email program other than Thunderbird (such as Outlook) always works. (Note: I don't have another email program so I have not personally verified it working on another email program, but several of the complaints I googled made this claim.) And it happens when Thunderbird is run on Windows as well as Ubuntu.  Mozilla claims it isn't a Thunderbird problem, but the fact that other email systems don't have the problem makes me think it is Thunderbird. a

1. Has anybody on this forum experienced the problem?
2. Does anybody have a fix or a work-around for this problem?
3. I don't like the way Thunderbird handles the problem (just refusing to send the email to anybody in the group).  I think it ought to list the web sites in error, but give the user the option of sending or not sending to the group.
4. How does one put pressure on Mozilla to fix this problem, when they have consistently claimed it is not their problem?

---

### Post by Keith_Helms on 2017-01-06
It may be that Thunderbird treats a send operation to a mailing list as a binary operation - the whole thing either works or it fails.  I found a lot of postings about various problems with Thunderbird mailing lists over multiple years and versions.

I found this as a possible workaround or test:

> I don't have a solution but I do have an easy work around. While composing an email open the address book and select the list you  are trying to send to, highlight all the names in the list and drag to  the To: box.

I'd give that a shot just to see if it works like you want when sending to a bunch of individual recipients where using a mailing list would fail.  That would narrow your problem down to mailing lists.  If that also fails, well maybe there really is a size limit problem.

---

### Post by Ralph L on 2017-01-11
Keith_Helms:
Thank you for responding.  I will try your suggestion of copying and pasting the group list into the "To" line, when group sending fails.  However, I would sure like to get Mozilla to fix the problem.

---

### Post by SeijiSensei on 2017-01-11
Frankly, it sounds much more like a problem with your email provider than with Thunderbird.

That message from Xfinity suggests the bad addresses have unresolvable domains.  That has nothing to do with the size of the message:

> The actual problem is that there is a DNS problem with the domain part of the email address. Comcast won't accept email to (or from) email domains that are currently undeliverable.

Have you reviewed all the addresses on your list to make sure they have valid domain parts?

I manage listservers and have encountered various problems with the big email providers.  Google, for instance, routinely complains about messages sent to multiple domains that it hosts.

---

