---
title: "Loading system files into RAM"
date: 2007-07-17
forum: General Help
---

### Post by kiv on 2007-07-17
Because ubuntu only uses a fraction of my ram with nothing running (about 10%) is there a way to load any extra system files into the ram to improve performance?

You could do this with a reg tweak on xp.. just wondering if its possible on ubuntu?!

Thanks.

---

### Post by mcduck on 2007-07-17
> **kiv said:**
> Because ubuntu only uses a fraction of my ram with nothing running (about 10%) is there a way to load any extra system files into the ram to improve performance?

You could do this with a reg tweak on xp.. just wondering if its possible on ubuntu?!

Thanks.

It would hardly make any sense to load any extra system data into RAM, as everything you are using is already loaded there.

However you may want to load application data into RAM. To do that check 'preload'. It basically learns what programs you use most and then starts preloading those into RAM at boot time.

---

### Post by kiv on 2007-07-17
Thank you!

Where is the preload option?

---

### Post by mcduck on 2007-07-17
> **kiv said:**
> Thank you!

Where is the preload option?

I haven't tried it myslf, but I suppose you just need to install Preload and it will work automatically.

So, 'sudo apt-get install preload' should do the trick

---

### Post by kiv on 2007-07-17
> **mcduck said:**
> I haven't tried it myslf, but I suppose you just need to install Preload and it will work automatically.

So, 'sudo apt-get install preload' should do the trick

Thanks mcduck!

---

