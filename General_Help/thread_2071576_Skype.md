---
title: "Skype"
date: 2012-10-15
forum: General Help
---

### Post by jbh000911 on 2012-10-15
How do I install Skype into Ubuntu 12.04?  I've tried the package manager and software center - and both give a message that a dependency skype-bin is required but not avaiable!

How do I progress from here?

:p

---

### Post by sammiev on 2012-10-15
Try [this]("http://www.skype.com/intl/en-us/get-skype/other-downloads/").

---

### Post by lazarojhr16 on 2012-10-15
like the post before. go to the skype website, ^ he probided the link. pick linux, the one you are using and it will give you a .deb file that can be installed on the terminal using sudo dpkg -i or by using the software center or any other package manager like synaptic. not sure if they have a 12.04 version though.

---

### Post by sammiev on 2012-10-15
> **lazarojhr16 said:**
> like the post before. go to the skype website, ^ he probided the link. pick linux, the one you are using and it will give you a .deb file that can be installed on the terminal using sudo dpkg -i or by using the software center or any other package manager like synaptic. not sure if they have a 12.04 version though.

After he/she down load the deb file they can select by a right click to open with the default which will be a software installer for the deb file. :)

---

### Post by jbh000911 on 2012-10-16
Thanks for the responses. Using the external Skype download didn't resolve the problem as there were a stack of unresolved dependencies associated with the installation, resulting in a broken package!
 e both have the same version of Skype available Skype 4.0.0.8-0oneiric1  but generated the same responses when trying to install it:

                             An unresolved dependence
                                   Skype:
                                                    Depends: skype-bin

I'm running Ubuntu 12.04 LTS with the Lubuntu desktop.   

So, the question is how to resolve this dependence issue?   Is this a bug or what?

Cheers  ;)

---

### Post by sammiev on 2012-10-16
I had it running in 12.04 but have upgraded to 12.10 since. Copy & paste the errors here so we could see what's happening.

---

### Post by jbh000911 on 2012-10-16
Have got it sorted.

Selected a fast mirror and forced a system update -101MB of updates. Rebooted and then tried Package Manager again. Totally different response this time - with a long list of dependencies shown.

Skype is up and running - has been tested between Aus & NZ.

I'm surprised that I had to force a system update as I expected to get auto notification of Security updates, as earlier versions of Ubuntu flag that updates are available.

Anyway, the Skype issue is resolved.

Thanks      :P

---

### Post by sammiev on 2012-10-16
> **jbh000911 said:**
> Have got it sorted.

Selected a fast mirror and forced a system update -101MB of updates. Rebooted and then tried Package Manager again. Totally different response this time - with a long list of dependencies shown.

Skype is up and running - has been tested between Aus & NZ.

I'm surprised that I had to force a system update as I expected to get auto notification of Security updates, as earlier versions of Ubuntu flag that updates are available.

Anyway, the Skype issue is resolved.

Thanks      :P

Great to hear. Maybe select Thread Tools above and mark this Thread as solved. :)

---

