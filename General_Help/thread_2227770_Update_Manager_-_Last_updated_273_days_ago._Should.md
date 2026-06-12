---
title: "Update Manager - Last updated 273 days ago. Should I worry?"
date: 2014-06-03
forum: General Help
---

### Post by rbscairns on 2014-06-03
When I run Update Manager, I am told the the last update was 273 days ago.  When I press the "Check" button, it starts unpdating cache but stops part way through and tells me to check my internet connection. I check my internet connect and all is working well. I then clicked on details and received the following:
> W:Failed to fetch [http://packages.medibuntu.org/dists/precise/Release.gpg](http://packages.medibuntu.org/dists/precise/Release.gpg)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://packages.medibuntu.org/dists/precise/free/source/Sources](http://packages.medibuntu.org/dists/precise/free/source/Sources)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://packages.medibuntu.org/dists/precise/non-free/source/Sources](http://packages.medibuntu.org/dists/precise/non-free/source/Sources)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://packages.medibuntu.org/dists/precise/free/binary-i386/Packages](http://packages.medibuntu.org/dists/precise/free/binary-i386/Packages)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://packages.medibuntu.org/dists/precise/non-free/binary-i386/Packages](http://packages.medibuntu.org/dists/precise/non-free/binary-i386/Packages)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://packages.medibuntu.org/dists/precise/free/i18n/Translation-en](http://packages.medibuntu.org/dists/precise/free/i18n/Translation-en)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://packages.medibuntu.org/dists/precise/non-free/i18n/Translation-en](http://packages.medibuntu.org/dists/precise/non-free/i18n/Translation-en)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
, E:Some index files failed to download. They have been ignored, or old ones used instead.
I have also tried different Ubuntu achieves and get the same results.

Should I be concerned about this problem? If so, what can I do to update my cache?

---

### Post by QIII on 2014-06-03
Hello!


Medibuntu is long dead.  You need to remove it from your sources.

What version of Ubuntu are you using?

---

### Post by rbscairns on 2014-06-03
Thank you Qlll. I went into Update Manager settings and, under the "Other Software" tab, I removed everything that had a medibuntu mentioned.

I was then able to update my cache!

ASUS eee B202, Atom N270 1.6GHz CPU, 1GB RAM, 160GB SATA HDD, Ubuntu 12.04 with Gnome Classic

---

### Post by QIII on 2014-06-03
I would start by removing medibuntu.

---

### Post by monkeybrain20122 on 2014-06-03
I would use synaptic to run updates manually instead of relying on the update-manager. Update-manager is not very flexible, if one repository is out (like medibuntu) or temporary unavailable it stops all updates.

---

### Post by LastDino on 2014-06-04
> **monkeybrain20122 said:**
> I would use synaptic to run updates manually instead of relying on the update-manager. Update-manager is not very flexible, if one repository is out (like medibuntu) or temporary unavailable it stops all updates.

+1 to this, or rely on command line.

You might as well consider upgrading to 14.04 by fresh install, if possible, otherwise do upgrade when 14.04.1 comes out in August.

---

