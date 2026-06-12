---
title: "Eclipse 3.2 Problems"
date: 2006-07-01
forum: General Help
---

### Post by GTar on 2006-07-01
Anyone else having problems with the new Callisto release of Eclipse?

I can't seem to install CDT correctly through their Software Updates feature, an unexplained exception occurs when the module is downloaded. Any ideas why this is happening?

Is there a better way to install CDT manually?

Cheers,

---

### Post by mlind on 2006-07-01
I downloaded CDT from Callisto without problems. Try using another mirror maybe?
German mirror worked fine for me.

I don't know how else you can get the extension, their site isn't even updated yet
for v3.1.

---

### Post by GTar on 2006-07-01
Yeah I noticed they don't seem to have 3.2 support in the CDT downloads section.

Tried almost all the mirrors avaliable and continually get the same problem. I've only downloaded the Runtime Binaries as opposed to the entire SDK, could that be an issue?

---

### Post by mlind on 2006-07-01
[QUOTE=GTar]Yeah I noticed they don't seem to have 3.2 support in the CDT downloads section.

Tried almost all the mirrors avaliable and continually get the same problem. I've only downloaded the Runtime Binaries as opposed to the entire SDK, could that be an issue?[/QUOTE]


I don't know, I selected whole CDT thingy from update view. Try installing it to
alternative location instead of eclipse/plugins.

---

### Post by tonyr on 2006-07-02
I downloaded Callisto w/o problems.  On the Eclipse.org download page I selected 
**I Build C/C++ Applications**, downloaded the Eclipse tarball, used the Software
Updates selector, selected Callisto Discovery and Eclipse Project Updates, and used the 
US servers  **ibiblio** and **Eclipse Foundation Callisto Mirror 2**.

I went through the first CDT tutorial.  The editor is very flakey on my machine (really slow,
stops to think for awhile at weird intervals), but I'm an Eclipse newbie and haven't 
explored how to tune it.

---

### Post by Ziggurat on 2006-07-04
"An exception ocurred while downloading feature from ***. Do you want to retry?

I get this trying to install anything using Callisto


Anybody having this error??

I download and install eclipse 3.2 yesterday, not using synaptic.

Thanks

---

### Post by mlind on 2006-07-04
[QUOTE=Ziggurat]"An exception ocurred while downloading feature from ***. Do you want to retry?

I get this trying to install anything using Callisto


Anybody having this error??

I download and install eclipse 3.2 yesterday, not using synaptic.

Thanks[/QUOTE]

I've never had errors with plugin download, have you tried this from clean & new
workspace ?

---

### Post by Ziggurat on 2006-07-04
I solve the problem. I wasnt using sun java vm. I have it installed but it wasnt selected as default.

---

