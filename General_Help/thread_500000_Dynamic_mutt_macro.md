---
title: "Dynamic mutt macro"
date: 2007-07-13
forum: General Help
---

### Post by kspider on 2007-07-13
I get around 100 emails a day from the servers that I manage. Procmail dumps them all into the same mbox, which is the way I like it. I want to create a macro that creates a limit based on the host of the sender of the current email in the index - in my case its the name of the server that emailed me. This way, I could quickly see all the emails from each server.

So, if the current email iss from [email]root@server.something.com[/email] i'd like a limit like:
~L server

The best I can come with is something like:

macro index <esc>s "<enter-command>unset wait_key\n<pipe-message>formail -x From:|sed -e 's/\w\+\@\(\w\+\)\..*/\1/'>/tmp/muttlimit\n<enter-command>set wait_key\n<limit>~L `cat /tmp/muttlimit`<enter>" "Change limit"

But this doesn't work.

Any thoughts?

Thanks

---

### Post by andrew.46 on 2007-07-16
Hi,

 I am not clever enough to write such a thing but I am pretty sure that there would be some on the mutt-users mailing list who could:

[http://www.mutt.org/mail-lists.html](http://www.mutt.org/mail-lists.html)

              Andrew

---

### Post by kspider on 2007-07-16
Thanks.  I'll give them a try.

---

