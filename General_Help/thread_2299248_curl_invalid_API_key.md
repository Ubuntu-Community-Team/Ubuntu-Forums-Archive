---
title: "curl invalid API key"
date: 2015-10-16
forum: General Help
---

### Post by leiser-alexander on 2015-10-16
Hi,
I try to gather some weatherdata from openweathermap.org.
I need the data in the xml format like discribed here [http://openweathermap.org/current#format](http://openweathermap.org/current#format)
But when  I try to gather them with curl or wget (here is an example adress:  [http://api.openweathermap.org/data/2.5/weather?q=London&mode=xml&appid=bd82977b86bf27fb59a04b61b657fb6f](http://api.openweathermap.org/data/2.5/weather?q=London&mode=xml&appid=bd82977b86bf27fb59a04b61b657fb6f)  )
I get the following error:
```

alex@alex-P170HMx:~$ curl http://api.openweathermap.org/data/2.5/weather?q=London&mode=xml&appid=bd82977b86bf27fb59a04b61b657fb6f[1] 6193
[2] 6194
alex@alex-P170HMx:~$ Invalid API key. Please see http://openweathermap.org/faq#error401 for more info.
[1]-  Fertig                  curl http://api.openweathermap.org/data/2.5/weather?q=London
[2]+  Fertig                  mode=xml

```

Has anyone an idea how I can resolve this?

greetings
Alex

---

### Post by sandyd on 2015-10-16
Add quotes, if you don't, bash will interpret the different symbols in the URL.

i.e.
```

curl -L http://api.openweathermap.org/data/2.5/weather?q=London&mode=xml&appid=*apikey*

```

And I suggest getting a new API key now since you've posted it on the forums.

---

### Post by leiser-alexander on 2015-10-17
Hi,
thank you very much. Problem is solved.

This is just the example API key from openweathermap, so no problem there.

greetings
Alex

---

