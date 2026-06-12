---
title: "How to set default Thunderbird account?"
date: 2014-08-22
forum: General Help
---

### Post by sturdy on 2014-08-22
I have two email acounts accessed by Thunderbird. When I look at Account Settings, the first account is at the top and bold font. The second account is below and in unbolded font. So I assume the bold font indicates the first account is the default account. Email always goes out thru the first (default) account unless I remember to change the From address each time I send an email. Of course I seldom remember! But I cannot find a way to change the default From account. Can someone point me in the right direction...TIA.

---

### Post by howefield on 2014-08-22
Thunderbird > Edit Menu > Account Settings > Click on account to be made default > Account Actions > Set as Default.

---

### Post by sturdy on 2014-08-22
Duh, now I do feel dumb. I looked all over for that. Thanks

---

### Post by sturdy on 2014-08-28
Well, I thought this thread was solved but even though I set the new default server (call it From A), Replies to email still revert to From B. New emails are created with the default From address but replies are not created with the the correct default From unless I manually change it each reply.

---

### Post by amanchesterman on 2014-08-29
Just to get this clear about your replies: if you receive mail on the A account and you click 'reply', the reply goes from A; and if you receive mail on the B account and you click 'reply', the reply goes from B; and what you want is for all replies to go from A, is that correct?

'Cos on my Thunderbird setup (with four accounts) the default is always that the reply goes from whichever account received the mail I am replying to: I wasn't aware that you could change that.

---

### Post by sturdy on 2014-08-29
Thanks for the response. I receive email only on account A but it appears that if I click reply the default return account is always B. Doesn't seem logical but that is what is happening. It is a PITA.

---

### Post by amanchesterman on 2014-08-29
I think the way round your problem may be to manage **identities** rather than **accounts**. I haven't tried it myself, but Thunderbird lets you set up different identities for each account. You could make it that replies you send from the default return account (B) appear to the recipient to come from whichever account you wish -- i.e. from A, if you want. There's also a 'reply to' option, i.e. you can tell the recipient to reply to a different account from the one you actually use to send the mail. There's quite a bit of stuff about this on the Thunderbird help pages, which may be useful to you.

Obviously this isn't 'solving' the problem as you state it, it's a workaround, but if it gets rid of the PITA it may be worth doing. ;)

---

### Post by sturdy on 2014-08-30
Thanks, I'll look into **identities**. My problem is that when forum mail is replied to and uses the wrong account, the reply is rejected because that account is not identified as a member of the forum. Thanks, again.

Edit:

Now I see the issue. As I mentioned I have two accounts, A (default) and B. I also have filters to move incoming mail to Local Folders. New mail always goes out from the default account (A). When I reply to unfiltered mail from the Inbox of either A or B, mail goes out from A or B aas appropriate. However, when I Reply to mail that was filtered to a Local Folder, the outgoing account (From) is the last account previously used instead of the default account as would be expected. Seems like this might be a Thunderbird bug.

---

### Post by amanchesterman on 2014-08-30
Yes it looks like a bug, Thunderbird is supposed to use the default account when replying to mail in a local folder: [see here](https://support.mozilla.org/en-US/questions/996194). You might get some help with it on the Mozilla support forum.

---

### Post by sturdy on 2014-08-30
Thanks for the assist. Not such a big PITA now.

---

### Post by sturdy on 2014-08-30
Kind of a back-door solution but this worked for me. I checked the link to the Mozilla Support Forum where there is a discussion of similar issues. The interesting part was the comment that when accounts other than the default account are removed then reinstalled, default and other accounts work as expected. I removed my secondary account, reinstalled it, and joy at last. No more PITA so I am marking this as solved. Thanks for the link amanchesterman.

---

