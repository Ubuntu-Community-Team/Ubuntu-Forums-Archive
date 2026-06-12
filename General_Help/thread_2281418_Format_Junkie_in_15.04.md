---
title: "Format Junkie in 15.04"
date: 2015-06-06
forum: General Help
---

### Post by Miykel on 2015-06-06
Been trying to install format junkie in ubuntu 15.04,add ppa then update but when I run  install formatjunkie I get  "Unable to locate package formatkunkie"
regards Miykel

---

### Post by Bashing-om on 2015-06-06
Miykel; Hello;

Did you check and make sure the PPA supports 15.04 ?
Show the source URL and I will verify .

[INDENT][INDENT]when all else fails
[INDENT][INDENT][INDENT]check the source
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by egeezer on 2015-06-06
If the reply was exactly as you posted it, I believe you are the victim of a typo, not that I haven't done the same thing a few hundred times, with the same result! :-)

---

### Post by grahammechanical on 2015-06-06
> This PPA currently has support for Precise, Quantal, and Raring.  It does not have support for any other releases.

[https://launchpad.net/~format-junkie-team/+archive/ubuntu/release](https://launchpad.net/~format-junkie-team/+archive/ubuntu/release)

When we use add-apt-repository to add a PPA to our software sources the command will include the release code name as part of the PPA url. So, in this case the url will contain the name "vivid." But there is not an archive at that url. And that is why apt-get says "unable to find package."

Regards.

---

### Post by Miykel on 2015-06-06
Yes I see; no wonder it won't work, will have to boot back into 14 to reformat ahy media until things catch up to 15;

This is the official PPA for the Format Junkie.
 This PPA currently has support for Precise, Quantal, and Raring.  It does not have support for any other releases.

Thank you so much guys, I appreciate the help
Regards Miykel

---

