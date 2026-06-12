---
title: "Possible network problem?"
date: 2008-02-27
forum: General Help
---

### Post by irishgoth8822 on 2008-02-27
I have this problem with my computer on a regular basis:

[http://ubuntuforums.org/showthread.php?t=705376](http://ubuntuforums.org/showthread.php?t=705376)

Last night when the slowdown started, i tried to pay careful attention to what i was doing and what i had just done. I dont know that this has any connection but i think it has happened in this sequence quite a few of the times ive gotten a slowdown:

my internet signal (i use wireless) started to get reeeally slow and caused me to get kicked off my instant messaging client (pidgin v. 2.3.1).  in trying to get it to reconnect, it got to the point where my computer was nominally 'connected' to the signal, but for all intents and purposes, it was dead.  when that happens--out of an old windows-wireless-networking habit, i think-- i usually go into network admin and try disconnecting and reconnecting, just in case. i also, for some reason im not even sure of myself, perhaps obsessive compulsiveness, usually click on the 'general' and 'hosts' tabs and delete all of the entries under either. i think in my mind i am somehow clearing everything so the computer can start from scratch.

everytime i clear those entries, thats when i tend to notice that now my applications and the entire system are lagging, not just the internet. could there be a connection? (no pun intended).

***also, looking at it this morning, there are now no 'hosts' under the hosts tab--should i re-add them, and if so, how? normally they are automatically detected. the DNS tab has the domain and IP listed again, but the hosts tab is blank. the lag at the moment has not yet reached the point where i have to reinstall, so hopefully i can figure this out before i have to do that....

******AND, i ran the network admin from the terminal line, and happened to leave terminal open--i just noticed that it is repeatedly running this script:

```
** (network-admin:7004): CRITICAL **: gst_xml_element_find_first: assertion `parent != NULL' failed 
```

---

### Post by irishgoth8822 on 2008-02-27
i opened our home router just to test a theory, and when i got the faster internet working and rebooted, my computer is now back to normal.

however, i cant keep the router open (my father worries about getting brain cancer or something silly like that), so is there anything i can enable or disable or something to keep a slower connection from screwing up my whole system?

---

