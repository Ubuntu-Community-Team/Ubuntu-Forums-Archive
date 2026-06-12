---
title: "Lost Keyring Manager password"
date: 2007-09-25
forum: General Help
---

### Post by kcbnac on 2007-09-25
I managed to completely forget my Keyring Manager password.  I feel like an idiot.

Is there a way I can:

A) wipe it out
or
B) 'Brute Force' it (I have a short list of keywords for it to use, as its a combination of normally secure phrases...I just made it MORE secure than usual...)

I'd prefer option B - without manually typing it in.  I've tried that, and about run out of patience.

Thanks in advance for any and all help!

(And next time, I'm setting it to my account password...)

---

### Post by DouglasK on 2007-09-25
I'm not sure of any way to to B.  It's supposed to be pretty secure.

as for a:
[LIST]
[*]Click Tools, Administration, Keyring Manager
[*]Deny any request(s) for access
[*]In the Keyring manager, Click View, Keyrings
[*]Highlight the default keyring on the left hand pane
[*]Deny any request for access
[*]Click File, Delete Keyring
[/LIST]

Hope this helps out

~~Douglas

---

### Post by kcbnac on 2007-09-25
Then I suppose it'll ask me to recreate one next time I hit something where it would save it?  (As if there never was one in the first place?)

---

### Post by DouglasK on 2007-09-27
> **kcbnac said:**
> Then I suppose it'll ask me to recreate one next time I hit something where it would save it?  (As if there never was one in the first place?)


exactly... with no keyring, it should just create a new one.

---

### Post by kcbnac on 2007-10-01
Exactly what happened.

System->Administration->Keyring Manager

Selected 'default' and it prompted me for the password for the keyring.

I selected 'Deny'

Went to the top menu: Keyring->Delete Keyring

Confirmed I wanted to delete it.

Went to reconnect to the network, it prompted me for the wireless key, and then prompted me to create a keyring password.

I'm all set!  Thanks for the help guys!

---

