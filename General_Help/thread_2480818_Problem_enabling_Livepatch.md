---
title: "Problem enabling Livepatch"
date: 2022-11-11
forum: General Help
---

### Post by eliasmys1 on 2022-11-11
Hi!

I tried enabling Canonical Livepatch, according to the tutorial here: [https://ubuntu.com/security/livepatch/docs/client/enabling](https://ubuntu.com/security/livepatch/docs/client/enabling).
But, I repeatedly encountered the following error:

```

Stderr: Could not retrieve client information.: unauthorized

Stdout: 
Unable to enable Livepatch: Failed running command '/snap/bin/canonical-livepatch enable <REDACTED>' [exit(1)]. Message: Could not retrieve client information.: unauthorized

```

I already have my machine attached to Ubuntu Pro, which, as mentioned, includes Canonical Livepatch.
I closed (by pressing "X") my Canonical Livepatch Client earlier and, now, cannot find a way to re-enable it.

Please help!

---

### Post by eliasmys1 on 2022-11-11
Just to inform you, I managed to enable LIvepatch, so everything is ok, but any additional help will be valuable.

---

### Post by Time Light on 2022-12-14
> **eliasmys1 said:**
> Just to inform you, I managed to enable LIvepatch, so everything is ok, but any additional help will be valuable.

I'm really curious, how did you manage to enable Livepatch? Because I tried uninstalling livepatch, clearing out the machine-id and making a new one, and pretty much tried *everything* there is.

But I still get this error upon attempting to enable Livepatch with sudo pro enable livepatch:
```
One moment, checking your subscription first
Stderr: Could not retrieve client information.: unauthorized

Stdout: 
Unable to enable Livepatch: Failed running command '/snap/bin/canonical-livepatch enable <REDACTED>' [exit(1)]. Message: Could not retrieve client information.: unauthorized

```

And I get this error if I try sudo ua enable livepatch:
```
One moment, checking your subscription first
Stderr: Could not retrieve client information.: unauthorized

Stdout: 
Unable to enable Livepatch: Failed running command '/snap/bin/canonical-livepatch enable <REDACTED>' [exit(1)]. Message: Could not retrieve client information.: unauthorized

```

Why does it say unauthorized? Is this a permissions issue? Is this saying the encryption key is incorrect? What is it? I don't understand...

---

### Post by MAFoElffen on 2022-12-15
Both of you are standard free users & have a limit of 5 (free) machines that you can use your user token key for... Before changing the machine ID, don't you first need to disenroll the machine? And if the machine no longer exists, then I think you need to contact Ubuntu Pro support to get help manually disenrolling the missing machine from your subscription... 

Just going off what I asked Ubuntu Pro support about that and the answer they gave me, if a system crashed and didn't exist anymore, how that affected user's subscriptions.

---

