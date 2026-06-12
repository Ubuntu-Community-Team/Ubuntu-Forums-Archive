---
title: "Running Mono apps"
date: 2004-11-18
forum: General Help
---

### Post by Enygma on 2004-11-18
I had mono running no problems before I had to do a reinstall (bad hard disk).
This time I did an upgrade in Synaptic and let it upgrade everything right after the install. 
The only problem is that mono isn't working properly now.  

I can compile and run a simple "Hello World" program so it's there alright but any time I try to run something like Tomboy or Blam or Monodevelop or Monodoc I get an error like this:

```

** (./MonoDevelop.exe:4619): WARNING **: Could not find assembly System, references from /usr/lib/monodevelop/bin/./MonoDevelop.exe (assemblyref_index=1)
     Major/Minor: 1,0
     Build:       5000,0
     Token:       b77a5c561934e089

cannot open assembly ./MonoDevelop.exe

```

another one:

```

** (browser.exe:4630): WARNING **: Could not find assembly monodoc, references from /usr/share/dotnet/monodoc/browser.exe (assemblyref_index=1)
     Major/Minor: 1,0
     Build:       0,0
     Token:       0738eb9f132ed756

cannot open assembly browser.exe

```

Has anyone got any ideas? 
It's weird cause this worked perfectly before.

Thanks!

---

### Post by mattisking on 2004-11-18
Yes, you need to install the package monodoc which is heavily utilized in many of these packages but not part of the core mono installation.

---

### Post by Enygma on 2004-11-18
I have monodoc installed, I get the second error when I try to run it. 
I've installed every mono package I could find in the repositories.

I'm going to try to compile it from source to see how that goes.

---

### Post by jdong on 2004-11-18
From my experience Hoary repos have better working mono. I'm running hoary and monodevelop works perfectly.

---

### Post by Enygma on 2004-11-19
Did a re-install and it worked fine, must be something to do with the smart update.

---

