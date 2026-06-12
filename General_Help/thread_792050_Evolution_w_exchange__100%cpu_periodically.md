---
title: "Evolution w/ exchange:  100%cpu periodically?"
date: 2008-05-12
forum: General Help
---

### Post by sp00ki on 2008-05-12
I'm currently using Evolution to check an MS Exchange account (at work).
I'm using Debian Etch, but i had the same issue running Ubuntu 8.04 with the same exchange account.
Periodically (ranging from once ever five to fifteen minutes) Evolution shoots up to 100% load and remains there for roughly five minutes.
While this is occurring, all functionality hangs (sometimes giving me gnome's "darkened window").
I can kill all evolution related processes and relaunch, but i'm hesitant to as evolution takes quite a bit of time to load all messages and start.

I'm wondering:  has anyone who's encountered the above problem been able to resolve it?
I'm running evolution 2.6.3 with evolution-exchange.

Incidentally, it also appears to utilize just under 1GB of memory while this is happening.

---

### Post by papikondalu on 2008-05-13
I had seen this when GAL server was pointing to a wrong location. After setting it to the correct GAL server this 100% CPU problem is not seen.

However, the exchange connectivity is flaky. It works the first time evolution is launched. After a while the connectivity is lost. Evolution does not even notify that the connection is lost. When I don't see any email for a while, I realize that there is some issue with evolution. When I click on Send/Receive, I get a message that 'could not connect to evolution-exchange server'.  That is when I restart evolution to get new messages. This behavior is annoying.

Also, there are issues with Google calendar setup. It does not sync all entries. I can see these entries by adding the google calendar in webcal mode.

-PK

---

### Post by arcanus on 2008-05-13
I can see that my evolution client is using 25% CPU and the Exchange backend shooting up to the same after a while. Its definitely a memory leak in the app...  Lets just hope the devs can find and fix it, because evolution is afaik the only client that integrates exchange calendars and contacts as good as evolution does.

Oddly enough there is a g-conf process running at the same CPU utilization at about the same time.

I haven't been able to find out when the CPU creeps upwards, but i can certainly hear it when the fan on my laptop runs through the roof ;)

Magne

---

### Post by jcro001 on 2008-05-22
I have exactly the same issue. Evolution starts using 100% CPU. I need to close and reopen it. I also noticed that if I run a long process like podencoder then Evolution does not take over the CPU. Also, after I disabled my Exchange email account this does not happen anymore.

---

### Post by arcanus on 2008-05-22
Funny thing, as I compose new messages in evolution, i can see the CPU go 10-20% up. Every time... And it doesn't go down when I close the composer. So when i write 5 mails... Well, guess what happens :D

This is regardless of what mail i use. (I haven't dissableded my exchange plugin, so it might be it's causing the problems...)

Magne

---

### Post by mitchellfx on 2008-05-22
Does anyone know if this bug been reported? It's quite obnoxious...

---

### Post by the_maassk on 2008-05-23
> **arcanus said:**
> Funny thing, as I compose new messages in evolution, i can see the CPU go 10-20% up. Every time... And it doesn't go down when I close the composer. So when i write 5 mails... Well, guess what happens :D

This is regardless of what mail i use. (I haven't dissableded my exchange plugin, so it might be it's causing the problems...)

Magne

Happened to me too. This might help:

[http://ubuntuforums.org/showthread.php?t=775381](http://ubuntuforums.org/showthread.php?t=775381)

---

