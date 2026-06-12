---
title: "help!!! mutt +  imap = gmail.... default action is delete msgs"
date: 2007-11-27
forum: General Help
---

### Post by freeballer on 2007-11-27
I almost got myself in a load of crap when I tried using mutt to work with gmail last night. I configured it with the info below (minus user/pass), it downloaded the msgs fine but aftewards when i tried to exit mutt it says setting msg to delete or something to that effect.

I went into my gmail account afterwards and sure enough all msgs were in process of disappearing out of my inbox. Luckily they were still in the "all mail" and I just restored the whole thing to inbox again....

So how the heck can I make the default option to not do that?!



```

set spoolfile = imaps://imap.gmail.com:993/INBOX

set imap_user = 'emailaddy'
set imap_pass = 'password'

set smtp_url="smtp://emailaddy@smtp.gmail.com:587/"
set smtp_pass = 'password'

set folder = imaps://imap.gmail.com:993
set postponed="imaps://imap.gmail.com/[Gmail]/Drafts"
set record="imaps://imap.gmail.com/[Gmail]/Sent Mail"

set imap_check_subscribed="yes"
set imap_list_subscribed="yes"

set header_cache="~/.mutt/hcache/"
set message_cachedir="~/.mutt/msgcache/"
set certificate_file=~/.mutt/certs

bind browser <return> view-file
```

---

### Post by seventhc on 2007-12-07
'all mail' is just a folder, like an archive. It isn't getting deleted. It will only get deleted if you move it to the trash. When I first set up mutt, mine went to the trash and i changed that to go to 'all mail' instead, thankfully the trash doesn't get deleted for 30 days :) and I was able to move it to the 'all mail' folder. I prefer it this way, but if you don't want it going to 'all mail' you will have to edit your muttrc.

---

### Post by freeballer on 2007-12-07
what option in muttrc does this? there is one that says copy / move, is that the right one?

---

### Post by seventhc on 2007-12-07
you said when you delete them they go into the 'all mail' folder so they are being saved. or if 'd' is deleting them to trash u might use 's' for save instead. I'm not sure if I'm fully understanding you though.
right now, the way mine is set up, 'd' will delete it, and 's' saves it to all mail.
I'm actually using a different muttrc now than what i was using a few days ago, but i have a backup of it. so pls let me know exactly what u need and maybe i can help more. :)

---

### Post by freeballer on 2007-12-07
well it's not the general use that I have a problem with. mutt marks them read and all folders are showing but what's happening is when closing mutt ONLY. They seem to be moved to the all mail folder or deleted items (I can't honesly remember exactly where) instead of keeping in inbox. to keep my inbox and other items intact so it's easier to sort from sent, drafts, etc... unless I delete something myself.

I found an option to set in ~/.muttrc "set move=no" on an unrelated site. It seems to be right but I don't want to risk loosing my mailbox. So would this do what I want (keeping everything else same, except the changes I make [eg. moving to folder -- which I know will create a label in gmail]) or are there other option(s)?

---

### Post by seventhc on 2007-12-07
your best bet would be to test it. delete some mail, and then log into gmail and check the trash to confirm it wasn't moved to the trash. The trash in gmail doesnt get deleted until 30 days later, so it is safe to experiment.

if when you log into gmail and you see it in your inbox, then it most likely worked. but double check everything just to be safe. :)

I think that 'set move=no' should work, but it really depends what else is in the muttrc. I think some lines can over ride others or cancel each other out because that happened to me. i set it to no, but i had a line in there that seemed to over ride it. thats what it seemed like to me anyway so just double check everything. :)

---

### Post by andrew.46 on 2007-12-22
Hi,

 I suspect that as you mentioned you need to set the following in your ~/.muttrc:

```
set move=no
```This is a quad option line:

> # set move=ask-no
#
# Name: move
# Type: quadoption
# Default: ask-no
# 
# 
# Controls whether you will be asked to confirm moving read messages
# from your spool mailbox to your ``$mbox'' mailbox ...Those imap settings look hauntingly familiar, do you remember which guide they came from?

            Andrew

---

### Post by freeballer on 2007-12-22
unfortunately no, I did not bookmark it and just cleared my cache/history last night.
Its just something I found on google after I saw the move command....

the move worked fine on my other google acc, so after I install linux again on my htpc I will use that for my main acc

---

### Post by steveo_mcg on 2008-01-08
This is going to seem like a stupid thing to have done and i know i shouldn't try thing when i'm tired. Any i've just downloaded my imap mail box to a mbox file through mutt, is there any way to restore them to the server? I really need to be able to access this account from every where. I stupidly thought it was caching it instead of downloading it. I have since found the cache option	:-({|=

---

