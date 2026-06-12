---
title: "PPA/Muon etc. What are these people doing in my machine?"
date: 2021-11-24
forum: General Help
---

### Post by GhX6GZMB on 2021-11-24
During my fiasco and subsequent succes installing Brave (a marathon), I rummaged around in the Lubuntu install managers.
Eg, Muon and "Software sources".

And I found some strange characters there:
Fabio Pedretti
Panda Jim

Who are these guys? And why do they have security keys on my machine?

Anyone have an idea?

---

### Post by guiverc on 2021-11-24
I would likely run `sudo apt update` and read the output there.

They're likely related to PPAs or 3rd party sources you've added to your machine.

eg. have you installed Oibaf video drivers for example (Fabio Pedretti is/was one of the maintainers)..  eg. [https://keyserver.ubuntu.com/pks/lookup?fingerprint=on&op=index&search=0x96094089633E31EC17F1A696FB3C2AA90622608A](https://keyserver.ubuntu.com/pks/lookup?fingerprint=on&op=index&search=0x96094089633E31EC17F1A696FB3C2AA90622608A) is one of two authorized uploader keys to the [Oibaf PPA]("https://launchpad.net/~oibaf").   It's likely this applies to both your names, and I'd use the 3rd party details seen in the output of `apt update` for exploration of what you've added to your system.

---

### Post by aug7744 on 2021-11-25
"And I found some strange characters there: Fabio Pedretti Panda Jim"
Possibly you had added launchpad repository ....
Panda Jim is GIMP PPA repository for current release
[https://launchpad.net/~ubuntuhandbook1/+archive/ubuntu/gimp?field.series_filter=focal](https://launchpad.net/~ubuntuhandbook1/+archive/ubuntu/gimp?field.series_filter=focal)

Not care about it :)

---

