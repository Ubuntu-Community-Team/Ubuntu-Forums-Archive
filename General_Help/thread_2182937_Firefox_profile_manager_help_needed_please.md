---
title: "Firefox profile manager help needed please"
date: 2013-10-23
forum: General Help
---

### Post by Kate_Austin on 2013-10-23
I am having problems with Firefox Profile manager  ... This all started when my ISP crashed while i was in the middle of upgrading to Saucy Salamander 13.04 .. I lost everything .. I have managed to get my pc back up and running and also finish the upgrade ....  but am still having problems with the FFPM .. I can open multiple accounts fine but have to open a Terminal and command it each time  and when i close the terminal that account closes with it .. when i open the profile manager i am getting this error code ~~> (process:1876): GLib-CRITICAL **: g_slice_set_config: assertion `sys_page_size == 0' failed
This is what i am typing into the terminal ~~> 
firefox -no-remote -P


 .. I am desperate .. No one seems to know about Ubuntu or the FFPM ... You are my last chance before i just give up .. thank you .. Kate :confused:

---

### Post by bibble235 on 2013-10-23
Perhaps [https://bugzilla.mozilla.org/show_bug.cgi?id=833117](https://bugzilla.mozilla.org/show_bug.cgi?id=833117)

They suggest maybe 

export G_SLICE=always-malloc

Might work

---

### Post by Kate_Austin on 2013-10-23
thank you so much i will try that :)

---

### Post by Kate_Austin on 2013-10-23
i right clicked on the terminal at the bottom and moved it to workspace down.. where its gone i dont know but its out of my way for now . lol

---

