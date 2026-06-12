---
title: "Deja Dup - Only back up when on specific network?"
date: 2014-04-03
forum: General Help
---

### Post by Roasted on 2014-04-03
Hello friends. I'm working with Deja Dup on my Ubuntu system which backs up to my Ubuntu server on my LAN. Thing is, I'm often away from home when using this system. As a result it seems as if Deja Dup tries (and fails) to back up to my server's IP when I am actually away from the LAN, but then doesn't (seem to, anyways) try again when I'm on the LAN later that same day.

Is there a way to trigger Deja Dup to run specifically when connected to a certain SSID?

---

### Post by CaptainMark on 2014-04-03
You didn't mention but I'm going to assume you're on wifi (hence the mobile system) if so you can jot up a small bash script if your familiar with them.
```
if [[ "$(iwgetid)" == *network_name* ]] ; then
    deja-dup --backup
fi

```*Small caveat: This assumes your wifi network name appears anywhere in the output of iwgetid so should work for almost all cases. I would advise that you don't have a generic network name either like some people leave the name as whatever it is out of the box when they get the router.

---

