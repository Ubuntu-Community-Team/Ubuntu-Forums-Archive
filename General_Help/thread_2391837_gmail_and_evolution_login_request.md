---
title: "gmail and evolution login request"
date: 2018-05-13
forum: General Help
---

### Post by yazdzik-k on 2018-05-13
Dear Friends,

Google,Alphabet,  or gmail,  or whoever the people are who make life miseable for end users world wide seem to want to paste a code into evolution,  where,  obviously,  there is no place so to do.  

The only solution I have is to log out to avoid the pop up saying evolution gmail:contacts needs something or another.   

I have used evolution since Ximian,  and cannot understand what has happened,  as immediately upon login,  everything,  calendar,  contacts,  &c is there.

Also,  for some reason,  I cannot keep gmail contacts,  which sync with handy,  two laptops,  tablet &c,   as my default contacts,  that must be manually edited each evolution session.  Evolution is obviously always running,  and should realise I do not want local contacts as my default,  as in 2018,  one enters a new contact on the phone,  one expects it automatically to be on the computer.  What is happening?

Evolution 3.28.1-2

Linux XXXXXX  4.15.0-20-generic #21-Ubuntu SMP Tue Apr 24 06:16:15 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

Ubuntu 18.04,  kept updated.

This does not happen with debian testing/sid running Mate desktop,  same evolution version.  

I can only surmise it is something gnome specific.







Best,
M

---

### Post by kerry_s on 2018-05-13
did you check the plugins to make sure there on?

---

### Post by yazdzik-k on 2018-05-13
Dear Kerry,

Thank you for answering.  What plugins? 

Evolution plugins are installed,  but not of those would affect authentication,  as they are unrelated to SSL,  7c.

Best,

M

---

### Post by kerry_s on 2018-05-13
i meant:
evolution-> edit-> plugins-> automatic contacts

see if it's still checked & configured for your contacts sync.

i'm not sure what your other question is. my guess is you have autologin & it asks for the key?
passwords & keys-> right click login-> change password, put your current password, leave the new password blank, just hit continue.

---

### Post by yazdzik-k on 2018-05-13
Thanks,  I do have automatic contacts checked,  so it should sync between all computers and cell phones and web browsers wherever I am,  since the point is gmail is gmail,  however fetched.
I have checked all the keyring stuff,  and it appears all in order.  There is no reason that google should mistrust this instance of evolution,  since on gmail settings on the web it is listed as trusted with the various permissions.  I suspect something to do with gnome online accounts,  but since I try to avoid that entirely,  I am not sure why it would make a difference whether I use evolution with/without gnome,  with/without gnome accounts,  and so on.  You are very helpful,  and it is appreciated.

---

### Post by kerry_s on 2018-05-13
ohh, i used the online accounts for mine, so you maybe right about that.

---

### Post by yazdzik-k on 2018-05-13
Dear Kerry,

Thank you,  that provides a good starting place.  I think evo 3.28 is much more tightly integrated into gnome,  or  just the fact that Ubuntu is now running pure gnome,  may be what is throwing me.  Plus,  of course,  gmail changes security procedures more often than most people bedsheets.   

I shall post back with results.

Gratefully,

M

---

### Post by kerry_s on 2018-05-13
yeah, there really pushing security on everything these days.

---

